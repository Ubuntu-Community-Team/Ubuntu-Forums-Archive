---
title: "OpenSSL or OpenPGP for files on usb drive"
date: 2012-03-12
forum: Security
---

### Post by jaz0nj4ckal on 2012-03-12
Folks:
I am trying to encrypt files on my USB flash drive. I am always losing them at school.

I am not looking for entire drive encryption, but only at the file level. I want it to ask a password when opening the file.

should I use OpenSSL or OpenPGP for individual file AES-256 encryption?

thank you.

---

### Post by ottosykora on 2012-03-12
> **jaz0nj4ckal said:**
> Folks:
I am trying to encrypt files on my USB flash drive. I am always losing them at school.

I am not looking for entire drive encryption, but only at the file level. I want it to ask a password when opening the file.

should I use OpenSSL or OpenPGP for individual file AES-256 encryption?

thank you.

gpg was easy to use earlier as there was very nice plugin to nautilus to encrypt decrypt with gpg just with right mouse click.

This feature should be now again available as stated here:
[http://ubuntuforums.org/showthread.php?t=1928660](http://ubuntuforums.org/showthread.php?t=1928660)

There is again a plugin called seahorse-nautilus and then all should work.
I did not test it myself so far, have 11.04 ubuntu still and this can use the old plugin still.

Note that while it is possible to make plain symetric encryption with pgp/gpg, it is in general used so that you encrypt it to a certain key and will then need the gpg and the private key on the target machine ready to be able to decrypt it.

To use just plain AES symetric encryption, there might be some more simple ways of doing it.

---

### Post by sudodus on 2012-03-12
I guess you want something that will work on most computers. One option is to have a boot stick with a persistent live system, another one to have a 'normal' installed system (but installed onto the stick). Then you can easily have the ***gpg*** software with or without any GUI enhancement and run pgp encryption.

If you learn the basic terminal commands options for gpg, you can also add ***gpg.exe*** and run it in windows 'dosprompt' (if you borrow a windows computer, that is already running).

---

### Post by jaz0nj4ckal on 2012-03-12
I found the following, which shows how to use SSL, but I didn't think SSL could encrypt files, but I have seen a few sources saying it could be used.

If you want the encryption to be platform independent, you can use openssl:
 
**Encryption:**
openssl aes-256-cbc -in attack-plan.txt -out message.enc


**Decryption:**
openssl aes-256-cbc -d -in message.enc -out plain-text.txt

would this be a viable solution for what I want?

---

### Post by sudodus on 2012-07-07
> **jaz0nj4ckal said:**
> I found the following, which shows how to use SSL, but I didn't think SSL could encrypt files, but I have seen a few sources saying it could be used.

If you want the encryption to be platform independent, you can use openssl:
 
**Encryption:**
openssl aes-256-cbc -in attack-plan.txt -out message.enc


**Decryption:**
openssl aes-256-cbc -d -in message.enc -out plain-text.txt

would this be a viable solution for what I want?
Late reply, but yes it is viable solution. Maybe because you added the question as an edit, which did not update the 'unread flag' for me. New posts (replies) are easier to observe.

Or you can use 7z (7-zip). One weak spot is the password. Use a long one, that is not found in a dictionary.

---

