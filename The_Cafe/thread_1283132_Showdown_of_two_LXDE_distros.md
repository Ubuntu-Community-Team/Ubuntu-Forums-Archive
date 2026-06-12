---
title: "Showdown of two LXDE distros"
date: 2009-10-05
forum: The Cafe
---

### Post by Hallvor on 2009-10-05
PCLinuxOS LXDE vs. Debian LXDE

I was bored yesterday, so I wanted to compare the PCLinuxOS LXDE edition with Debian Lenny LXDE on my Dell GX240 (1,5 GHZ with 512 MB RAM).

PClinuxOS – install and first impression

Downloaded the image, and I was surprised it was that big. (I remember having tested TinyMe a while back, and that image was some 200 MB.) I made an install cd and booted it up. I then installed it to the hard drive. 

The artwork was quite nice and the desktop was intuitive and easy to use. Upgrading the system with Synaptic was as problem free as always. The Midori webbrowser was very snappy and nice, but I could not get the adblock filter to work. This is a big deal to me, since I often visit newspages with a lot of ads (both images and heavy flash content) that tend to choke the CPU of old computers. After a little googling, I found that the adblock filter will only work with a later version of Webkit. I them gave up and installed Firefox. After installing Firefox, I could understand why it was not chosen as default browser. It took 10 seconds to load, and I could feel the pain of my computer trying to load it. Adding an adblock filter to Firefox was easy, and visiting the same sites without ads made everything much better.

Checking the memory usage through free –m, I discovered that the memory usage was well above 100 MB on a the default desktop with just the console running. I found that a little strange since LXDE is very light, and thought that memory usage would be well below that. I tried turning off some services, and saw to my surprise that bluetooth was enabled by default. I turned everything off and rebooted, but still memory usage was above 100 MB. 

When playing an mp3, CPU usage went very high, and stabilized on 30-40%. I could not help feeling that the system was a little sluggish for everyday use.


Debian LXDE – install and first impression

Next up was Debian LXDE. This was an install CD, so it was not possible to see if it would run well on my hardware. (I am not sure of there even is a livecd for the LXDE edition.) The first screen greeted me and asked if I would like to install LXDE or XFCE (they are on the same CD), so naturally I chose LXDE and graphical install. Installing Debian is very straightforward, but I prefer to do the partitioning with a livecd and a tool I am comfortable with, like gparted. In this case I used the same partitions as with PCLinuxOS LXDE, so it was not a problem. The install went on and finished without a problem. On first boot the system felt very fast, but it was also a very basic desktop. On the other hand I like to add just what I need. I set up the repositories through leafpad (basic text editor), added nonfree and contrib in sources list, the Debian Multimedia repository and Debian Backports. Afterwards I made an aptitude update && aptitude safe-upgrade to install the latest upgrades. I then went on to install flashplugin, w32codecs and libdvdcss2 for flash, multimedia and DVD playback, along with VLC and Audacious. 

Debian LXDE uses Iceweasel as default browser. This is the same as Firefox, but it is rebranded because of licensing issues. All normal Firefox plugins will work on it. I added adblock plus, but had to go with a previous version since Debian LXDE still uses the 3.06 version. (Security is not a problem since xulrunner is updated regularly.) Iceweasel was much faster on Debian LXDE, and used about half the time to launch according to the stopwatch. Memory usage was just a little more than 50 MB on a vanilla LXDE desktop  – less than half of the PCLinuxOS LXDE edition. The desktop also felt much more reponsive than the latter.

The good

Both these systems were nice in their own way. The PCLinuxOS LXDE edition was very easy to use and should be very straightforward, even with no previous Linux experience. If you want to set up wireless, add a printer, and do a lot of other stuff, the chances are that there is a GUI for it in the PCLinuxOS LXDE edition and not in Debian LXDE. Another advantage was that flash and codecs worked out of the box in PCLinuxOS LXDE, and having a single repository and the latest packages is also very convenient.

Debian LXDE was on the other hand very light, and an ideal system for low-spec computers. RAM usage was very low, and I always had plenty of RAM available. The software is very stable and well tested and is often a little more conservative than the latest and greatest (since Debian Lenny was released in February 2009). That is a good thing for an old computer.


The bad and the ugly

