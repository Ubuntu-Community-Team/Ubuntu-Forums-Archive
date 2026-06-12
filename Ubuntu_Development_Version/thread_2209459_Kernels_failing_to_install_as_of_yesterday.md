---
title: "Kernels failing to install as of yesterday"
date: 2014-03-05
forum: Ubuntu Development Version
---

### Post by devin-a-hudson on 2014-03-05
Here is the pastebin of my terminal output: [http://pastebin.com/CfUc3ymr](http://pastebin.com/CfUc3ymr)

 This install of Ubuntu 14.04 dev was made about a week ago. I don't have any ppa's providing alternative kernels or other major package changes.

Would anyone know how to fix this issue?

Thanks.

---

### Post by zika on 2014-03-06
```
sudo apt-get update
sudo apt-get install -f
sudo apt-get dist-upgrade
```
Be carefull when answering to the question for the last command...

---

### Post by varunendra on 2014-03-06
Not sure why this should cause an error -
```
/usr/sbin/grub-mkconfig: 11: /etc/default/grub: **i915.i915_enable_rc6=1**: not found
```
..but try removing that entry from you /etc/default/grub file using a live CD/USB, then try what zika suggested above.

You may also have to do -
```
[s]sudo dpkg configure -a[/s]
sudo dpkg --configure -a
```
..from recovery mode > root shell, after removing the offending entry from the /etc/default/grub file.

---

### Post by ventrical on 2014-03-06
> **devin-a-hudson said:**
> Here is the pastebin of my terminal output: [http://pastebin.com/CfUc3ymr](http://pastebin.com/CfUc3ymr)

 This install of Ubuntu 14.04 dev was made about a week ago. I don't have any ppa's providing alternative kernels or other major package changes.

Would anyone know how to fix this issue?

Thanks.


```


  [B]sudo -i dpkg --configure -a


```



[/B]

---

### Post by devin-a-hudson on 2014-03-06
> **varunendra said:**
> Not sure why this should cause an error -
```
/usr/sbin/grub-mkconfig: 11: /etc/default/grub: **i915.i915_enable_rc6=1**: not found
```
..but try removing that entry from you /etc/default/grub file using a live CD/USB, then try what zika suggested above.

You may also have to do -
```
[s]sudo dpkg configure -a[/s]
sudo dpkg --configure -a
```
..from recovery mode > root shell, after removing the offending entry from the /etc/default/grub file.

These instructions seemed to have worked!  :)

Thank you, and everyone else that offered help  :)

---

### Post by varunendra on 2014-03-06
Glad it worked. :)

And Thanks for the feedback! It helps not only us build out confidence in a particular solution, but also helps others by indicating which of the suggested solutions worked. :)

**PS:**
If you really need that driver parameter, you should be able to add it again to grub now. Or [s]more safely[/s], you can write a .conf file in /etc/modprobe.d directory to load that parameter. That is usually an easier way, but may fail if the driver is loaded BEFORE the files in that directory are parsed. Let me know if you really need that parameter and wish to try the other method.

---

### Post by zika on 2014-03-07
> **varunendra said:**
> Glad it worked. :)

And Thanks for the feedback! It helps not only us build out confidence in a particular solution, but also helps others by indicating which of the suggested solutions worked. :)

**PS:**
If you really need that driver parameter, you should be able to add it again to grub now. Or more safely, you can write a .conf file in /etc/modprobe.d directory to load that parameter. That is usually an easier way, but may fail if the driver is loaded BEFORE the files in that directory are parsed. Let me know if you really need that parameter and wish to try the other method.I do find that it is easier and even safer to use parameters such as the one mentioned above in the kernel boot line because, once the need for it die or there is a change that should be made, it is much easier to change it in Grub (on boot) than to get stuck with it and have to do chroot ... Speaking from experience not just from the top of my (almost empty, old) head... ;)

---

### Post by varunendra on 2014-03-07
> **zika said:**
> it is much easier to change it in Grub (on boot) than to get stuck with it and have to do chroot..
Yup, I completely agree, that is an advantage in Grub boot line parameters. Besides, some parameters may not work with the .conf file method at all.

It is just usually easier to tell newbies how to boot with a live media and delete or modify a .conf file, than to explain how to get the grub menu > identify and edit the boot line, and boot. That, plus the two steps (edit /etc/default/grub + update-grub) Vs a single step (echo "..." | tee /etc/modprobe.d/file.conf) while creating it. :p

**PS:**
I had actually thought of removing the term 'safer' before posting, forgot it. Thanks, zika, for bringing it up. Going to correct it now. :)

---

### Post by zika on 2014-03-07
[QUOTE=varunendra;12949394That, plus **the two steps** (edit /etc/default/grub + update-grub) Vs a single step (echo "..." | tee /etc/modprobe.d/file.conf) while creating it. :p[/quote]
With sed (+ tee && etc) even that becomes one-liner...):P

---

