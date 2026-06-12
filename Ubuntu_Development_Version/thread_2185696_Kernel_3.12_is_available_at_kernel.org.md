---
title: "Kernel 3.12 is available at kernel.org"
date: 2013-11-03
forum: Ubuntu Development Version
---

### Post by Doug S on 2013-11-03
I have been watching for it, because of some testing I want to do...

---

### Post by VinDSL on 2013-11-03
Nice.  Thanks.

I need a stable kernel for my notebook - don't feel like upgrading to yet_another_rc every week...  ;)

---

### Post by VinDSL on 2013-11-03
Whoops!

Guess we better throw a link in here, eh what?

[https://www.kernel.org/pub/linux/kernel/v3.x/?C=S;O=D](https://www.kernel.org/pub/linux/kernel/v3.x/?C=S;O=D)

EDIT

N/M  

I'm not used to going to the main page.  That surely makes it easier...  :D

[https://www.kernel.org/](https://www.kernel.org/)

---

### Post by Doug S on 2013-11-03
> **VinDSL said:**
> Whoops! Guess we better throw a link in here, eh what?Sorry, I actually forget where to find it, as I use git and just, mindlessly, do:```
git pull
time make -j8 deb-pkg
```
Edit: I forgot to mention, the changes between RC7 and this stable 3.12 are very minimal.

---

### Post by dbass81 on 2013-11-03
No changelog yet?  I usually read those... oh well.  Here goes to another 2 hours of compile time on my single core 2.2 Ghz laptop...

---

### Post by VinDSL on 2013-11-03
> **Doug S said:**
> Sorry, I actually forget where to find it, as I use git and just, mindlessly, do:```
git pull
time make -j8 deb-pkg
```
Edit: I forgot to mention, the changes between RC7 and this stable 3.12 are very minimal.

Sweet!

I've never tried that before...  ;)

---

### Post by pqwoerituytrueiwoq on 2013-11-03
3.12 now available in mainline:
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.12-saucy](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.12-saucy)

---

### Post by Doug S on 2013-11-03
@pq...q: Did you happen to notice some significant changes in the intel_pstate.c driver in 3.12RC7? It fixed some very small but lingering jitter in reported frequencies in one of the tests I was doing way back about the 3.10RC4time frame. Reported frequencies pretty much now agree (to enough significant digits anyways) to what I would expect for each pstate.

@VinDSL: The advantage with using the git method is: The download (which was just changes) took less than a minute; A complete re-compile was not required and only took about 7 minutes, and most of that time was due to my restoring some files I had changed. Of course, other times not so lucky and a complete re-compile is required.

---

### Post by pqwoerituytrueiwoq on 2013-11-03
have not looked at those very closely lately, i do think the temps are higher than with ondemand on my laptop

---

### Post by tad1073 on 2013-11-03
What's the difference 3.12.0-1 and 3.12.0-031200?
[TABLE]
[TR]
[TD]

[/TD]
[/TR]
[/TABLE]
[TABLE]
[TR]
[/TR]
[/TABLE]

---

### Post by pqwoerituytrueiwoq on 2013-11-03
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.12-saucy/CHANGES](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.12-saucy/CHANGES)
that probably

---

### Post by VinDSL on 2013-11-03
> **Doug S said:**
> @VinDSL: The advantage with using the git method is: The download (which was just changes) took less than a minute; A complete re-compile was not required and only took about 7 minutes, and most of that time was due to my restoring some files I had changed. Of course, other times not so lucky and a complete re-compile is required.
Okay, thanks.  I'll try that, one of these days.

The 3.12 kernel is compiling on my Latitude, as I type.

I noticed yesterday, on the desktop box I'm using right now, that usb flash drives and the dvd drive weren't working.  It's one of those things you don't notice, until you go to use them, you know?  

For some reason, they weren't enabled by default.  I just checked the .config file on the notebook, and they weren't enabled in it either. Sooo, I had some work to do in menuconfig :)

We'll see how it goes -- takes about 30 minutes to compile 3.12 on my lappy.  I'll probably have to strip some depends out of the control file, when its done -- been having to do that lately, before the debs will install (in Peppermint Four OS).

Fingers crossed...

---

### Post by VinDSL on 2013-11-03
w00t!

Watching it compile...

This is the first time I haven't gotten an error on vmlinux.o

That's encouraging!  :D

---

### Post by VinDSL on 2013-11-03
Alrighty then...

Still need to hack the control file.  :P

---

### Post by VinDSL on 2013-11-03
Works... :)

