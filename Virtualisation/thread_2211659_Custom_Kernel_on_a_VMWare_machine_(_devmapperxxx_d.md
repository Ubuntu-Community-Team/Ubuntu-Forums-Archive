---
title: "Custom Kernel on a VMWare machine ( /dev/mapper/xxx does not exist )"
date: 2014-03-17
forum: Virtualisation
---

### Post by judah2 on 2014-03-17
Hey ,
I've got a 12.04 Ubunutu machine , and I'm having issues when trying to update to a 3.12.13 Kernel...
For some reason whenever I use the 3.12.1 Kernel version , It works just fine , but 3.12.13 is giving me some serious issues...

It says :

```
Gave up waiting for root device.  Common problems:
 - Boot args ( cat /proc/cmdline)
    - Check rootdelay= (did the system wait long enough?)
    - Check root= (did the system wait for the right device?)
 - Missing modules (cat /proc/modules; ls /dev)
ALERT! /dev/mapper/xxxxx-root does not exist. Dropping to a shell!
```

And the weird thing is that It claims the file /dev/mapper/xxxxx-root does not exist, and when I try booting to my older kernel ( 3.5.x )
It works without any errors... ( I've tried searching for /dev/sdaX and I couldn't find them there either )

I've updated lvm2 and cryptsetup ( even though I've got nothing encrypted , just to make sure...) but I didn't get any progress...

I remember I used to have that kind of problem but the fix to it was to re-run the boot.<service_name> file right after the system boots, since It ran in a wrong order....

Is there anything I can do - Or should I just return to 3.12.1 ( or even go in the opposite direction ? )

Note : The machine sits in a network that has no internet connection , thus downloading and inserting new packages and installations could be a little rough...

---

