---
title: "New install and GUFW error"
date: 2016-03-06
forum: Ubuntu Development Version
---

### Post by sammiev on 2016-03-06
Hi Folks,

New install of Unity tonight and GUFW is no longer working.

---

### Post by MikeMecanic on 2016-03-06
No problem here Sammiev.  Import profile as usual with no incidence.

[PHP]System:    Host: u Kernel: 4.5.0-040500rc7-generic x86_64 (64 bit) Desktop: Unity 7.4.0
           Distro: Ubuntu 16.04 xenial[/PHP]

---

### Post by sammiev on 2016-03-06
Thanks, I can do everything from the command line anyways.

```
sudo ufw status verbose
[sudo] password for sam: 
Status: active
Logging: on (low)
Default: deny (incoming), allow (outgoing), disabled (routed)
```

Strange it works in all the other flavors of 16.04 but Unity.

---

### Post by MikeMecanic on 2016-03-07
> **sammiev said:**
> Thanks, I can do everything from the command line anyways.

```
sudo ufw status verbose
[sudo] password for sam: 
Status: active
Logging: on (low)
Default: deny (incoming), allow (outgoing), disabled (routed)
```

Strange it works in all the other flavors of 16.04 but Unity.


Unless you don't want to show them, I don't see any rules in the verbose?  If you have some rules and I guess you have, you should try to purge it and re-install GUFW.  
About the new command line to load the rules (import), did it work?

```
[LEFT][SIZE=3][COLOR=#000000][FONT=Georgia]sudo chmod 600...[/FONT][/COLOR][/SIZE][/LEFT]

```

---

### Post by sammiev on 2016-03-07
Check the md5sum again and tried a different usb stick with the same results. 

Download todays ISO and check the checksum with md5sum and installed to a new USB stick.

GUFW will not work with Unity at this time.

---

### Post by MikeMecanic on 2016-03-28
GUFW opens normally when adding the following packages (without them it won't open):

[HTML]Commit Log for Mon Mar 28 16:21:12 2016


Installed the following packages:
python-gi (3.20.0-0ubuntu1)
python-gobject (3.20.0-0ubuntu1)
python-gobject-2 (2.28.6-12ubuntu1)[/HTML]

All the best,

---

### Post by sammiev on 2016-03-28
> **MikeMecanic said:**
> GUFW opens normally when adding the following packages (without them it won't open):

[HTML]Commit Log for Mon Mar 28 16:21:12 2016


Installed the following packages:
python-gi (3.20.0-0ubuntu1)
python-gobject (3.20.0-0ubuntu1)
python-gobject-2 (2.28.6-12ubuntu1)[/HTML]

All the best,

Thanks Mike,

python-gobject (3.20.0-0ubuntu1) was missing.

Works so far! :)

---

