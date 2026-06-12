---
title: "ServP7 GTX580M"
date: 2011-07-13
forum: System76 Support
---

### Post by jordan313 on 2011-07-13
I recently purchased a new serval professional with a core i7 2720QM, 8gig RAM, GTX 580M, 500GB Harddrive, Centrino Advanced-N Wifi

Anyways, I initially tried to tri-boot ubuntu, crunchbang, and win7. When I installed the nvidia drivers from the debian repo and rebooted xserv wouldnt load (on the crunchbang install). I decided to remove the crunchbang install, but accidently hosed the ubuntu install. Now when I try to reinstall ubuntu from a brand new 11.04 iso (tried 3 different downloads/burns) first I get an error detecting network interfaces during install (even with wired ethernet plugged in), and once the install has finished and I try to boot to ubuntu xserv will not load. I think ubuntu is trying to load the wrong drivers for my video card. The strange thing is crunchbang will boot xserv (using basic drivers not nvidia). Also the video drivers supplied for windows7 by system76 do not work, when I try to install them it says no supported  hardware. Knowing that system76 uses clevo hardware, I was able to find new 580M drivers on the sager website (they also use clevo) which fixed the issue.

So anyways, please help me get a functional ubuntu install back on my serval.

---

### Post by jordan313 on 2011-07-13
Also, I forgot to mention that the GTX580M isnt even listed on the drivers page of nvidia's own website. (for either windows or linux)

---

### Post by jordan313 on 2011-07-13
I also just noticed that if I try to boot from the ubuntu 11.04 live cd, it crashes/black screens and prints a bunch of hex codes and "nouveau" a bunch of times and never boots

---

### Post by jordan313 on 2011-07-14
Well, I tried using a 10.04 disc and it worked. I got video, which leads me to believe there is a difference in open source nvidia drivers between 10.04 and 11.04. I was also able to install the latest drivers from nvidia and get my gfx card functioning properly.  The problem is that under 10.04 my wifi card does not get picked up. The system76 driver package tells me that ubuntu supplies all drivers for my system, which probably would be true if I were on 11.04 like it came wiith.I read somewhere that my wifi chipset (intel centrino advanced-n 6230) is only supported in the newer kernel. So I tried to upgrade from 10.04 to 11.04 using the ubuntu update manager but when it finished and rebooted it would no longer load again.

I am getting very frustrated and would appreciate some help. If someone from system76 could  just let me know how they originally installed ubuntu on my system so that I could mimic it that would be great.

---

### Post by jordan313 on 2011-07-16
So I'm still completely stuck with a "linux laptop" that won't run linux. Does anyone from system76 check these forums regularly?

---

### Post by isantop on 2011-07-18
I'm very sorry for the slow response. I do usually check the forums daily, but I was out of the office a few weeks ago, and have been working back up on forums and email since then. 

When we install Ubuntu on the machines, we use an imaging server that installs Ubuntu, then update it and run the System76 Driver to complete the setup process. It sounds to me like there is either a repeating issue trying to burn the image, or a hardware problem. What process are you using when you create the image, and which image are you downloading. Where are you getting it from? Also, which OS are you trying to create the CD in?

---

### Post by jordan313 on 2011-07-19
Downloaded from ubuntu.com tried the regular 11.04 64-bit (4 times now), the alternate installer, and even the minimal. Burned on the system76 laptop running Windows 7, burned on desktop running Debian Squeeze, burned on Macbook Pro running OSX 10.6x . All of them are crashing at the same exact spot. I believe it is when the "nouveau" open source nvidia drivers try to load. It would probably work if I could install the proprietary nvidia drivers but I never even get a chance to use the console or a desktop. I'm not an expert but I have a hunch that it doesn't like the new GTX580M. When I downloaded the nvidia win7 drivers from system76.com it said it did not detect an nvidia graphics card and I had to use a different/older driver from SagerNotebooks (another clevo reseller). Everything has been running perfectly in windows (and was running perfectly in ubuntu until the /boot was corrupted and I had to try and reinstall) so I don't think there is a hardware issue. 

I read somewhere that from 10.04 to 11.04 there was a change in nvidia open source drivers and I think that the ones in 11.04 do not like my card. Which would explain why 10.04 works (but no wifi because its an older kernel). 

Lost and confused.....any suggestions?

---

### Post by isantop on 2011-07-19
We can prevent the Nouveau drivers from loading. Insert one of your Standard Desktop CDs, then boot the computer. When you see the purple screen with the white symbols at the bottom, press the enter key. This will allow you to choose a language, then take you to the traditional Ubuntu CD boot menu. From here, press F4 and select "Safe graphics mode", then boot the CD. You should be able to use the installer now, and then install the proprietary graphics drivers once the system is installed.

---

### Post by jordan313 on 2011-07-19
I followed your steps, but when I press F4 there are only three options:

1)Normal
2)User Driver Update Disc
3)OEM Install (Manufacturers)

I tried all of these options and got the same result as before. I have attached a screenshot of what happens every time it crashes. 

[[IMG]http://img706.imageshack.us/img706/8181/photophq.jpg[/IMG]](http://imageshack.us/photo/my-images/706/photophq.jpg/)

---

### Post by jordan313 on 2011-07-20
any other ideas?

---

### Post by isantop on 2011-07-22
Try pressing F6, then select "nomodeset" and hit enter to but an "x" next to it. Then boot. Does that help?

---

### Post by jordan313 on 2011-07-28
I'll try that next. The problem is definitely something with the newer kernel, and most probably the graphics drivers. I ended up trying crunchbang 10 statler (debian squeeze based), and I was able to install the nvidia binary as well as proper drivers for wifi to get the wifi working on the older kernel. Everything was working great, but when I tried installing an updated liqourix kernel, I was met with the same issues. So right now I have everything set up and working properly, but I am stuck on 2.6.32-5-amd64

---

### Post by jordan313 on 2011-08-06
Just wanted to say.....BINGO! That worked. And I found out that the "Use Safe Graphics" F4 option doesn't always show up on 64 bit versions, but if it had been there (like in a 32 bit install), then that option would have worked the same.

Also, nvidia finally has the GTX580M listed on their drivers page! The newly released 280.19 works very well in linux and in the (beta) windows version.

Thanks for all your help! SYSTEM76 ROCKS! (you guys should send big stickers with your systems like apple does, I would stick one on my car if it was free)

---

