---
title: "My openSUSE honeymoon is over."
date: 2013-04-17
forum: Ubuntu, Linux and OS Chat
---

### Post by Roasted on 2013-04-17
Hello! Recently I got the urge to try out some other distros. Having a Debian PPC instance on an old PowerBook already, and being that I recently tried out Fedora and Arch, I decided to look elsewhere for another "top tier" Linux OS to tinker with. openSUSE came on the radar right away. In my reading I learned that they support Gnome and KDE rather equally, even though KDE is the default. I liked this outlook a lot as it made openSUSE come across as rather agnostic about things like this. I also loved how on the larger DVD it asked you which environment you want. I must say, 12.3 as a whole is a very solid openSUSE release. As time progressed I began to run into a few headaches that made me take a step back and ask "...really?" I've highlighted some of them below.

First off, my Nvidia drivers on my desktop just never worked. I would boot up and my system would go into a hard lock. I had no explanation for it and no idea what to do, nor did several openSUSE users I spoke to. I ended up having to do a reinstall. I did several manual installs, each time going through the installer slower to question "am I messing something up?" Each time I booted up, installed updates, installed Nvidia, and it tanked. Eventually I took an image snapshot of my SSD (root) drive and saved it on my file server. That way in a matter of two and a half minutes I was back online with a fresh install (SSD and gigabit LANs are great). Each time I tried different troubleshooting steps that I found online, but ultimately I got no where. Kernel 3.7 vs 3.8 did not make a difference in my experience either. 

Moving along, I fired up openSUSE on another system that I have here, which is a laptop with a Broadcom wireless card. It appeared as if no drivers were assigned to it out of the box because I saw no wireless entry in network manager. I looked on their online repository system, software.opensuse.org. It's basically their way of distributing PPAs, as most software there auto-installs a repo for updates in the future. It's actually a really awesome place to find 1 click installers for certain software, such as Restricted Formats, Nvidia drivers, and other programs that might not be in the default repos. I found the broadcom driver and installed it. Upon each reboot, my system went into a panic of some sort. I booted to recovery mode and it did the same thing there, making recovery mode useless in my case. Luckily, this was fixed by removing the wireless card, booting up, and upgrading from kernel 3.7 to 3.8. Then it was fine - but I still had no wifi networks.

Printers were another frustration. Any time I would add a network printer, I just had... nothing. I search via IP and it would not find my Epson nor HP Laserjet. I admittedly didn't try localhost:631, but I also felt as though I should at least SEE the printers when I directly scan via IP address. But in the end, no luck here, so I moved on to other issues I was experiencing.

I think the last straw was, honestly, the simplest problem of them all. I did not see gscan2pdf available to install. I looked on their online software search and found it, so I was pretty relieved. When I installed it the system flagged that it was missing a dependency, but this wasn't a dependency that seemed to be available to manually install. A quick Google search revealed quite a few people asking the same question, with most users saying "I just use xsane" or something else. There really is no comparison to gscan2pdf, so at this point I decided that was enough.

I know I'm going to come across as a real nit picker, but I admittedly had a few other quirks that I ran into as well. I'm sure some people may disagree with me here but this is just my 2 cents. I didn't like how the installer defaulted to automatic login. I know that's something simple, but really? It's just a checkbox, but I think good 'out of box' security would at least require a basic login. Secondly, the laptop I mentioned earlier is a Lenovo. I put an SSD on it. I let openSUSE do it's automatic partitioning and ran through the prompts. When I fired it back up it would not boot to my SSD. Even if I went into the BIOS boot menu and selected the SSD, it would not boot. No errors or anything, just simply... nothing. It would return to the boot menu in about 1-2 seconds and that was that. On a hunch, I remembered seeing a "Booting" section under the summary at the end of the installer, just before the point where you hit the final "install" (aka, yes I am sure). I ran through the installer again and got to the end where the summary was. It asked me if I wanted to install GRUB to / or to MBR. By default with that laptop, the automatic installer chose /, so it was booting off of the root drive. I switched it to MBR and it then booted fine when the installation was done. Now, I do admit, this is NOT a big deal - but as a Linux user of 7 years of multiple distros, it took me a couple seconds to pick up on this... and the big reason I was even aware of this was because I saw another user in the IRC channel talking about this. Another quirk was the fact that network manager was not enabled by default (instead ifup was enabled by default). Fortunately openSUSE/YaST does a good job of auto activating it, but you have to reboot first. So on my laptop, I boot up after the installation, but I have no connectivity and no network manager. From a basic user standpoint, I have no idea what's wrong except that I cannot connect. If I reboot, network manager came up by default then. This did not happen on my desktop, so I have to assume the system realized I had wireless-based hardware and it enabled network manager on those units. Nice touch, but... why not just activate network manager by default, and if the user wants, enable ifup by default instead with a simple click? Lastly, I found it strange that by default, I needed root override to manage a wireless network. I like the idea of locking it down if you were to put your system in front of a child to play with, but by default? Eh. Maybe this is just my 2c talking, but it's just how I feel about usability vs security. I mean, require root override for certain network manager tasks, but default to automatic login during the installer?

