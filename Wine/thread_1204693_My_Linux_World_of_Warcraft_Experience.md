---
title: "My Linux World of Warcraft Experience"
date: 2009-07-05
forum: Wine
---

### Post by Laids on 2009-07-05
Well let me just say that the last 30 hours or so have been pretty painful as I made the decision to finally get off of windows and use linux as my main OS after playing around with both for years.  I would have switched sooner but as an avid gamer I always felt the need to keep Windows as my main operating system and rarely booted into Linux because of it.

I decided a couple of days ago that if I could get Warcraft to work in linux that I would finally make the switch.  After hours and hours of troubleshooting and googling I have got it working and I would like to share my setup / mistakes for anyone that is going through similiar problems.

**My Rig**

Asus G50V-A1 Gaming Laptop
Intel Core 2 Duo T9400 (2.53GHz/6MB L2/1066MHz FSB/ 35W TDP)
Intel PM45 + ICH9 chipset
4GB DDR2-800 RAM
15.4-inch WSXGA+ (1680x1050) glossy display
Nvidia GeForce 9700M-GT w/ 512MB GDDR3
2x 250GB 5400RPM SATA hard drives
([More Details]("http://www.notebookreview.com/default.asp?newsID=4612"))

I use this laptop as my main system and it does everything from typing up reports to playing games.  I figured this would be a pretty good machine to toss linux on as I could dedicate a physical hard drive to the O/S while keeping Windows as a backup on the other drive.  A decent amount of ram and a pretty powerful mobile graphics card should get me by.

**My Journey**

Ok I have to admit I was a little nervous due to the fact that I never installed linux on a laptop before and I figured it would be a driver / config nightmare and I really did not want to screw up my windows partition just incase Linux was a complete failure.  I decided on Unbuntu because it seemed to be the most mainstream / user friendly distro out there.  Another big help was all the built in support and hardware detection which I am sure would have given me issues with builds that I am more familiar with.  

Ubuntu 9.04 64 bit installed onto my 2nd harddrive without a hitch and in about 20 minutes I was dual booting into linux.  My following step was to install the Nvidia drivers.  I installed them directly from Nvidia's site and they seemed to work fine.  Next I decided to install Wine.  I installed the newest version of wine (1.1.25) from their site.  So far so good.  Now for Warcraft.  After much searching I decided I would copy my Warcraft installation from my Windows drive seeing how I did not want to re-download all 15+ gigs of the client/patches.  Now this is where things started going terribly wrong.  I could not get Wine to load Wow.exe.  Everytime I would try to load it I would get an error (**err**:seh:raise_exception Unhandled exception code c0000005 flags 0).  Followed by Wow.exe hanging and using up 100% CPU forcing me to kill the process.

I went through the net and searched for every possible solution.  My 3d rendering was working correctly, drivers seemed up to date, tried with sound on and off, tweaked wine registry, ran it in OpenGL, etc etc.  If it was out there I tried it and could not get it to work.  So I figured maybe it is a Wine issue as I remember from years back Wine + Gaming didn't always go together that great.  So I remembered about Transgaming.  I went off and purchased Cedega.  Set it up and long story short I came to the same problem of the Wow.exe crashing out as soon as I loaded it.  Next I tried Crossover Pro.  Same result.  Next was Crossover Games.  Same problem...  I then tried PlayOnLinux and actually did a full installation from the installer as it seemed impossible to import an already installed version of the game with this application.  Same result...

So it was about 30 hours of trying to figure it out and I was about to throw in the towel and boot back into Windows and format my drive back into NTFS for storage.

**My Epiphany**

So as I was booting back into Windows it came across my mind that perhaps the issue was that I was running 64 bit version of Linux and Wine was having issues running Warcraft as it is a 32 bit application which uses OpenGL, 3D rendering, etc.  I spent a few more hours farting around with 32bit Nvidia libraries, tweaking settings, etc.  I even got so desperate as to install directx9 as suggested by some forum I translated from Russian...


**On the Right Track**

So after some hair pulling and nail biting I removed Unbuntu 64 bit.  Convinced that the 64 bit was my issue, I installed Unbuntu 32 bit version.  Instead of installing the Nvidia drivers from their website (185) I used the Nvidia drivers suggest by Unbuntu (180).  Instead of using the latest build of Wine, I used the stable release of 1.0.1.  I moved over my Warcraft installation from my Windows drive.  Loaded up Wow.exe and to my suprise it didn't crash.  After about 30 minutes of tweaking I got to run in a decent sized windowed mode with all my mods and maintain about 30-40 fps while in a 25 man raid.

[B]My Fun

[/B][[IMG]http://img104.imageshack.us/img104/4064/screenshotefq.th.png[/IMG]]("http://img104.imageshack.us/i/screenshotefq.png/")[[IMG]http://img9.imageshack.us/img9/8186/screenshot1rbo.th.png[/IMG]]("http://img9.imageshack.us/i/screenshot1rbo.png/")[[IMG]http://img21.imageshack.us/img21/5011/screenshot4hkq.th.png[/IMG]]("http://img21.imageshack.us/i/screenshot4hkq.png/")[[IMG]http://img237.imageshack.us/img237/7310/screenshot7.th.png[/IMG]]("http://img237.imageshack.us/i/screenshot7.png/")

[B]The How To

[/B]So now we are at the conclusion that it is easier to install Wow on Linux with Wine using 32 bit rather then 64 bit.  I am sure running it on 64 bit is possible as I read a lot of different posts of people that did it but I just could not get my Nvidia card to cooperate with the 32 bit libraries.  Once I got the correct versions of Ubuntu, Wine and the Nvidia drivers loaded on my system I used a combination of these two guides to setup WoW.

[http://www.wowwiki.com/Wine](http://www.wowwiki.com/Wine)
[https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft)

Note that I found it very helpful to run Wow.exe in "Virtual Desktop" so it would create a windowed mode for the game to run in, making it possible to easily alt tab without losing sound or causing graphical errors.

If anyone is having similiar issues with 64 bit and the game crashing when trying to load try going with the 32 bit version and see if it helps you at all too.

---

### Post by THR45H on 2009-07-05
n00b

---

### Post by Rody on 2009-07-05
just a question. Did you install the 64bit nvidia drivers? It Makes a big difference. The problem with 32bit programing nowdays is that our memory and hardware are outgrowing them. you have 4 gigs of ram and are probebly only using about 3.2-3.5 gigs due to the 4 gig limit of 32bit OS. 

On the flip side congrats on getting wow to run on linux, a lot of people seem to have all kinds of problems doing it.

rody

---

### Post by Laids on 2009-07-05
> **Rody said:**
> just a question. Did you install the 64bit nvidia drivers? It Makes a big difference. The problem with 32bit programing nowdays is that our memory and hardware are outgrowing them. you have 4 gigs of ram and are probebly only using about 3.2-3.5 gigs due to the 4 gig limit of 32bit OS. 

On the flip side congrats on getting wow to run on linux, a lot of people seem to have all kinds of problems doing it.

rody

Yes I installed the 64 bit version of the Nvidia drivers.  My problem came that I "think" Wine/Wow emulation did not like the 64 bit library.  I could get wine to run other non-3d programs but as soon as I started doing something in OpenGL, such as WoW it would crash/not work.  

It was a hard decision for me to goto the 32bit version, it was basically out of frustration and a last ditch effort to get it to work.  I am using 3.3 gigs of my 4 gigs of ram on Linux.  I do have Vista 64bit on my other harddrive which I can boot into if needed.  Currently I just don't have any applications or reasons that I "have" to work in a 64 bit environment, so until then I will enjoy my WoW :)

---

