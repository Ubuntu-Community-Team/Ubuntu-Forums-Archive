---
title: "Linux killed my video card"
date: 2007-04-18
forum: The Cafe
---

### Post by Afkpuz on 2007-04-18
I'm a recent convert to linux and used to play games every now and then.  I have an ati x700 radeon mobility video card and it ran like butter in windows.  I knew coming to linux that I would basically lose my gaming abilities, but I've lost a ton in the way of graphics.  Long story short, my screensavers can't even run without skipping.  In windows, my video card could tackle some of the top end games with huge settings.  Can't we with our combined knowledge and bring linux graphics up to snuff?  I mean, come on. Screen savers shouldn't demand all that my video card can dish and then some.  Not to mention, I tried running Plane shift (which is "designed" for linux) and the graphics make me sick.  The log in screen looked like it was 16 bit and my video card couldn't keep up with the mouse moving!  I have to wonder how linux handles 3d graphic design.  I can even see problems with when I drag windows around in a cluttered desktop.  So I guess this post can be boiled into 2 questions:

1.) Is it simply a case of finding the right driver?

2.) Can we expect Linux  to ever reach the graphical capabilities of windows? (I'm talking cross-application use of the video card)



This issue won't cause me to leave linux, but I wonder if there's more that can be done.

---

### Post by nalmeth on 2007-04-18
1.) Is it simply a case of finding the right driver?
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

Ubuntu doesn't ship with ATI or Nvidia's binary drivers, and the open source ones that are shipped can only pretty much handle 2D.

---

### Post by starcraft.man on 2007-04-18
First things first, there is nothing wrong with Linux and 3d graphics... Anything that is opengl runs perfectly when you have the right drivers installed. Quite clearly, there would be no way [Beryl]("http://beryl-project.org/") would exist otherwise. That being said, I'm pretty sure you couldn't have installed the proper drivers for your ati card if your getting those troubles.

Use [Envy]("http://albertomilone.com/nvidia_scripts1.html") to rectify that and for more information on installation of drivers and or eyecandy I direct you to [Ubuntu Guide]("http://ubuntuguide.org/wiki/Ubuntu_Edgy"). That should help... this also probably should have been in the beginner thread... *looks around for a mod*

Oh and in response to question 2, Beryl has many plusses that Vista Aero users can just drool for and curse at microsoft, so Ubuntu is already "THERE".

---

### Post by Adamant1988 on 2007-04-18
In many cases it's simply an issue of not having the driver.  The behavior you're experience (skipping screensavers, etc.) is an indicator that you're not taking advantage of your graphics card because you don't have the driver.  I myself am a user of the ATi Radeon X600 card and it requires the driver fglrx to work properly.  

Notice that if you're using feisty you can go to "system" > Administration > Restricted Manager"  (I think) and it will download and install the drivers for you, all you have to do is restart and you're off.  

Hope this post has helped.

---

### Post by FuturePilot on 2007-04-18
The open source drivers that come with Ubuntu are really bad with 3D stuff. Once I installed the Nvidia binary driver, my screensavers and everything is so smooth.

---

### Post by Afkpuz on 2007-04-18
I've already tried using the fglrx driver.  Screen savers worked, but Plane shift was only moderately better.  I could move the mouse smoothly in game, but gameplay still looked terrible.  Is it just Plane Shift?

---

### Post by maniacmusician on 2007-04-18
It's the fact that you have ATI. ATI chooses not to provide decent linux support, and so their Linux userbase suffers. Simple as that.

---

