---
title: "Access remote hard drive from another computer"
date: 2010-01-12
forum: Security
---

### Post by Toast2120 on 2010-01-12
Good evening. Been looking to get a way to solve this problem so here I go.

Computer 1:
runs Linux and ONLY Linux
has multiple hard drives popped in the loading bays
One of those drives stores the OS
The other drives exist simply for backup

Computer 2:
Windows 7 64 bit
Average Windows installation, nothing tweaked
likes cookies (the chocolate kind)

What I want to do is pull data from any of the hard drives attached to my Linux box from my Windows machine. I have been moving small amounts of data from the drives to my OS drive and those parts share easily, but I want to move away from that method to move large amounts of data at the same time.

I have tried using Samba as it is used for file sharing between systems and that I have to give my Windows box permission through Samba. 

Trick is, I'm not sure where to start, though I have an idea and wanted to know if this is the right track before I start editing my file system. This is the method I was looking into:

[http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/domain-member.html#machine-trust-accounts](http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/domain-member.html#machine-trust-accounts)

So far I have tried modifying some comments in /etc/samba/smb.conf

[Hard drive]
   comment = Samba server's Hard drive
   browseable = yes
   read only = no
   locking = no
   path = /media/566B543040F6DFF3 
   guest ok = yes

include = /home/samba/etc/smb.conf.BASIL

usershare allow guests = yes

Any ideas?

---

### Post by adam814 on 2010-01-12
Seems like that would do the trick, but to me it sounds like overkill.  I would think the purpose of having your own domain would be to centralize authentication and set group policy and such.

It seems like samba alone in a workgroup should be sufficient for just sharing files at home, but that's just my opinion.  Going the domain route is certainly a valid option.

---

### Post by Jive Turkey on 2010-01-13
```

[Hard drive]
comment = Samba server's Hard drive
browseable = yes
read only = no
locking = no
path = /media/566B543040F6DFF3 
guest ok = yes

include = /home/samba/etc/smb.conf.BASIL

usershare allow guests = yes

```
I would change that to look like this:
```

[Hard drive]
comment = Samba server's Hard drive
browseable = yes
read only = no
locking = no
path = /media/566B543040F6DFF3
guest ok = no

```
I'm not sure what that "include =" directive is doing there.  You should check to see what's in that file ending in ".BASIL"

An alternative to samba would be to install Filezilla on the Windows computer and use it to connect via sftp (ssh server on linux), if your aim is to grab a huge amount all at once this might work better.

---

### Post by Sarmacid on 2010-01-13
There's a program called WinSCP that can be used to copy files from and to a Unix/Linux server running ssh.

---

