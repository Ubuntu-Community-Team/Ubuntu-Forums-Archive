---
title: "I need to setup a server.... no idea how... please help me...."
date: 2010-01-29
forum: Server Platforms
---

### Post by Thanh-BKK on 2010-01-29
Hello.

I need to setup something server-ish at my office and i have, plain and simple, no idea how to do it. This is the situation:

11 computers

All run Ubuntu 9.04 Jaunty

Each one has it's own, static, real IP (leased line) for internet

Each one has Samba installed

Each one has vsftpd installed

So far, each one had a flash drive to which the user of that computer could write and read, and me (admin) could do that as well via Samba (in the office) or FTP (from home/wherever by laptop). 

But now this is going to be reversed, meaning one of the computers (mine) will have one removable hard disk (formatted in NTFS for Windows compatibility), on it a bunch of folders representing the other 10 computers.

Now each one of the other 10 computers must have read/write access to ONE of those folders but NOT the others, if possible so with an individual password (not MY password!) 

And the 11th computer (mine) to which that drive is physically connected must have read/write access to ALL of those folders, if possible WITHOUT needing a password. 

I have no problem getting vsftpd going so now each of the machines has a launcher on the desktop that accesses their respective folder, however they all need to enter MY username and password, which is obviously not ideal. Also they have access to my entire machine that way, not just their folder.

Please help me, the server newbie, on getting this configured the right way. Samba or FTP doesn't matter. 

Kind regards.....

Thanh

---

### Post by lisati on 2010-01-29
One way to do it would be to set up users on the server that correspond to each of the machines, and edit the vsftpd.conf file to restrict each user to their home directory - if memory serves correctly the relevant setting is connected to chroot.

---

### Post by Thanh-BKK on 2010-01-29
Hi.

But that would not work because as mentioned the folders to be shared are on a removable drive - if i create users each one's home folder will be in the, well, /home folder....... 

Kind regards.....

Thanh

---

### Post by Iowan on 2010-01-29
[Here]("https://help.ubuntu.com/8.04/serverguide/C/index.html") is some server information. Sounds like you may be looking for [LDAP]("https://help.ubuntu.com/community/OpenLDAPServer").

---

