---
title: "NIS masterserver configuration problem"
date: 2005-05-17
forum: Server Platforms
---

### Post by _Pete_ on 2005-05-17
I have followed the instructions from here:

[http://www.ubuntulinux.org/wiki/SettingUpNISHowTo](http://www.ubuntulinux.org/wiki/SettingUpNISHowTo)

After doing the server setup I got errors like this:

petriai@machine:~$ ypcat passwd
ypcat: can't get local yp domain: Local domain name not set

root@machine:~ # ypcat passwd
ypcat: can't get local yp domain: Local domain name not set

What can be wrong ?

---

### Post by alastair on 2005-05-17
I've been setting up a new server at work and NIS is one of its roles. I thought I had it done but had not tested it. I just did.

Some points :

the NIS domain name is stored in :

/etc/defaultdomain

On the server, once things are configured i.e.

/etc/ypserv.securenets
/etc/ypserv.conf

Make sure you create the maps and push them out i.e.

cd /var/yp
make

Or all at once :

(cd /var/yp ; make)

Seems to work for me.

---

