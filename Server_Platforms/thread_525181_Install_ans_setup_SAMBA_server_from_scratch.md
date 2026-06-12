---
title: "Install ans setup SAMBA server from scratch"
date: 2007-08-14
forum: Server Platforms
---

### Post by switch13 on 2007-08-14
I have installed Ubuntu Dapper Drake 6.06 on my pc at home, which has no internet connection.
Now my question is the following. How do I successfully install SAMBA with smbldap tools with user authentication ect.

I have freshly installed Ubuntu, then downloaded samba 3.0.25b tar.tar package, installed it with...
./configure
make
make install
I seemed to install with no problems, but when I want to start SAMBA there is no way of starting it.
/etc/init.d/samba start
does'nt do anything, because there is no samba executable in init.d folder.
It's like it never really installed it.
I always started samba with that command.

Can someone please tell me what am I missing or doing wrong?
Can you please try to give me a detailed tut on how to install samba with no internet connection.

I have done it about 5 years ago, but can't remember how I did it.
I don't have a problem with setting up the smb.conf file and profiles.
Just with installing SAMBA and getting it to work. :confused:

Your help would be greatly appreciated!!
Thanx.

---

### Post by wjp.reg on 2007-08-14
I´m puzzled as to why you would not install samba and all components/dependencies using synaptic or apt-get and the ubuntu install disk?

Without an internet connection, how do you propose to receive updates?

Here´s a wiki for setting up a samba server [https://help.ubuntu.com/community/SettingUpSamba]("https://help.ubuntu.com/community/SettingUpSamba")

---

### Post by switch13 on 2007-08-14
I don't need to do any updates or anything... it's just for having a server at home where I can add users to, and share files from for users.
Don't even try to understand.
It's just for backup and other purposes.

How do I install samba from the CD? It needs a internet connection.

Is there a way to install samba without a internet connection????

Please try to help me!

---

