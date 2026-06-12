---
title: "Error About Home Dir Permissions After Setting Up NFS"
date: 2007-12-02
forum: Server Platforms
---

### Post by betes on 2007-12-02
Hi all-

I followed the instructions in this thread:
[http://ubuntuforums.org/showthread.php?t=249889&highlight=nfs+howto](http://ubuntuforums.org/showthread.php?t=249889&highlight=nfs+howto)
to get NFS file sharing set up between my desktop and laptop.  That involved changing my /etc/exports file to give read-write permission to the laptop.  This is the line from the /etc/exports file:

/home 192.168.1.1/24(rw,no_root_squash,async)

Now when I reboot and log in on the desktop I get this error message:
"User's $HOME/.dmrc file is being ignored. this prevents the default session and language from being saved. File should be owned by user and have 644 permissions. User's $HOME directory must be owned by user and not writable by other users."

Here's another thread from someone with the same error message,
[http://ubuntuforums.org/showthread.php?t=390539](http://ubuntuforums.org/showthread.php?t=390539)
 but the thread linked in the answer is over my head.  I can't tell if it relates to my situation at all.

Can anyone tell me if the error message is related to the NFS (I'm just assuming it is because it started about the time I set up the NFS) and/or what can be done to fix it?

-Thanks for everyone's help

---

### Post by HermanAB on 2007-12-02
Well, you are overloading your local home directory with a distant home directory - do you really want to do that?

I'd just mount the distant directory as something generic like /data or whatever.  To me, the home directory is too important to have it subject to the instabilities of a network and all the configuration head-aches that will cause.

---

### Post by betes on 2007-12-02
> **HermanAB said:**
> Well, you are overloading your local home directory with a distant home directory - do you really want to do that?

I'd just mount the distant directory as something generic like /data or whatever.  To me, the home directory is too important to have it subject to the instabilities of a network and all the configuration head-aches that will cause.

I'm a beginner at this so I might be mistaken, but I don't think I am overloading my local home directory.  I'm exporting my home directory from my desktop (which is the /etc/exports file line from my OP).  I didn't mention in my original post that I am mounting the shared file in a generic location on my laptop (called /shared).  The error message comes on my Desktop, which is sharing its /home directory, not on the laptop, which is mounting it.

---

### Post by betes on 2007-12-04
This is a bump, but one with purpose, which is to ask, is this the correct forum for this thread?  Is NFS considered a server?  Perhaps it belongs under networking?

---

