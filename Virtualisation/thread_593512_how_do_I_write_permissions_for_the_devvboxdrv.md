---
title: "how do I write permissions for the dev/vboxdrv"
date: 2007-10-27
forum: Virtualisation
---

### Post by Tucatts on 2007-10-27
Almost there. Now I am getting this. 

he VirtualBox kernel driver is not accessible to the current user. Make sure that the user has write permissions for /dev/vboxdrv by adding them to the vboxusers groups. You will need to logout for the change to take effect..
VBox status code: -1909 (VERR_VM_DRIVER_NOT_ACCESSIBLE

Many thanks!

---

### Post by bodhi.zazen on 2007-10-27
You need to add you user to the vboxuser group :

go to System -> Administration -> Users and Groups

Select the "Manage Groups" -> Scroll down to vboxusers -> select (click) the group vboxusers -> Click "Properties" -> tick off you user box

Close out Users an groups, 

Log off and back in.

---

### Post by Tucatts on 2007-10-27
Hey bodhi.zazen,
MANY THANKS for the info. Once I set permission it was smooth sailing. All set up. Gotta love this forum!
Tucatts

---

### Post by papatech on 2008-01-26
> **bodhi.zazen said:**
> You need to add you user to the vboxuser group :

go to System -> Administration -> Users and Groups

Select the "Manage Groups" -> Scroll down to vboxusers -> select (click) the group vboxusers -> Click "Properties" -> tick off you user box

Close out Users an groups, 

Log off and back in.

--Thanks! This has helped me too.

---

### Post by extant59 on 2008-03-22
i love you all. thank you :)

---

### Post by sayantandas on 2008-03-30
thanks a lot.
works a charm

---

### Post by TheLittleGuy on 2008-04-26
How haven't even been a member for 5 mins and already solved a problem thanks a lot

---

### Post by pcjunkie on 2008-04-27
Its no longer working in Hardy, The user groups other than your own are greyed out and cannot be configured.

[edit]

My bad...

It took about 2 minutes but the password dialog arrived. Fixed.

---

### Post by masterchief324@gmail.com on 2008-05-03
> **bodhi.zazen said:**
> You need to add you user to the vboxuser group :

go to System -> Administration -> Users and Groups

Select the "Manage Groups" -> Scroll down to vboxusers -> select (click) the group vboxusers -> Click "Properties" -> tick off you user box

Close out Users an groups, 

Log off and back in.

All of my groups are disabled. PLS HELP!!!:confused:

---

### Post by oboreruhito on 2008-05-04
> **masterchief324@gmail.com said:**
> All of my groups are disabled. PLS HELP!!!:confused:

Did you click the Authenticate button at the bottom right of the groups window?

---

### Post by dyrer on 2008-05-05
VirtualBox kernel driver not installed. The vboxdrv kernel module was either not loaded or /dev/vboxdrv was not created for some reason. Please install the virtualbox-ose-modules package for your kernel, e.g. virtualbox-ose-modules-generic..
VBox status code: -1908 (VERR_VM_DRIVER_NOT_INSTALLED).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}

 I have enabled user to vboxuser

---

### Post by bodhi.zazen on 2008-05-05
There is a bug with VirtualBox OSE

[https://bugs.launchpad.net/ubuntu/+source/virtualbox-ose/+bug/179807](https://bugs.launchpad.net/ubuntu/+source/virtualbox-ose/+bug/179807)

Workaround fro the moment is to remove (purge) the OSE and use the PUEL (closed source) edition.

---

### Post by agata94 on 2008-06-03
and it also helped me! :D thankss a loottt

---

### Post by biasedopiniondrummer on 2008-06-22
worked great for me 2! thanks!

---

### Post by blackened07 on 2008-11-03
> **bodhi.zazen said:**
> You need to add you user to the vboxuser group :

go to System -> Administration -> Users and Groups

Select the "Manage Groups" -> Scroll down to vboxusers -> select (click) the group vboxusers -> Click "Properties" -> tick off you user box

Close out Users an groups, 

Log off and back in.

thank u very much it worked instantly

---

### Post by philetus on 2008-11-03
You have to click on "unlock" the groups.

---

