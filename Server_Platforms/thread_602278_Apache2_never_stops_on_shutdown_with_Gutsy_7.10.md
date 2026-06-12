---
title: "Apache2 never stops on shutdown with Gutsy 7.10"
date: 2007-11-04
forum: Server Platforms
---

### Post by Railsbuntu on 2007-11-04
Hello,

Yesterday I noticed that on my 7.10 Ubuntu Server, Apache2 does not shut down when I issue the command:
```
sudo shutdown -P now
```

When I issue this command, all the daemons shut down, and when it is the turn of Apache, dots are printed on the screen endlessly and then the shutting down does not happen.

However, issuing the following works:
```
sudo /etc/init.d/apache2 stop
```

That is a recent problem, and I don't recall what I could have installed that could hurt apache in such way.

---

### Post by digitalzen on 2007-11-04
Hey Railsbuntu,

I'm having all sorts of problems with my Apache2 also. I'm thinking somethings borked with it and 7.10....

```
sudo /etc/init.d/apache2 stop
``` wont work for me either and im still serving pages i tried to uninstall apache...

---

### Post by Railsbuntu on 2007-11-05
A little update. Actually I was wrong, even if I stop the apache server by hand, then issue the shutdown command, it still won't stop.

I need to press ctrl+Alt+Del, then I get:
```
Control-Alt-Delete pressed
httpd (no pid file) not running

blablabla
```
And the computer reboots.

What is going on with apache? :confused:


EDIT: I have recently installed Citadel on my server, could it mess up my apache?

---

### Post by inphektion on 2007-11-05
I had apparmour'd apache and then it wouldn't shut down.  I had to allow it more areas.  Not sure if they is related or not but if so then put apparmour in learning mode for apache.

---

### Post by Railsbuntu on 2007-11-05
It seems that citadel and apache are trying to use the same ports, thus giving all this trouble. I will report once it is fixed.

---

### Post by jimbojones on 2007-11-05
How did you install Citadel?  I had problems with the init.d citadel script and it would not stop the citserver properly, hanging my whole system when I would try to reboot or shutdown.  I was unable to get a resolution with that script and have sense installed Citadel via the EZ Install and it works fine now.

---

