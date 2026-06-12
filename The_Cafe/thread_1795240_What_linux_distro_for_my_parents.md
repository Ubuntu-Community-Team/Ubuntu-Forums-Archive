---
title: "What linux distro for my parents?"
date: 2011-07-02
forum: The Cafe
---

### Post by Duncan J Murray on 2011-07-02
Thought I would gauge the waters.  They are quite used to 10.04, until their laptop broke down.  They've bought a new one, which seems pretty powerful (thinkpad SL510), so shouldn't have any problems with unity, but comes with Windows 7.  They live in another country to me, and I'm worried that there is no virus-checker installed.  Also they're complaining about lots of pop-ups which they don't understand the answers to - I'm worried they're going to do something silly and trash the computer!

But, I'm not going to be there to install linux for them, which could be a problem.  I was thinking of a dual-boot set up.  I was thinking 10.04 might be a good idea, but there's all that extra faff installing the restricted extras.  So 10.10 might be better in that regard, and 10.10 has the ubuntu software centre with ratings etc...  Problem is it is EOL early next year, which is really annoying.  11.04 will be EOL a bit later, but I'm worried about changing their interface, and also some bugs will probably need ironed out.

Hmmmmmmm.  Suggestions?

---

### Post by handy on 2011-07-02
Mint or Fuduntu.

If the machine's specifications are low, definitely Fuduntu.

They are both great, easy to install & polished.

---

### Post by NightwishFan on 2011-07-02
I wouldn't give them anything rolling. I vote Ubuntu 10.04 or Debian 6.

---

### Post by Aquix on 2011-07-02
Linux mint..

I run mint 11 now and most things work perfectly out of the box.

---

### Post by Paqman on 2011-07-02
I'd say there are two important criteria:
[LIST=1]
[*]What are they confident using?
[*]What are you confident supporting?
[/LIST]

Given that:

> **Duncan J Murray said:**
> They are quite used to 10.04

I'd say that's at least one vote for Ubuntu 10.04. There's no reason to put them on a more recent release just because their machine could run it, that's looking at things from a technical (geek) perspective instead of a user needs one.

Give them something they find easy to use, and you find easy to support (or don't have to support much). Stable release for sure, Ubuntu LTS sounds perfect TBH.

>  there's all that extra faff installing the restricted extras

Faff? It's one package. Send them an apturl link that says "click here" maybe? Or a script that installs any packages and executes any commands you want, with instructions telling how to make it executable and run it?

---

### Post by Linuxratty on 2011-07-02
Mepis,Mint,Xubuntu.

---

### Post by in-dust-rial on 2011-07-02
go and read if there is a nice current solution to remote-desktops within the community.
i used nomachines software to do so. 
and my parents are not really experienced with computers... so i would not use a rolling release, since every change to the system might be critical to their productivity.

---

### Post by sanderd17 on 2011-07-02
Don't let them install a new distro without you being near.

But I vote for Mint. At home they use Mint 10 (Mint 11 didn't work because of some problems similar to Ubuntu 11.04).

---

### Post by Duncan J Murray on 2011-07-02
Thanks guys.

I think 10.04 does seem the most sensible, but I do like the new software centre on the later versions...  Agreed 11.04 just seems silly, and 10.10 will require sorting out in the near future anyway.

Bit worried about them attempting an install themselves, but it's the only option at the moment...

May need to talk them through it...

D

---

### Post by Duncan J Murray on 2011-07-02
PS, I agree linux mint would be good, too...

---

### Post by Chame_Wizard on 2011-07-02
Linux Mint,is better than Ubuntu 11.04.

---

### Post by Bucky Ball on 2011-07-02
10.04 LTS. No brainer. Longest support, stable, and you won't be around there every five minutes fixing things. 

I built and maintain a computer for my mother-in-law and only ever use the reliable LTS releases. Why? She lives 750Kms away and I'm over there maybe twice a year. There two weeks ago and upgraded 8.04 LTS to 10.04 LTS with a couple of mouse clicks, bit of tweaking and all good. Check it out at christmas when I'm over there again. All good. ;)

I wouldn't consider using anything but LTS for a user who just wants to use the machine for everyday (she's never opened a terminal, not interested, never had to).

---

### Post by RoflHaxBbq on 2011-07-02
Debian. It's stable, and easy, and will run on any computer.

Just pop in the CD and do a core install will standard utilities.
Configure network, then configure repos and install DE.
(apt-get install xorg gnome-session gnome-panel gnome-applets nautilus gnome-themes metacity gdm)
That will give you a fully working DE. Make sure you do not configure sudo and don't give your parents root privileges because sooner or later they will derp it.
Then it's just a matter of installing independent applications etc. which I'm sure you will have no problem with (you will need to install 'menu' before instal applications)

---

### Post by Old_Grey_Wolf on 2011-07-02
I would go with 10.04. Ubuntu 10.04 will be supported for a few years. They are comfortable with it. 

It isn't that hard to install ([http://news.softpedia.com/news/Installing-Ubuntu-10-04-LTS-141550.shtml](http://news.softpedia.com/news/Installing-Ubuntu-10-04-LTS-141550.shtml)). Just edit the information in that link to include only the dual-boot portions. 

