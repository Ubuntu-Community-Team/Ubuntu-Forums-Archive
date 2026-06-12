---
title: "Home File Server &amp; Win98"
date: 2008-10-24
forum: Server Platforms
---

### Post by Cosmin-Coral on 2008-10-24
I've recently set up an old box as a File Server at home.
I'm using a pretty basic smb.conf with a share that is deliberately open for all users.

My 2 XP boxes are happily connecting, but the only way I've managed so far to get the Win98 box to connect is to log in as guest (using map to guest = bad user & guest ok = yes). However while this allows Win98 to read all files & write to those that it put there, it can't write to those written from XP. (Presumably the guest account just does not have permission to write to a 'real' users files.)

In the pages I have read, many cover forcing Win98 to use non-encrypted passwords, but these appear to be older pages, as Samba obviously does use encrypted passwords these days. And the various changes I've tried have not helped.

Any suggestions as to what else I can try to authenticate Win98 (and loose the 'guest'?). I need to keep any visual changes on the machine to a minimum to avoid complaints from certain members of the family! ('What use is this Linux anyway?' ;))


smb.conf:
[global]
workgroupname = WORKGROUP
netbios name = Xray
encrypt passwords = yes
password level = 20
map to guest = bad user
hosts deny = ALL
hosts allow = 192.168.1. 127.0.0.1

[data]
path = /datastore
read only = no
browseable = yes
guest ok = yes
create mask = 0777
directory mask = 0777

---

### Post by hyper_ch on 2008-10-24
do you want to have the network shares as drive allocated that gets auto connected upon booting?

If not, install openssh server on the server and download [http://www.winscp.com](http://www.winscp.com) and use that to connect from win98 to the ubuntu ssh server using your username and password from the ubuntu server.

---

### Post by Cosmin-Coral on 2008-10-24
> **hyper_ch said:**
> do you want to have the network shares as drive allocated that gets auto connected upon booting?...Yes I do - it is doing so at present. It has to work as invisibly as possible ;). I guess a 'connect when the link is clicked' would work too though.

---

