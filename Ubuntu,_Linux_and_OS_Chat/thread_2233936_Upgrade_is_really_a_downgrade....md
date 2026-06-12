---
title: "Upgrade is really a downgrade..."
date: 2014-07-11
forum: Ubuntu, Linux and OS Chat
---

### Post by jjhudak on 2014-07-11
For the longest time, I was running 10.1 in a VirtualBox and quite happy with it.
I decided to upgrade to the latest LTS desktop, also in VBox.  
To my surprise and horror, this version is 1) intuitively non-obvious, 2) Extremely SLOW.
I've tried many things to fix the slowness but, have been unsuccessful....and the UI makes it extremely unplesant to do anything...so, I bagged it!
(not starting a flame war over the UI...that has been done an gone....just voicing my opinion)

I have been using Ubuntu for over 8 years and followed the development and read the perspectives as the 'Unity' desktop debuted /emerged. I had a lot of reasons to delay upgrading, and when it came time, I figured  Unity can't be that bad....well in my opinion, it is...
So I went back to Debian on my desktop and continue to use Ubuntu on my servers.
But before ditching Ubuntu desktop completely...is there any currently maintained LTS version that has the look n feel (and hopefully snappyness) of the 'old' desktop?  
Best regards

John

---

### Post by jusko on 2014-07-11
14.04 is slow on VirtualBox - there are many reports on forums about that. It's little slow even if you set 10GB RAM, good amout of VRAM etc for that machine. It's simple - 14.04 is little slow on VM if you asked about that.

> But before ditching Ubuntu desktop completely...is there any currently  maintained LTS version that has the look n feel (and hopefully  snappyness) of the 'old' desktop?

Xubuntu LTS (3 years of support)?

PS: Unity in Ubuntu is a combination of OS X and Canonical vision - so if someone likes OS X, then Unity will be something known for them. It have nice lookin but it may been something strange to unfamiliar with GNOME3 or OS X.

---

### Post by kansasnoob on 2014-07-11
> is there any currently maintained LTS version that has the look n feel (and hopefully snappyness) of the 'old' desktop? 

More than one .......... I prefer this:

