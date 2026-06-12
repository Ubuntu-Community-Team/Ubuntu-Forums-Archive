---
title: "Smallest Linux distro"
date: 2012-01-05
forum: Server Platforms
---

### Post by deepakdeshp on 2012-01-05
I am looking for a smallest Linux distro with Apache.  It has to fit in smallest size and just serve web pages to the Window clients.

---

### Post by Lars Noodén on 2012-01-05
You're probably looking for Puppy Linux.  That will be close to as small as you get.  Slitaz and TinyCore are also small.  You'll have to investigate further yourself.  In the worst case, install each of them and check the size.

If you are not absolutely set on having Apache, nginx (the #2 most popular web server) is much, much smaller and has most of the same capabilities.

---

### Post by snowpine on 2012-01-05
What are your hardware specs?

Ubuntu Server has very modest system requirements:

> Ubuntu Server (CLI) Installation

    300 MHz x86 processor
    128 MiB of system memory (RAM)
    1 GB of disk space
    Graphics card and monitor capable of 640x480
    CD drive 

See also [Ubuntu Server Guide]("https://help.ubuntu.com/11.04/serverguide/C/preparing-to-install.html"). 

---

### Post by Lars Noodén on 2012-01-05
> **snowpine said:**
> What are your hardware specs?

Ubuntu Server has very modest system requirements:

If needed, you can even skip the graphics card requirement and install via serial cable.

---

### Post by deepakdeshp on 2012-01-05
> **snowpine said:**
> What are your hardware specs?

Ubuntu Server has very modest system requirements:

I am planning to boot the Linux system without a disk drive , may be e Flash drive from a small box with minimum configuration . From this box the content would be served by the Apache web server.

---

### Post by snowpine on 2012-01-05
Be aware that very old computers often have difficulty booting from a flash drive.

Again, if you want to tell us your hardware specs, maybe I can make some specific recommendations. Absent any details, my general recommendation is Ubuntu Server. :)

---

### Post by Vegan on 2012-01-05
I used Linux server on a Pentium II running at 300 MHz fine. I had 512 MB of memory installed so it ran fine. 

Old SDRAM is now very low cost and widely available in a junk box.

I used a small 20 GB disk fine and it acted as my web server until I got something better to use.

---

### Post by Doug S on 2012-01-05
snowpine: Where did you get the 300Mhz cpu requirement from? I have not seen it before.
 
I am running Ubuntu server 11.10 on a 15 year old 200 Mhz computer with 128 Mb of memory. Apache runs fine, as does a minimal iptables rule set. (I am claiming the prize for the most pathetic Ubuntu server (joke)).

---

### Post by snowpine on 2012-01-05
> **Doug S said:**
> snowpine: Where did you get the 300Mhz cpu requirement from? I have not seen it before.

[https://help.ubuntu.com/community/Installation/SystemRequirements#Ubuntu_Server_.28CLI.29_Installation](https://help.ubuntu.com/community/Installation/SystemRequirements#Ubuntu_Server_.28CLI.29_Installation)

It is a "recommendation" not a hard limit.

---

### Post by volkswagner on 2012-01-05
Sounds like a good project to use a TurnkeyLinux Appliance.

You can use the[ LAMP stack]("http://www.turnkeylinux.org/lampstack"), [Core]("http://www.turnkeylinux.org/core"), or start with the barebones minimum, they call [JEOS]("http://www.turnkeylinux.org/bootstrap"), "just enough OS".

They can be installed (bare metal or VM) or run in live mode.

---

### Post by lykwydchykyn on 2012-01-05
Tinycore is only 11MB, though you have to install apache separately (it has a package manager).  It has a gui-less option called microcore that's even smaller.

I used tinycore on an old thin client, booting off a 256 MB flash drive, to make a server that plays our hold music.  Even has a web interface, courtesy of vlc.

---

### Post by bluexrider on 2012-01-05
> **deepakdeshp said:**
> I am looking for a smallest Linux distro with Apache.  It has to fit in smallest size and just serve web pages to the Window clients.[B]Damn Small Linux is a very versatile 50MB mini desktop oriented Linux distribution.

[http://www.damnsmalllinux.org/](http://www.damnsmalllinux.org/)


[/B]

---

### Post by Mia1990 on 2012-01-05
for a file server you may want to look at [Freenas]("http://www.freenas.org/") it will boot and run off a usb drive and maybe a cd leaving your hard drive for storing your files  it may also wouk with Apache I just don't know I use Ubuntu Server..

---

### Post by deepakdeshp on 2012-01-05
The idea is to give an Apache server on a mass scale with minimum cost and configuration which will help the clients to run multimedia files like movies etc. They will be stored on the Apache Linux server may be on the external drive .And command line is fine as I do not need the additional packages which will come with the GUI.

---

### Post by Vegan on 2012-01-05
You are best off with a fortune worth of RAM to do that.

I also suggest as many CPU cores as possible.

I jokingly asked in the Hyper-V if it could peer an old IBM solicitation for 1000 instances of Linux, it can almost do it

Use a fast bare metal hyypervisor and use SSD storage.

---

### Post by deepakdeshp on 2012-01-06
> **Vegan said:**
> 
Use a fast bare metal hyypervisor and use SSD storage.

I do not want to virtualize the servers as the servers will be a single server at one location and 10000s of all such servers will work independently, each one separated by a distance of 10 miles or so.

---

### Post by Lars Noodén on 2012-01-06
@deepakdeshp, how do your hardware specs compare to what @snowpine showed in post #3?  It looks like the odds favor a recommendation of Ubuntu Server.

---

### Post by deepakdeshp on 2012-01-06
There are various suggestions to my question Thank you all. Tinycore (11mb for the bare system) and damnsmalllinux work in really small memory. Ubuntu will take substentiaally lots of memory. I will tyr the small distros before drawing any conclusion.

At home I use Ubuntu server extensively.  Till now I used Ubuntu desktop too but recently I switched to Mint12

---

### Post by lykwydchykyn on 2012-01-06
> **deepakdeshp said:**
> Tinycore (11mb for the bare system) and damnsmalllinux work in really small memory.

I'd avoid damnsmall for anything new.  Development halted on it years ago, and the packages for it are very out of date.

---

### Post by Cookieh on 2012-01-06
Would suggest using plain no gui UNIX but does not allow you to search on web, or even see web pages, but Puppy Linux would be excellent choice...

---

