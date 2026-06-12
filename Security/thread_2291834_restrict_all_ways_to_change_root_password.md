---
title: "restrict all ways to change root password"
date: 2015-08-23
forum: Security
---

### Post by sh.nobahari65 on 2015-08-23
Hello everyone
I'm new with Ubuntu and I have an UBUNTU 14.04 server on an ESXi virtual machine that I need to send it as demo system somewhere, I need to restrict all ways to change root password and access source codes on the system.
after digging through internet I found below link that explain 4 methods to change root password:
[http://www.c-integration.com/blog/showpost.php/83-reset-linux-root-password-without-knowing-the-password](http://www.c-integration.com/blog/showpost.php/83-reset-linux-root-password-without-knowing-the-password)

Is there any other ways to access root privileges on UBUNTU system? and how to restrict them?

Thank you very much

---

### Post by TheFu on 2015-08-23
With physical access, any competent admin can gain root. If anyone has general sudo access, they have root.

So - if you don't want people to be able to ever gain root, then you must use whole disk encryption and do not allow anyone to have sudo.

OTOH, nobody there will be able to patch the system without a specialized sudo config and even with it locked down for just patching, a cleaver admin/person would be able to get root.

If you need perfect security from gaining root, that doesn't exist in a practical way.  If you just want to stop an average end-user from gaining it, 
* use whole disk encryption. This prevents average people from booting a live-environment, mounting the encrypted disk, using chroot to make the passwd file available for the passwd program to change and resetting the password. It is only a knowledge thing, not real security. You will have to give them the disk encryption passphrase regardless or the system will not boot.
* Setup the system for automatic patching. 
* Setup the system for automatic backups of the most critical files. Whenever encryption is involved, excellent backups are MANDATORY. It is hard to fix a disk that is encrypted using most current tools. I've never been able to fix a corrupt disk (logical or physical corruption) when it was encrypted.
* If the system is for 1 purpose, make that be the only thing that runs when the end-user logs in.  That means NOT running a full DE. You'll want a minimal X/Windows system that doesn't have any menu.

Normal Unix permissions can be used to restrict access to the code, but **don't put the source on the shipped system.** If it is all scripts, that can be very hard, since to run scripts, the user must be able to read them. Some languages have obfuscation tools or ways to compile into a binary.  It would be better, IMHO, to have a client/server setup and not allow any login access to the server at all. Only allow the client access to the server API, nothing more.

So - what is the program/application?  What is the architecture? Perhaps we can help with a different solution than you've considered so far?

---

