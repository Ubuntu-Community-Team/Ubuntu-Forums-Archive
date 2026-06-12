---
title: "Ubuntu is asking for the install disk, but It's been lost"
date: 2008-02-27
forum: Server Platforms
---

### Post by grittyminder on 2008-02-27
This has to be a silly problem with an easy answer but I can't seem to find anything...

I'm running Ubuntu Server 6.06.1 and I'm trying to install shorewall. The problem is that Ubuntu is asking for the install disk in order to proceed with the installation and I've lost the installation disk. The latest version of Ubuntu Server LTS seems to be 6.06.2. Downloading the iso for 6.06.2 and mounting it doesn't seem to work (Ubuntu seems set on wanting 6.06.1).

Any ideas?

P.S. I'm unable to use bittorrent or anything like that

---

### Post by igknighted on 2008-02-27
all you need to do is comment out the CD as an install source.  Open the file /etc/apt/sources.list (as root/sudo) in you editor of choice, and either comment out (put a # in front of the line) or delete the first line, which should be the CD.

---

### Post by tubezninja on 2008-02-27
Just curious: is there a reason why the CD isn't commented out by default?  I haven't really run into a situation yet where I need to go back to the original CD after a successful install.

---

### Post by az on 2008-02-27
> **scaredpoet said:**
> Just curious: is there a reason why the CD isn't commented out by default?  I haven't really run into a situation yet where I need to go back to the original CD after a successful install.

If you install using the alternate or the server cd, you use the text installer which uses a repository on the disk.  It doesn't use the same method as installing from the desktop cd.

It makes more sense to use local repos instead of remote ones.

---

### Post by grittyminder on 2008-02-27
Ahaha, how silly of me. Thanks a bunch for the answer! :)

---