With my frustrations out on the table, I would like to give credit where it is deserved and say that openSUSE does an outstanding job in so many areas, such as their Gnome and KDE port. I also had several discussions with some core Gnome developers on openSUSE and they are a brilliant group of individuals. They work fast and accurate. I also loved how in the installer mdadm was supported out of the box. That way I could assign my RAID drive to mount to /home. In the regular Ubuntu installer, I must install without mounting /home, reboot, install mdadm, reboot (so mdadm comes online), catch the UUID of the array, assign it to /etc/fstab as /home, reboot - done. openSUSE made this step exponentially nicer, so they get a solid +1 there. I also loved their agnostic outlook on desktop environments in terms of supporting each one rather extensively. openSUSE is not a distro I would sneeze at running in the future, but right now, I like having my system boot without panics once I install certain drivers, and I like having my printers connect with relative ease. Unity is also turning out to really blossom, as Unity in 13.04 seems to have addressed a few frustrations I had with it in the first place. For the time being I may stick with Unity and see how things go. If all else fails, at least there's a decent KDE/Gnome/LXDE/XFCE alternative in the *buntu family.

At any rate, I think it's important to remember that each distro, each desktop environment, every piece of software we utilize in some way shape or form is a tool. In every given scenario it's only logical to use the best tool for the job. Think about it. Does a mechanic feel biased towards one tool or another? No - a mechanic doesn't care. The mechanic will pick up whatever tool needed to get that transmission bolted properly to get the job done so he can move on to the next repair. In the technology world, sometimes that special tool is Ubuntu, sometimes it's openSUSE, sometimes it's OSX, Fedora, Windows, or BSD. But for me, I think it's absolutely incredible to know that there's an operating system out there that is easy enough that Grandma can use, but advanced enough that I could use it as a core server. That's why I'm back. :D

---

### Post by carl4926 on 2013-04-17
It can be a learning curve whenever you distro hop.
But I'm sure you'll find it like home here and 13.04 is proving to be a great release

---

### Post by Roasted on 2013-04-17
> **carl4926 said:**
> It can be a learning curve whenever you distro hop.
But I'm sure you'll find it like home here and 13.04 is proving to be a great release

Truth be told, I've distro hopped quite a lot. It's kind of like a Chinese buffet to me. Tons of good stuff out there, but your plate is only so big. I always felt as though I did a pretty good job keeping an open mind when I went to other distros. Learning yum and zypper instead of apt-get is a bit of a curve, but it's all about associating the differences and similarities in how each component and feature works. I don't feel as though openSUSE had that much of a learning curve at all. Okay, I use RPM instead of DEB packages, and I use zypper instead of apt-get. I had a PDF of a zypper cheat sheet I found online which helped me substantially. Beyond that, Gnome Shell is Gnome Shell. I had a similar/identical environment on Ubuntu GNOME too. 

It's just... when I got down to actual usability, that's when I felt somewhat frustrated. My Nvidia drivers not working whatsoever despite the troubleshooting I tried, and the fact my printers never came up were small things that just amounted to a bigger picture. I don't want to come across as "I tried and failed cause I rage quit" in my trials with openSUSE, but after a while I start to question - what am I doing here? Ubuntu does all of these things I need just fine. Why am I elsewhere?

It was a recent G+ post from Linus Torvalds that kind of struck a nerve with me (in a good way) I guess. He had posted that he wanted some sort of pre-built home file server/backup system. He explicitly said I don't want to build anything, I want to open a box and have it done so I can spend my time doing other things. That comment was what got me wondering why I was fiddling with certain issues that just weren't existent on Ubuntu. Don't get me wrong, Ubuntu is not perfect, but on that note - what is? Like I said, I think the world of other distros and they all do a fantastic job, but I still have to do **my** job too... In most cases, less fiddle time = more work time. :)

---

### Post by deadflowr on 2013-04-17
I myself stopped distro-hopping a while ago, not because of the burden of getting stuff to work right, but because of the fact that updates, or what nots, here or there would render my efforts moot and I'd have to redo stuff again.( Kinda a long run on sentence there)
Ubuntu has been the only one which, when I set up drivers and such, has kept my settings for as long as I have the system set.(knock on wood)

But the simplicity of Ubuntu probably means, I do everything totally wrong on the other distros.

I've sowed my oats as it where, and found I like having things set, without having to reset them later on for no fault of my own.

---

### Post by smellyman on 2013-04-17
Opensuse has a great community, great tools, looks great, loads of support, great devs....

but always falls short for me.

they should dominate!

---

### Post by wildmanne39 on 2013-04-19
I do all of my trying out different disro's these days in virtualbox so I do not have to miss up my prodution machine.

It has been a long time since I ran SuSe but I could not get much help from there forum and that played a large part in me coming to ubuntu.

---

### Post by BigSilly on 2013-04-21
Total opposite for me. I've been playing with openSUSE for a while, since about 11.4 after the Ubuntu switch to Unity. Not because I dislike Unity or anything, but because a number of problems left me struggling to get Ubuntu to run without some problems. In general though, I stuck with Ubuntu because of the community of enthusiasts. There's always exciting software available on Ubuntu, and help if you need it. And this is still true.

But recently I completely switched over to openSUSE because of freezes and lockups with Ubuntu. And I think, just as I had with Ubuntu years ago, I'd spent enough time with the OS that I became completely accustomed to how it worked. Things that seemed obtuse at first made more sense over time, and are now second nature. And the real deal sealer is the fact that the hardware runs much better with openSUSE. It has better battery life, is faster and I haven't had any freezes or other nasty bugs. It's not perfect, no OS is. But I'd say, taking into account my admittedly limited Linux experience, that openSUSE 12.3 is the best distro I've ever used.

---