It was sad to see that a distro like PCLinuxOS LXDE that I thought was quite lightweight indeed felt like a slug. I feel pretty confident that Debian with both Gnome and KDE 3.5 would run better on the same hardware than PCLinuxOS LXDE did. No wonder, since there is a GUI for almost everything, but I probably had high expectations because I thought it would be a little like TinyMe, that was both lightweight and had great config tools last time I tried it. PCLinuxOS LXDE is very easy to use and very convenient, but it is also very heavy and in my opinion that defeats the purpose of having a lightweight DE. There are many lightweight distros out there, but few that hit the nice compromise between lightweight and ease of use. TinyMe was in my opinion one of those, but sad to say PCLinuxOS LXDE only scores in ease of use in my book. Still, if you are tired of KDE and don`t want to use Gnome or XFCE, LXDE is very simple, solid and good looking, living up to classic GNU/Linux principles of KISS.

The bad thing about Debian LXDE is in the ease of use category. Sure, it was easy enough to install, but it is a distro for intermediate users. Anyone can use it after it is set up right, but configuring it is not straightforward if you are new to GNU/Linux. It is not much work to set up the repositories and install multimedia, and it can be done in a few minutes, but if you don`t know what to do you could be googling for a while. Other things that have a nice GUI for in PCLinuxOS LXDE, you`ll have to fix using the command line in Debian LXDE or editing config files. If you want certain hardware to work, like wireless, you may have to install the kernel module manually. I don`t know of many beginners who immediately would throw themselves at something like that.


… and the winner is..

The purpose of using a lightweight desktop environment like LXDE is in my opinion to run well on old computers, and only one of the distros did that. But if you prefer ease of use, you like LXDE, need the latest and greatest software in a rolling release distro PCLinuxOS LXDE may be a good choice. However, I wish that the team would remove as much bloat as possible, even at the expense of a little user friendliness. That way PCLinuxOS LXDE would be a good compromise between user friendliness and ease of use. LXDE is probably not the first choice of beginners anyway, so it should in my opinion be tailored towards intermediate PCLinuxOS users. That means they can probably turn on services like bluetooth themselves using the GUI or check Synaptic for updates without notification.

However, for use on an old computer Debian LXDE wins hands down because of superior performance. It is in my opinion also the only one of these two that is suitable for that purpose. Would I recommend it to a beginner? Probably not. Would I recommend it to my friends? Absolutely! Setting it up can be done in a few minutes after installation. Using it afterwards is as easy as using PCLinuxOS, Ubuntu or Linux Mint. If grandmother needed a distro, I could set it up in a few minutes and I`d know her computer would be all right for the next couple of years.

------------
Edit: For some other reason, all references to TinyMe were edited (not by me!) to read "TinyTurd" in the finished post on the PCLinuxOS Forum, before it was deleted: "We don't do this vs that anymore in the area because it tuned into a fan boys distro promotion area" the moderator explained.

---

### Post by Plumtreed on 2009-10-05
You have presented a precise, well considered review. While surprised to see it in the 'Cafe' I enjoyed reading it and I appreciate hearing your comments. Thank you!  

I don't know anything about the Debian LXDE but I have used PCLXDE which I thought excellent and really quite fast. I have always felt that when you take something like a main OS like PCLinuxos and produce a 'Lite' version like PCLXDE you merely reduce the number of programs used and, therefore, there is essentially no change in the 'speed' of an operating system. However, LXDE being quick, expresses the perception that the operating system is also faster.  

Did you find these systems faster for any reason other than the inclusion of LXDE?

---

### Post by Hallvor on 2009-10-05
Thank you! :)

> **Plumtreed said:**
> 
Did you find these systems faster for any reason other than the inclusion of LXDE?

Well, I must say that I enjoy applications like 
Xarchiver, Leafpad, LXterminal and the PCMan file manager. All of these are very light and fast, but I think there are large differences as to how much is installed by default and how the system is set up. I don`t think the core system is any different than the main distro. The Debian system is much cleaner but without all the bells and whistles. But because of this, there is lower CPU and memory usage with more juice to power the applications. Just my two cents.

---

