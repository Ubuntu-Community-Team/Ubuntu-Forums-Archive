---
title: "Wine just keeps crashing."
date: 2009-07-18
forum: Wine
---

### Post by Askar450 on 2009-07-18
Has anyone here successfully got Wine 1.1.2x working with Ubuntu 9.04? I'm having an issue getting Wine to work without crashing on me, I've tried all 1.1.20+ version and 9.4+ ATI drivers they are not helping. The whole system crashes but I can still move my mouse, I've tried fresh installs and they do nothing... Wine crashes when its in a game for 10 seconds. If anyone has any ideas i'd appreciate it >.<.
CPU : AMD Athlon X2 64 2.6 GHz
RAM : DDR2x2 GBs
IGP : ATI Radeon HD 3200
OS : Ubuntu 9.04 32-bit

---

### Post by david_kt on 2009-07-18
> **Askar450 said:**
> Has anyone here successfully got Wine 1.1.2x working with Ubuntu 9.04? I'm having an issue getting Wine to work without crashing on me, I've tried all 1.1.20+ version and 9.4+ ATI drivers they are not helping. The whole system crashes but I can still move my mouse, I've tried fresh installs and they do nothing... Wine crashes when its in a game for 10 seconds. If anyone has any ideas i'd appreciate it >.<.
CPU : AMD Athlon X2 64 2.6 GHz
RAM : DDR2x2 GBs
IGP : ATI Radeon HD 3200
OS : Ubuntu 9.04 32-bit

This problem is due to graphic card, not wine/ubuntu 9.04.
You could try below:

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

Enable the accelerated ATI graphics driver in the 'Hardware Drivers' (System->Hardware drivers), then do:

```
sudo dpkg-reconfigure -phigh linux-restricted-modules-`uname -r`
sudo insmod /lib/modules/`uname -r`/volatile/fglrx.ko
```

Log out and log in. 

DK

---

### Post by Askar450 on 2009-07-18
Its telling me its not installed 
"Package `linux-restricted-modules-2.6.28.13-generic' is not installed and no info is available."

---

### Post by Askar450 on 2009-07-18
Nevermind I was typing it wrong but now the second command is telling me the fglxr file cannot be found, I "locate fglrx.ko and its in updates not updates folder not volatile

---

### Post by Askar450 on 2009-07-18
This is what I'm geting when I type in[FONT=monospace] [/FONT]sudo insmod /lib/modules/`uname -r`/volatile/fglrx.ko
insmod: can't read '/lib/modules/2.6.28-13-generic/volatile/fglrx.ko': No such file or directory
any ideas?

---

### Post by david_kt on 2009-07-18
> **Askar450 said:**
> This is what I'm geting when I type in[FONT=monospace] [/FONT]sudo insmod /lib/modules/`uname -r`/volatile/fglrx.ko
insmod: can't read '/lib/modules/2.6.28-13-generic/volatile/fglrx.ko': No such file or directory
any ideas?

Have you done this:

Enable the accelerated ATI graphics driver in the 'Hardware Drivers' (System->Hardware drivers)

?

DK

---

### Post by Askar450 on 2009-07-18
Yes that is the first thing I did.

---

### Post by david_kt on 2009-07-18
> **Askar450 said:**
> Yes that is the first thing I did.

Not sure why it is not available, may be try to install fglrx manually:

```
sudo apt-get install xorg-driver-fglrx
sudo dpkg-reconfigure -phigh linux-restricted-modules-`uname -r`
sudo insmod /lib/modules/`uname -r`/volatile/fglrx.ko
```

DK

---

### Post by Askar450 on 2009-07-18
Tried that already it says its there but I can't find it.

---

### Post by Askar450 on 2009-07-18
Now this is odd, I did a fresh install cause I thought maybe I messed something up, I copied the fglrx.ko from before the format I copy that in to the volatile folder and I ran the command but not it saying the same thing.
"insmod: error inserting '/lib/modules/2.6.28-13-generic/volatile/fglrx.ko': -1 File exists"
where is that file, I can't find it so how does it exist?

---

### Post by Rich43 on 2009-07-18
ati cards dont work as well as nvidia with wine due to poor drivers.

---

### Post by Askar450 on 2009-07-18
Yes, lol but I want a solution for this if you know any way of getting the fglrx.ko it would be greatly appreciated.

---

### Post by david_kt on 2009-07-18
> **Askar450 said:**
> Yes, lol but I want a solution for this if you know any way of getting the fglrx.ko it would be greatly appreciated.

Try:

```
sudo aticonfig --initial -f
```

and reboot. IF still could not solve, try my next post.
DK

---

### Post by david_kt on 2009-07-18
If still unsuccessful, may be you want to install from AMD website:

[http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.5&lang=English](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.5&lang=English)

The direct download link is here:
[https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-9-6-x86.x86_64.run](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-9-6-x86.x86_64.run)

The instruction to use is here:

[https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_cat95-inst.pdf](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_cat95-inst.pdf)

DK

---

### Post by Askar450 on 2009-07-18
I will say first Thank you for taking the time and helping me David, second I've done aticonfig --initial -f so I'll just jump to the next one. Aticonfig --initial -f only prolongs it but it still crashes I think we have progress though, lol it use to crash the system and the mouse would work now it crashes the whole thing XD.

---

### Post by Askar450 on 2009-07-18
I guess there is no solution to my problem ; ; I did not check the links before typing that up but I've already done that too the only thing it fixes is the flickering that comes from having compiz+wine together.

---

### Post by david_kt on 2009-07-18
> **Askar450 said:**
> I guess there is no solution to my problem ; ; I did not check the links before typing that up but I've already done that too the only thing it fixes is the flickering that comes from having compiz+wine together.

There is one way that you could try, i.e. to use opensource driver (not sure if it already come with the default installation of Jaunty).

[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

DK

---

### Post by Askar450 on 2009-07-19
Going to try this hopefully it works. >.<

---