[http://ubuntuforums.org/showthread.php?t=2220264](http://ubuntuforums.org/showthread.php?t=2220264)

---

### Post by tgalati4 on 2014-07-11
Linux Mint MATE will give you that old school feeling.

---

### Post by ibjsb4 on 2014-07-11
> .is there any currently maintained LTS version that has the look n feel (and hopefully snappyness) of the 'old' desktop?  

Yep and xubuntu is a good choice, but you also have the option to change your current install to the old look by installing the flashback desktop.  It will run on metacity wm and should speed things up.

```
sudo apt-get install gnome-session-flashback
```

And choose your desktop at the login window.

---

### Post by jjhudak on 2014-07-11
thanks for all the replies...will check them out.

Yea, I just don't buy into the 'vision'....I love new ideas and concepts, but for me, they have to be well thought out, and at least allow me to do my work without getting in the way or taking what used to be 1 step and turn it into 3.  Gee, and what sort of 'vision' is there when one of the realestate hogs is a link to Amazon?   - sounds like a money grab and someone is in bed with amazon to me....
J

---

### Post by ajgreeny on 2014-07-11
> **jusko said:**
> 14.04 is slow on VirtualBox - there are many reports on forums about that. It's little slow even if you set 10GB RAM, good amout of VRAM etc for that machine. It's simple - 14.04 is little slow on VM if you asked about that.



Xubuntu LTS (3 years of support)?

PS: Unity in Ubuntu is a combination of OS X and Canonical vision - so if someone likes OS X, then Unity will be something known for them. It have nice lookin but it may been something strange to unfamiliar with GNOME3 or OS X.
I have a VM in VirtualBox of 64 bit ubuntu 14.04, using the unity DE and that runs fine, with no obvious signs of the slow OS that you talk of.  I have set it to use all 4 cores of my i5-3570K, and 4GB of my total 8GB of ram.

@OP: You don't mention your hardware; is it up to the job of running 14.04 unity, which is now quite a resource hog, in my opinion.

I also agree that Xubuntu is the one to try; it is now my favourite OS of the *ubuntu family, amazingly easy to use, with a classic style desktop, and extremely customizable. You can even make it look just like gnome 2 if you want to, though I now prefer the default XFCE look as it comes.

---

### Post by buzzingrobot on 2014-07-11
> **jjhudak said:**
> thanks for all the replies...will check them out.

Yea, I just don't buy into the 'vision'....I love new ideas and concepts, but for me, they have to be well thought out, and at least allow me to do my work without getting in the way or taking what used to be 1 step and turn it into 3.  Gee, and what sort of 'vision' is there when one of the realestate hogs is a link to Amazon?   - sounds like a money grab and someone is in bed with amazon to me....
J

Like it or not, most folks these days get their first exposure to computing on phones and tablets, not traditional Windows-esque panel-and-menus interfaces. While no interface can be intuitive -- they all require learning -- we typically and erroneously use that word to mean "what we already know how to do".

It's worthing noting that not only do phones and tablets do away with hierarchical text menus, they also hide the file system.  User of those devices rely on the applications to store and retrieve data that need to be stored and retrieved. (It's been my experience that users will inevitably use the directories suggested by the application they're using, on Windows, OS X or Linux. They generally are unable to save a file in a different location and then, later, find it. Most have no understanding of the actual struture of the filesystem, and many assume the display in their file manager is a literal representation of it.)

The Amazon icon in Unity's Launcher can easily be removed with a right-click. (I remove almost all the icons immediately after an install.) It is part of what is generally considered an unpopular attempt at monetization (Canonical being something other than a charity). No need to explain in detail here, but it is analgous to the Amazon Associate links in millions of blogs and other sites:  If someone clicks through to Amazon and buys something, the site hosting the link gets a tiny bit of cash.)  All this can be disabled in the settings tool, and will be Opt-In in the next release.

---

### Post by Kai_Staats on 2014-07-12
John,

I concur. Nearly the same situation. I was very, very pleased with Ubuntu 10.04 running under VMWare on OSX. I reluctantly upgraded to 14.04 (I need a modern Python devel environment and did not want to built it by hand) and am appalled at the state of affairs in a "modern" OS. If I wanted my workstation to look and feel as a tablet, I'd be using a tablet. I have spent the better part of 3 days attempting to get my desktop back to what I consider the basics of a proper user interface.

1) Installed "Gnome Flashback" -- I do not desire my Workstation to look / feel like a Tablet:
[http://www.omgubuntu.co.uk/2014/04/ubuntu-14-04-classic-gnome-flashback-session](http://www.omgubuntu.co.uk/2014/04/ubuntu-14-04-classic-gnome-flashback-session)

2) Modified the Applications menu (using the built-in Main Menu editor) to present only those item I need.

3) Fixed the Place menu to open a file browser instead of the Disk Use application -- How did 14.04 ship in this non-functioning state?!
[http://askubuntu.com/questions/300972/places-opens-in-disk-usage-analyzer-in-ubuntu-13-04](http://askubuntu.com/questions/300972/places-opens-in-disk-usage-analyzer-in-ubuntu-13-04)

4) Modified the Places menu to the best of my ability -- (see notes below):
[http://choorucode.com/2010/07/25/how-to-add-or-remove-places-entries-in-nautilus/](http://choorucode.com/2010/07/25/how-to-add-or-remove-places-entries-in-nautilus/)

As I was unable to add new items, nor get the existing menus to recognize full paths, I replaced the existing Directories in my /home/[username] directory with sym links (ln -s) to the location I desired such that Documents links to the shared Documents Folder in OSX (via VMWare) instead of a local Ubuntu repository. Same for Pictures, Music, Data (a 2nd drive), etc.

5) Invoke auto-start for all applications which were running when I last logged out -- Why is this not on by deafult?!
[http://askubuntu.com/questions/48321/how-do-i-start-applications-automatically-on-login](http://askubuntu.com/questions/48321/how-do-i-start-applications-automatically-on-login)

Ihave yet to make #5 work. I installed gconf-editor and then gnome-session, but I am still not given the option as presented in the link above. I have tried to install the full GNOME suite, but their server is not responding. I may create unique desktop config files as noted in the same article (above).

I will remain with this heavily modified Gnome environment if I can get a few more bugs worked out, else I will give KDE a go. I installed XFCE just for kicks, as we based a few of the YDL distros on this. It remains super simple, fast, and customizable, but a lot of work to get back to the basics.

To address the issue of speed, VMWare remains exceptionally fast (faster than OSX for OpenOffice, GIMP for direct comparison) Ubuntu 14.04 is as quick in loading, manipuliating, and saving files as the native OSX. For me, completely worth the $120 + $60 USD I have spent for 2 licenses over 4 years.

As the former CEO and developer of Yellow Dog Linux, I have to say I am disappointed. Ten years ago we delivered an operating system which required less effort at the command line than what is shipping now. It saddens me to see that Ubuntu is following Apple's lead in assuming the general userbase is growing less capable instead of more. The original reason the Linux desktop appealed to so many people was the choices it presented. When you spend 10-- 12-- 14 hrs a day engrossed in your computer interface, to have it custom tailored to your asthetic needs allows it to feel like home. Safe. Comfortable. Quick to respond. The underlying functionality which provides this is now buried deep within the config files. Gnome and Ubuntu are apparently working with the false assumption that we no longer desire to have our desktop look, feel, and work as an extension of who we are--individuals.

---

### Post by buzzingrobot on 2014-07-12
> **Kai_Staats said:**
> John,

> 
5) Invoke auto-start for all applications which were running when I last logged out -- Why is this not on by deafult?!

