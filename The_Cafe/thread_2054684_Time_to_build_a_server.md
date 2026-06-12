---
title: "Time to build a server"
date: 2012-09-07
forum: The Cafe
---

### Post by Gone fishing on 2012-09-07
I'm need a server to run a small network of PCs at the moment running XP. I want to run LDAP and SAMBA (Domain authentication for Windows and later Linux Authentication (slowly, slowly catchy monkey)), NFS, Squid and Probably Postfix with Courier IMAP and Squirrel mail and RAID1 probably, I'll probably run another box with pfsense as a firewall. 

The question is on what? I've used Opensuse in the past (and before anyone laughs it was very solid). I've also run FreeBSD, which I thought was great and the documentation is good, important if like me you a bit inexperienced and don't do this often, I tried Ubuntu server once but had stability problems when users logged on the authentication tended to freeze, but I would give it another go. However, Debian and centOS are appealing.

Please your thoughts.

---

### Post by SeijiSensei on 2012-09-07
I routinely build servers on CentOS.  Some of the software I use like [MailScanner]("http://www.mailscanner.info/") is well-packaged for RedHat-flavored platforms.  I also use packages like sendmail which Ubuntu frowns upon.  You will find that things are organized somewhat differently in the filesystem, and you'll have to get used to using yum and rpm rather than apt-get and dpkg.  

I started in the RH world and came to Ubuntu when I decided I wanted something that treated non-free software for the desktop more leniently than Fedora.  But for servers I stick with CentOS.  Having been fighting recently with the Ubuntu implementation of sendmail on a mail server running 12.04, I'm not in a hurry to switch over either.

RedHat and CentOS are much more likely to be found in server rooms than Ubuntu.  That's because RedHat has been supporting servers in enterprise settings since about 1996 or so.  (I'm not sure about Debian, though I'm betting it's less common as well.)

Install a copy of VirtualBox and build a few VMs with various server OSes.  See which you prefer.

---

### Post by Gone fishing on 2012-09-07
Thanks for the reply - CentOS is certanly towards the very top of my list, my experience with Ubuntu (Hardy I think) wasn't great. I'm also thinking about Sendmail as it's the default in FreeBSD, so I would be interested on your thought concerning Sendmail.

---

### Post by cariboo on 2012-09-08
> **Gone fishing said:**
> I'm need a server to run a small network of PCs at the moment running XP. I want to run LDAP and SAMBA (Domain authentication for Windows and later Linux Authentication (slowly, slowly catchy monkey)), NFS, Squid and Probably Postfix with Courier IMAP and Squirrel mail and RAID1 probably, I'll probably run another box with pfsense as a firewall. 

The question is on what? I've used Opensuse in the past (and before anyone laughs it was very solid). I've also run FreeBSD, which I thought was great and the documentation is good, important if like me you a bit inexperienced and don't do this often, I tried Ubuntu server once but had stability problems when users logged on the authentication tended to freeze, but I would give it another go. However, Debian and centOS are appealing.

Please your thoughts.

Your best bet to get your questions answered is to check out the [Server Platforms]("http://ubuntuforums.org/forumdisplay.php?f=339") sub-forum, most of your questions have already been answered.

---

### Post by CharlesA on 2012-09-08
> **Gone fishing said:**
> Thanks for the reply - CentOS is certanly towards the very top of my list, my experience with Ubuntu (Hardy I think) wasn't great. I'm also thinking about Sendmail as it's the default in FreeBSD, so I would be interested on your thought concerning Sendmail.
I just build a simple LAMP server on a Debian box. For what you want to do I would go for CentOS or Scientific tbh.

---

