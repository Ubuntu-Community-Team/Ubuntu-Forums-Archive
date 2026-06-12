---
title: "Encrypted folder on USB drive that works with Windows and Ubuntu"
date: 2010-05-07
forum: Security
---

### Post by cipherboy_loc on 2010-05-07
My friend wants to have an encrypted folder on his 4GB USB attached flash drive, but sometime here in the near future I will help him dual boot Windows and Ubuntu. My question is this: Are there any encryption methods for folders (or we could make the folder a .zip archive and encrypt that) that are cross platform? The key would be stored on the flash drive, but it would need a password to access it. This way, if his flash drive gets lost, his private data is protected. 

I have one more question related to my friend's flash drive. He wants me to create a program (I was thinking a shell script) that would run when the flash drive gets plugged into a computer. This script will collect some data like user name of the user who plugged in the flash drive, the public and private ip address of the machine, the work group of the machine (Windows only), the hostname of the machine, and then send an email to my friend with that data. I have created the bash script, in case it gets plugged into a computer that run Linux, but now the issue is the Windows script/program and the auto running of the script/program. More specifically:

[LIST=1]
[*]How do you get the Windows script/program to run when the flash drive is plugged into a Windows computer? I have heard that unless you have enabled an auto run feature somewhere, a .ini file will be ignored.
[*]What program should I use to send the email from Windows? I would prefer something that either is portable (A.K.A. it does not leave settings on the computer on which it is run), or something that is installed by default on Windows systems XP through 7.
[*]How do I get the Linux script to run when it gets plugged into a Linux computer?
[*]Any ideas on how to create a Mac OS X startup script?
[*]I think I will be able to use most of the standard BASH commands on a Mac, but I still need to send the email. For Linux I will be downloading and compiling msmtp, but that leaves out Mac.
[/LIST]

Thanks in advanced for your help,

---

### Post by HermanAB on 2010-05-07
Here you go:
[http://www.aeronetworks.ca/luks-usb-howto.html](http://www.aeronetworks.ca/luks-usb-howto.html)
[http://www.aeronetworks.ca/LUKS-Mount-FreeOTFE.pdf](http://www.aeronetworks.ca/LUKS-Mount-FreeOTFE.pdf)

---

### Post by cipherboy_loc on 2010-05-08
Another related question: Is it possible to export my linux key to a format that allows me to encrypt/decrypt files encrypted with the linux key on windows?


--Cipherboy

---

### Post by euler_fan on 2010-05-09
An alternative to LUKS is [Truecrypt]("http://www.truecrypt.org/docs/"). It has a portable mode (I linked to the docs page) which looks like it meets your needs.

---

