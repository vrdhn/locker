locker
======

locker is a future proof way to leave text message, which can only
be retrieved by the person(s) knowing answert to several questions.

It requires:
1. openssl for encryption
2. sha1sum for passphrase generation
3. sh for execution

I think these are going to be around forever, and generated
locker files can be unlocked by anyone knowing all the answers.




Making locker
=============

    ./make-locker  passcode.locker.sh
	# openssl will be used for encryption
	# sha1sum will be used for making passphrase from answers.
	# Enter text to be protected terminated by single '.' at the end.
	The passcode is 12345678
	.
	# Protection Layer : 1 , Enter Question
	What is 5 + 5 ? ( Hint: it's not 10 )
	# Protection Layer : 1, Enter Answer
	55
	# Protection Layer 1 is finished.
	# Protection Layer 2 : Enter Question
	# or enter '.' to finish the locker.
	.
	# You have protected with 1 layer of encryption.
	# The locker file is saved in passcode.locker.sh
	
	
Decrypting locker
=================

	./passcode.locker.sh
	# openssl and sha1sum found. We are good to go.
	# Layer 1: Enter the answer to following question
	=> What is 5 + 5 ? ( Hint: it's not 10 )
	11
	# Layer 1 decryption failed. Please try again
	=> What is 5 + 5 ? ( Hint: it's not 10 )
	55
	# Correct answer. There are no more layers to decrypt. Here is the message:
	The passcode is 12345678
	
