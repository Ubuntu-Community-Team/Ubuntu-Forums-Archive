---
title: "preconfigured Samba/print/share server"
date: 2008-02-06
forum: Server Platforms
---

### Post by Sasquatch2000 on 2008-02-06
I know Ubuntu comes with a built in "LAMP" installation. 

What I'm wondering is if there is any way to set it up to do a typical office type server install. This would include file sharing (Samba), printer sharing, and other typical tasks. 

The intended target of this is for home or small office networks which have outgrown peer to peer file sharing, but are not rich enough for a dedicated Windows server. 

This install should be simple, easy, and thorough. 


Anything like this exist to date?

---

### Post by freebeer on 2008-02-06
I'm not aware of any "out-of-the-box" solutions, but it is definitely do-able.  What you've described is what I've set up here.  I'm running a Ubuntu server (actually the desktop flavor) with Samba as a Primary Domain Controller which replaced my old NT 4 box.  You may not need Samba to act as a PDC, so the set up will be easier.

---

### Post by Sasquatch2000 on 2008-02-06
Whatever works best. This will be with XP and Vista clients.

How does it work if NOT as a PDC?

---

### Post by freebeer on 2008-02-06
My primary reason for using a PDC is to set appropriate permissions for access to files and certain printers.  For instance, I have  a color printer that I don't want certain people to use, so with the PDC permissions set up properly, someone logging in without the correct permission doesn't have access to that machine.  Or in the case of files, I have certain folders, such as, say, Accounting, that I don't want available to just anyone.  Members of the Administrator group and Accounting, etc. do have read/write privileges in that folder.  You can achieve this through other means, but by doing it through Samba, it works well for me.

If you don't need that level of security, then you can configure Samba with simple shares.  Less planning and less complexity is the result.

---

### Post by Iowan on 2008-02-06
Which flavor Ubuntu server are you running? [howtoforge.com]("http://www.howtoforge.com/howtos/linux/ubuntu") has several permutations of Ubuntu Samba servers, [ Here]("http://www.howtoforge.com/ubuntu-home-fileserver") is one.

---

### Post by UbuWu on 2008-02-06
[ClarkConnect]("http://www.clarkconnect.com/") does most of this out of the box.

---

### Post by UbuWu on 2008-02-06
And here is a great guide for setting it up yourself on ubuntu:

[http://www.rrcomputerconsulting.com/view.php?article_id=3](http://www.rrcomputerconsulting.com/view.php?article_id=3)

---

### Post by freebeer on 2008-02-06
> **Iowan said:**
> Which flavor Ubuntu server are you running? 

My PDC is running 7.10.  My home machine, running Samba as well, but not as a PDC, is 6.04.  I started with 6.04 trying to learn the ropes before I rolled it out on an actual production machine.  The 6.04 has been solid (so has the 7.10 machine, btw) so I never felt any need to upgrade.

---

### Post by Sasquatch2000 on 2008-02-07
Thanks.

Any others? Any word on if this might happen in the future? 

A simple server setup would greatly benefit them into making inroads against Windows.

---

### Post by AlistairH on 2008-02-08
> **UbuWu said:**
> [ClarkConnect]("http://www.clarkconnect.com/") does most of this out of the box.

As does [SME Server]("http://www.smeserver.org/") which, unlike ClarkConnect, is free.

If you are comfortable getting your hands dirty though, I'd suggest doing it in Ubuntu. You'll learn a lot more (as I still am) and you'll be able to configure your machine exactly how you want it rather than the way SME server does it.

That said, I've installed a number of SME Servers for clients and they've all been rock solid. I've only ever had to reboot them once and that was when I was upgrading the OS and taking the opportunity to do the hardware as well.

---

### Post by Sasquatch2000 on 2008-04-11
How does Ubuntu 8.04 "Hardy Heron" change any of this?

---

### Post by Deathrend on 2008-04-11
I'm a major windows-server person.. so I still set all of my file/folder/printer permissions using Active Directory.  Once you learn Samba, it's not to bad, but it takes a learning curve if you're not ready for it.

My two main (Personal) servers run Ubuntu Server 8.04.  One hosts LAMP/IMAP/RoundCube/Webmin Cluster, while my other hosts VMWare Server/iSCSI target/Samba/Media Server/Network storage/ with an external eSATA Araay with give or take 9 TB of storage.

With that said, I've been using Ubuntu for a month or so, I've used Linux off and on for around 8 years, however I've works for mostly Windows only places, as well as one old school NetWare LDAP *shutter*.

If I can do it, anyone can, once it's going, it works so well, just a matter of getting it there.  Google is your friend, if it involves Ubuntu, someone's tried it, and wrote a how to, just a matter of finding it :)

