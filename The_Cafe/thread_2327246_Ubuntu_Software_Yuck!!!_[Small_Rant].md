---
title: "Ubuntu Software??? Yuck!!! [Small Rant]"
date: 2016-06-08
forum: The Cafe
---

### Post by Kale_Freemon on 2016-06-08
Hey all. Just wanted to share my opinions of the "Ubuntu Software" (US) that replaced "Ubuntu Software Center" (USC) in 16.04, and see what other people thought of it as well. Should a Ubuntu dev see this, that would be awesome, but that's not the point here. I'm not paying for it, so I'm not going to complain too much and expect to be coddled to by Canonical. That being said, I thought it'd be nice to see what others think.

For one, part of my problem with US is that it seems to be a lot slower than the USC. While I do enjoy the overall look and feel of it (seems more polished than USC), I don't like that it takes about half a minute for it to pull up search results. USC seemed to do this quicker when I used it in prior versions. On top of that, I also noticed that it seems to take its sweet time when I click the "Updates" button at the top.

Another issue I have is that it seems as if I am being pushed into using US to install updates now. For example, almost everyday I will receive a notification from Ubuntu that there are updates available, but the Software Updater won't be the one to notify me by popping up like it used to. While the Software Updater does still open up automatically when it detects updates, it would appear that these updates are being detected by US first. This annoys me as I much preferred it when I had one central place to go to update my software, which worked quite well for me and wasn't intrusive (I usually wouldn't know it even opened until I looked at the launcher).

What seems to be going on, to me, is that Canonical is taking the "fix what isn't broken" approach for the sake of change. Honestly, if it ain't broke, don't fix it. Hopefully Canonical doesn't continue with this approach, as it is starting to sour my overall experience with Ubuntu.

Having said all of that, I am still enjoying Ubuntu 16.04 overall. It works well on my System76 Lemur (Lemu5). I just finished paying it off after a year, hahaha.

What is everyone else's thoughts on this? Do you like the new US?

---

### Post by grahammechanical on 2016-06-09
It is actually a re-branded Gnome Software. And I understand why It replaced Ubuntu Software Centre (USC). The developers wanted a software store that used something called AppStream. And that meant rebuilding USC. Whereas, Gnome software does do AppStream. 

I think that Gnome Software was not fully developed at the time it was chosen. And I also think that Ubuntu Software was brought into Ubuntu 16.04 very late in the 16.04 development cycle. Too late to be fully tested. Either that or too early in the Gnome Software development cycle to be of much use.

I actually installed Gnome Software from PPA when I first heard about this change midway through the xenial development cycle and it did not have any software in its catalogue. In fact all it did was load its application window very quickly. A lot of work has been done since March to bring this utility up to standard and the work is still not finished. Every application needs metadata to explain what the application does and an icon as well. Very few applications have these things.

Yes, I do think that if the standard is "finished & polished" software, then Ubuntu Software has been brought in too soon.

Regards

---

### Post by buzzingrobot on 2016-06-09
You can change how often the the software updater checks for updates via its GUI.  I wouldn't be surprised of it and the new USC are out of synch on that.

---

### Post by yoshii on 2016-06-09
Personally, I just use apt-get, synaptic, "sudo dpkg -i *.deb", and gdebi.  I removed gnome-software from my system.  
I wasn't really very fond of Ubuntu Software Center either.  For overviews of software, I check the author homepages.  
Synaptic can trigger a web page lookup of the official homepage.  So you can still see what the program looks like and get support info.  
Gdebi is much smoother for package installation, and Synaptic is very capable and pretty stable too.  
People who don't have internet access can still do offline installs using dpkg as mentioned above.

---

### Post by brashley46 on 2016-06-09
I also have had the speed problem with gnome-software on my Xubuntu 16.04 desktop. After a 5-week trial it seems to be speeding up a tad, but it is still slower than UbuntuSoftware Center was; I have retained both on my box for comparison. It is nice IMHO that gnome-software will do updates, but it is slower at actually loading them than software-updater. 
Gnome-software also loads a lot slower than USC. I have to wait for ten or fifteen seconds for the front page to load, and then I have to hit the + icon to get it to actually fit my screen ... every single time. USC loads to a size that actually fits my screen in about 3 seconds.

I'm running Xubuntu 16.04, generic kernel, on a six-year-old Cybertron PC with an AMD Athlon-X2 processor and a 1 TB hard drive.

---

### Post by QDR06VV9 on 2016-06-09
> **yoshi2 said:**
> Personally, I just use apt-get, synaptic, "sudo dpkg -i *.deb", and gdebi.  I removed gnome-software from my system.  
I wasn't really very fond of Ubuntu Software Center either.  For overviews of software, I check the author homepages.  
Synaptic can trigger a web page lookup of the official homepage.  So you can still see what the program looks like and get support info.  
Gdebi is much smoother for package installation, and Synaptic is very capable and pretty stable too.  
People who don't have internet access can still do offline installs using dpkg as mentioned above.
+1 I just do not seem to be a big fan of Software managers...outside of Synaptic && Gdebi what more dose a person need?:D (Jokingly)

---

### Post by Kale_Freemon on 2016-06-09
> **yoshi2 said:**
> Personally, I just use apt-get, synaptic, "sudo dpkg -i *.deb", and gdebi.  I removed gnome-software from my system.  
I wasn't really very fond of Ubuntu Software Center either.  For overviews of software, I check the author homepages.  
Synaptic can trigger a web page lookup of the official homepage.  So you can still see what the program looks like and get support info.  
Gdebi is much smoother for package installation, and Synaptic is very capable and pretty stable too.  
People who don't have internet access can still do offline installs using dpkg as mentioned above.

I use apt-get most of the time, if I already know exactly what I'm looking for. But, sometimes, I'll pop into the "Software Center" to see if I can find something that I'm looking for. For example, I was recently looking for an engine to play the classic DOOMs.  Using the "Software Center" made it just a little easier.

---

### Post by Omar_Jair on 2016-06-09
i personally use the synaptic package manager, it looks horrible but it is a great package managing tool, about the ubuntu software center vs the ubuntu software, the only thing i do not like its the speed and the problem those 2 have when it comes to show apps on the unity dash, i personally like the USC more because you have a little more familiar GUI than synaptic or console, US does seem good but it does take a lot more time to download and to apply changes.

---

### Post by 6975 on 2016-06-11
Known that feel Bro. At first you've gnome-software & no USC. Soon later you'll realize the gnome-software 
can't even install .deb file & doesn't even show version like USC.  At worse if you install ubuntu customly 
gnome-software will not show all software catalogue. Only show a installed software list 
which is kind of more useless than USC.

USC can be such buggy to install. However it'll be such useful if you treat it as
a software guide book to search to software & check to version, picture of that software.
I mostly use apt-get install install via repo but use 
USC for search software in main repo before apt-get install in terminal
But I'll never use USC to install software than search. For physical .deb installer I'll use gdebi install.

I'm start get jealous of "Discover" KDE Neon's software center & Lubuntu Software Center.

---

### Post by carl4926 on 2016-06-11
Synaptic is my choice too if I need a UI

---

### Post by JayKay3OOO on 2016-06-11
I use the gnome one. It's OK, I prefer the one in Linux Mint. I generally use aptoncd and have a text file with all the software I use that I drop into a fresh terminal command. On the other hand it does not seem to smash your system to a crawl anymore.

---

### Post by jeremy31 on 2016-06-11
> **JayKay3OOO said:**
> I use the gnome one. It's OK, I prefer the one in Linux Mint. I generally use aptoncd and have a text file with all the software I use that I drop into a fresh terminal command. On the other hand it does not seem to smash your system to a crawl anymore.

The one that has the categories with icons?  That was nice but I rarely used it

---

### Post by izznogooood on 2016-06-12
Ubuntu mate has Software Boutique 
 
You can install it on Ubuntu plain with: sudo apt install ubuntu-mate-welcome

---

