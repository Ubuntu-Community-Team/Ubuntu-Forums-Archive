---
title: "new user thoughts"
date: 2007-05-08
forum: Testimonials &amp; Experiences
---

### Post by silent1643 on 2007-05-08
install:
so far im still new to ubuntu, about a week into it and i must say i did run into a few problems trying to dual boot with my xp machine. Mainly having partition errors with partition magic prior to the unbuntu install and then again with gparted. So after bypassing the general errors i received from gparted i continued with the install and was able to get ubuntu installed completely. However this also left my xp partition marked "unallocated space" and eventually just ended up formatting and resizing the ubuntu partition so now i only have ubuntu installed. 

My first thoughts of ubuntu, once i was logged into the desktop, was it was very simple and minimalistic at first glance. The use of the add and remove feature was one of the first things i browsed through along with the automatic update function. Eventually i found my hardware settings and noticed that everything was found automatically by ubuntu, which was great. I also noticed that my internet was working right away and was suggested by some forum members to get automatrix which would help me install additional software. Automatix was helpful because for some reason i couldn't install flash from the firefox browser. After doing this i read up on some windows equivalent software apps for linux and played around with gimp and open office and was impressed. Setting up my pop email in evolution was a breeze coming from an outlook environment, and was able to run this program in the system tray using the alltray application.

Some things that i started to notice a few days later were mainly visualization changes that i wanted to try wouldn't work. ATI drivers for one had known bugs and were still being worked out for future version, bummer. I tried to enable desktop effects BAM whole screen goes white for less than a minute. "Okay want try that again, Guess my drivers want work afterall". This was kind of a downer since i was looking forward to playing around with some of these eye candy apps. So i couldn't use combiz and i couldn't use beryl without following a series of un guaranteed configurations. So im pretty much left with only gnome themes and was able to find a few on gnome-look.org with ease of install thanks to the theme manager in ubuntu which was nice.

Another problem i did run into was replacing an icon png image under the file system, i did not have the correct permissions, thanks to the sudo function. I can see the use for this function, but would rather be able to turn it off and on easliy. Or at least prompt for a password when viewing the file system which would then enable all privileges.  I got around this by using the graphical sudo recommended by a forum patron. Now i can edit any files on my system. "Yay i feel like i own my system again". 

On the last few days i decided to install my digital camera, i was surprised that ubuntu found my camera as soon as it was plugged in and ask me if i wanted to transfer the pictures. +1 brownie point for ubuntu. Next i will see if it will find my flash memory cards.

So overall i like ubuntu, i feel less connected and strapped down to programs i would normally pirate (just being honest) and then worry if the install had a virus on it or was sending information across the net. Being away from Microsoft seems pleasant as well, I needed a change. I just wish the video card issues alot of people were experiencing were fixed. I really wanted to run beryl (even tho its still in early development), or at least compiz. Wonder how this issue will affect any games i try to play in the future?

So yes you could say i agree with this [article]("http://www.extremetech.com/article2/0,1697,2124101,00.asp") to a point. It all depends on your hardware if your going to love ubuntu or not. If you dont mind working around a few bugs, or getting help from ubuntu forums. If your quick to throw your mouse at the screen and punch a hole in the wall because you can't find the answer right away, you might want to just try out the live cd. For now im going to stick with ubuntu as a learning experience for myself, and hopefully with the next release everything will be worked out.

until the next release:
ubuntu team should focus on getting as much hardware compatable as it can including wireless internet.
focus less on graphical desktop experience and do what you say "it should just work"

---

### Post by Done_Fishin on 2007-05-08
I agree with you, Ubuntu is a nice breakaway fom MS.
my complaints are that I add usb disks or s second hdd and it won't see them automatically. I have found that i need to boot into Gparted then it sees the xetra disks but still only displays my NTFS image with read only permissions. Haven't figured out yet how to add a disk ( like I would in windows) and get an automatic read write access to partitions. I know it's all new and the info is out ther but it's buried under the correct phraseology whilst I have to guess at what it is.
I Booted Gparted from Live CD split my disk into partitions and then got asked how to manipulate them ? Blank, /, boot, usr, var .. what are all these things .. websearch to find a site .. I have already got an install running but wanted to do it over. it didn't run the same way because the first time I went manual an d created just 2 partitions, the next time round I created more including an extended partition & logical drives. At the point I wa being asked how to label the drives I dropped out!! Insufficient info and no help files.

---

### Post by silent1643 on 2007-05-09
> **Done_Fishin said:**
> I agree with you, Ubuntu is a nice breakaway fom MS.
my complaints are that I add usb disks or s second hdd and it won't see them automatically. I have found that i need to boot into Gparted then it sees the xetra disks but still only displays my NTFS image with read only permissions. Haven't figured out yet how to add a disk ( like I would in windows) and get an automatic read write access to partitions. I know it's all new and the info is out ther but it's buried under the correct phraseology whilst I have to guess at what it is.
I Booted Gparted from Live CD split my disk into partitions and then got asked how to manipulate them ? Blank, /, boot, usr, var .. what are all these things .. websearch to find a site .. I have already got an install running but wanted to do it over. it didn't run the same way because the first time I went manual an d created just 2 partitions, the next time round I created more including an extended partition & logical drives. At the point I wa being asked how to label the drives I dropped out!! Insufficient info and no help files.

yeah its a great breakaway from ms.. so much so that im willing to keep ubuntu and take the time to configure it, but im still left in the dark when it comes to my ati graphics card. I dont think they should have reeleased this package until this big bug was fixed. I dont see why windows can auto find hardware, but linux can't? I know linux is about freedom but maybe have this as an optional setting or something. I just dont get it, but then agian im not a programmer either.

---

### Post by Done_Fishin on 2007-05-09
> **silent1643 said:**
> yeah its a great breakaway from ms.. so much so that im willing to keep ubuntu and take the time to configure it, but im still left in the dark when it comes to my ati graphics card. I dont think they should have reeleased this package until this big bug was fixed. I dont see why windows can auto find hardware, but linux can't? I know linux is about freedom but maybe have this as an optional setting or something. I just dont get it, but then agian im not a programmer either.

The problem with Linux is that there is very little support from the manufacturers. The support seems to stem from volunteers who manage to get something to work BUT with limitations. It requires feedback from users to let these developers pick up and see what is going wrong. I suggest you try filing a bug report. Perhaps the problem is already known. try googling your error report to see if anyone found a workaround.

---

### Post by silent1643 on 2007-05-10
> **Done_Fishin said:**
> The problem with Linux is that there is very little support from the manufacturers. The support seems to stem from volunteers who manage to get something to work BUT with limitations. It requires feedback from users to let these developers pick up and see what is going wrong. I suggest you try filing a bug report. Perhaps the problem is already known. try googling your error report to see if anyone found a workaround.

well i already know that ubuntu knows about the ati and nivida card issues with the desktop effects, per some of the sticky topics i have read. They do have one stick post about filiing bug reports also under the beginner section of this forum, but its not really out there to where the public will see it. I only just found out about the launchpad system. Maybe ubuntu needs to advertise the launchpad error reporting feature more? Alot of users seem to post their errors in the forum, and then if there is no help simply move on. There are only (from what i see) 27 bug reports for Feisty... seems low considering all the activiy on the forums concerning errors or problems relating to install or hardware configuration.

---