I'd guess because there's no clamoring for it among Ubuntu users.


  [quote] Ten years ago we delivered an operating system which required less effort at the command line than what is shipping now. It saddens me to see that Ubuntu is following Apple's lead in assuming the general userbase is growing less capable instead of more. The original reason the Linux desktop appealed to so many people was the choices it presented. When you spend 10-- 12-- 14 hrs a day engrossed in your computer interface...

Are you sure you aren't projecting your own rather unusual experience and skill set on the general population?  I agree that if someone spends 14 hours a days at the keyboard leveraging habits and specific techniques refined over many years, then adjusting to an interface intended to appeal to mainstream, more or less casual, users, is certain to be frustrating. While there's nothing that can be done in one interface that cannot be done in another, obviously the way things are done will differ. 

The userbase is no more and no less capable that it was 10 years ago. The notion, though, that the appeal of Linux should be based on the willingness of users to learn enough to exploit the choices forced on them by the kinds of systems we had 10 years ago has proven false.  In fact, the steeper the learning curve, the narrower the appeal. Consumers want devices and tools they can use as soon as they turn them on, without reading and without learning.

And, there is an inevitable contradiction between the notion that Linux is all about "choice" and the conviction that Gnome 2 was the One True Interface. People are free to choose Unity if they like it, or Gnome Shell or older panel-and-menu interfaces like XFCE, KDE, LXDE, and Mate. (And Mate is probably your best option of you want that interface from ten years ago plus access to the Ubuntu software ecology.)

---

### Post by ibjsb4 on 2014-07-12
Nice post Kai_ and welcome to the forums :)

@buzzingrobot
No need to be so defensive, others can have a opinion :)

---

### Post by bapoumba on 2014-07-12
*Thread moved to **Ubuntu, Linux and OS Chat**.*

---

### Post by craig10x on 2014-07-12
Personally, i love unity and what canonical is doing with it...but you are free to use whatever desktop environment you prefer...but that does not mean the developer has to offer everything to cater to YOUR particular desires...freedom of open source applies to both the users AND the developers...that is something you apparently have forgotten...

Thanks to smart phones and apple computers, most people are familiar with the kind of interface that unity presents, so it's very modern and well known and accepted these days...why should ubuntu be forced to produced older interfaces/features  just because YOU desire it? 

Hope that doesn't sound harsh...i am just being truthful (and realistic) ;)

---

### Post by buzzingrobot on 2014-07-12
> **ibjsb4 said:**
> 

@buzzingrobot
No need to be so defensive, others can have a opinion :)

I wasn't intending to be defensive, and don't think I was. What would I be defensive about?

It just seems natural for me that people who have invested years of time and effort working in a panel-and-menu environment are probably going to find interfaces that abandon that paradigm to be highly annoying. They should simply find something else that's better equipped to handle their requirements.

---

### Post by cariboo on 2014-07-12
It always surprises me that so many professed long time Linux users don't seem to know that they aren't stuck using the defaut desktop environment. If you want, you can install the unity DE on Xubuntu, or you can install xfce on Ubuntu. Using a Linux distribution is about doing what you want to do, not what what the developers think you want to do.

---

