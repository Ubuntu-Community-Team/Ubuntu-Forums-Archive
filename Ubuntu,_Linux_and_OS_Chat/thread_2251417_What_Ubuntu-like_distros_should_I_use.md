---
title: "What Ubuntu-like distros should I use?"
date: 2014-11-04
forum: Ubuntu, Linux and OS Chat
---

### Post by flaymond on 2014-11-04
I got an old laptop and planning to install latest version of Ubuntu (14.04 LTS). I'm a little bit curious when i find out some of the OS did'nt work fine on old pc in here [http://askubuntu.com/questions/493189/why-is-ubuntu-14-04-so-slow-on-my-laptop](http://askubuntu.com/questions/493189/why-is-ubuntu-14-04-so-slow-on-my-laptop).

Im using:
 acer-Aspire 4315  with
-Intel Celeron processor 530
(1.73 Ghz.533 Mhz FSB, 1MB L2 Cache)
-14.1" WXGA Acer Crystalbrite LCD
-Up to 64 MB Mobile intel Graphics Media Accelerator X3 100
-512 MB DDR2
-80 GB HDD

2 GB RAM

32 bit


Should I use Lubuntu? Kubuntu or others Linux lightweight distributions?
or should i stay with Ubuntu (I got same pc and running Ubuntu)


Im using Windows Ultimate 7 before I installed Ubuntu on my pc (I switch it because my pc is really slow and need to reboot)

---

### Post by Bucky Ball on 2014-11-04
*Thread moved to **Ubuntu, Linux and OS Chat**.*

Why not download the ISOs, burn them to a disk or USB, boot from that and try them out. All the Ubuntu flavours have a 'Try' option. Or you could install them as a virtual machine try them.

Be aware that a full hard drive install will be faster and a better computing experience all round. ;)

I use a [minimal install ]("https://help.ubuntu.com/community/Installation/MinimalCD")and xfce4 desktop environment on a modern machine, but that would be fine/ideal for a low spec machine. Try Lubuntu (lightest) or Xubuntu (light).

---

### Post by sudodus on 2014-11-04
> **Bucky Ball said:**
> *Thread moved to **Ubuntu, Linux and OS Chat**.*

Why not download the ISOs, burn them to a disk or USB, boot from that and try them out. All the Ubuntu flavours have a 'Try' option. Or you could install them as a virtual machine in your Windows setup and try them.

Be aware that a full hard drive install will be faster and a better computing experience all round. ;)

I use a minimal install and xfce4 desktop environment on a modern machine, but that would be fine for a poor spec machine. Try Lubuntu (lightest) or Xubuntu (light).

+1

See also this link and links from it

  			 			[Try Ubuntu (Kubuntu, Lubuntu, Xubuntu,  ...) before installing it]("http://ubuntuforums.org/showthread.php?t=2230389")

---

### Post by flaymond on 2014-11-04
Does Lubuntu and Xubuntu have Libreoffice (I found that LibreOffice is a WOW and better than Microsoft Office) and very suitable for programming? (I switch to Ubuntu because the powerful of the Terminal and other environment that good for programmers). I love if my system getting fast processing....but i hate it when programming features and options disappeared....Is it really big difference between Ubuntu,Lubuntu,Xubuntu

---

### Post by sudodus on 2014-11-04
LibreOffice is very easy to install into Lubuntu (and is tested, so compatible). These flavours of Ubuntu have the same engine under the hood and can use the same application programs. You can install them from the Software Center, Synaptic, or with the terminal window (for example)

```
sudo apt-get install libreoffice
```

The 'only' differences are

- different desktop environments
- different selection of default application programs (but the same programs are available for all flavours of Ubuntu)

Edit: try them live, and install what suits you best :-)

---

### Post by Bucky Ball on 2014-11-04
> **InterProg said:**
> Is it really big difference between Ubuntu,Lubuntu,Xubuntu

Yes. The desktop environment and the default apps are the difference mostly. These are the flavours supported on these forums: Ubuntu, Kubuntu, Xubuntu, Edubuntu, Lubuntu, UbuntuGnome, Ubuntu Studio, and Mythbuntu.