### Post by IYY on 2007-04-18
> 
2.) Can we expect Linux to ever reach the graphical capabilities of windows? (I'm talking cross-application use of the video card)


Actually, with the right card it has higher capabilities. It's even used by movie studios that do a lot of CG work. 

So, yes, it's a matter of finding the right driver. ATI cards are not among the best supported ones, but you can still get better performance than you get now.

---

### Post by mips on 2007-04-18
Did you try to install the Restricted ATI drivers ???

---

### Post by starcraft.man on 2007-04-18
> **starcraft.man said:**
> First things first, there is nothing wrong with Linux and 3d graphics... Anything that is opengl runs perfectly when you have the right drivers installed. Quite clearly, there would be no way [Beryl]("http://beryl-project.org/") would exist otherwise. That being said, I'm pretty sure you couldn't have installed the proper drivers for your ati card if your getting those troubles.

Use [Envy]("http://albertomilone.com/nvidia_scripts1.html") to rectify that and for more information on installation of drivers and or eyecandy I direct you to [Ubuntu Guide]("http://ubuntuguide.org/wiki/Ubuntu_Edgy"). That should help... this also probably should have been in the beginner thread... *looks around for a mod*

Oh and in response to question 2, Beryl has many plusses that Vista Aero users can just drool for and curse at microsoft, so Ubuntu is already "THERE".

Aye, afkpuz have you actually installed ATI drivers yet? I don't think fglrx is what you are wanting to get your card working right, download the envy deb and then after installing select the latest ATI driver install and it should work.

---

### Post by Afkpuz on 2007-04-19
> **starcraft.man said:**
> Aye, afkpuz have you actually installed ATI drivers yet? I don't think fglrx is what you are wanting to get your card working right, download the envy deb and then after installing select the latest ATI driver install and it should work.

Mind spelling out how to do that?

---

### Post by mips on 2007-04-19
> **Afkpuz said:**
> Mind spelling out how to do that?

For those that want to try the ATI drivers provided by ATI in **Dapper&Edgy** please see:
[http://ubuntuforums.org/showthread.php?t=255929](http://ubuntuforums.org/showthread.php?t=255929) (is the support thread for the link below)
[http://albertomilone.com/driver.html](http://albertomilone.com/driver.html)   (you will find Envy on this site)

If you are using **Feisty** it gets easier, you simply select Restricted Drivers from the Add/Remove Programs menu Item. So maybe it would be a better option to simply install Feisty.

All the above also applies to nVidia.

---

### Post by lakersforce on 2007-04-19
> **Afkpuz said:**
> This issue won't cause me to leave linux, but I wonder if there's more that can be done.

If things really were as you described I would not hesitate a second to nuke linux and install Microsoft Windows, and not come back for a million years. Fortunately they are not as you described :)

---

### Post by ferose2 on 2007-04-19
> **lakersforce said:**
> If things really were as you described I would not hesitate a second to nuke linux and install Microsoft Windows, and not come back for a million years. Fortunately they are not as you described :)

I think they are as bad as hes describing. It's all ATi's fault. I prefer my 5 year old nVidia GeForce 4 MX 440 over my new 1 year old ATi Radeon x850 Pro. It runs much more stable, and the load isn't always 100% like it is with fglrx. MX440  ran most of my games noticeably faster than Windows did with the nvidia driver. My x850 run games like crap compared to Windows. I regret buying from ATi.:mad:

---

### Post by mips on 2007-04-20
> **ferose2 said:**
> I think they are as bad as hes describing. It's all ATi's fault. I prefer my 5 year old nVidia GeForce 4 MX 440 over my new 1 year old ATi Radeon x850 Pro. It runs much more stable, and the load isn't always 100% like it is with fglrx. MX440  ran most of my games noticeably faster than Windows did with the nvidia driver. My x850 run games like crap compared to Windows. I regret buying from ATi.:mad:

For all those ATI owners theres always places like EBay etc to dump those cards. You might take a knock or even make a profit you never know.

---

### Post by slimdog360 on 2007-04-20
well its only fair that linux killed your video card, since video killed the radio star. Video got its 'just desserts'

---

### Post by Afkpuz on 2007-04-20
Yea, I guess I was just bummed at the lack of ATI support in earlier versions of ubuntu.  I just upgraded to fiesty and was pleased to find out that it automatically loaded a driver that worked.  Usually I have to do the "sudo apt-get xorg" dance to get it to work.  I'm also running a laptop and it takes alot more work to change the video card than it would a desktop.  I guess i'm stuck with ati until I decide to build a desktop.  Anyways, fiesty is working good so I guess the problem is solved.

---

