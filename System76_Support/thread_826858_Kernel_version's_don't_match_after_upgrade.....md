---
title: "Kernel version's don't match after upgrade...."
date: 2008-06-12
forum: System76 Support
---

### Post by EmilyRose on 2008-06-12
Last night I ran upgrade to get some of the security updates. As I'm on dial up I do this most nights, run the upgrade then repeat the next night... After updating yesterday it said I needed to reboot, and when I finally got around to it, I get this error: 

"WARNING: the kernel version (2.6.22-14-generic) defined in /usr/src/linux/include/linux/version.h does not match the currently running kernel (2.6.24-19-generic) The cause of this problem is an incorrect kernel source path. Please check that /usr/src/linux points to the right tree. The cause of this is usually a missing or unconfigured kernel source tree (and sometimes an incorrect directory or symbolic link).

However, proper /boot/config-2.6.24-19-generic was found."

And then it obviously doesn't get past this... please help!!

---

### Post by thomasaaron on 2008-06-12
Please post the output of:

cat usr/src/linux/include/linux/version.h

---

### Post by EmilyRose on 2008-06-12
How? I can't get it to boot up past the above error... I'm posting off my old desktop...

---

### Post by EmilyRose on 2008-06-12
Ok. Take that back, I got in with the old 2.6.22-14-generic kernel... its slow and wierd... but when I type that command in it says:

#define LINUX_VERSION_CODE 132630
#define KERNEL VERSION(a,b,c) (((a) << 16) + ((b) << 8 ) + (c))

---

### Post by thomasaaron on 2008-06-12
Not sure what to do with that. :oops:

Probably the best thing to do would be to re-install the current kernel. That should re-define the symlink that is causing the problem.

What is the output of...
uname -r

---

### Post by EmilyRose on 2008-06-12
heh... well erm, how would I go about re-installing the kernel? I'm definetly going to need help with that... would it be easiest to just re-install the 8.04?

... logging in with 2.6.22-14-generic uname-r gives just that... but on bootup grub gives me several options:


Ubuntu 8.04.1, kernel 2.6.24-19-generic
Ubuntu 8.04.1, kernel 2.6.24-19-generic (recover mode)
Ubuntu 8.04.1, kernel 2.6.24-18-generic
Ubuntu 8.04.1, kernel 2.6.24-18-generic (recover mode)
Ubuntu 8.04.1, kernel 2.6.24-17-generic
Ubuntu 8.04.1, kernel 2.6.24-17-generic (recover mode)
Ubuntu 8.04.1, kernel 2.6.22-14-generic
Ubuntu 8.04.1, kernel 2.6.22-14-generic (recover mode)
Ubuntu 8.04.1, memtest86+

I havent tried all of them, but I know the default (2.6.24-19-generic) doesn't work, in normal or recovery mode and that 2.6.22-14 does (in either), which is what's supposedly in /usr/src/linux/include/linux/version.h so... yeah. 

Oh, umm.. if I were to finish updating the system, is it possible this might get fixed? I could always run into the library and update everything...

---

### Post by thomasaaron on 2008-06-12
You can't really upgrade your hardy install from your gutsy install. So I don't think that will work.

---

### Post by EmilyRose on 2008-06-12
Ok, so I've found that I can actually get to a the command line in 2.6.24-19-generic... but I don't know what to do in there :D I think I might be able to upgrade at hte library in 2.6.24-19 too in the recovery mode, but I'm not entirely sure... it'd be worth a try anyhow... 

Oh, and I tried er... erasing all the random wierd crap in /version.h (since it didn't seem to make much sense... and this old system has nothing in it)... but it didn't help :( Still have the same error, though I now get nothing when I cat it :D Don't know if thats an improvement though...

---

### Post by ChameleonDave on 2008-06-12
If you can get to the command line on the computer that you want to fix, and the internet is working, then you should be able to use apt to get the right kernel installed.

```
sudo apt-get update
sudo apt-get install --reinstall linux-headers-2.6.24-19-generic linux-image-2.6.24-19-generic linux-restricted-modules-2.6.24-19-generic linux-ubuntu-modules-2.6.24-19-generic
sudo apt-get purge linux-headers-2.6.22-14-generic linux-image-2.6.22-14-generic linux-restricted-modules-2.6.22-14-generic linux-ubuntu-modules-2.6.22-14-generic
```

---

### Post by thomasaaron on 2008-06-13
Right.

But, I am unsure of one thing? It looks like this might of happened in the middle of a kernel upgrade.

Your best first attempt at fixing this might be...
sudo apt-get update && sudo apt-get --assume-yes dist-upgrade

It may complete the hosed upgrade and fix any screwed up symlinks, etc...

---

### Post by EmilyRose on 2008-06-13
Hmm... well, I'm at the library now, where I *should* be able to get online... however, its not auto-connecting on boot up... and I don't know how to do so from the command line... if somebody can walk me through it, that'd be great. I know theres a proxy server I have to go through too, which I'd forgotten about...

---

### Post by thomasaaron on 2008-06-13
When you get to a command line, try:

sudo ifdown eth0
sudo ifup eth0

Hopefully that will get you online. However, didn't you say you were using a dialup modem? If so, it might not work. I'll have to research how you might get online from a dial-up from the command line. It can't be fun.

EDIT: Actually...

sudo pppconfig

...might do the trick. Look at this...
[http://www.debianadmin.com/setting-up-dial-up-connection-in-ubuntu.html](http://www.debianadmin.com/setting-up-dial-up-connection-in-ubuntu.html)

---

### Post by EmilyRose on 2008-06-13
Hmm... well neither pon nor wvdial seem capable of dialing either of the modems i have (one used to work in 7.10, but doesn't in 8.04, the other is a serial modem with usb-serial adapter that didn't work in 7.10, but did in 8.04...)... so i don't know. could i download the updates from this computer and then move them over somehow? Otherwise... what are my choices from here... could i re-upgrade from 7.10 to 8.04??

---

### Post by thomasaaron on 2008-06-13
Try re-upgrading to Hardy with a CD.

Boot into your 7.10 kernel. Insert a 8.04 CD, and follow the directions here...
[http://ubuntuforums.org/archive/index.php/t-764918.html](http://ubuntuforums.org/archive/index.php/t-764918.html)

Best,
Tom

---

### Post by EmilyRose on 2008-06-13
*happy dance* 

Ok, so I finally figured out my modem situation - turns out I was using the wrong stinking port (ttyS0 vs ttyUSB0)!! So, once I got that figured out pon worked beautifully! And so, 3.5 hours later, after running both thomasaaron and chamelaondave's codes, I'm back in buisiness!! TONS of thanks to both of you!!

 :happy dance:

---

### Post by hjj5899 on 2008-06-13
> **EmilyRose said:**
> Last night I ran upgrade to get some of the security updates. As I'm on dial up I do this most nights, run the upgrade then repeat the next night... After updating yesterday it said I needed to reboot, and when I finally got around to it, I get this error: 

"WARNING: the kernel version (2.6.22-14-generic) defined in /usr/src/linux/include/linux/version.h does not match the currently running kernel (2.6.24-19-generic) The cause of this problem is an incorrect kernel source path. Please check that /usr/src/linux points to the right tree. The cause of this is usually a missing or unconfigured kernel source tree (and sometimes an incorrect directory or symbolic link).

However, proper /boot/config-2.6.24-19-generic was found."

And then it obviously doesn't get past this... please help!!

:)  Yes, i agree with you .

---

