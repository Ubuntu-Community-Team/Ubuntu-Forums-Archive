---
title: "Will installing Win7 on Vmware affect performance ?"
date: 2012-05-09
forum: Virtualisation
---

### Post by Docmero on 2012-05-09
[CENTER]Hi
I am a new user on ubuntu 11.10 . [I]I have a dual boot system with win 7 . 
but I want to install win 7 on ubuntu 11.10 using virtualbox because I need many programs
 that wine doesn't support eg. Abbeyy finereader 11 !! I don't to restart every time I want to run such an app .[/I]
* 1-My concern is that I'm afraid that Ubuntu may become slow after installation because the Vmware will take alot of system resources .*
* 2-The second Issue I'm afraid that Win 7 performance on Virtualbox might be slow .*
* MY spec : Core I 5 750 *
*                4 GB ram 1333*
*               GTX 470*

* I want to know your opinion before I install the system on Virtualbox .*
* Thanks*
[/CENTER]

---

### Post by traditionalist on 2012-05-09
It can be slower, depends on what you are doing.  This is Windows 7 x64 Ultimate running on 12.04 in a VMware player with the system monitor showing the load;

I also have a couple of other applications running in the background. Firefox, Rhythmbox and a small compiler.

[[IMG]http://img35.imageshack.us/img35/4710/workspace1001y.th.png[/IMG]]("http://img35.imageshack.us/i/workspace1001y.png/")

[[IMG]http://img98.imageshack.us/img98/3073/systemmonitor003.th.png[/IMG]]("http://img98.imageshack.us/i/systemmonitor003.png/")


Of course it also depends on your hardware.  This is;

[[IMG]http://img33.imageshack.us/img33/8527/systemmonitor004.th.png[/IMG]](http://img33.imageshack.us/i/systemmonitor004.png/)


Regards...Trad

---

### Post by Docmero on 2012-05-09
1-What is the difference between Vmware and virtual box ? I thought they are the same .
2-How much resursed should I allocate to the virtual system to run Win7 ultimate 64 smoothly without affecting ubuntu 11.10 performance ?
3-From your experience , Have you faced any lag ? I intend to spare my dual boot for gaming and use the virtual system just for apps .

---

### Post by traditionalist on 2012-05-09
> **Docmero said:**
> 1-What is the difference between Vmware and virtual box ? I thought they are the same .
2-How much resursed should I allocate to the virtual system to run Win7 ultimate 64 smoothly without affecting ubuntu 11.10 performance ?
3-From your experience , Have you faced any lag ?

They are different programs.

[https://www.virtualbox.org/](https://www.virtualbox.org/)

[http://www.vmware.com/products/player](http://www.vmware.com/products/player)

In the one I showed I allocated 4 GB of ram, but you could use less. I don't notice any difference with most things when running the VM although this depends on what you run where.  No noticeable lag.

As for "experience", I have only been using Ubuntu for a little more than a week. I just got sick of Windows breaking, and all the other problems with it, and so decided to try this. Works perfectly. Although I am still tweaking my Ubuntu and some things are a little complex to set up, you need to read a lot! :)

Regards....Trad

---

### Post by Docmero on 2012-05-09
1-What should I use to install Vmware or Virtual box ?
2-I wanned to allocate only  1.4 GB of ram to system and leave the rest (2.6 GB) to ubuntu 11.10 ? Does it suffice ?
3- Me too , I've been using ubuntu for a little more than a week . The main advantage I noticed that I dont' want to lose is that it's very light and smooth .
Thanks for helping

---

### Post by traditionalist on 2012-05-09
> **Docmero said:**
> 1-What should I use to install Vmware or Virtual box ?
2-I wanned to allocate only  1.4 GB of ram to system and leave the rest (2.6 GB) to ubuntu 11.10 ? Does it suffice ?
3- Me too , I've been using ubuntu for a little more than a week . The main advantage I noticed that I dont' want to lose is that it's very light and smooth .
Thanks for helping

I had trouble with Virtual box, could not install my Windows 7 on it, so I tried the VMware player.  The VMware player works well after some tweaking ( Patches, see here;

[http://ubuntuforums.org/showthread.php?t=1976092](http://ubuntuforums.org/showthread.php?t=1976092)

[http://ubuntuforums.org/showthread.php?t=1953805](http://ubuntuforums.org/showthread.php?t=1953805)  )

I can't give you any useful advice on what possible settings to use as I don't know! :)

The settings I used were the defaults apart from the RAM.  I installed the Win7 using the host ( Ubuntu) disc drive. Worked perfectly with no problems at all, and was very quick.  It took ten minutes. No questions were asked, I put the licence key in first.

I could not get Virtual box to install my win 7, which is why I tried the VMware player instead. Everything works fine on it. Mainly I wanted it for my banking program, it wouldn't run on WINE, but everything else works fine as well.

Somebody with more knowledge and experience can doubtless give you more info.

As for me, after using this there is no way I am ever going back to Windows as a main system. It's fine in a VM, even the installation is a great deal easier than "normal".  Although I am a newbie on Ubuntu and still lack knowledge of many things I am generally very pleased with it. After some tweaking ( also using Gnome instead of unity) it does what I want very quickly and smoothly. The interface is very customisable although you need to read and try a lot! :)  I installed a number of times and tried a lot of stuff to get where I am now, and this can only get better the more I learn about it. Also there will doubtless be improvements in the system itself. I remember well how long it took to make the first releases of XP usable, and much the same applies to Win7. It took me several months to set up my win 7 how I wanted it, and it kept breaking, usually as a result of updates, and also because of viruses etc.  Re-installing from scratch is often the only option, with all attendant problems, and this is just too much. This is easy and quick on Ubuntu, a major point ( of many ) in it's favour.

One thing you MUST do. Make sure you have all your Windows stuff backed up before you start. Using the data I already had I have made a complete transition to Ubuntu with very few problems.  I think it is much better than Windows for a lot of reasons, but I think a lot of people will have trouble with it "out of the box". 

Regards....Trad

---

### Post by westie457 on 2012-05-09
Hi, as with practically everything in Linux it all comes down to personal choice.

Never having used VMware I cannot comment on it however I can comment on virtualbox.

The version in the repo's is stable and lacks some features - the ability to use USB devices is one. Personally I use OSE Virtualbox from here. [https://www.virtualbox.org/](https://www.virtualbox.org/)

Very stable with extra features and more recent versions.

There is some lag running virtual Windows due to the fact my laptop is relatively old and under specced (one processor running two OSes).

---

### Post by Docmero on 2012-05-17
I tried both apps today , Virtual box is easier , faster and can be better integrated in unity .
Vmware is a bit slower and doesn't integrate well (lag ) in unity  but better in networking , detecting any USB device ,  GFX and more stable .
After hours of experiments , I went with Vmware .

---

### Post by Docmero on 2012-05-17
I tried both apps today , Virtual box is easier , faster and can be better integrated in unity .
Vmware is a bit slower and doesn't integrate well (lag ) in unity  but better in networking , detecting any USB device ,  GFX and more stable .
After hours of experiments , I went with Vmware .Thanks guys for all the help

---

