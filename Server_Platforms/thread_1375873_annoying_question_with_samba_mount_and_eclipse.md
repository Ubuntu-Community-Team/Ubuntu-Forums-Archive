---
title: "annoying question with samba mount and eclipse"
date: 2010-01-08
forum: Server Platforms
---

### Post by jkarpago on 2010-01-08
Hi:

I have an ubuntu 9.10 server upgraded from ubuntu 9.04 server.
I have another computer, which is the computer I work. I have one folder shared with samba in my server and mounted in my work computer with cifs and fstab.
Before the upgrade I open a project in eclipse of the shared folder and worked great, but now everytime I save the file with eclipse and change to another file tab in eclipse ask me this: "The file 'file' has been changed in the filesystem. Do you want to overwrite the changes made in the filesystem?".
This question everytime I save a file, and is really annoying.
Why this new behaviour in ubuntu 9.10 server?.

---

### Post by ArsNatura on 2010-01-08
I have the same problem. Not only with Eclipse, with any editor.

This is my fstab line:
//192.168.1.250/data /media/Server cifs    auto,user=******,password=******,noexec,user,rw,iocharset=utf8    0    0

Any idea?

Thank you.

---

### Post by ArsNatura on 2010-01-11
up ;)

---

### Post by Harrison4 on 2010-01-29
It seems like you have to synchronize server system clock with yours.

To do this, just try to write in a console

ntpd -u ntp.ubuntu.com

You have to do this in both locations. If you're developing on Eclipse, try to check Refresh Automatically, on Preferences -> General -> Workspace

I use Zend 7.1 and Eclipse Galileo and this work for me. Hope this solution will help you

---

### Post by mvaldez on 2010-02-08
Hi. Maybe you are having the problem described in Ubuntu Bug 34813. That bug focus on gedit being unable to save a file in Windows or Samba shares mounted using cifs (not smbfs), but it also affects Eclipse and other editors.

[https://bugs.launchpad.net/gedit/+bug/34813](https://bugs.launchpad.net/gedit/+bug/34813)

It seems using the Ubuntu graphical interface to mount the share (which uses GVFS and FUSE) is a workaround but I don't think you can use that with Eclipse.

Also, using smbfs is another workaround, but as far as I know it is considered obsolete in favor of cifs.

I tried using sshfs (because in my network we no longer have Windows machines) but it has the same problem.

Sorry if this does not fix your problem, I know is very, very annoying working all day long with a dialog appearing every time you save or just change the window focus.


Regards,

Mario Valdez

---

### Post by mvaldez on 2010-12-19
Just an update. I no longer use Samba (cifs or smbfs) to mount the remote source code directory, now I use SSHFS. I don't know if the problem was fixed in SSHFS or in Eclipse, but I no longer have this issue since Eclipse 3.6 (I am using Eclipse PDT 2.2.0, 64-bits).


Regards, MV.

---

