---
title: "mediascanner-service-2.0 using large amounts of CPU"
date: 2014-02-18
forum: Ubuntu Development Version
---

### Post by ubername on 2014-02-18
HI

Recently mediascanner-service-2.0 is consuming most of my CPU, seems to run constantly and creates massive log files in ~/.cache/upstart. (over 11Gb when I left it running while I was away!)

I don't know what the problem is (I have recently installed a 3TB hard drive but there is not much on it, and the problem does not seem to have started at the time of installing)

I can't find much on google to help (anything for that matter) and I don't seem to be able to kill the process. I have tried switching off logging in zeitgeist using the System Settings  'privacy and security' GUI to no avail.

Can anyone point me at something which would allow me to prevent it from running at all, or in some way configure it to only look at my home directory, for example.


Or indeed any help at all would be gratefully received!

---

### Post by mc4man on 2014-02-18
Best way -  (unless you have some use for it, it's Not on a default install
```
sudo apt-get purge mediascanner2.0 libmediascanner-2.0-0
```

---

### Post by ubername on 2014-02-18
Thanks, that has done the trick, I wonder how I ended up with it installed - don't remember manually installing it.

I now have another problem, which is that something else appears to be using lots of cpu - perhaps I was mistaken in attributing the cpu usage to mediascanner. It was certainly using  a lot, but I am still seeing lots of usage which htop can't account for.

But that's for another thread, after a bit more digging.

---

### Post by mc4man on 2014-02-18
> **ubername said:**
> Thanks, that has done the trick, I wonder how I ended up with it installed - don't remember manually installing it.

I now have another problem, which is that something else appears to be using lots of cpu - perhaps I was mistaken in attributing the cpu usage to mediascanner. It was certainly using  a lot, but I am still seeing lots of usage which htop can't account for.

But that's for another thread, after a bit more digging.
May have come in with some unity8 packages that have no real use in 14.04, check & see if unity8 is installed.
If so then you can remove it & then **CK**. autoremove to see what else can go..

---

### Post by WunNation on 2014-09-27
I ran into this issue with the media scanner libraries as well today on 14.04. 
The library was frequently spiking briefly, and seemed triggering 'apport' to run at 100% of my processor speed according to htop.
Following the above instructions and removing the libraries (and then rebooting), resolved the issue on my system.

As to causes....
I did an Ubuntu Software Update yesterday, uninstalled the 'pipelight' package, and I installed Clementine 1.2.3. 
I'm not sure which caused the change to the system that caused this error.

---

### Post by Elfy on 2014-09-27
If you have a current issue with 14.04 you need to post in the main forum - we moved onto 14.10 in here months ago

closed

---