Because they are using Windows 7, I would instruct them on how to shrink the Windows 7 partition using Windows 7 ([http://www.sevenforums.com/tutorials/2672-partition-volume-shrink.html](http://www.sevenforums.com/tutorials/2672-partition-volume-shrink.html)). Just edit the information in that link to include only the info they need. 

You could also put together a file with cut and past commands to get it set up. Look at this post: [http://ubuntuforums.org/showthread.php?t=1469825](http://ubuntuforums.org/showthread.php?t=1469825). Just give them the pieces of that post that they actually need to do whatever they do on their computer.

If they use a wireless NIC or graphics card that is not supported out-of-the-box, that could be a problem; however, that can occur no matter what distro you choose.

Before you think they couldn't install it and follow the directions in the posts I linked to, look at my profile. There is a reason I use the name Old_Gray_Wolf -- 63 years old :).

Also, look at my signature. If there is anything on that computer they don't want to loose they need a backup!

---

### Post by Bandit on 2011-07-02
> **NightwishFan said:**
> I wouldn't give them anything rolling. I vote Ubuntu 10.04 or Debian 6.

This..  I voted 10.04LTS tho..

---

### Post by Duncan J Murray on 2011-07-02
> **Old_Gray_Wolf said:**
> I would go with 10.04. Ubuntu 10.04 will be supported for a few years. They are comfortable with it. 

It isn't that hard to install ([http://news.softpedia.com/news/Installing-Ubuntu-10-04-LTS-141550.shtml](http://news.softpedia.com/news/Installing-Ubuntu-10-04-LTS-141550.shtml)). Just edit the information in that link to include only the dual-boot portions. 

Because they are using Windows 7, I would instruct them on how to shrink the Windows 7 partition using Windows 7 ([http://www.sevenforums.com/tutorials/2672-partition-volume-shrink.html](http://www.sevenforums.com/tutorials/2672-partition-volume-shrink.html)). Just edit the information in that link to include only the info they need. 

You could also put together a file with cut and past commands to get it set up. Look at this post: [http://ubuntuforums.org/showthread.php?t=1469825](http://ubuntuforums.org/showthread.php?t=1469825). Just give them the pieces of that post that they actually need to do whatever they do on their computer.

If they use a wireless NIC or graphics card that is not supported out-of-the-box, that could be a problem; however, that can occur no matter what distro you choose.

Before you think they couldn't install it and follow the directions in the posts I linked to, look at my profile. There is a reason I use the name Old_Gray_Wolf -- 63 years old :).

Also, look at my signature. If there is anything on that computer they don't want to loose they need a backup!

Cheers!

Luckily the computer is pretty new, so hopefully that won't be a problem.  My dad is quite good technically (he managed to replace the fan on his thinkpad on his own - although it still hasn't fixed the problem - hence the new laptop), but he completely doesn't understand the concept of an operating system.  For many years, he thought that google was his operating system.  I'm thinking even a dual-boot setup might mess with his head, but it'd be nice to give him the option in case he needs it for some reason or another.

Thanks to everyone else for advice.  10.04 it is.

All best,

D

---

### Post by Shining Arcanine on 2011-07-02
> **Duncan J Murray said:**
> Thought I would gauge the waters.  They are quite used to 10.04, until their laptop broke down.  They've bought a new one, which seems pretty powerful (thinkpad SL510), so shouldn't have any problems with unity, but comes with Windows 7.  They live in another country to me, and I'm worried that there is no virus-checker installed.  Also they're complaining about lots of pop-ups which they don't understand the answers to - I'm worried they're going to do something silly and trash the computer!

But, I'm not going to be there to install linux for them, which could be a problem.  I was thinking of a dual-boot set up.  I was thinking 10.04 might be a good idea, but there's all that extra faff installing the restricted extras.  So 10.10 might be better in that regard, and 10.10 has the ubuntu software centre with ratings etc...  Problem is it is EOL early next year, which is really annoying.  11.04 will be EOL a bit later, but I'm worried about changing their interface, and also some bugs will probably need ironed out.

Hmmmmmmm.  Suggestions?

If the laptop is new, then you might not be able to use older versions of Ubuntu. Have them install 11.04 and then modify the bootloader to pass pcie_aspm=force to the kernel to workaround the 2.6.38 kernel power regression. Since they are used to 10.04's interface, you can configure the system to use GNOME instead of Unity.

---

### Post by Bucky Ball on 2011-07-02
> **Duncan J Murray said:**
> 
I was thinking 10.04 might be a good idea, but there's all that extra faff installing the restricted extras.  So 10.10 might be better in that regard ...

No different whatsoever and there isn't that much faffing. Installing the Medibuntu repo will fix most of that in one go. 

If it ain't broke don't fix it, 10.04 = support to 2013 and easy upgrade to 12.04 LTS when it emerges.

---

### Post by Copper Bezel on 2011-07-02
Again, it only gets complicated if there are hardware issues. Running 10.04 on a brand new machine might mean dinking up suspend, or wireless drivers, etc....

---

