---
title: "scp and commandline completion: ssh keys?"
date: 2006-10-27
forum: Server Platforms
---

### Post by mrbill on 2006-10-27
Hello,

I am using Ubuntu 6.0.6 LTS. I'm unable to retrieve the scp version, can't even find which package it's in (not very good at The Art of Managing the Package Manager - what was wrong with tarballs anyway?;).

Here's an observation:

when I want to copy a file and use commandline completion for the filename, and keep pressing TAB after the filename is completed,  I get the contents of the CWD (this is the checked out copy of a CVS module):

[email]exocat@exocat:~/soekris/sysroot.soek[/email]ris/etc$ cp mfsmount
CVS/            rc.conf.local   ssh/            tmp
mail/           rndc.key        sysctl.conf     update

But when I use scp, I get someting like this:

[email]exocat@exocat:~/soekris/sysroot.soek[/email]ris/etc$ scp mfsmount
|1|79EM2i8+DBU2czqrj+vLqsVZgE4=|5v7nk4S9dItRiCYOC28U9CvNVdE=:
|1|axc/SU6JE73gdmo7gfs8/K/lsug=|YsUpdc3J7ICHY8eai2w4OjtmCMs=:
|1|/B/q17mDzD1fDS4oyYGurSk300w=|b2SAmlDiyG/GLjYFBR+EmBlnjSU=:
|1|CkYleOUz9rkuiQY8DInBqKCHaBY=|YailNZ5jgPGEJWSqhpG5hn0dLVQ=:
|1|G3zuOLyNj3/Kfy0v/l/kvJLVMlw=|lC8bLiQVuPSLcRAROt5uQufiod8=:
|1|lYSCXK8Zc71M3avF3WwLtaBYCSM=|NimWfBM5sxnCQJTBiEKKVzgXovM=:
|1|rGLmpcz1Yb49CL31DvBXSx7ItF4=|oJNxhxDDlTrufm9UmN+BiT6R+l4=:
|1|vjhjT8xVsack9MPaoXk4wid3ChA=|QAqvsX7tngvViTn3VXZ05hordhI=:
|1|ztbmczpXX/SdA/evaCUMo9kLkaI=|qBC7She0HeKQ/75eGytlSSFW+j0=:
CVS/
mail/
rc.conf.local
rndc.key
ssh/
sysctl.conf
tmp
update

Looks like the keys ssh uses, but I'm not an expert. Is this a security bug? In any case, scp should not be giving away internal data like this (ssh displays "|1|" when commandline completion is done, but that's it).

Bill

---

### Post by mrbill on 2006-10-27
Bye the way, I removed "mfsmount" and a bunch of other files from the command output to keep the message short, but it was there inside the CWD. Another lesson in not to edit command output in submits. The bigger picture is still the same.

---

