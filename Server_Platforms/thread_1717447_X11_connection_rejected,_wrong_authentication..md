---
title: "X11 connection rejected, wrong authentication."
date: 2011-03-29
forum: Server Platforms
---

### Post by wlraider70 on 2011-03-29
I'm ssh'ed into my headless server from a VMbox.

Below is a more detailed output the short version is I have the wrong authentication for x11

"X11 connection rejected because of wrong authentication"


```


luke@vbuntu:~$ ssh 10.10.10.2
luke@10.10.10.2's password: 
Linux media.zion.com 2.6.32-29-generic #58-Ubuntu SMP Fri Feb 11 19:00:09 UTC 2011 i686 GNU/Linux
Ubuntu 10.04.2 LTS

Welcome to Ubuntu!
 * Documentation:  https://help.ubuntu.com/

Last login: Tue Mar 29 18:44:41 2011 from 10.10.10.102
luke@media:~$ sudo gedit

(gedit:13202): Gtk-WARNING **: cannot open display: 
luke@media:~$ exit
logout
Connection to 10.10.10.2 closed.
luke@vbuntu:~$ 
luke@vbuntu:~$ ssh -X 10.10.10.2
luke@10.10.10.2's password: 
Linux media.zion.com 2.6.32-29-generic #58-Ubuntu SMP Fri Feb 11 19:00:09 UTC 2011 i686 GNU/Linux
Ubuntu 10.04.2 LTS

Welcome to Ubuntu!
 * Documentation:  https://help.ubuntu.com/

Last login: Tue Mar 29 18:53:20 2011 from 10.10.10.102
/usr/bin/xauth:  error in locking authority file /home/luke/.Xauthority
luke@media:~$ sudo gedit
X11 connection rejected because of wrong authentication.

(gedit:13301): Gtk-WARNING **: cannot open display: localhost:10.0
luke@media:~$ 


```


I've gotten some similar messages through VNC but I can get picture in a VNC

---

### Post by volkswagner on 2011-03-29
Whenyou ssh inyou need to specify xsession.

Try:
```
 ssh -X 10.10.10.2
```

That is a capital X.

---

### Post by wlraider70 on 2011-03-29
I get the same error with that code

---

### Post by volkswagner on 2011-03-29
Ah, I remember similiar issues.  I don't recall offhand. 

Does it happen when you have a monitor attached to the server?

I think one step was to set autologin.

---

### Post by wlraider70 on 2011-03-29
Thanks for your help.

I found the answer here [http://ubuntuforums.org/showthread.php?t=22558](http://ubuntuforums.org/showthread.php?t=22558)


short version 
sudo rm ~/.Xauthority

---

