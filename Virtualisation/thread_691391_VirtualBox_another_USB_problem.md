---
title: "VirtualBox another USB problem"
date: 2008-02-08
forum: Virtualisation
---

### Post by sDoky on 2008-02-08
Hi fellas, I'm experiencing some difficulties running this awesome utility for my Ubuntu feisty fawn.

[ [IMG]http://www.imagehosting.com/out.php/t1565186_Screenshot.png[/IMG]](http://www.imagehosting.com/out.php/i1565186_Screenshot.png)

I've figured out that there's some package missing however I'm not sure. Anyone knows what does that mean???

---

### Post by Sunforge on 2008-02-08
I had a similar error in Gutsy when attempting to share USB with a virtual machine on Virtualbox, then I found this:

[http://www.virtualbox.org/ticket/747](http://www.virtualbox.org/ticket/747)

I don't run Feisty so can't confirm if the above will help you but it might be worth looking in your /etc/init.d/mountdevsubfs to check...

---

### Post by sDoky on 2008-02-08
> **Sunforge said:**
> I had a similar error in Gutsy when attempting to share USB with a virtual machine on Virtualbox, then I found this:

[http://www.virtualbox.org/ticket/747](http://www.virtualbox.org/ticket/747)

I don't run Feisty so can't confirm if the above will help you but it might be worth looking in your /etc/init.d/mountdevsubfs to check...

Thanks a lot, unfortunately it does nothing, those quotes for bash are probably correct, except for the 'domount'... (isn't it supposed to be just 'mount' ?! cuz it says: 'command not found' unless I'm supposed to do something else with it) However it makes no change, maybe just because I'm dull, who knows... I've figured out that the ```
/etc/init.d/mountdevsubfs.sh
``` script starts or stops the usbfs service according to the parameter. I've tried everything from that page...
Also - what version do you people have? the one from their web page or the OSE version??

---

### Post by Sunforge on 2008-02-08
If it helps I'm running 1.5.4 binary 64 bit on Ubuntu Gutsy 64 bit which might put me a little way from the average here. 

Unfortunately I'm no USB or script guru so it's unfortunate that the fix suggested didn't work for you.

---

### Post by jefferystone on 2008-02-09
I was getting this error:

 Could not load the Host USB Proxy Service (VERR_FILE_NOT_FOUND). The
 service might be not installed on the host computer.

Added the following lines to /etc/fstab:

```
#usbfs
none /proc/bus/usb usbfs devgid=46,devmode=664 0 0
```

---------

This worked fine for me.  Taken from [[COLOR="Blue"]**Message #40 here.**[/COLOR]]("http://ubuntuforums.org/showthread.php?t=341740&page=4")

Sincerely,

Jeffery Stone

---

