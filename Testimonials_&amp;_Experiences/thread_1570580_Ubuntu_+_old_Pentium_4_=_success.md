---
title: "Ubuntu + old Pentium 4 = success"
date: 2010-09-08
forum: Testimonials &amp; Experiences
---

### Post by webb1976 on 2010-09-08
Hello,

I just installed an older version of Ubuntu (8.04) on an old Pentium 4 (1 Ghz) processor with only 256MB of ram. I decide to use an older version to not tax the PC too much.

I am also running Win XP (service pack 3) on another PC with a Pentium 4 (2+ Ghz) processor and 2GB of ram. I did not think that the old PC would be able to do much web-browsing..... I was going to use it to learn Linux commands and install a few apps well.

Was I in for a shock. The old PC actually performs surfing the web than my other one. It is really amazing. I was going to add more ram to the old one but now I am curious to see just how far I can push this machine. I am not going to upgrade to newer versions for fear that my machine can't handle it.

My wife was watching me surf last night and she was curious what that orange bird-looking thing on the desktop was. I performed a ton of updates and everything is running great. Firefox is a JOY compared to IE.

I had ran Ubuntu a few years ago, and it left a little to be desired with so much device support missing. The Ubuntu community deserves a BIG pat on the back to making this distro as easy and stable as it is.  I am already thinking about installing some of the apps from Ubuntu studio to see how they will perform.

Anyway, I am confiscating all the old P4 machines from friends and family to get new life from them.

---

### Post by Jazzy_Jeff on 2010-09-08
If you think Firefox is quick try using open source Chromium or regular Google Chrome.

---

