---
title: "Hashing system info NOT ENCRYPT it"
date: 2008-03-12
forum: Security Discussions
---

### Post by carnagex420x on 2008-03-12
Ok, heres my problem i dual boot with all my music, pix, video, etc. on my linux part. alternatively on  the smaller part. is windows w/ a few games and i use the EXT2FS so i can access my media from linux obviously. i dont want to encyrpt my HDD but i wanted to hash as much user info and passwords as possible. i have a protected BIOS that boots straight to the HDD and requires auth. from grub. so the only way my system can be comprimised is by my HDD being removed. i use a program to encrypt files so the info i want safe is (and i dont keep files like WEB PSSWRDS, or have real sensitive data to encrypt my whole system). Plus i reallly dont want to reinstall again.

---

### Post by euler_fan on 2008-03-12
I'm not sure I understand what you want to do . . . do you mean replace your files by their hashes? If this is the case hashes are essentially one way (the good ones anyway). Ergo you will be replacing your files with a string of characters you can't hope to efficiently recover any information from.

If you mean how do you set of a secure container on the Linux side for storing your sensitive files but don't want to or need to encrypt everything, I would say to take a look at TrueCrypt as you can also move the container to your Windows partition and open them.

There are ways to encrypt your machine without encrypting the boot sector. This is a common topic of many threads. Most require backup-and-reinstall operations.

Good luck.

---

