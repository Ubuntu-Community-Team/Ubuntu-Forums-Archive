---
title: "security only updates"
date: 2005-04-21
forum: Server Platforms
---

### Post by King_Rocker on 2005-04-21
Hi

I'm thinking of trying out Ubuntu. I've done an install on a box so far without an internet connection.  I've looked around the wiki and this forum and I'm not quite sure about selecting/downloading security/bugfix only updates. I know that updates per se can be done through synaptic or through the 'apt-get update' command.

Currently my distro is mandrake 10.1 and I can access security/bugfixes updates alone for downloading. 

Does the synaptic package manager do the same (I cant see that it does offer a custom security/bugfix selection only.  I can see the following:  sections, status, alphabetic, custom filters, search history - but as I understand these relate to packages installed or to be installed - I want to know where to select security/bug fix updates only) or do I only use 'apt-get update'?

Cheers.

---

### Post by Leif on 2005-04-21
If you use the standard repositories you will only receive bugfixes and security updates by default. There is an update manager if you like doing things in gui, otherwise do "sudo apt-get update" and "sudo apt-get upgrade". New versions of packages do not get released in the standard repositories.

---

### Post by King_Rocker on 2005-04-22
Thanks for the repy Leif.

The 'penny dropped' this morning and I think I kind of answered my own question when I was writing it - but you have clarified it more so.

Thanks again.

---

