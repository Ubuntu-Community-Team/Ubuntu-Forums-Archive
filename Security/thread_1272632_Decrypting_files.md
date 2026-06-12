---
title: "Decrypting files"
date: 2009-09-22
forum: Security
---

### Post by hotstepperk on 2009-09-22
hi. I'm having problems decrypting a file i'd encrypted using seahorse. I made a new PGP key, went through the process of setting it up and even managed to encrypt a simple .txt file (which made a new .pgp file) However, im trying to get it working with another ubuntu computer, so I exported my key and even signed the same .txt file and upon importing it to a friends computer, its still unable to decrypt the message. Its kept my key as a trusted key in his list but isn't able to decrypt it. 

Can someone please help me get the decryption working. I'd like to start using PGP to encrypt and send data to relevant friends, not so cause its sensitive, but because I can :)

---

### Post by Agent ME on 2009-09-23
What happened:
When you exported your key, it exported the public part of your key. (This is what is needed for someone to encrypt a file to you. This is what you give away to people freely.) In order to decrypt a file meant for you, you need the private part of your key. (This is the one that is meant for you alone. Whoever has this can decrypt files encrypted to you.)
_________

It sounds like you're using GPG wrong. You're thinking of GPG as symmetric encryption mistakenly: where you lock a box with your key, and give it to a friend who unlocks it with an identical key.

GPG mainly uses public key encryption, which works differently. In public key cryptography, you have a copy of your friend's public key. It's a special key that can only lock boxes. Only your friend has the corresponding private key which is needed to unlock the box.

To do this with Seahorse, you have a friend make himself a key on his computer, and export his public key and give it to you. You then encrypt a file with his key as a recipient, and make the file available to him. No one else but him can decrypt the file. In fact, you can't even decrypt it unless you set yourself as one of the recipients (some programs do this automatically).
_________

However, symmetric key cryptography (same key locks and unlocks) is sometimes useful. Maybe you want to send the file to a group of people, but you don't know who all of them are and the group could change in the future. The group might have a secret codeword it knows its files are encrypted by.

To encrypt a file by a password (which can be decrypted by the same password), type in a terminal "gpg -c *filename*" and type in the password.

---

### Post by Sarmacid on 2009-09-23
[Maybe this will help]("http://ubuntuforums.org/showthread.php?t=895038")

---

### Post by hotstepperk on 2009-09-23
Thanks. Finally got it working. I made my key-pair, gave out the public key and was able to send it out to others who encrypted files with my public key and I was able to open it with my private key. Also managed to sign and encrypt files with a friends public key and my private key.

thank you Sarmacid and AGENT ME

---

