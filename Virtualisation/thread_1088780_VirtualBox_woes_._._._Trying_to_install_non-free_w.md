---
title: "VirtualBox woes . . . Trying to install non-free without any luck"
date: 2009-03-06
forum: Virtualisation
---

### Post by CheshireMac on 2009-03-06
Hey folks. I'm going insane trying to get VB running with USB, and I've tried all the HowTo's for the OSE version. Now I'm trying to get the non-free version installed, and I can't get it past the install. I keep getting the error:
```
compilation of the kernel module failed
```
I'm really interested in getting this running so I can use my iPod touch with my own computer. If anyone can help, I'd really appreciate it. Thanks.

---

### Post by Shazaam on 2009-03-06
Lets start fresh...
1. Get rid of all residual vbox files. Open terminal and run this-
```
sudo apt-get remove virtualbox --purge
```
2. If you haven't done so already install these...
 a. build-essential
 b. dkms
 c. headers=
```
sudo apt-get install linux-headers-$(uname -r)
```
3. Follow this guide to add the virtualbox repo and the key, then install Vbox...
[http://ubuntuforums.org/showthread.php?t=1074160](http://ubuntuforums.org/showthread.php?t=1074160)
4. Enjoy!

---

### Post by HermanAB on 2009-03-07
The trick is to compile your kernel.  That is the best way to ensure that your development environment is configured perfectly.  Following a reboot with your newly compiled kernel, installation of Virtualbox or VMware is a snap and let's face it, to any Real Geek, compiling the kernel is fun!

Google for kernel compile help or look at this:
[http://aeronetworks.ca/kernel-compile-howto.html](http://aeronetworks.ca/kernel-compile-howto.html)

Cheers,

Herman

---

