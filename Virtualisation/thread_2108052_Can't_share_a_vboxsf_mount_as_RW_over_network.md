---
title: "Can't share a vboxsf mount as R/W over network"
date: 2013-01-23
forum: Virtualisation
---

### Post by N00b-un-2 on 2013-01-23
This may sound a little crazy, but essentially what I'm trying to do is extend the functionality of my Windows host by running a light headless linux server as a Windows service at boot and I'm ALMOST 100% there.

I have Debian Wheezy running as an Apple Filing Protocol (netatalk) server on top of Windows.  

I have the directory on my Windows host that I want to share, in this case C:\users\ryan\Share set as a virtualbox machine folder.

I've edited the Debian virtual machine's /etc/fstab to mount the share at boot which works fine.
I've double checked that the file permissions are correctly set to RW and are owned by the target user, in this case "ryan".

I've installed and configured all the requisite packages for netatalk and have properly configured the AFP server to share files.

The shares I create on the Debian machine are visible over the network and are accessible/mountable with my username and password.

The issue I'm running into though is that as long as the AFP server is configured to share a directory that is local to the Debian server, I have read/write access without any issues.

However, when I set the AFP share to the vboxsf machine folder, I can still access the share over the network with my username and password.  However, on any Mac computers on my network, when I mount the AFP share I get an error message that states:

> 
**MESSAGE FROM SERVER**
Something wrong with the volume's CNID DB, using temporary CNID DB instead.Check server messages for details. Switching to read-only mode.

at this point I'm stuck.  is it even possible to achieve this or is the cnid database going to throw an error (due to mismatch between vboxsf and ntfs perhaps?) and then default to read only access?

I guess another way to attack this issue would be to give virtualbox raw disk access to my hard drive, but from what I understand, this can't be done with the disk mounted by the host operating system.

---