---

### Post by andguent on 2008-04-13
Mini howto (partially to show how easy it is to do :) ):

Note: This was partially typed up from memory, not actually tested.

sudo su
apt-get install samba
mv /etc/samba/smb.conf /etc/samba/smb.conf.orig
nano /etc/samba/smb.conf

Paste the following text in, and then do a Ctrl-X, Y, Enter
```

[global]
   workgroup = MSHOME
   server string = 
   wins support = yes
   dns proxy = no
   log file = /var/log/samba/log.%m
   max log size = 1000
   syslog = 0
   panic action = /usr/share/samba/panic-action %d
   security = user
   encrypt passwords = true
   passdb backend = tdbsam
   obey pam restrictions = yes
   invalid users = root
   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n *passwd:*password\supdated\ssuccessfully* .
   load printers = yes
   printing = cups
   printcap name = cups
   printer admin = @lpadmin
   socket options = TCP_NODELAY
   domain master = yes
[homes]
   comment = Home Directories
   browseable = no
   valid users = %S
   writable = yes
   create mask = 0700
   directory mask = 0700
[printers]
   comment = All Printers
   browseable = no
   path = /var/spool/samba
   printable = yes
   public = no
   writable = no
   create mode = 0700
[print$]
   comment = Printer Drivers
   path = /var/lib/samba/printers
   browseable = yes
   read only = yes
   guest ok = no
[Shared]
   comment = Shared to all
   path = /opt/samba/shared
   writable = yes
   guest ok = yes
   create mask = 777
   directory mask = 777
   force user = nobody
[Private]
   comment = Private share
   path = /opt/samba/private
   guest ok = no
   writable = yes
   valid users = @private
   force group = private
   create mask = 770
   directory mask = 770
```

mkdir -p /opt/samba/shared /opt/samba/private
adduser bob
adduser sally
adduser roger
groupadd private
adduser bob private
adduser sally private
adduser bob lpadmin
adduser sally lpadmin
adduser roger lpadmin
smbpasswd -a bob
smbpasswd -a sally
smbpasswd -a roger
/etc/init.d/samba restart
exit

Tada, all done. This should give you a functional but basic file sharing server. It doesn't do any domain logons, and doesn't allow the users to change their samba share passwords easily. However it does give you a public share and a private share, plus all of your home directories.

Definitely look in the original smb.conf for tips and other options, or review all of the good howto's already posted.

---

### Post by foolano on 2008-04-13
You can set up a PDC configuration in just a few minutes using the last available packages of [eBox]("http://www.ebox-platform.com") in Ubuntu Hardy.

It automatically creates a samba PDC configuration using an LDAP backend. You will be able to manage it via a simple web interface to perform tasks such as: adding and deleting users.

eBox also ships a whole bunch of other modules to deploy more network services.

---

### Post by gsiliceo on 2008-04-13
You can vote to change this in ubuntu using the brainstorm page, theres already an idea voting to make samba easier. Please vote here.
[Improve file/folder sharing experience (Samba)]("http://brainstorm.ubuntu.com/idea/403/")

---