### Post by Photonic Nature on 2010-09-08
AFAIK, The only problem you may have with running the latest releases on a P4 would be your choice of desktop environment. In which case Gnome usually runs fine but if you want something lighter you could opt for other available options such as Xubuntu which uses the lightweight XFCE desktop.
xubuntu.org:
[http://www.xubuntu.org/](http://www.xubuntu.org/)
Other derivatives:
[http://www.ubuntu.com/project/derivatives](http://www.ubuntu.com/project/derivatives)
[https://wiki.ubuntu.com/DerivativeTeam/Derivatives](https://wiki.ubuntu.com/DerivativeTeam/Derivatives)

The latest Linux kernels will not affect your system performance per se, but the desktop environment and software you choose will. 

Not running the latest versions may leave you open to security vulnerabilities and other issues.

Supported Hardware:
[https://help.ubuntu.com/10.04/installation-guide/i386/hardware-supported.html](https://help.ubuntu.com/10.04/installation-guide/i386/hardware-supported.html)

One other caveat is the switch to grub2 since v9.10.
However that will not affect performance, just tweaking annoyances.

Welcome to the awesome world of Linux. 
Enjoy and never look back!

---

### Post by cchhrriiss121212 on 2010-09-08
Linux is great for reviving old machines. I would also recommend you try out a lightweight distro, but I would vote for Lubuntu or Crunchbang as opposed to Xubuntu which is almost as intensive as regular Ubuntu.

---

### Post by webb1976 on 2010-09-08
@ JazzyJeff

I have heard of Chronium before ...but I did not know you could run Google Chrome directly on your system. I guess you could using Wine.

Which one would you suggest me testing, and where can I download Chronium?

---

### Post by webb1976 on 2010-09-08
@ chris

I actually did try out Xubuntu on a virtual machine (they were using VirtualBox). I did not see much of a difference between that regular Ubuntu (although the desktop was different).

I have heard of Lubuntu.... is it really much more lightweight than regular Ubuntu? Crunchbag I have not heard of.....can you tell me more  about it

Actually I am looking at installing Ubuntu Studio on another machine. Do you recommend 9.04 or jumping to 10? I am actually starting some web development and doing some music and I have heard good things about Ubuntu Studio. Can I get  away with using it on my newer PC with 2GB of ram?

---

### Post by Photonic Nature on 2010-09-08
> **webb1976 said:**
> @ JazzyJeff

I have heard of Chronium before ...but I did not know you could run Google Chrome directly on your system. I guess you could using Wine.

Which one would you suggest me testing, and where can I download Chronium?

Chromium is in the ubuntu repositories... it runs directly in linux so do not complicate things with wine.
search for it in synaptic: SYSTEM > ADMINISTRATION > SYNAPTIC PACKAGE MANAGER

Google Chrome is available straight from Google:
[http://www.google.com/chrome](http://www.google.com/chrome)

anything else you are curious about... just Google it :)

---

### Post by Photonic Nature on 2010-09-08
another lightweight & cool Linux option is eLlive:
[http://www.elivecd.org/](http://www.elivecd.org/)

			 			   			**_Minimum Requirements:_** The 			minimum hardware for running Elive is a 100 Mhz CPU and 			64 MB of RAM, but the minimum recommended hardware is 			300 Mhz and 128 Mb of RAM. You do not need any special 			graphics card or 3D acceleration to run Elive.

---

### Post by cchhrriiss121212 on 2010-09-08
> **webb1976 said:**
> @ chris

I actually did try out Xubuntu on a virtual machine (they were using VirtualBox). I did not see much of a difference between that regular Ubuntu (although the desktop was different).

I have heard of Lubuntu.... is it really much more lightweight than regular Ubuntu? Crunchbag I have not heard of.....can you tell me more  about it

Actually I am looking at installing Ubuntu Studio on another machine. Do you recommend 9.04 or jumping to 10? I am actually starting some web development and doing some music and I have heard good things about Ubuntu Studio. Can I get  away with using it on my newer PC with 2GB of ram?
Both Lubuntu and Crunchbang use Openbox which is a lightweight window manager that will be easier on your RAM and cpu usage. 
[Crunchbang]("http://crunchbanglinux.org/") is a minimalist distro, but it is just as feature-full as any other OS. It makes use keyboard shortcuts, conky, and has a lot of useful things installed by default (VLC, DVD playback, flash etc.). The newest version, CB10 or Statler, is in the alpha stages and is based on Debian, and although it is an alpha it is just as stable as any Ubuntu release. I use it on my 8 year old laptop and my main production desktop, and have had very few issues. The current stable release is based on Ubuntu 9.04. It also has a great support community.

Regarding studio I would recommend using 9.10 as it has been good on my machine, and comes with an rt kernel (unlike 10.04). 2GB is plenty, though your audio performance will be shaped more by CPU and sound card. Before installing studio give LMMS a go, and see whether it can do all you need. If it is too basic for you, then look into using jack and things like Qtractor, Hydrogen etc.

---

### Post by webb1976 on 2010-09-08
> **cchhrriiss121212 said:**
>  Before installing studio give LMMS a go, and see whether it can do all you need. If it is too basic for you, then look into using jack and things like Qtractor, Hydrogen etc.

What is LMMS? And those other distros sound VERY interesting. I had heard of Openbox but was not sure what it was. So it is a window manager like Gnome/KDE...intresting. And Xubuntu uses XFCE as its window manager. Got it.

You know I do have some older machines that it will be interesting to see just what I can squeeze out of it.

---

### Post by webb1976 on 2010-09-08
> **Photonic Nature said:**
> another lightweight & cool Linux option is eLlive:
[http://www.elivecd.org/](http://www.elivecd.org/)

                                        **_Minimum Requirements:_** The             minimum hardware for running Elive is a 100 Mhz CPU and             64 MB of RAM, but the minimum recommended hardware is             300 Mhz and 128 Mb of RAM. You do not need any special             graphics card or 3D acceleration to run Elive.

WOW:cool:

I had absolutely no idea you could get something anywhere near that smooth on a PC with a Pentium II proccessor in it. Heck I just got rid of a PC with an old Celeron in it that would have been perfect for that. I think I will run it virtual in a machine to try it out (should not be a problem at all).

I am VERY impressed by that. I wonder what type of browser comes with it.

---

### Post by MasterNetra on 2010-09-08
> **Photonic Nature said:**
> Chromium is in the ubuntu repositories... it runs directly in linux so do not complicate things with wine.
search for it in synaptic: SYSTEM > ADMINISTRATION > SYNAPTIC PACKAGE MANAGER

Google Chrome is available straight from Google:
[http://www.google.com/chrome](http://www.google.com/chrome)

anything else you are curious about... just Google it :)

+1

Google provides a .deb (Ubuntu oriented actually) and a .rpm of its browser. Which also adds google's repo for Chrome when you install the .deb ... I assume the same with the Fedora/Redhat .rpm but haven't installed it on Fedora. Don't see why not though.

---

### Post by NightwishFan on 2010-09-08
Here are a few tips that make a world of difference on old machines:

Tip number one is to increase swappiness. This moves less used parts of memory into swap earlier leaving more real RAM for what you are doing. I see practically no downside to this, as on a machine with a lot of RAM, swap will not be touched anyway. I use this on all of my machines. Here is how:
```
sudo su
echo 'vm.swappiness = 100' >> /etc/sysctl.conf
exit
```

Tip number two is suggested in the Ubuntu Community Documentation for low memory installs. It disables a few proprietary modules. I would recommend you review which ones you may need or not though. If you have a Nvidia card, I would leave 'nv' on. Run:
```
sudo nano /etc/default/linux-restricted-modules-common
```

Then paste this, and press ctrl+x, then y, to save the file.
```
DISABLED_MODULES="ath_hal fc fglrx fwlanusb ltm nv"
```

This should be valid on any Ubuntu variant, such as Xubuntu/Lubuntu as well.

---

### Post by cchhrriiss121212 on 2010-09-08
> **webb1976 said:**
> What is LMMS? 
It is a DAW that is easy to get recording or making music with and it has many synths installed by default. To try it out just go to synaptic package manager and search for it, it is a relatively small download too, about 13MB.

---

### Post by mastablasta on 2010-09-09
i've put Latest ubuntu , changed theme to clearlook and removed the backroung image. on 256MB RAM computer it takes about 120 MB. when idle and a bit more when browsing and doing other things.

---

### Post by webb1976 on 2010-09-09
> **mastablasta said:**
> i've put Latest ubuntu , changed theme to clearlook and removed the backroung image. on 256MB RAM computer it takes about 120 MB. when idle and a bit more when browsing and doing other things.

I may try that as well. Wow guys thx so much for your help. I see I have alot of catching up to do in the open-source world. ;)

---

### Post by NCLI on 2010-09-09
> **webb1976 said:**
> @ chris

I actually did try out Xubuntu on a virtual machine (they were using VirtualBox). I did not see much of a difference between that regular Ubuntu (although the desktop was different).

I have heard of Lubuntu.... is it really much more lightweight than regular Ubuntu? Crunchbag I have not heard of.....can you tell me more  about it
They are both very lightweight distros. You should know that Lubuntu still hasn't been declared stable by Canonical.

> Actually I am looking at installing Ubuntu Studio on another machine. Do you recommend 9.04 or jumping to 10? I am actually starting some web development and doing some music and I have heard good things about Ubuntu Studio. Can I get  away with using it on my newer PC with 2GB of ram?
I would always recommend installing the latest Long-Term Support version, which is 10.04. Especially because 9.04 will not be support past this October:
[IMG]http://upload.wikimedia.org/wikipedia/en/timeline/2e489a50fd4ca3af1629df2abf5ee271.png[/IMG]

BTW: You may want some more RAM in your newer machine if you want to use it for intensive stuff like video editing. 4 GB should do.
> **cchhrriiss121212 said:**
> Both Lubuntu and Crunchbang use Openbox which is a lightweight window manager that will be easier on your RAM and cpu usage. 

Lubuntu uses LXDE, not Openbox.

> Regarding studio I would recommend using 9.10 as it has been good on my machine, and comes with an rt kernel (unlike 10.04). 2GB is plenty, though your audio performance will be shaped more by CPU and sound card. Before installing studio give LMMS a go, and see whether it can do all you need. If it is too basic for you, then look into using jack and things like Qtractor, Hydrogen etc.
A realtime kernel is also available for 10.04.

---

### Post by del_diablo on 2010-09-09
Chrome is too heavy. Use Opera.

---

### Post by cchhrriiss121212 on 2010-09-09
> **NCLI said:**
> ...
Lubuntu uses LXDE, not Openbox.


A realtime kernel is also available for 10.04.
To clear this up: 
LXDE is a Desktop Environment, and [Openbox]("http://en.wikipedia.org/wiki/Openbox") is a Window Manager. [LDXE]("http://en.wikipedia.org/wiki/LXDE") makes use of the openbox window manager, so Lubuntu uses both LXDE and Openbox. I mentioned Openbox because it was a similar component to both distros.  

It is correct that an rt kernel is available for 10.04, but in my opinion it is best for a new user to install something that does not require much tweaking.
The current stable rt kernel is 2.6.31.12 which is the same version included in 9.10. 
The kernel Studio 10.04 has no support for firewire cards unless you switch to another kernel.
This is why (IMO) 10.04 was not a good Studio release. 9.10 is still supported by Canonical and the [various music production PPAs]("http://ubuntuforums.org/showthread.php?t=1350304") out there.

---

### Post by webb1976 on 2010-09-09
> **cchhrriiss121212 said:**
> To clear this up: 
LXDE is a Desktop Environment, and [Openbox]("http://en.wikipedia.org/wiki/Openbox") is a Window Manager. [LDXE]("http://en.wikipedia.org/wiki/LXDE") makes use of the openbox window manager, so Lubuntu uses both LXDE and Openbox. I mentioned Openbox because it was a similar component to both distros.  


I keep on forgetting the difference between the X windows server, window managers (Openbox, Kwin, and Sawfish), and the actual desktop environments that use them (LXDE, KDE, Gnome). 

Microsoft has definitely dumbed-down everyone about how GUI's actually work. It really is interesting see how much goes on with all of this stuff.

---

### Post by webb1976 on 2010-09-09
Wow...there are a ton of different window managers out there. There are quite a few lightweight ones as well: Fluxbox, Openbox, Enlightment

Now i see why Elive was recommended because it uses Enlightment. 

I actually visited Linux Mint and saw that they already have packaged version using XFCE, FLuxbox, and LXDE. I think I will try the LXDE one and comare it to Crunchbang or Lubuntu.

Anyway, it is really amazing to see what can be run on a PC when people are TRULY consciousness of how much processing power is being allocated/wasted by a GUI.

---

### Post by NCLI on 2010-09-09
> **cchhrriiss121212 said:**
> To clear this up: 
LXDE is a Desktop Environment, and [Openbox]("http://en.wikipedia.org/wiki/Openbox") is a Window Manager. [LDXE]("http://en.wikipedia.org/wiki/LXDE") makes use of the openbox window manager, so Lubuntu uses both LXDE and Openbox. I mentioned Openbox because it was a similar component to both distros.  
Duh. My bad, sorry :(

---

### Post by armandh on 2010-09-10
two important things

you think it is fast now try 512 mem
before moving from 8.04.1 to later be sure you have enough of a graphics card.

I've got a 933 P-III with 512 meg and a 64 MB AGP video card that rocks 9.10 but also one with onboard shared mem video that won't run later than 8.04.1 [with out killing compiz]

---

### Post by webb1976 on 2010-09-10
Thanks to everyone's comments here. I actually downloaded a few distros and I am going to try a few of them out over the weekend. they are:

- Elive
- Crunchbang (LXDE)
- Mint (LXDE)
- Mint (XFCE)
- Xubuntu

I am going to try these ALL on my 256 MB ram PC. What is so crazy is that all of these up-to-date distros should run REALLY well on my machine.

I just installled Chrome, VirtualBox OSE, and LMMS. I was impressed with the speed of Chrome. The big difference is in loading "all the stuff" on the page.

I just kee getting impressed with how far Linux has come. I ahve a HUGE laundry list of stuff to try.

---

### Post by leclerc65 on 2010-09-10
Two more suggestions: Jolicloud 1.0 and Puppy 5.0.1.

Yes I love to recycle old computers too.:p

---

### Post by armandh on 2010-09-13
+1 on puppy for the older and slower
just flys on an old 600 mhz P-III 
96 meg of PC 100 mem and a 16 meg video card

866 is about the bottom end for playing a DVD movie without too much chopp

---

### Post by webb1976 on 2010-09-13
> **leclerc65 said:**
> Two more suggestions: Jolicloud 1.0 and Puppy 5.0.1.

Yes I love to recycle old computers too.:p

Hmmm.... I will take a look at those. I guess I will try Puppy first since another person voiced their approval as well.

Can anyone tell me anything more about Joliocloud????

Also, I was going to install ELive but they force you to contribute a monetary donation:confused: and only give you 5 licenses. What kind of stuff is that.

Anyway, I was going to try Cruchbang next and give that a go. we will see what we end up with.

Thanks guys for all your help

---

### Post by Jazzy_Jeff on 2010-09-13
Elive uses the enlightenment desktop. If you want to try out a distro with it go here [http://www.pclinuxos.com/](http://www.pclinuxos.com/).

---

### Post by webb1976 on 2010-09-13
> **Jazzy_Jeff said:**
> Elive uses the enlightenment desktop. If you want to try out a distro with it go here [http://www.pclinuxos.com/](http://www.pclinuxos.com/).

Thanks... the reason I was trying out Elive was because I was curious to see how much you could get done with a tiny foot print (minimum 64MB; recommend 128MB).

I see the PCLinux needs a bit more (I had never heard of it). I will try the out though. It looks cool.

---

### Post by leclerc65 on 2010-09-13
Please correct me if I am wrong.
Jolicloud 1.0 is lightweight Ubuntu 10.04, very good for under-powered  notebooks like eeePC 701 ... Very hard to choose between Jolicloud and Cruncbang. Wireless and playing media files is good OOTB (for my eee by the way). For real antique good-for-nothing PC's, nothing ,except Damn Small Linux, beat the Puppy Family. Of course TinyCore is excellent, but you have to install tons of stuff to make it useable.

---

### Post by Photonic Nature on 2010-09-14
> **webb1976 said:**
> 

Also, I was going to install Elive but they force you to contribute a monetary donation:confused: and only give you 5 licenses. What kind of stuff is that.


SIMPLE...
 Naturally the guy wants some dough for his troubles. Donations are exactly that, and are usually optional. 
If you find that you like the distro.... please consider a donation to help support it. That's just common courtesy.

[http://elive.leviathan-avc.com/stable/](http://elive.leviathan-avc.com/stable/) 
I just downloaded the latest stable Elive and tried to install it into a VM to see what's up with the donation thing.
You are right, He wants money for the Installer module (min of $15), but you are also given the option during install to get a code in exchange for writing a article about Elive on any website, and given examples of those who have already done so. 
But that is if you want to INSTALL it.
It runs all you want via live CD to try it.

OK here's what the Elive website says:
[I]**Hey, This is not FREE !**

  If you are a truly defender of the free software you must know better  what are you defending, you can [/I] *[start from here]("http://www.gnu.org/philosophy/selling.html").  Free software has no relation with gratis, please [read this explanation  from gnu.org]("http://www.gnu.org/philosophy/selling.html"). You need to know also that due to this confusion of  terms, the word **free software [has changed]("http://www.debian.org/intro/free")  to *[I]open source software in 1998.
  After that you know that free has no relation with cost. This payment  is required to pay the development of Elive, that is the full time work  of the Developer 'Thanatermesis' and also to pay external development  and/or services. Think that more money is made and more development can  be possible to pay and so, a better final product (Elive). But in any of  the cases, you are not obliged to pay for Elive, nobody obliges you to  use Elive. Without any cost, Elive would not be the same, at least not  with all its features, usefriendly things, and the lot of work involved.  By other side, if your problem is that you can't possibly pay for any  personal reason, we don't want to prevent anybody from using Elive so we  propose alternatives which are described in the payment process.
  Even if you are in face to a computer screen with thousands of  pixels, the result of the Elive Operating System is that is made by a  human person, a person that unfortunately are living in a  monetary-dependent system, in other words, who pay my taxes ? and not  only the taxes but also my roof and food if my only full-time work is to  make Elive. Im a truly and convinced defender of the venus project, it  proposes a future without money, unfortunately im not actually living on  any venus city, they doesn't exist right now, I would like to live in a  venus world and make Elive only for pleasure but the reality is that I  still on this world. If you really don't understand the point of the  payment, then I must say... "don't use Elive!", basically because nobody  obliges you to use it and because you don't like it!, so why to lost  time complaining ? if you really think that Elive is not worth of the  minimal requirement, why just don't ignore it ? I don't want to  monopolize the world with Elive, I do not care at all if you use it or  not, so just use anything that you want, you have thousands of  alternatives, you have the choice.
**The cost of the Installer Module**[/I]   [I]

  The cost of the Installer Module is a selectable value by the user,  but the minimum is set to 15 $[/I] [I]
**When will the next Stable version be  Released?**[/I]   [I]

  A problem with Elive is the perfectionism that it strives to achieve.  However Elive does not simply focus on perfectionism, as you may have  undoubtedly noticed a lot of work goes into adding features which result  to a 'never-finished' stable release. We are constantly trying hard to  come up with more fast stable releases with or without these features  (there's no problem to try to put them on the next stable release),  actually it is a lot of hard work to finish implementing the remaining  features and fix the bugs for the next stable version.[/I]  
-------------------------------------------------------------------

You might want to check this too:
[https://help.ubuntu.com/community/Enlightenment](https://help.ubuntu.com/community/Enlightenment)
[http://www.ubuntugeek.com/howto-install-e17-enlightenment-desktop-in-ubuntu.html](http://www.ubuntugeek.com/howto-install-e17-enlightenment-desktop-in-ubuntu.html)
[http://maketecheasier.com/run-enlightenment-e17-on-ubuntu-karmic/2010/01/14](http://maketecheasier.com/run-enlightenment-e17-on-ubuntu-karmic/2010/01/14)
[http://www.unixmen.com/linux-tutorials/764--install-enlightenment-e17-in-ubuntu-910-karmic-ko](http://www.unixmen.com/linux-tutorials/764--install-enlightenment-e17-in-ubuntu-910-karmic-ko)



Anyway...
Since we are pointing you at lightweight distros.... here's one that runs on bare metal and I have yet to find one Smaller...
[http://www.damnsmalllinux.org/](http://www.damnsmalllinux.org/)
**What is DSL?**

 **Damn Small Linux is a very versatile 50MB mini desktop oriented Linux  distribution.**

Damn Small is small enough and smart enough to do the following things: 
[LIST]
[*]Boot from a business card CD as a live linux distribution (LiveCD)
[*]Boot from a USB pen drive
[*]Boot from within a host operating system (that's right, it can run  *inside* Windows)
[*]Run very nicely from an IDE Compact Flash drive via a method we call  "frugal install"
[*]Transform into a Debian OS with a traditional hard drive install
[*]Run light enough to power a 486DX with 16MB of Ram
[*]Run fully in RAM with as little as 128MB (you will be amazed at how  fast your computer can be!)
[*]Modularly grow -- DSL is highly extendable without the need to  customize
[/LIST]

---

### Post by mastablasta on 2010-09-14
trouble with DSL is that development has stalled. otherwise it's great piece of work and i would like to see them continue and develop on this.

---

### Post by scottuss on 2010-09-14
DSL is pretty much useless in this day and age. I hate to say it because in theory, what they've achieved is awesome. A full distro in such a small package. However, it looks like c*** and development has ceased so it's going to get no better.

You can do the basics with it, but don't get into thinking it's anything near as good as a "full" distro.

---

### Post by webb1976 on 2010-09-14
I have used DSL before and it works great if all you to do is setup a box to do a task (like be a http, DHCP, DNS, mail server) really quick. 

I would not consider it great foreveryday use but it is EXTREMELY fast and compact for those purposes.

As for Elive, my main gripe with it is that you can only install it on 5 different machines. I was going to try it out on a virtual machine to see how I liked it and I ran into the whole 5 machine limit.

To me that sounds very Micorsoft. I guess I could go ahead and try it out anyway and say the heck with it.

---

### Post by snowpine on 2010-09-14
I gladly paid $15 for Elive. If you like the distro, it is a small price to pay. Charging money for your Linux distribution is 100% acceptable.

---

### Post by perspectoff on 2010-09-14
> **webb1976 said:**
> WOW:cool:

I had absolutely no idea you could get something anywhere near that smooth on a PC with a Pentium II proccessor in it. Heck I just got rid of a PC with an old Celeron in it that would have been perfect for that. I think I will run it virtual in a machine to try it out (should not be a problem at all).

I am VERY impressed by that. I wonder what type of browser comes with it.

I run several Ubuntu machine with multiple servers (currently Karmic Koala) on them (including a desktop) on Celeron. No problems. I probably won't get rid of them for quite some time. They are painful with Windows XP, but not Ubuntu.

---

### Post by perspectoff on 2010-09-14
I can't say I recommend Lucid Lynx for old machines. Too many of then use Intel integrated graphics or have other hardware issues that are going to give some headaches.

I really liked Hardy Heron on old, old machines, if one is recommending LTS versions.

Puppy Linux (based on the Ubuntu minimal installation) is also quite nice, if an alternative to Lubuntu (Xubuntu is nowadays too bloated and not a very nice desktop, IMO) is desired. DSL used to be superb for USB sticks, for example, that had little space, but, I agree, except for some embedded uses or a desire for extremely, extremely fast performance, DSL is probably not worth looking at anymore.

---

### Post by dzon65 on 2010-09-14
> **Jazzy_Jeff said:**
> If you think Firefox is quick try using open source Chromium or regular Google Chrome.
I have my FF tweaked to hit at least as hard as chrome.

---

### Post by webb1976 on 2010-09-14
> **snowpine said:**
> I gladly paid $15 for Elive. If you like the distro, it is a small price to pay. Charging money for your Linux distribution is 100% acceptable.

I don't mind the $15 so much as only being able to get 5 licenses for it. I was goingtotest it out on a virtual machine and THEY SUGGESTED you don't install in a virtual because there are one of oyur install attempts out the window. It seems that hosae 5 installs are by machine and so once you do it on1 you cannot install it on that one again.

To me that sounds a bit fishy.

But I am defintely going to check out Puppy Linux and give the a whirl.

Also, where can i find information about Edubuntu. There is a small organization that was donated about 20+ P4 Dell OPtiplexes (512 MB ram), that they want to ry and load educational software on. I wanted to check out what Edubuntu had so I could check it out.

---

### Post by snowpine on 2010-09-14
> **webb1976 said:**
> I don't mind the $15 so much as only being able to get 5 licenses for it. I was goingtotest it out on a virtual machine and THEY SUGGESTED you don't install in a virtual because there are one of oyur install attempts out the window. It seems that hosae 5 installs are by machine and so once you do it on1 you cannot install it on that one again.

Let me get this straight, you are not willing to pay $3 per computer for a stable operating system? :(

But maybe you are a little confused; you can test Elive in Virtualbox **for free**; you only have to pay if you want to install to your hard drive.

Also I see from their website they will waive the fee if you volunteer to help out with the project, or even just review Elive on your blog/website.

To be clear, I am not defending Elive (I don't even use it personally) but their price seems very low compared with Microsoft, Apple, Red Hat, etc.

---

### Post by scottuss on 2010-09-14
> **snowpine said:**
> Let me get this straight, you are not willing to pay $3 per computer for a stable operating system? :(

But maybe you are a little confused; you can test Elive in Virtualbox **for free**; you only have to pay if you want to install to your hard drive.

Also I see from their website they will waive the fee if you volunteer to help out with the project, or even just review Elive on your blog/website.

To be clear, I am not defending Elive (I don't even use it personally) but their price seems very low compared with Microsoft, Apple, Red Hat, etc.

But it has nothing to do with monetary value. I'd gladly pay £100 for Ubuntu, as long as it is as Free as it is now.

I don't oppose people making money from software, but I do oppose restrictions, DRM and proprietary closed source technology.

---

### Post by mastablasta on 2010-09-15
if you get only 5 installs with it that is actually a sort of DRM.

---

### Post by armandh on 2010-09-15
not every OS has a dot-com sugar dad.
but free is an Ubuntu +
and complex regi$tration is a big minus
this sort of greatly disadvantaged OS is why I rarly install XP

---

### Post by Jazzy_Jeff on 2010-09-15
I agree that the person who makes the distro should be able to charge for its use, but not regulate how many times you can use it. For this reason I would not even consider donating as he puts it to that distro.

If Ubuntu asked for a donation to use its operating system I would have no problems with it as long as I could put it on all of my machines as often as I wanted. I would be donating to the work being put into the product not a licensing fee.

---

### Post by snowpine on 2010-09-15
So if bread is on sale for $2, you should be able to pay $2 and then take as many loaves as you like? :)

---

### Post by Jazzy_Jeff on 2010-09-15
> **snowpine said:**
> So if bread is on sale for $2, you should be able to pay $2 and then take as many loaves as you like? :)

This means you are buying a license and not donating to the project.

---

### Post by webb1976 on 2010-09-15
See I don't mind donating to the project. 

As long as when i  donated I was allowed to download and install it as need be. But this  stuff is a bit silly. I don't mind supporting a project........and  sending a few pennies their way is fine. 

But the moment you  start doing DRM type stuff that changes the landscape for me. I don't  particularly care for being watched/monitored just to install the OS.  That just just doesn't sound right to me. Maybe some of you have not  used this so let me explain.

In order to install ELive the  installer gives you a code. You then have to login to their website  using that code to get the actual license. It then logs your current PC  and assigns it to one of your 5 licenses.  The reason they suggest you  don't use it on a virtual machine is because one of your licenses will  be used there and then when you attempt to install it natively on your  PC another one is used.

Maybe, I am wrong on this but something about that doesn't feel right to me. Oh well, I will be off to try Crunchbang

---

### Post by snowpine on 2010-09-15
Entering a code to activate your software is an old and widespread technique, and Elive did not invent it. Let's agree to disagree whether or not it is a legitimate business tactic. ;)

CrunchBang is a good choice (it's what I use on a couple of my machines) so no argument there!

---

### Post by Photonic Nature on 2010-09-15
OK, so they want a whole 3 stinking dollars per computer, really, is that such a big deal?
Elive used to be free back in it's earlier stages, but now since it is this guys only source of income, I really don't see a problem.
Especially at such a cheap rate. You could always pay over $100 USD for a single license of Winblows and have to upgrade your hardware too.
My God man, how many freaking cheap machines are you planning to deploy?
As if 5 weren't enough.

The whole point of this thread was to direct people to the available options for obsolete hardware to have fun with.

It is a cool distro and well worth the $15.

The problem with OSS is that it has attracted and spoiled too many people that now expect everything for nothing and want to cry :-({|= about some guy trying to earn a living for peanuts.

Just like the $2 bread comment above... If there weren't restrictions on how many loaves or machines you could have, what would be the point of charging money for your work?
If people are just going to take advantage of you and give out copies of your work, it defeats the purpose.

Would you pay $2 for unlimited bread and stay at the counter giving away the whole inventory for your $2 ?
Hey, as long as your hand touches it first, it's your bread right? And of course you could do whatever you wanted to do with it.
Would that store stay open for long?
Who is paying for this guys house, electricity, internet connection, hosting, car, food, etc... ???
Would you prefer to give him $15 and distribute his work to all your acquaintances under your special unlimited license and have the poor guy live on the street? 
Did you vote for Obama?

Just remember where you came from and that you can always go back to virusville using 'their' constant barrage of inferior OS' that you have to pay to upgrade.
[http://www.amazon.com/gp/search/ref=a9_sc_1?rh=i:aps,k:windows+7&keywords=windows+7&ie=UTF8&qid=1284599133]("http://www.amazon.com/gp/search/ref=a9_sc_1?rh=i:aps,k:windows+7&keywords=windows+7&ie=UTF8&qid=1284599133")

](*,)Man, Now I'm sorry I brought it up.

---

### Post by Jazzy_Jeff on 2010-09-16
If people wanted to give this away I am sure they could find a hack very easy. I don't mind him asking for money for his work, I would be glad to donate. But I am always tinkering with my computers and there are times I have to reinstall because I really messed something up. So I would have to keep paying for new licenses for the same computer. 

I don't see how the bread thing relates. How about going into a restaurant and paying 10 dollars for all you can eat and then they say ooops sorry, you can only have 5 portions. 

If people want to pay for this distro and don't mind that they can't reinstall on the same machines as many times as they want then go for it. I don't see a problem with it. I just won't do it myself. For me, I could not afford it. I have become disabled and live on a fixed income, so I can't afford to keep shelling out money. I do donate to different projects when I have the money.

And what does Obama have to do with it? He is being blamed for everything when most of the problems started before he took office. That is all I am going to say on that. I seems like you get upset very easily. I will pray for you to find peace.

---

### Post by snowpine on 2010-09-16
The Elive developer is a nice guy, if your hard drive dies and you need an extra license, he will probably hook you up. And if you can't afford the $15, you can volunteer to help with the project, or even just write an Elive review on your blog. You can even use your review to [share your thoughts on the payment system]("http://reddevil62-techhead.blogspot.com/2010/03/elive-20-topaz-gem-that-comes-at-price.html") if you like. :)

Personally, I gladly paid the $15 just to experiment with Elive for a few days. I like to test different Linux distros, and $15 is cheaper than a trip to the movies. If I were actually planning to use it as an everyday OS for a year, that's only 4 cents a day, or less than a penny a day per computer if installed on 5 computers!

---

### Post by webb1976 on 2010-09-16
> **Photonic Nature said:**
> OK, so they want a whole 3 stinking dollars per computer, really, is that such a big deal?
Elive used to be free back in it's earlier stages, but now since it is this guys only source of income, I really don't see a problem.
Especially at such a cheap rate. You could always pay over $100 USD for a single license of Winblows and have to upgrade your hardware too.
My God man, how many freaking cheap machines are you planning to deploy?
As if 5 weren't enough.

The whole point of this thread was to direct people to the available options for obsolete hardware to have fun with.

It is a cool distro and well worth the $15.

The problem with OSS is that it has attracted and spoiled too many people that now expect everything for nothing and want to cry :-({|= about some guy trying to earn a living for peanuts.

Just like the $2 bread comment above... If there weren't restrictions on how many loaves or machines you could have, what would be the point of charging money for your work?
If people are just going to take advantage of you and give out copies of your work, it defeats the purpose.

Would you pay $2 for unlimited bread and stay at the counter giving away the whole inventory for your $2 ?
Hey, as long as your hand touches it first, it's your bread right? And of course you could do whatever you wanted to do with it.
Would that store stay open for long?
Who is paying for this guys house, electricity, internet connection, hosting, car, food, etc... ???
Would you prefer to give him $15 and distribute his work to all your acquaintances under your special unlimited license and have the poor guy live on the street? 
Did you vote for Obama?

Just remember where you came from and that you can always go back to virusville using 'their' constant barrage of inferior OS' that you have to pay to upgrade.
[http://www.amazon.com/gp/search/ref=a9_sc_1?rh=i:aps,k:windows+7&keywords=windows+7&ie=UTF8&qid=1284599133](http://www.amazon.com/gp/search/ref=a9_sc_1?rh=i:aps,k:windows+7&keywords=windows+7&ie=UTF8&qid=1284599133)

](*,)Man, Now I'm sorry I brought it up.

Okay, the Obama comment is crazy........ what does that prove. Secondly, it does not make alot of sense to pay $$$ for an operating system that is designed to run on legacy hardware. If I had to pay for Ubuntu/Red Hat/ Mint I could understand that better.  I am not here try and start an argument..... and yes I can afford $15....but what if other distros wanted money just to try them out too 8-[

See you, have to think this out to its logical conclusion. I have nothing against OSS. My concern though is that this could be something problematic. I thought that the benefit of the Linux community is the ability to try out and see various distros. If other distros did the same thing what would the landscape look like :-k

I may still try ELive out, but to the casual person it is going to be a hard sell.

---

### Post by snowpine on 2010-09-16
> **webb1976 said:**
> Okay, the Obama comment is crazy........ 

Agreed, let's leave US politics out of this. :)

> **webb1976 said:**
> I thought that the benefit of the Linux community is the ability to try out and see various distros. If other distros did the same thing what would the landscape look like :-k

You can try and evaluate Elive for free; I'm not sure where you're getting this misinformation.

---

### Post by Photonic Nature on 2010-09-16
OK gang, it was a long bad day and I was frumpy. Sorry for ranting.
To each their own.
The Obama thing is just an inside feeler gauge for depth of character and intelligence that I use.
Take it to mean whatever you want, I'm Not going political on you, just feeling you out.
Further explanation and politics are not in the scope of this thread or forum.

Keeping with the scope of things, this thread is supposed to be informative without debate of topic.
My apologies again, for running my pie-hole in the wrong direction.

Thanks for the prayers.

Blessings to all.

P.S. 
Elive as we know by now, is built using Enlightenment... [http://www.enlightenment.org/p.php?p=about&l=en](http://www.enlightenment.org/p.php?p=about&l=en)
You may find many other distros and platforms using it.
Let's drop the elive debate.

---

### Post by Jazzy_Jeff on 2010-09-17
> **Photonic Nature said:**
> OK gang, it was a long bad day and I was frumpy. Sorry for ranting.
To each their own.
The Obama thing is just an inside feeler gauge for depth of character and intelligence that I use.
Take it to mean whatever you want, I'm Not going political on you, just feeling you out.
Further explanation and politics are not in the scope of this thread or forum.

Keeping with the scope of things, this thread is supposed to be informative without debate of topic.
My apologies again, for running my pie-hole in the wrong direction.

Thanks for the prayers.

Blessings to all.

P.S. 
Elive as we know by now, is built using Enlightenment... [http://www.enlightenment.org/p.php?p=about&l=en](http://www.enlightenment.org/p.php?p=about&l=en)
You may find many other distros and platforms using it.
Let's drop the elive debate.


I was just bored and was having fun with you...hehe. I apologize for taking over the thread to amuse myself. 

If anyone wants to try out Enlightenment I believe PCLinuxOS has a version available.

---

### Post by NightwishFan on 2010-09-17
I would not mind if distributions cost money. It makes sense to their own goals to "not" cost at times. Sometimes because they just like to have it offered to everyone at the same terms.

---

### Post by webb1976 on 2010-09-20
> **Jazzy_Jeff said:**
> I was just bored and was having fun with you...hehe. I apologize for taking over the thread to amuse myself. 

If anyone wants to try out Enlightenment I believe PCLinuxOS has a version available.

I actually am going to try out PCLinuxOS. It is interesting though how much RAM these "lite" OS's are starting to require. I am actually falling in love with my Ubuntu 8.04. It does everything I want it to do on my 256mb RAM machine.

The newer distros even using lightweight GUIs (tried Linux Mint using Openbox/LXDE) ran slower. I am going to give it another try as the slowness may be the result of it downloading a bunch of updates, but we will see.

As I said though, I will be taking a look at Crunchbang next and then PCLinux. Thanks guys for all your feedback. I can't tell you how much fun I am having getting the absolute max out of these P4 machines:P

---

### Post by scottuss on 2010-09-20
> **snowpine said:**
> So if bread is on sale for $2, you should be able to pay $2 and then take as many loaves as you like? :)

That analogy is not appropriate for several reasons.

There's nothing wrong with charging for software, and charging whatever you, as a developer, think that it is worth. 

But putting restrictions on how it is used is the issue.

Perhaps Bread Brand should tell me that if I buy their £2 loaf, I can't make toast with it? Or if I want to chop it to make croutons for my soup, the same loaf will cost me £5?

Also: bread costs every time to make. Loaf 1 costs the same to make as Loaf 2. Instance of software 1 costs to make, after that, instance n = no extra cost (development etc aside)

Conclusion: Your analogy is flawed.

---

### Post by snowpine on 2010-09-20
> **scottuss said:**
> That analogy is not appropriate for several reasons.

There's nothing wrong with charging for software, and charging whatever you, as a developer, think that it is worth. 

But putting restrictions on how it is used is the issue.

Perhaps Bread Brand should tell me that if I buy their £2 loaf, I can't make toast with it? Or if I want to chop it to make croutons for my soup, the same loaf will cost me £5?

Also: bread costs every time to make. Loaf 1 costs the same to make as Loaf 2. Instance of software 1 costs to make, after that, instance n = no extra cost (development etc aside)

Conclusion: Your analogy is flawed.

Agreed; all analogies are, by definition, flawed... if they were 100% accurate they would not in fact be analogies but precise statements of truth. ;) So let's stop beating around the bush with food-related analogies:

It is 100% legal and common business practice to limit the installation of software to an agreed-upon number of licenses, using either implicit (honor system) or explicit (activation code) means. Microsoft, Red Hat, Adobe, and many other software developers do so, and if anyone has ever successfully sued Microsoft and won the case that "my purchase of a single Windows 7 license allows me to install it on as many computers as I want" please provide a citation.

Furthermore, as a creative artist who earns royalties from the sale of my work, I take issue with your "it is immoral of the creator to expect payment for each copy of the work consumed" notion. If I have reacted strongly to the thread, now you know the reason why. :)

---

### Post by ventrical on 2010-09-20
The main thing is that  many of the LINUX FREE frugal systems can run older legacy PCs much more efficiently than other  ealier published commercial software and  it helps the end_user economy save money and inspires , perhaps, the underprivlidged and poor to take up PCeeing and surfing and allows a cheaper , older system to perform  with some 'thunder n' lighting' like the newer systems being sold.

  Lets face it.. LINUX OSes have mustard- unlike other OSes which are mostly heavy on the mayo.

  I mean .. you guys are talking bread - aren't you ? :popcorn:

---

### Post by mastablasta on 2010-09-21
not to meniton you can keep using the perfectly good old computer with new programmes. While in windows they (software makers) just don't support the old stuff anymore. for everything these days you must have Xp or preferably win7. if your computer can only run 2000 well cause it has only 256MB ram then what?

---

### Post by webb1976 on 2010-09-21
> **mastablasta said:**
> not to meniton you can keep using the perfectly good old computer with new programmes. While in windows they (software makers) just don't support the old stuff anymore. for everything these days you must have Xp or preferably win7. if your computer can only run 2000 well cause it has only 256MB ram then what?

Exactly.............. You just hit the nail on the head there. It's just a matter if your box is running the daemons/processes to get it done. And since the kernel cn be updated pretty much all the time, you can use these OS's for a while. I am DEFINITELY shocked at how well Ubuntu 8.04 is holding up :mrgreen:

You hardly breathe on a PC with those specs running XP (especially with any service packs on it)

---

### Post by ventrical on 2010-09-21
> **mastablasta said:**
> not to meniton you can keep using the perfectly good old computer with new programmes. While in windows they (software makers) just don't support the old stuff anymore. for everything these days you must have Xp or preferably win7. if your computer can only run 2000 well cause it has only 256MB ram then what?

Yes.. like with the frugal install - Lubuntu !! So like there is not giving one'self an ulcer waiting to get hit with malware or (explorer not responding)!! So that old PC can't really be obsoleted or destroyed by the WIn Domino effect.

And all your work from previous versions of Win can be recovered and archived on a USB or CD and this saves a lot of work from digging through old hard drives .. etc.. especially if you have a modder's or minimalist's mindset.

---

### Post by armandh on 2010-09-21
using an old slot 1 P-III, 800mhz, 100mhz FSB, 
256 meg PC 100 mem. AGP video with 16 meg mem, 
1.7 GB hdd, pci sound and lan cards

but running puppy 4.11
plays u tube music videos just fine

---

### Post by Chame_Wizard on 2010-09-22
Linux and oldies,always a good match.:guitar:

---

### Post by webb1976 on 2010-09-22
> **armandh said:**
> using an old slot 1 P-III, 800mhz, 100mhz FSB, 
256 meg PC 100 mem. AGP video with 16 meg mem, 
1.7 GB hdd, pci sound and lan cards

but running puppy 4.11
plays u tube music videos just fine

I really need to try Puppy out if it will work on a P3 machine. Thanks

---

### Post by perspectoff on 2010-09-22
> **Photonic Nature said:**
> AFAIK, The only problem you may have with running the latest releases on a P4 would be your choice of desktop environment. In which case Gnome usually runs fine but if you want something lighter you could opt for other available options such as Xubuntu which uses the lightweight XFCE desktop.
xubuntu.org:
[http://www.xubuntu.org/](http://www.xubuntu.org/)
Other derivatives:
[http://www.ubuntu.com/project/derivatives](http://www.ubuntu.com/project/derivatives)
[https://wiki.ubuntu.com/DerivativeTeam/Derivatives](https://wiki.ubuntu.com/DerivativeTeam/Derivatives)

The latest Linux kernels will not affect your system performance per se, but the desktop environment and software you choose will. 

Not running the latest versions may leave you open to security vulnerabilities and other issues.

Supported Hardware:
[https://help.ubuntu.com/10.04/installation-guide/i386/hardware-supported.html](https://help.ubuntu.com/10.04/installation-guide/i386/hardware-supported.html)

One other caveat is the switch to grub2 since v9.10.
However that will not affect performance, just tweaking annoyances.

Welcome to the awesome world of Linux. 
Enjoy and never look back!

Hardy (8.04) is still supported with updates and is a current version. It is not insecure. Don't give him inaccurate advice.

Further, brand new versions of software apps, in my experience, have as many bugs as very old versions, making them equally insecure.

I really like Puppy, but I saw another thread where a guy was trying to get a version that runs in only 160Mb RAM! 

I think only Lubuntu will run in 160 Mb RAM.

---

### Post by alanmoore78 on 2010-10-08
> **webb1976 said:**
> I really need to try Puppy out if it will work on a P3 machine. Thanks

I used Puppy two years ago on an eMachines eTower 600i with a Celeron II, 600MHz, Socket 370 (that's a whopping 66MHz FSB!).  256MB of RAM and a 6GB hard drive.  A single MB of video memory, even!  It was as snappy as a P4 1.8 with 2000 SP4 I had later (and is sitting to my right awaiting an Ubuntu install).  Sadly I left some slot covers off on the back and a mouse peed on the motherboard and killed it one night.

Puppy is great for a 128MB or 256MB machine, PII, Celeron II, PIII, even slower P4's.  Anything newer and Ubuntu has plenty of flavors that will work well.

---

### Post by armandh on 2010-10-08
ubuntu is my first choice of the linux distros. 

I have 9.10 working fine on a 933 P-III 512 meg of PC 133 mem and a 64 meg AGP video card, PCI sound/lan etc. Runs well, twirly cube and all!

BUT  

some older on board shared memory video just won't fly with compiz

I know this because I removed everything compiz when set up on the 933 and then moved the Hdd to the less capable machine. they are also ok with Ubuntu 8.04 and B4

Later than 8.04 ubuntu sans compiz worked fine until the first update.

puppy works fine on even less capable boxes than the 800 one I posted above but 800 is about the bottom for flash video and playing DVDs reasonably well.

a lot depends on the video capability!!!

fortunately some old onboard video is PCI along with an AGP slot for upgrade. my daughter has one of these as a back up box to her laptop.

---

### Post by Elfy on 2010-10-08
Thanks for participating - the OP has not been back for a fortnight. Closed.

---

