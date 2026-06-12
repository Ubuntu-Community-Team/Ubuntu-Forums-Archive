---
title: "xp drive letter"
date: 2011-01-21
forum: Server Platforms
---

### Post by robertrose6 on 2011-01-21
I would like my Ubuntu server to show up as a drive on my XP home machine. I have loaded samba on to the server but I can only get it to show as the printer and faxes under my work group. Can you guys help me out? Also is there a way to have my Ubuntu laptop to auto mount the server when I am on my home network?



Thanks

---

### Post by mikewhatever on 2011-01-21
"xp drive letter"- what's that about?

Have you configured the samba server? If not, look at the links below.
[https://help.ubuntu.com/10.04/serverguide/C/samba-fileserver.html](https://help.ubuntu.com/10.04/serverguide/C/samba-fileserver.html)
[https://help.ubuntu.com/6.06/ubuntu/serverguide/C/configuring-samba.html](https://help.ubuntu.com/6.06/ubuntu/serverguide/C/configuring-samba.html)

---

### Post by Thirtysixway on 2011-01-21
I do have a blog post about it

[http://noobbox.com/2009/04/auto-mount-samba-share-ubuntu-and-windows](http://noobbox.com/2009/04/auto-mount-samba-share-ubuntu-and-windows)

---

### Post by CharlesA on 2011-01-22
You probably need to define a share first, then just use the "map network drive" feature on the XP box.

---

### Post by robertrose6 on 2011-01-22
Ok so I got the server to show up on XP but now I don't have permissions to access the samba share.Now the user name on the xp is different then the user name on the share but i am not sure if that makes a differences.

---

### Post by CharlesA on 2011-01-22
It does.

You need to have the same username/password unless you want to have to punch in the credentials each time you want to access that share.

---

### Post by Morbius1 on 2011-01-22
At the moment we don't even know if you set up your samba shares to require a username and password from the client. For all we know you set up guest shares and the password prompt is a Linux permissions issue. Why not post the output of the following commands so we can see how your shares are set up:
```
testparm -s
```
```
net usershare info --long
```

---

