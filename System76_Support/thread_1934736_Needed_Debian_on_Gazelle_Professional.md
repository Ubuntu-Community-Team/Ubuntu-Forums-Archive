---
title: "Needed Debian on Gazelle Professional"
date: 2012-03-02
forum: System76 Support
---

### Post by rmflagg on 2012-03-02
Hi everyone,

   I just got my Gazelle Pro yesterday and one of the things that I need to have is Debian installed on the machine.  Everything installs fine until the nvidia drivers.
   After the installation, I followed the instructions on the Debian wiki about installing them and I also found a script that auto-installs everything needed.  After rebooting, about 1/2 way into the boot sequence, I get a black screen with a blinking cursor and goes no further.

   Does anyone out there have any experience with Debian on the newest Gazelle Pros?

Thanks,
RMFlagg

---

### Post by Therion87 on 2012-03-03
It's not an issue with Gazlle, the drive install isn't complete. I've had this issue before. Boot to run level 3, and run nvidia-xconfig and reboot that should get you going. If the package isn't installed and you can connect to the internet search for it with apt-get and install and run it.

---

### Post by rmflagg on 2012-03-09
> **Therion87 said:**
> It's not an issue with Gazlle, the drive install isn't complete. I've had this issue before. Boot to run level 3, and run nvidia-xconfig and reboot that should get you going. If the package isn't installed and you can connect to the internet search for it with apt-get and install and run it.

Well, I gave this a shot, but no luck.  All that I get is a blinking cursor and an otherwise blank screen.

The video card in the Gazelle Pro is a nVidia GeoForce GTX 560M.  Does anyone have any luck getting this card to run with Debian?

---

### Post by mchauber on 2012-03-09
Boot the system into runlevel 3 and run the following command:

```
# lsmod|grep nouveau
```if it lists the nouveau mod, then run the following command:

```
# rmmod nouveau
```Then check /etc/modprobe.d/blacklist.conf and make sure that it contains the following line:

```
blacklist nouveau
```After that, do a reboot and let us know how that goes.

HTH


BTW.  Which Which version of Debian and which kernel are you running?

---

### Post by BBQdave on 2012-03-09
> **mchauber said:**
> BTW.  Which Which version of Debian and which kernel are you running?

I was thinking the same. If trying to use debian 6 (kernel *linux 2.6.32*), that new machine will not be supported.

You could try Debian 7 (testing) which has newer kernel *linux 3.x* and support for newer hardware.
Or, Debian 6 and back-port to newer kernel *linux 3.x.*

---

### Post by rmflagg on 2012-03-09
Yes, I was trying to use the 2.6 kernel of Debian Squeeze.  I will tryout Debian 7 and see how that goes. 
I shall return!

---

### Post by mchauber on 2012-03-10
The thing that sticks out to me is that you said you found a script that does the install for you.  While there's not necessarily anything wrong with that, I have to wonder how the script was written.  Was the script written for a specific kernel?  Are you running the same kernel that the script compiled for?

Every time your kernel gets updated, you'll need to create a mod for that specific kernel, else the kernel will not load the nvidia driver.

If the problem is truly with the nvidia mod not being loaded, then it won't be an issue of what version of Debian you are running, but could very well be what kernel you are running and what kernel your mod was compiled for.

The following link provides the best set of instructions I've seen for getting the nvidia driver up and running on Debian, and if followed correctly, it Just Works(tm).  Following these instructions also kills off the nouveau driver (which conflicts with the nvidia drivers, and will keep it from running unless you either disable it or rip it out all together):

[http://wiki.debian.org/NvidiaGraphicsDrivers#non-free_drivers](http://wiki.debian.org/NvidiaGraphicsDrivers#non-free_drivers)

If you are able to login to your system (booting into level 3), then any problems you may (but probably don't) have with newer hardware would be easily spotted in /var/log/.  You've probably already looked, but I'm just sayin'...  I doubt that going to a pre-release is going to solve the issue because I know for a fact that the nvidia drivers work fine with Debian 6 (providing the mod was installed and built correctly).

HTH

---

### Post by HunkirDowne on 2012-03-20
> **rmflagg said:**
> Yes, I was trying to use the 2.6 kernel of Debian Squeeze.  I will tryout Debian 7 and see how that goes. 
I shall return!

Getting straight to my point, should I install the System 76 Driver to distros other than Ubuntu?  What about: Mint (Ubuntu-derived, not LMDE)? Debian? OK, now how about LMDE? OpenSUSE (or other non-Debian derivatives)?

I too have a Gazelle Professional and installed Debian.  I just checked this thread out and may try the video drivers thingy at some point.  I may even try installing Aptosid as this would be a 'neat' package to get the newer kernels -- I know, unstable != testing but I've had decent experiences in the past with Aptosid.

Before I try messing with the video (and perhaps Aptosid video may go better than Debian Stable) I would really like to get my wireless to work, something I was not able to do in Debian (but I did not try installing wicd, just messing around with the interfaces file).

Finally, for my default (OEM) installation, is there any problem using apt instead of "Ubuntu Software Center"?  Other than it is just a comfortable habit, I have no strong reason to use the command line.  Still, my typing is adequate and I use it quite a bit.

Alas, my mouse is more an extension of my keyboard than the other way around.  :lolflag:

---

### Post by ubuntu27 on 2012-03-21
> **HunkirDowne said:**
> Getting straight to my point, should I install the System 76 Driver to distros other than Ubuntu?  What about: Mint (Ubuntu-derived, not LMDE)? 

I don't work for System76.

I imagine that the driver will work in Mint since it is a Ubuntu derivatibe. Someone from System76 might be able to confirm. :)

Or you could wait for someone who might have already tried doing that.

> **HunkirDowne said:**
> 
Finally, for my default (OEM) installation, is there any problem using apt instead of "Ubuntu Software Center"?  Other than it is just a comfortable habit, I have no strong reason to use the command line.  Still, my typing is adequate and I use it quite a bit.

Alas, my mouse is more an extension of my keyboard than the other way around.  :lolflag:

It is fine to use the terminal. :)  The great thing about the terminal is that it gives you an output or info of what you are doing or what is going on.


It is your choice.

---

### Post by jml on 2012-03-21
A System 76 employee can confirm,but it is my understanding that the driver will only work on Ubuntu and I believe Kubuntu and Xubuntu.  The custom Driver will not load on systems that use "buntu" derivatives like Mint.

Joe

---

### Post by isantop on 2012-03-22
> **jml said:**
> A System 76 employee can confirm,but it is my understanding that the driver will only work on Ubuntu and I believe Kubuntu and Xubuntu.  The custom Driver will not load on systems that use "buntu" derivatives like Mint.

Joe

The driver will work on any OS that identifies as normal Ubuntu. Kubuntu, Xubuntu, etc. will all work, but Mint, Debian, etc. will not.

---

