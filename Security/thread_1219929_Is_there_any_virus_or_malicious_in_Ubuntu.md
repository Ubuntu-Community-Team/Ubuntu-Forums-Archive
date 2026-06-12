---
title: "Is there any virus or malicious in Ubuntu?"
date: 2009-07-22
forum: Security
---

### Post by karumudi7 on 2009-07-22
I am new to ubuntu. I want to know that is there any viruses or any thing that can trouble us? like viruses,trojan horses,malicious programs in windows.:confused:

---

### Post by HermanAB on 2009-07-22
No, Ubuntu is secure by default.  It is completely up to you how malicious you want to be.

---

### Post by RetroX on 2009-07-22
Windows has viruses because any EXE can have any access to any part of the system it wants.  Windows lets EXEs run as "System" and then they have full access to the computer.

In Ubuntu, whenever a program tries to access the package repository, any system files, any root-owned files, etc., it asks you to type in your password, making it fully safe.  So unless you type in your password for a random prompt, I think you're fine.

Plus, while I hate to say this, only about 4% of all computer users use Linux and UNIX-based OSes.  I'm sure that most of that 4% use Ubuntu, but still, that isn't very big.  What would be incentive for a hacker to create a virus for 4% of all people when they could create a virus easily for 90% of all people?

You'll never get a virus in Ubuntu; the only way your computer will mess up is if you make it that way, so just be careful and you'll be fine.

---

### Post by TuckLive on 2009-07-22
Give this a good read:

[[COLOR="Blue"]Ubuntu Security[/COLOR]]("http://ubuntuforums.org/showthread.php?t=510812")

---

### Post by sasho_zl on 2009-07-22
In answer to your question " Is there any virus or malicious in Ubuntu?" the answer is yes, there are malicious programs written for linux, but most of them are old and the exploits that they were using have being patched for a long time ( this is true for the worms and viruses).
You have to be careful when installing programs from untrusted sources because it is easy for somebody to compile statements that would make damage to your system and to add them to a program. For example yesterday I almost compiled a program that included "rm -rf /" in its source code.
Also you should be aware of programs called "rootkits" that can compromise your entire system and put it under the command of someone else. This is one more reason to be careful with installing programs from sources outside of the repositories. Even software downloaded from a the site of a trusted vendor could contain malware if the server has being hacked and the programs replaced. That is why it is always a good idea to match the checksums of the program you download with the checksum provided by the software vendor. This is the reason those checksums exist. If even one byte of the program has been changed the checksum will not match! Also the checksums are usually kept on a different servers with the idea that a hacker would have to hack them also to change the checksum.

---

### Post by koenn on 2009-07-22
> **RetroX said:**
> 

Plus, while I hate to say this, only about 4% of all computer users use Linux ...  What would be incentive for a hacker to create a virus for 4% of all people when they could create a virus easily for 90% of all people?

eternal fame, loads of prestige, a huge ego boost, ...

---

### Post by philcamlin on 2009-07-22
no there are no viruses for linux :popcorn:

only proof of concet ones

---

### Post by khelben1979 on 2009-07-22
Some known viruses for Linux:

[Linux malware - Wikipedia]("http://en.wikipedia.org/wiki/Linux_malware#Viruses")

---

### Post by bodhi.zazen on 2009-07-22
I am closing this thread now as I think the question of quite broad and has been answered.

In general, when you ask such general questions it indicates you need to get to know how security works on Linux.

TuckLive gave you a fine link to get started.

The answer to your question "Is there any virus or malicious in Ubuntu?" is "yes"

That statement is well qualified by sasho_zl 9and others, thank you).

yes I have seen Linux cracked , most often due to weak passwords, disabling a password for sudo, physical access, and serves (VNC is probably most common these forums).

The default installation, out of the box, is quite secure, and Ubuntu has outlasted both Vista and OSX where the 3 systems have been compared head-to-head.

See also : [USN list | Ubuntu - Security alerts]("http://www.ubuntu.com/usn")

---