Have a look at the [minimal install link]("https://help.ubuntu.com/community/Installation/MinimalCD") I gave in my last post. It might grab your interest. All the flavours are based on the base kernel. You then add what you like to that. So the flavours are a bunch of stuff on top of the base kernel.

With a minimal install, you get the base kernel, then you install only the things you want/need. That includes desktop environment and all apps. It is a learning curve, but a good one.

---

### Post by flaymond on 2014-11-04
Ohh! Nice! Thank you! I really feel 'good' when you say that every Ubuntu distros is based on same engine...and ty to you both moderators...its very detailed information!

---

### Post by vasa1 on 2014-11-04
> **sudodus said:**
> ... Xubuntu comes with LibreOffice, ...
I think it has Abiword + gnumeric: [http://packages.ubuntu.com/utopic/xubuntu-desktop](http://packages.ubuntu.com/utopic/xubuntu-desktop)

---

### Post by sudodus on 2014-11-04
You are right vasa1. I have been using my Xubuntu desktop for so long (and using LibreOffice) so I have completely forgotten, that I installed it separately.

(I checked in 14.04.1 'Trusty'. It comes with Abiword and Gnumeric too, so it is not only in 14.10 'Utopic')

---

### Post by stalkingwolf on 2014-11-04
I use mint 13 on hp minis with similar specs and it works just fine.  You can find people here that use all manner of buntu flavors and forks.

---

### Post by Bucky Ball on 2014-11-05
> **stalkingwolf said:**
> I use mint 13 on hp minis with similar specs and it works just fine.  You can find people here that use all manner of buntu flavors and forks.

Hehe, very true. I have a minimal install with pcmanfm as file manager (Lubuntu), xfce4 desktop environment (Xubuntu), lxterminal (Lubuntu), Leafpad, Libreoffice, Thunderbird, etc. etc. I just use what a like and I like hybrids! Been doing it this way for a few years and suits me perfectly as I can create the monster I want (eat your heart out, Dr Frankenstein!).

---

### Post by flaymond on 2014-11-05
Hey, now i downloaded the Lubuntu .iso file..adn ready to boot....btw...i had try lubuntu dekstop on my ubuntu running pc......its not so good ( for me at least)...and i found out on Internet that Xfce (Xubuntu default desktop) getting popular an told that the Xfce is so 'user-friendly). Now my question is....how can I install Xfce desktop without package on Lubuntu? (i want download the softwares by myself and i want the Xfce destop environment)

---

### Post by Bucky Ball on 2014-11-05
You simply open a terminal and:

```
sudo apt-get install xfce4
```

Substitute 'lxde' for 'xfce4' for the Lubuntu desktop environment. Log out, choose 'xfcesession' from the Sessions menu, log in. That's it. ;)

DON'T install *buntu-desktop anything! That drags in ALL default apps and dependencies and everything else and is like installing the whole of Xubuntu as well as Ubuntu. Bloat, redundancy, and not needed.

You only want to try the desktop environments, by the sounds of it. If you want to try Xubuntu, run in a virtual machine or make a disk, or USB, boot it and 'Try Xubuntu'. If you like it, install to another partition (you can have as many installs as you like, within reason - I have three installs and three spare partitions for playthings). 

Installing Ubuntu then lubuntu-desktop and xbuntu-desktop is going to get messy. Just the DEs or try from install media. ;)

---

### Post by flaymond on 2014-11-05
Now im typing using Lubuntu (in 'trying' mode) and the perfomance is very efficient, very fast, simple and lightweight......I will try your method..I hope it work just fine and dandy just like now (Super Fast OS ever i try..and i will make this flavour as my default OS for this PC)...and Thanks for all advance! You guy help me so much in customizing and settting up my new Unix-like os! :p

---

### Post by Bucky Ball on 2014-11-05
No probs.  It will be faster when installed to a partition and an all round better experience. ;) Being able to make your own choices is one of the things a lot of people love about Linux and there must be SO many unique setups out there. Enjoy. Minimal install next. :shock:  ;)

---

### Post by bro2 on 2014-11-05
Really just get whatever has your favorite default DE/Kernel version and such. For example, Elementry OS looks awesome, but its latest version is based on Ubuntu 12.4, so that's making me hesitate on trying it since the Radeon drivers there are probably just a file called feces.sh.

---

