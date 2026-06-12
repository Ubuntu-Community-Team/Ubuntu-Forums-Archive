---
title: "help with ubuntu server 8"
date: 2009-06-04
forum: Server Platforms
---

### Post by nellyneils007 on 2009-06-04
Hi everyone, im a newbie to ubuntu server, i downloaded and installed ubuntu server 8 successfully but my query is, does it have a GUI, coz right after rebooting it returned with the terminal (tty1), if there's a GUI, how do i switch to it?
 Secondly, during installation, it never prompted me for a root password, it only asked for a normal user, how do i access the server as root?
 Thank you guys.


Dell Optiplex 360n
1GB Ram
160 GB HDD
Ubutntu Server 8

---

### Post by jonabyte on 2009-06-04
To install a gui desktop for Ubuntu Server, login and type:

```
sudo apt-get install ubuntu-desktop 
```

---

### Post by jonabyte on 2009-06-04
Here is more information about Root and Ubuntu:

[https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo")

You can always use use:

```
sudo
```

before each command to run it in superuser/root/admin mode.

---

### Post by theozzlives on 2009-06-04
root is disabled, use sudo

---

### Post by cdenley on 2009-06-04
By the way, for future reference, there is no such thing as ubuntu 8. You probably mean ubuntu 8.04.

8.04 = released April 2008
8.10 = released October 2008
9.04 = released September 2009
9.10 = ETA October 2009

See the pattern? The version number is [2 digit year].[2 digit month].

---

### Post by nellyneils007 on 2009-06-05
Hi Guys,
 Thank you soo much for your swift and really helpful replies; i really appreciate and hope that God will reward you kindly.
>          Here is more information about Root and Ubuntu:

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

You can always use use:

     Code:
     sudo 
that link was so help full. i got everything about the Sudo feature.

---

