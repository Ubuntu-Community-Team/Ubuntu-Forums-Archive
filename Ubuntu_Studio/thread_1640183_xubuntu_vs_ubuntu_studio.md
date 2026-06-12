---
title: "xubuntu vs ubuntu studio"
date: 2010-12-07
forum: Ubuntu Studio
---

### Post by Fardin on 2010-12-07
I have xubuntu and I added zynaddsubfx, hydrogen, and rosegarden on my xubuntu.

I've never tried ubuntu studio.

Is there any advantage to have ubuntu studio?

---

### Post by tubular on 2010-12-07
> Is there any advantage to have ubuntu studio?

no - i am assuming u use a rt-kernel

for a pleasant surprise as to what a Linux music production environmet can accomplish, try avlinux ;)

---

### Post by Fardin on 2010-12-07
> **tubular said:**
> no - i am assuming u use a rt-kernel

for a pleasant surprise as to what a Linux music production environmet can accomplish, try avlinux ;)


How di I check to see what kernel I have?

What are additional features that avlinux offer that ubuntu does not have?

---

### Post by cchhrriiss121212 on 2010-12-07
You can check your kernel using the uname -a command from a terminal, you will be running the generic kernel which is fine for most people. An rt or low latency kernel is worth it for getting latency down to a minimum, but if you are getting on OK without it you won't be gaining much.

AVlinux or Ubuntu Studio won't offer you any extra features, they are designed to be an out of the box OS for production work. If you are new to Linux they give a good representation of all the best FOSS programs, but if you are already know what you want, they don't really give you anything special. 

Ubuntu Studio is based on regular Ubuntu so it has the Gnome DE, AV Linux is based on Debian and uses LDXE and there is also KXStudio based on Ubuntu which uses KDE. AV Linux might be a bit faster on older hardware as LDXE is a lighter DE.

