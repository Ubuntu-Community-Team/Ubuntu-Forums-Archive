---
title: "Samba share - file permissions from windows Domain"
date: 2009-03-21
forum: Security
---

### Post by mattyb_53 on 2009-03-21
Pardon me for being a bit new here.
Ive just setup a new Ubuntu installation and have successfully hooked her up to a Windows 2003 domain.

Ive mounted a new drive and also been able to read, write and execute from XP, Vista and Mac machines. (a bit of a mix I know!!)

My problem is, when i right click on a file or folder in the share from a windows machine (be it vista or xp) I can set permissions (eg, a domain user or group with say modify permissions, or read only).
However, when I go to "Apply" the settings, the new users and/or groups ive added drop off the list and im left with "Everyone", "MACHINE\Administrator" -> the default Ubuntu users.

How do I fix this problem? what step have i missed?

---

### Post by HermanAB on 2009-03-22
Well, it depends on whether the server is Linux or Windows - not clear from your description.  The valid users and groups will be whatever exists on the server.

Cheers,

Herman

---

### Post by mattyb_53 on 2009-03-23
Well, the domain controller is the Windows 2003 box and the Ubuntu server is a client of the domain.

Do I have to sync my Ubuntu box with the domain to get the users and groups to work?

---

### Post by koenn on 2009-03-23
you need extended posix acl, the standard unix file modes aren't sufficient for what you are trying to do

you install posix acl (don't remember the name of the package, try a search), then mount the relevant partition with option acl.

[http://users.telenet.be/mydotcom/howto/linuxsbs/samba4.htm](http://users.telenet.be/mydotcom/howto/linuxsbs/samba4.htm)

---

### Post by mattyb_53 on 2009-03-24
Thanks koenn.
Ill have a crack at that this afternoon and get back to you.
Ive seen a lot of documentation but not a lot of guides for dummies like me!:p

---