[INDENT][[IMG]http://vindsl.com/images/vindsl-notebook-3-nov-2013-1(650x407).png[/IMG]]("http://vindsl.com/images/vindsl-notebook-3-nov-2013-1.png")[/INDENT]

---

### Post by dbass81 on 2013-11-04
Compiled last night took 2 hours on my single core 2.2 Ghz CPU... looks good so far.  Boots up fast, no errors!  xD

---

### Post by VinDSL on 2013-11-04
> **dbass81 said:**
> Compiled last night took 2 hours on my single core 2.2 Ghz CPU... looks good so far.  Boots up fast, no errors!  xD
I'm getting a "problem loading in-kernel x.509 certificate (-129)" warning at boot, on my Dell Latitude.

Doesn't seem to be hurting anything.  It just pops up for a second or two, then goes away.

---

### Post by VinDSL on 2013-11-04
w00t!  That was easy...  :D

The solution was to set the hardware clock from the system time by running the following command:

```
sudo hwclock --systohc
```

"Release Notes for Unbreakable Enterprise Kernel Release 3 - October 2013"

SOURCE:  [http://docs.oracle.com/cd/E37670_01/E48380/html/ol_fikniss.html](http://docs.oracle.com/cd/E37670_01/E48380/html/ol_fikniss.html) (bottom of the page)

Heh!  Gotta love those [metasearch engines]("https://en.wikipedia.org/wiki/Metasearch_engine")...

---

### Post by dbass81 on 2013-11-04
> **VinDSL said:**
> I'm getting a "problem loading in-kernel x.509 certificate (-129)" warning at boot, on my Dell Latitude.

Doesn't seem to be hurting anything.  It just pops up for a second or two, then goes away.

No error here.  My laptop is a Dell Inspiron 1300 based on the i915gm chipset.  The hardware is probably a lot different.  Last time I had a kernel warning on boot was with the 3.11.2 and 3.11.3 kernels.  I filed a bug on Bugzilla and it was already fixed in 3.11.4.

---

### Post by dbass81 on 2013-11-04
> **VinDSL said:**
> 
For some reason, they weren't enabled by default.  I just checked the .config file on the notebook, and they weren't enabled in it either. Sooo, I had some work to do in menuconfig :)


You can copy your current kernel config before you compile a new kernel by running this command in your kernel source directory:

cat /boot/config-`uname -r`>.config

I had the same problem for my wireless adapter when I built a new kernel.

---

### Post by Doug S on 2013-11-04
> **dbass81 said:**
> You can copy your current kernel config before you compile a new kernel by running this command in your kernel source directory:
cat /boot/config-`uname -r`>.config
I had the same problem for my wireless adapter when I built a new kernel.For kernel testing, I only use the kernel from kernel.org and not the ubuntu one. However, when I have configuration issues I rarely know what to do, so I will download and install the ubuntu version of the same kernel and then copy the .config file as mentioned by dbass81. Typically it is at most once per kernel series that I have to do this extra step.

---

### Post by VinDSL on 2013-11-04
> **dbass81 said:**
> You can copy your current kernel config before you compile a new kernel by running this command in your kernel source directory:

cat /boot/config-`uname -r`>.config
Nice!  I like that...

That's the same file I use, but I copy n' paste it to my source folder in /home and rename it (I compile in /home).

3.12 final (for want of another word) is working fine on my Dell Latitude D620.  It just had a problem loading that cert.  The command (above) fixed the prob -- haven't seen it since.

I need to start whittling down the kernel now.  Parallel port support comes to mind.  Do I really need that on my Latitude notebook?!?!?  LoL!  :D

---

### Post by philinux on 2013-11-05
Small write up on this.

[http://www.omgubuntu.co.uk/2013/11/linux-kernel-3-12-goes-stable-gpu-features?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+d0od+%28OMG!+Ubuntu!%29](http://www.omgubuntu.co.uk/2013/11/linux-kernel-3-12-goes-stable-gpu-features?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+d0od+%28OMG!+Ubuntu!%29)

---

### Post by dbass81 on 2013-11-05
> **philinux said:**
> Small write up on this.

[http://www.omgubuntu.co.uk/2013/11/linux-kernel-3-12-goes-stable-gpu-features?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+d0od+%28OMG!+Ubuntu!%29](http://www.omgubuntu.co.uk/2013/11/linux-kernel-3-12-goes-stable-gpu-features?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+d0od+%28OMG!+Ubuntu!%29)

Sorry for being off-topic, but your avatar made me think of this Boris riddle from Goldeneye, "You sit on it, but you can't take it with you?"

Thanks for the link.  So the changes are mostly GPU related.

---

### Post by kevpan8152 on 2013-11-05
With 3.12 Mainline my Laptop Fan seems to behaving better than before however it still does occasionally turn on while Updating/Upgrading my system. I have a Second Gen Intel I3 Processor, 500 GB Hard Disk Drive, 4 GB of RAM, an Intel Graphics Media Accelerater 4000 Graphics Card, Realtek Integrated Sound, and Atheros WIFI with Blue Tooth integration.

---

### Post by dbass81 on 2013-11-05
> **VinDSL said:**
> 
I need to start whittling down the kernel now.  Parallel port support comes to mind.  Do I really need that on my Latitude notebook?!?!?  LoL!  :D


Good luck.  I have tried that in the past, and I always manage to remove something needed, causing a kernel panic on boot.  It seems like everything is loaded as a module anymore so really no reason to customize it too much.  I just make sure everything I need is loaded as a module or built-in and leave the rest alone.

---

### Post by VinDSL on 2013-11-05
> **dbass81 said:**
> Good luck.  I have tried that in the past, and I always manage to remove something needed [...]
Yep!

Neck bone's connected to the head bone... and that's how Herman was born.  :D

**[http://www.youtube.com/watch?v=MEpwnRsoj-s](http://www.youtube.com/watch?v=MEpwnRsoj-s)**

---

### Post by sammiev on 2013-11-05
I switch 3 systems over to Kernel 3.12 today after running 3.12 rc7 over the last week which was so kind to me. After having the day to play with them, all seems to be solid. :)

---

### Post by KegHead on 2013-11-15
> **pqwoerituytrueiwoq said:**
> 3.12 now available in mainline:
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.12-saucy](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.12-saucy)

hi!

What is the order of opening the debs?

thanks!

KegHead

---

### Post by Mateusz Stachowski on 2013-11-15
You should install all three at the same time. Open terminal with Ctrl + Alt + T shortcut and then type this command:

```
sudo dpkg -i 
```

Next just drag and drop the .deb packages on the terminal and press enter to start install.

---

### Post by kevpan8152 on 2013-11-15
> **dbass81 said:**
> Compiled last night took 2 hours on my single core 2.2 Ghz CPU... looks good so far.  Boots up fast, no errors!  xD

Have you guys ever considered downloading the PPA Mainline Files, Put them in a Folder named KERNEL inside your home folder, Open up a Command Line Terminal, and then type cd KERNEL, finally type (sudo dpkg -i *)? Without the () and the ?, It's a whole lot easier than trying to install it through Software Center! Just FYI! Edit: Takes a whole lot less time as well!

---

### Post by kevpan8152 on 2013-11-15
I should also let you guys know that there is a Trusty 3.12 Kernel at the Kernel Mainline PPA website (It's been there since November 8th) just in case anyone has missed it!

---

### Post by VinDSL on 2013-11-16
> **kevpan8152 said:**
> Have you guys ever considered downloading the PPA Mainline Files [...]?
Yep!  I use mainline kernels all the time.

Only reason(s) I went back to compiling them is because 'paul_in_london' came up with a dandy time-saver.

Used to take 4 hours to compile a kernel on this box -- the way I was doing it.  Paul's method cut the time down to 30 minutes.  :)

I usually add a couple of things (not subtract) when I compile a kernel -- they're just fun to play around with, you know?  If it ain't broke, break it.

Plus, I like to add my nick to the package name -- and, the machine ID -- call it artistic license, if you will.

Anyway, I still use mainline kernels, when I'm in a pinch for time...

---

### Post by zika on 2013-11-16
> **kevpan8152 said:**
> Have you guys ever considered downloading the PPA Mainline Files, Put them in a Folder named KERNEL inside your home folder, Open up a Command Line Terminal, and then type cd KERNEL, finally type (sudo dpkg -i *)? Without the () and the ?, It's a whole lot easier than trying to install it through Software Center! Just FYI! Edit: Takes a whole lot less time as well!Is this a trick question or a joke?

---

### Post by kevpan8152 on 2013-11-16
> **zika said:**
> Is this a trick question or a joke?

You're right i should have just said do a sudo dpkg -i * instead of installing them through Software Center.

---

### Post by zika on 2013-11-16
> **kevpan8152 said:**
> You're right i should have just said do a sudo dpkg -i * instead of installing them through Software Center.OK, so it is a joke...

---

### Post by philinux on 2013-11-21
[http://www.linuxtoday.com/upload/linux-kernel-3.12.1-is-now-available-for-download-131120134006.html?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+linuxtoday%2Flinux+%28Linux+Today%29](http://www.linuxtoday.com/upload/linux-kernel-3.12.1-is-now-available-for-download-131120134006.html?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+linuxtoday%2Flinux+%28Linux+Today%29)

---

### Post by fooman on 2013-11-21
> **3.12.1 is out.**



thanks philinux!  freshly compiled and running smoothly here...

```
Current Date/Time: Thu Nov 21 14:13:24 EST 2013
Distro Release: Ubuntu Trusty Tahr (development branch)
Kernel Release: Linux 3.12.1-foomans-custom-kernel2
Gnome Release: GNOME Shell 3.8.4
Unity Release: unity 7.1.2

OpenGL vendor string:   NVIDIA Corporation
OpenGL renderer string: GeForce GTX 480/PCIe/SSE2
OpenGL version string:  4.4.0 NVIDIA 331.20
```

[https://www.kernel.org/](https://www.kernel.org/)

:D

---

