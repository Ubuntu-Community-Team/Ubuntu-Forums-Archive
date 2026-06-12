---
title: "Whatever happened to Xubuntu?"
date: 2009-10-03
forum: Testimonials &amp; Experiences
---

### Post by dawynn on 2009-10-03
I still see this in the Ubuntu mailings:
"Xubuntu 9.10 comes with the light-weight Xfce 4.6 desktop environment to provide a desktop designed for productivity while conserving system resources."

Yet, I also see this from Linux magazine:
[http://www.linux-mag.com/cache/7520/1.html](http://www.linux-mag.com/cache/7520/1.html)
"The Xfce desktop is very lightweight and well suited to machines with small amounts of memory and processing power, but Xubuntu’s implementation has essentially massacred it. They’ve taken the beautifully lightweight desktop and strangled it with various heavyweight components from GNOME."

Wow.  In these side-by-side tests, the distribution that claims to be the "lightweight" distribution weighs in heavier than a distribution aiming at mainstream and top-of-the-line machines.

Personally, I've tried !# (Crunchbang) and found that its not quite my thing, but it was close.  Adding lxde helped a bit.  I'm willing to give this Lubuntu thing a go when it comes out, but I'm wondering what happened along the way?  Where did Xubuntu go wrong.

Just so this doesn't turn into a complete flame war.  Please try to keep comments constructive.  What lessons can we learn from Xubuntu?  What could a "lightweight" distribution do to *stay* a lightweight distribution?  What could Xubuntu do to return to being a lightweight distribution?

I, personally, think it would be cool if Xubuntu and Lubuntu started a friendly competition to see who could have a functional desktop, with the lowest hardware requirements.  I've enjoyed restoring some old computers, and would love to have *ubuntu-based choices for which gui frontend I install on older PC's.

---

### Post by snowpine on 2009-10-03
Xubuntu is simply Ubuntu with the Xfce desktop environment (instead of Gnome). Ubuntu is not a "lightweight distro" by any stretch of the imagination, and neither is Xubuntu. I'm not sure why so many people find this surprising...

If you want a truly "lightweight distro" for ancient hardware, your best bet is something designed to be lightweight from the ground up (like Puppy or SliTaz). The first version of Ubuntu was released in 2004... why should Canonical have any obligation to support hardware more than 5 years old?

Xubuntu is a great choice for a user with modern hardware who happens to prefer Xfce to Gnome/KDE.

---

### Post by betolima on 2009-10-03
I don't know .. I run Xubuntu and it's pretty fast and light .. right now I have 335 Mb of RAM occupied and I have firefox, amsn running .. I 'm also running Awn .. And it feels like it would run well on poorest processors too (maybe without Awn) .. 

Anyway, as long as that's the last upgrade of this system, you have to agree that it's a very good performance if compared with the recent options (mean Vista) .. you'll be only able to run on a old machine CompetitionXP or Competiton95 ... And, in fact, Xubuntu is lighter then Ub.. or Kub..

---

### Post by RedSquirrel on 2009-10-03
> **dawynn said:**
> I've enjoyed restoring some old computers, and would love to have *ubuntu-based choices for which gui frontend I install on older PC's.

In that case, try a minimal installation and add your favourite window manager (or desktop environment). For example:

[http://psychocats.net/ubuntu/minimal](http://psychocats.net/ubuntu/minimal)

In place of icewm, you could use fluxbox, openbox, xfce4, etc.



> **snowpine said:**
> Xubuntu is simply Ubuntu with the Xfce desktop environment (instead of Gnome). Ubuntu is not a "lightweight distro" by any stretch of the imagination, and neither is Xubuntu. I'm not sure why so many people find this surprising...

A few years ago, Xubuntu was light but somewhere along the way they started adding a bunch of heavy stuff to it.

Unless the machine is really ancient (and underpowered), an Ubuntu minimal installation with a light WM can run quite well on old hardware.

---

### Post by loudog23 on 2009-10-03
Hi,
As Redsquirel mentionned, a minimal install is great and actualy easier than you might think
Have a look here -> [http://ubuntuforums.org/showthread.php?t=1281934](http://ubuntuforums.org/showthread.php?t=1281934)

To answer your question, actualy i don't know sine i only use gnome. But i have to admit i would like a minimal distributin with auto wifi and desktop only.

EDIT: I 'cleaned' my post and made a little how to instead

---

### Post by RedSquirrel on 2009-10-03
> **loudog23 said:**
> Hi,

I just setted ubuntu on and 600mhz 512mb ram laptop
total mem usage under 100 mb

Here what you do:
1. Download ubuntu server edition

The [Minimal CD]("https://help.ubuntu.com/community/Installation/MinimalCD") is pretty nice. It's only about 10 MB. :)

---

### Post by ikisham on 2009-10-03
loudog23, that was very synthetic of yours. Congratulations.

#! (specially the lite version which comes only with the most commonly used software) is actually a Ubuntu minimal with a thought out configuration of Openbox. Unfortunately its looks is not for everyone. Also if one has, say, only cable network, then there's no need for the Network Manager applet which, from my observations, can use up to 10+ MB of RAM.

dawynn, if you like you could try a minimal installation (use loudog23's guide, only with the minimal iso instead) and add xfce instead of gnome-core. I only recommend that if you use karmic wait for the final release.
I know you were actually asking about Xubuntu...

---

### Post by Hallvor on 2009-10-05
> **snowpine said:**
> Ubuntu is not a "lightweight distro" by any stretch of the imagination, and neither is Xubuntu. I'm not sure why so many people find this surprising... [...] Xubuntu is a great choice for a user with modern hardware who happens to prefer Xfce to Gnome/KDE.


Search for Xubuntu on google, and you`ll find this: "An official version of Ubuntu Linux that uses the XFCE desktop environment. **Designed for low-specification computers**." 

Xubuntu has been hyped to be a good choice for low spec computers all along. It is not that light, and not suited at all for low-specification computers imho.

---

### Post by Lampi on 2009-10-05
try fluxbuntu ... THIS is lightweight :)

---

### Post by Bucky Ball on 2009-10-05
> **dawynn said:**
>   I've enjoyed restoring some old computers, and would love to have *ubuntu-based choices for which gui frontend I install on older PC's.

You already do. Install packages you want with CLI install and load the desktop environment of your choice. I think there is the option for a command line install on the install cd.

You can also use the minimal install cd and I think that gives you a choice too.

---

### Post by darrenn on 2009-10-05
Here is an excellent article from distrowatch on how to make a really fast xubuntu. 

> Minimal Xubuntu 9.04

Last week we took a look at how two distributions can be so very different even though they are based on the same technology (and even the same distribution). What we found was that the Ubuntu variant, Xubuntu, which comes with the Xfce desktop, used more than twice the amount of memory over Debian's implementation of the same desktop. The major difference came at the time of loading the desktop, where Xubuntu used almost ten times as much memory. Yes, almost 10 times (well, actually around 9.314705882 times). So why? Where does all this extra usage come from? Essentially it is due to Xubuntu's use of numerous services from the Ubuntu desktop environment, such as their graphical package manager and updater, network manager, power manager, proprietary driver manager and more, all of which use more memory. Debian on the other, chooses to use the software which comes with Xfce by default.

So, does that mean all is lost? Not at all! The comparison was between two end products - Xubuntu 9.04 and Debian 5.0.1 Xfce. As you can see not all products are created equal, but there's no reason as to why we cannot perform a more customised Xubuntu install. This would allow us to pick and choose the packages we want, therefore making it more lightweight. DistroWatch has previously published a few other similar HOWTOs, one for minimalist Ubuntu 8.10 and another for minimalist openSUSE 11.1. If your computer is a desktop machine which sits on a local network, why does your system need a resource-hungry service like NetworkManager? If you don't have any hardware in your machine which needs proprietary drivers, then why have jockey installed? As you will see, Xubuntu can be just as lightweight as Debian!

To do this, it's best to start from a small base and work your way you up. If you'd prefer to install the full Xubuntu and then reduce it, you can do that too! The main down side is that you need to know what the major packages are in order to remove them and their dependencies. Some packages will share the same dependencies, so removing one package will not remove the dependencies of the other, which is of little benefit. It will not be as lean as starting from a small base and working your way up, but it does have the benefit of not needing to perform the more tricky ncurses based install. Remember that if you start with a basic system, you can always get the full desktop by installing the xubuntu-desktop meta package. In fact, this is a great way to work out what packages included in the full Xubuntu desktop are missing from your minimal install. Running this command will show what packages Xubuntu wants to pull in, which you can then take note of and install the ones you want manually.

Xubuntu 9.04 command-line install

Xubuntu 9.04 command-line install
(full image size: 8.5kB, screen resolution: 471x258 pixels)

Get yourself an Alternate Install CD of any Ubuntu 9.04 flavour and boot to it. At the boot prompt, press the F4 key to bring up the install mode submenu. Using your keyboard, select Install a command-line system. Once the system has booted to the text based installer you are ready to begin. Select your language, location and then configure your keyboard. If you are using DHCP to automatically assign network addresses then you should receive an address, else you will need to configure your network manually. Enter a hostname and configure the clock. Partitioning your hard drive should be the same as other installs, just take extra care if you're not using a blank new hard drive. Create a new user, enabling an encrypted private directory if you wish. Set the clock and reboot the computer. You should now have a minimal Xubuntu install which we are going to tweak further.

This basic system was just a terminal login and needed a minimal Xfce environment for comparison to the others. To achieve this, I needed the following packages; X.Org, the GNOME Desktop Manager and Xfce itself. These were easily installed with the following command:

     $ sudo apt-get install xorg gdm xfce4 xfce4-goodies

After the installation was complete, rebooting the system booted to Ubuntu's GNOME Desktop Manager which allowed a log in to Xfce. Naturally at this point the system is very bare, but it represents the most basic Xfce system available. This is the system that is compared in the tables below as Xubuntu 9.04 (Minimal). The other test that I did was to install all the same packages that Debian Xfce installs to get their desktop, but under Xubuntu. These results are also in the table below as Xubuntu 9.04 (Debian package list).

Xubuntu 9.04 Minimal Xfce desktop

Xubuntu 9.04 Minimal Xfce desktop
(full image size: 8.5kB, screen resolution: 800x600 pixels)

So how does this base install compare? Last week we saw that the major difference comes when Xubuntu loads the Xfce desktop. You can see this has been substantially reduced and is much more close to the times under Debian.

Time Taken
Distribution 	Single Mode 	GDM 	Desktop 	Firefox 	Total
Xubuntu 9.04 	18.60 sec 	11.45 sec 	25.48 sec 	12.09 sec 	67.62 sec
Debian 5.0.1 	17.82 sec 	14.62 sec 	10.46 sec 	5.41 sec 	48.31 sec
Xubuntu 9.04 (Minimal) 	16.39 Sec 	15.27 Sec 	11.12 Sec 	6.56 Sec 	49.34 Sec
Xubuntu 9.04 (Debian package list) 	18.33 Sec 	20.44 Sec 	11.21 Sec 	6.69 Sec 	56.63 Sec


Memory Usage
Distribution 	Single Mode 	GDM 	Desktop 	Firefox 	Total
Xubuntu 9.04 	13.03 MB 	39.41 MB 	63.34 MB 	24.82 MB 	140.60 MB
Debian 5.0.1 	11.58 MB 	26.96 MB 	6.8 MB 	19.61 MB 	64.95 MB
Xubuntu 9.04 (Minimal) 	12.20 MB 	25.06 MB 	13.65 MB 	20.90 MB 	71.81 MB
Xubuntu 9.04 (Debian package list) 	13.02 MB 	24.56 MB 	16.14 MB 	22.00 MB 	75.72 MB


So, the basic Xubuntu install with X.Org, GDM and Xfce is very similar to the default Debian Xfce system. From there, one can begin to expand the environment to make it prettier and to add functionality as required. As mentioned, I also tested Xubuntu by installing the same packages as Debian. When this happened, Xubuntu starts to once again increase its memory usage. Debian's default Xfce system installs 627 packages, while a command-line Xubuntu system with that same package list installed has 807 packages. This suggests that the binaries under Xubuntu are built against a greater number of libraries, which therefore pull in more dependencies. The benefit is broader compatibility and functionality, at the cost of efficiency.

The complete Xubuntu desktop does look stunning, so to get that look from a minimal install one simply needs to install the xubuntu-default-settings meta package. This will then pull in all the artwork and packages required and configure the system, giving that lovely looking desktop. Keep in mind that while extras are pulled in from Xubuntu, they will start to increase the amount of memory used. The base install is pretty nice and light, but what happens when I start adding some of the packages included in the default Xubuntu install? Some of the services that Xubuntu includes out of the box which contribute to its extra memory usage are: the artwork including Usplash, NetworkManager, the GNOME application installer and system updater, the proprietary driver manager, Jockey, and the power manager from GNOME. I installed each of these in order, to see how much extra memory was consumed at each step.

    * The package xubuntu-default-settings, which pulls in usplash and artwork, etc, increased memory usage by around 15MB.
    * The package network-manager, which pulls in avahi, bluetooth, cups, samba-common, wpa_supplicant, etc, increased memory usage by around 10MB.
    * The package gnome-power-manager, which pulls in gvfs, gnome-mount, etc, increased memory usage by 3MB.
    * The package update-notifier, which pulls in launchpad-integration, snaptic, update-manager, etc, increased memory usage by around 8MB.
    * The package gnome-app-install, which pulls in GNOME icons, python-launchpad-integration, etc, increased memory usage by around 9MB
    * The package jockey-gtk, which pulls in nvidia-common, scripts, python-inotify, etc, increased memory usage by around 11MB.

These numbers are very approximate, but you can see that the more you introduce, the more resources you need. Keep it simple by adding what you need, or removing what you don't.


Conclusion

Xubuntu is a great distribution, but its default selection of packages does not necessarily suit itself to low-memory systems. By performing a command-line install and building from there, users can achieve a much more lightweight system while still taking advantage of all that Xubuntu has to offer. This method provides an install that is much closer to the Debian system we compared Xubuntu with last week. Out of the box, these two systems are very different, but break them down to the core and they are much more evenly matched. One of the great things about Linux is that you're not stuck with what someone tells you to use. You have choice and you have the freedom to make your system whatever you want it to be!

---

### Post by Bucky Ball on 2009-10-05
Good read but better to provide the link than duplicate info.:)

The article suggests you use Gnome. Why not Xfce4 - that is the lightweight part.

---

### Post by darrenn on 2009-10-05
Link to original article. 

[http://distrowatch.com/weekly.php?issue=20090504](http://distrowatch.com/weekly.php?issue=20090504)

> The article suggests you use Gnome

Not sure what you are talking about... do you mean about how they are installing the gnome gdm? Yeah its not the entire gnome desktop that they are installing.

---

### Post by random turnip on 2009-10-05
Xubuntu is a nice environment for slightly out of date computers that can't quite run full Ubuntu.  It's hardly designed to be ran on machines with hard drives smaller than todays average RAM.

---

### Post by dawynn on 2009-10-05
Thank you all for very informative responses!  You've given me some new ideas to try.

Actually, I have no interest really in restoring machines from much further back than the P3 era (high-end P2's, *maybe*).  My own home desktop is about the early P4 era.

I do like the light aspect though.  My wife's laptop is a dual-core, but I installed linux mint XFCE edition (another Ubuntu spin-off).  After reading your responses, I'm thinking some of these ideas might help reduce resource usage, even in her resource-plentiful machine.

Thanks much!

---

### Post by fela on 2009-10-05
Try a minimal install of Gentoo, or better yet Tiny Core Linux, and you'll think that all *buntus are bloated pigs.

It's all to do with what you do with your computer and what your computer can handle. *buntu is good if you want a full featured operating system with lots of software already installed, but TCL is good for very basic hardware. Gentoo is good for just about everything as long as you're a good OS modder and know your way around.

---

