---
title: "Reading a LUKS partition"
date: 2008-09-01
forum: Security
---

### Post by desm on 2008-09-01
I encrypted a partition under Debian. I now use Ubuntu and don't have debian installed any more. I get the following error upon running cryptsetup:

Failed to setup dm-crypt key mapping.
Check kernel for support for the aes-cbc-plain cipher spec and verify that /dev/sdb5 contains at least 133 sectors.
Failed to read from key storage
Command failed: No key available with this passphrase.

And yes, I acknowledge the stupidity of my mistake. Is there any way I can read the partition and get the data off?

---

### Post by mrsteveman1 on 2008-09-01
what does the luks header of this partition say?

sudo cryptsetup luksdump /dev/sdb5

---

### Post by desm on 2008-09-02
Version:       	1
Cipher name:   	aes
Cipher mode:   	cbc-plain
Hash spec:     	sha1
Payload offset:	1032
MK bits:       	128
MK digest:     	ee 47 50 c2 4c db 89 47 fa 28 96 a5 4d f1 9e af cc dc dd 81 
MK salt:       	3b 2f 2b 4b a8 48 c6 55 14 d5 af 9f d0 5c 9a 2c 
               	99 dd 72 0b b8 97 39 0d 59 f7 41 37 71 5d 9f 88 
MK iterations: 	10
UUID:          	d62ffb64-b7f1-4577-8de2-8e2e03a96da0

Key Slot 0: ENABLED
	Iterations:         	87346
	Salt:               	09 9c 5f 40 d5 7c 35 2a b6 54 4e 31 10 53 c4 01 
	                      	29 38 6b 8d f6 79 28 45 01 17 c8 8d 77 69 72 84 
	Key material offset:	8
	AF stripes:            	4000
Key Slot 1: DISABLED
Key Slot 2: DISABLED
Key Slot 3: DISABLED
Key Slot 4: DISABLED
Key Slot 5: DISABLED
Key Slot 6: DISABLED
Key Slot 7: DISABLED

---

### Post by mrsteveman1 on 2008-09-02
hmmmmkay.

There apparently is no aes-cbc-plain module in Ubuntu hardy, if there ever was. I do see aes-generic and aes-i586, and there is a cbc module

My best guess would be to modprobe aes-generic or aes-i586, along with cbc, and see if that is enough to make it work. If not the only thing i can think of to do would be to use it on another system and move the files.

If it is just giving the error because it expects a module that has been renamed, it might be possible to just edit the header. I'll play with my system and see what i can find out.

---

### Post by desm on 2008-09-03
I tried again today, and it just worked. So I'm not entirely sure what happened there, but I don't have a problem any more under debian or ubuntu.
Thanks for the help all the same!

---

