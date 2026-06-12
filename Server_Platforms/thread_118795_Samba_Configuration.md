---
title: "Samba Configuration"
date: 2006-01-17
forum: Server Platforms
---

### Post by Cubicegg on 2006-01-17
Hi List,

I've been playing around with Swat which I am finding more difficult to use than manually editing the samba.conf files.

I'm trying to make my Linux machine the pdc on our network and to create 2 users that can log in from any 1 of 2 xp desktops.  Now when trying to find the pdc XP says it cant find it. However when trying to connect to the linux machine via \\ipaddress i can get in to the machine but I need to assign user name and passwords to different shares and I'm having problems trying to do this - can anybody help on both these topics?

thanks James

---

### Post by pochonox on 2006-01-17
i got the same problem :(

---

### Post by SlowJet on 2006-01-18
[QUOTE=Cubicegg]Hi List,

I've been playing around with Swat which I am finding more difficult to use than manually editing the samba.conf files.

I'm trying to make my Linux machine the pdc on our network and to create 2 users that can log in from any 1 of 2 xp desktops.  Now when trying to find the pdc XP says it cant find it. However when trying to connect to the linux machine via \\ipaddress i can get in to the machine but I need to assign user name and passwords to different shares and I'm having problems trying to do this - can anybody help on both these topics?

thanks James[/QUOTE]




Samba as a pdc is a Windows NT 4.0 box. It does not understand XP ntfs 1.3.

You can only use share mode , not user mode.
You must have a W2k3 server and use the ldap to tie into the w2k3 directoy service to logon on from XP machines.

I have set up samba 10 times on different installs and had it working on dapper on 2 boxs with a windows xp (all sharing) and now with 3.0.21a, the two 2 dapper boxes will not share with each other, nor will the share show on Xp, only the computer sever name which is denied access.

I am thinking it is depper dapper problems than samba, but only a reinstall later will verify that.

SJ

---

### Post by LordHunter317 on 2006-01-18
[QUOTE=SlowJet]Samba as a pdc is a Windows NT 4.0 box. It does not understand XP ntfs 1.3.[/quote]It understands NTFS just fine.

> You can only use share mode , not user mode.This is also just plain wrong.  security=share is slated for removal in Samba 4.x, **and should not be used at all in 3.x**

> You must have a W2k3 server and use the ldap to tie into the w2k3 directoy service to logon on from XP machines.No, wrong.

> I have set up samba 10 times on different installs and had it working on dapper on 2 boxs with a windows xp (all sharing) and now with 3.0.21a, the two 2 dapper boxes will not share with each other, nor will the share show on Xp, only the computer sever name which is denied access.Which should tell you that you should be asking for help, not posting mistruths.

Anyrate, the OP needs to post his smb.conf to get anyhelp.  As for SWAT, don't bother, it's crap.

---

### Post by bluefrog on 2006-01-19
samba.org menu "by example"

james

---

### Post by Iowan on 2006-01-19
[QUOTE=Cubicegg]... I need to assign user name and passwords to different shares and I'm having problems trying to do this - can anybody help on both these topics?

thanks James[/QUOTE]
The [b]valid users =[b] parameter will let you assign users to shares.

---

### Post by LordHunter317 on 2006-01-20
No, you shouldn't be doing that.  You should use filesystem permissions to control access wherever possible.

---