### Post by mdmarmer on 2009-10-05
LXDE will also appeal to users who are dissatisfied with KDE 4 and Gnome.  Remastersys has a very nice LXDE distro which includes an excellent LXDE Control Panel. [http://www.geekconnection.org/remastersys/rll.html](http://www.geekconnection.org/remastersys/rll.html)

I'm working with some other folks on an easy-to-use LXDE (Debian testing) distro that will include all multimedia.  A (somewhat old) test .iso is here [http://www.filehosting.org/file/details/58563/canabix.iso](http://www.filehosting.org/file/details/58563/canabix.iso)
I'm planning to upload another test .iso soon.  This project is at [http://community.canabix.org/smf/](http://community.canabix.org/smf/) and [http://canabix.blogspot.com](http://canabix.blogspot.com) or on OFTC irc at #canabix

Mike

---

### Post by Plumtreed on 2009-10-05
In these forums there is a development that uses LXDE. Masonux is a very efficient use of LXDE with Ubuntu. Have you had a look at it? 

Interesting ideas, Mdmarmer, I will follow the developments on Canabix closely. It looks like a good concept.

Very few OS really offer any extra speed on older computers without some loss of functionality. Slitaz and Puppy operate in RAM and do go quickly.

---

### Post by XubuRoxMySox on 2009-10-05
The best of both worlds, and best implementation of LXDE in a truly lightweight Ubuntu-based distro that I have played with thus far is Masonux. It has none of the hiccups that my own rookie first-attempt at "Ubuntu Lite" has. It has the ease of PCLXDE for setup and installation, but the featherweight speed of Debian LXDE.

-Robin

---

### Post by doorknob60 on 2009-10-05
I haven't tried PSLOS LXDE, but maybe I'll try it out in Vbox sometime. I do know that Debian with LXDE works very well though. I run it on two computers with limited resources (a laptop with 192 MB of RAM and 450 HMZ CPU, and a Desktop with 128 MB RAM and a 700 Mhz P3) and it works great on both. Wireless works fine on my laptop too (don't remember if it involved additional setup, but I think I just compiled the madwifi driver, which is two or three commands, and takes only a minute or two. It has an Atheros PCMCIA card). It's not the easiest to set up, but for beginners you can't recommend Arch (that wouldn't end up well) so Debian is one of the better choices (I've helped people with no previous Linux experience install Debian over IM, although I've done that for Arch too I guess :P). Anyways, Debian LXDE is a great distro for old computers, and for people with Ubuntu experience (like people that are reading this), it shouldn't be too hard.

---

### Post by Plumtreed on 2009-10-05
> **dixiedancer said:**
> The best of both worlds, and best implementation of LXDE in a truly lightweight Ubuntu-based distro that I have played with thus far is Masonux. It has none of the hiccups that my own rookie first-attempt at "Ubuntu Lite" has. It has the ease of PCLXDE for setup and installation, but the featherweight speed of Debian LXDE.

-Robin

Well put,Robin! It is not just me then? I think Masonux is an excellent execution of an LXDE system. It combines the 'ease-of-use' of Ubuntu, including NetworkManager, with the dexterity of LXDE. I wonder where Lubuntu is going to go.

---

### Post by bodhi.zazen on 2009-10-05
I advise you try lubuntu.

If you want > the team would remove as much bloat as possible, even at the expense of a little user friendliness.This is what minimal installs are for .

[Minimal CD Image - Community Ubuntu Documentation]("https://help.ubuntu.com/community/Installation/MinimalCD") 

Minimal installs work that way for Ubuntu, Debian, Arch, Gentoo, Fedora, Slackware, ...

You get the idea.

If you are installing a distro, with a gui, you will always get unwanted features.

If you want to try a very nice minimal distro try Crunchbang lite or lubuntu.

If you want a minimal install go with Slitaz.

---

### Post by dragos240 on 2009-10-05
> **dixiedancer said:**
> The best of both worlds, and best implementation of LXDE in a truly lightweight Ubuntu-based distro that I have played with thus far is Masonux. It has none of the hiccups that my own rookie first-attempt at "Ubuntu Lite" has. It has the ease of PCLXDE for setup and installation, but the featherweight speed of Debian LXDE.

-Robin


Where have I seen your avvy before? I've seen it somewhere. [/offtopic]

---

### Post by NormanFLinux on 2009-10-05
PCLXDE runs quite beautifully on an HP Mini 2133 with a low powered Via CM-7 processor. It boots up fast and shuts down fast. A fully configured desktop doesn't appear sluggish.

---

### Post by PhoHammer on 2009-10-05
Great review! I can see you put some time into it.

> **bodhi.zazen said:**
> I advise you try lubuntu.


I thought that the lubuntu was a livecd only, no install to disk
option. Unless there is some secret Linux ninja install I don't
know about...yet. I'm sure there probably is.:popcorn:

---

### Post by NormanFLinux on 2009-10-05
Lubuntu can be installed to the disk from the command line by running ubiquity. That will bring up the installer. Its biggest shortcoming at this point is the lack of support for wireless cards.

---

### Post by Plumtreed on 2009-10-06
I didn't do any research before hand but as Bodhi suggested, I gave Lubuntu a try. All went well except that WICD couldn't detect my 'wireless'!

In my experience, WICD doesn't do well with USB Drives and things. I also recall that it will only work if 'wired' is not connected. So I would probably have to install Networkmanager.

Masonux has NetworkManager included so gets my vote at the moment.

---