Any program or feature you find on these distros can be had in the standard repos or a PPA. So you can browse through their lists of programs and install them yourself to see what they are like. Here is a good PPA for music from the guy who runs KXStudio:
[https://launchpad.net/~falk-t-j/+archive/lucid]("https://launchpad.net/%7Efalk-t-j/+archive/lucid")

---

### Post by Fardin on 2010-12-07
> **cchhrriiss121212 said:**
> You can check your kernel using the uname -a command from a terminal, you will be running the generic kernel which is fine for most people. An rt or low latency kernel is worth it for getting latency down to a minimum, but if you are getting on OK without it you won't be gaining much.

AVlinux or Ubuntu Studio won't offer you any extra features, they are designed to be an out of the box OS for production work. If you are new to Linux they give a good representation of all the best FOSS programs, but if you are already know what you want, they don't really give you anything special. 

Ubuntu Studio is based on regular Ubuntu so it has the Gnome DE, AV Linux is based on Debian and uses LDXE and there is also KXStudio based on Ubuntu which uses KDE. AV Linux might be a bit faster on older hardware as LDXE is a lighter DE.

Any program or feature you find on these distros can be had in the standard repos or a PPA. So you can browse through their lists of programs and install them yourself to see what they are like. Here is a good PPA for music from the guy who runs KXStudio:
[https://launchpad.net/~falk-t-j/+archive/lucid]("https://launchpad.net/%7Efalk-t-j/+archive/lucid")

I am relatively new to linux (2 months).  I explore it as a hobby.  Last week I got into the magic world of digital audio that linux offers and it was like stepping on a quicksand!
I've been playing with rosegarden and zynaddsubfx.  In rosegarden I sense the latency so it would be very good to get Zero latency.
How do i change my kernel to rt kernel?

Also please forgive my lack of knowledge, could you explain what ppa is? I checked the site that you referred. It seems like there are lots of packages in there, I'm not sure what they are.
thanks for your insight.

---

### Post by cchhrriiss121212 on 2010-12-07
Sorry I forget to explain the terminology sometimes:
A PPA is a personal package archive, and anyone can start one up. They allow someone to select specific apps and package them specifically for Ubuntu. I take it by now you know that Ubuntu installs things via a package manager (ie Software Center or Synaptic) from a selected group of software (ie the repositories or repos for short).
Once you add a PPA to your system, the software it contains is added to your package manager available for download. The package manager system is for security as it allows only trusted software on your system. So by installing a PPA you let your system know that this software is also safe to install. It is up to you to decide what PPAs are trustworthy.
As a rule it is a good idea to enable PPAs temporarily to install what you want, then disable them after.

Regarding latency: are you using jack?

---

### Post by Fardin on 2010-12-07
> **cchhrriiss121212 said:**
> Sorry I forget to explain the terminology sometimes:
A PPA is a personal package archive, and anyone can start one up. They allow someone to select specific apps and package them specifically for Ubuntu. I take it by now you know that Ubuntu installs things via a package manager (ie Software Center or Synaptic) from a selected group of software (ie the repositories or repos for short).
Once you add a PPA to your system, the software it contains is added to your package manager available for download. The package manager system is for security as it allows only trusted software on your system. So by installing a PPA you let your system know that this software is also safe to install. It is up to you to decide what PPAs are trustworthy.
As a rule it is a good idea to enable PPAs temporarily to install what you want, then disable them after.

Regarding latency: are you using jack?

yes I do use jack.

I did write uname -a
and got this:
Linux mao-Dell-DE051 2.6.35-23-generic #41-Ubuntu SMP Wed Nov 24 10:18:49 UTC 2010 i686 GNU/Linux
do not know how to find out if it's rt kernel or not?

---

### Post by cchhrriiss121212 on 2010-12-08
That is the generic kernel, you would not have an rt kernel unless you installed one yourself. If you want to install one try using this PPA:
[https://launchpad.net/~abogani/+archive/ppa]("https://launchpad.net/%7Eabogani/+archive/ppa")
If you look at the setup window of qjackctl. you will see that you can adjust the latency by changing the frame rate, 10ms should be acceptable.

---

### Post by Fardin on 2010-12-08
> **cchhrriiss121212 said:**
> That is the generic kernel, you would not have an rt kernel unless you installed one yourself. If you want to install one try using this PPA:
[https://launchpad.net/~abogani/+archive/ppa]("https://launchpad.net/%7Eabogani/+archive/ppa")
If you look at the setup window of qjackctl. you will see that you can adjust the latency by changing the frame rate, 10ms should be acceptable.


Is installing rt kernel simple enough for a newb or do i need to read about it before i try?

---

### Post by cchhrriiss121212 on 2010-12-08
Definitely try it out if you have the time and patience to learn, but as I said it is not strictly necessary. It is not too difficult and I can explain the basics of kernel installation here:

[LIST]
[*] Add the PPA (if needed)
[*]Open synaptic and select the kernel image for installation along with the headers
[*]From terminal do a "sudo update-grub" which should display your new kernel in addition to the old one
[*]Reboot and hold the shift button to see the GRUB menu. Select your new kernel and see if it works (sometimes a new kernel will not work on your hardware or have some other odd issue so always keep the old one around).
[*]Optional step - Install startup manager to configure your GRUB menu. You can use it to determine how long GRUB will show up for, and what the default kernel will be.
[/LIST]
You might be wondering what kernel to install from that PPA. I would recommend the low latency version as it is a bit newer than the rt version. Feel free to try them both and compare though, you can have as many kernels as you like and they are easy to remove with synaptic.

---

### Post by tubular on 2010-12-08
> **Fardin said:**
> How di I check to see what kernel I have?

What are additional features that avlinux offer that ubuntu does not have?

if u have Ubuntu Studio - you have the rt-kernel ...not to bash Ubuntu Studio with my last message - but av-linux does have some added plugins etc. which can also be installed in Ubuntu Studio (which also has its good points too)

---

### Post by Totalchaos on 2010-12-11
> **Fardin said:**
> I have xubuntu and I added zynaddsubfx, hydrogen, and rosegarden on my xubuntu.

I've never tried ubuntu studio.

Is there any advantage to have ubuntu studio?

well it is even simpler on nowadays if you have Xubuntu installed on your computer you should just 'apt-get install linux-rt"(depending on ubuntu version it can be 'linux-realtime' ; 'linux-preempt' but hope you get the idea) followed by 'apt-get install ubuntustudio-audio ubuntustudio-audio-plugins' 
and voala ;)

although ubuntu-studio uses gnome for default gui in many cases xfce is better for audio production mostly for it's lightness

The difference in AVlinux is : it's based on Debian unstable, you receive some proprietary software like 'renoise' and 'energy-xt",  and there is some extra modules in the RT-kernel (wi-fi etc.)

---

