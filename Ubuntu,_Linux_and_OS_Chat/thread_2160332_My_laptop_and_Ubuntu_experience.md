---
title: "My laptop and Ubuntu experience"
date: 2013-07-06
forum: Ubuntu, Linux and OS Chat
---

### Post by exploder on 2013-07-06
I got an HP DV6 laptop for Christmas last year, it came with Windows and of course I wanted to run Linux on it. To make a long story short, I tried a lot of different distributions on the laptop but always ran into some kind of hardware problems. I had Ubuntu 12.04 x64 installed from a newer iso using the 3.4 kernel and the proprietary ATI drivers. All was well until a kernel update broke the drivers and I could not get them working again.

I installed OpenSuse 12.3 x64 KDE and it ran fine until an update caused problems with the Ralink WiFi. Sometimes the WiFi would connect but most of the time I had to log off and back on for it to connect. I was out of DVDs and was digging through a huge pile of them on my desk, I found a 12.04 x64 disk that still used the 3.2 kernel and decided to give it a try. I installed, updated, installed all the codecs, etc and everything was working fine.

I decided to stick with the open source ATI drivers because they were working fine and plymouth was displaying right. Since I did the install there has been an update to the kernel and some of the xserver packages but no breakage of any kind this time around. Generally I try and go with rolling and LTS releases and my thinking was that 12.04 has lots of support time remaining. I added a couple of ppa repos to have the current LibreOffice and Gimp packages, the rest of the included software seemed fine to me.

I installed MyUnity to make the launcher look more like the current versions of Unity and to have the show desktop icon in the launcher to minimize apps the way I wanted. I disabled apport to get rid of those pesky false error messages and the system seems pretty solid. I was a little worried about temperature problems but the laptop throttles down to 800 MHz and I played a couple of movies to test it out. No real problems with temperature that I could notice so I think it is fine.

I had not used Unity for a while but after adding the show desktop icon to the launcher, adding all my day to day apps and changing the launcher's appearance a bit with MyUnity the system is pretty user friendly now. My daughter says the system is a lot like her MacBook Pro, she likes Unity. I like Unity since I made those few adjustments I mentioned and it does look pretty nice on the laptop's 15.6 inch screen. I like the simplicity that the older version of Unity has, just wish it had the newer icon set that was included in 13.04 but in any event it looks pretty nice.

I thought I would write about my experience in case anyone else was facing similar issues on this same hardware. My laptop is an HP DV6 with A6 AMD/ATI graphics, 8 GB DDR 2 RAM, Ralink WiFi, Altec Lansing sound, 640 GB SATA Toshiba Hard Drive, HP SATA DVD Multi Function drive and a built in web cam. Everything hardware related is working fine, even the web cam using Cheese. 

Processor use stays pretty low on all 4 cores using the open source drivers, memory use is decent and no problems with the laptop getting hot. I went through quite a few different distros trying to get everything to work right and even a couple I tried that worked felt sluggish and slow with this hardware. 12.04 feels reasonably quick and responsive, I did tweak a few settings to make the dash a little quicker on the rare occasions I need to use it. 

Like I said, I hope this is of some help to anyone using this hardware or similar hardware. I think staying with the 3.2 kernel and going with the open source ATI drivers made the difference here. Time will tell but I do not think I will have any more problems like before with updates breaking things. Unity seems just fine after the few tweaks and giving myself a couple of days to get used to it again. The bottom line is now my laptop is usable and reliable running Linux and I should be able to keep it running for quite some time, hopefully until 2017.

---

### Post by craig10x on 2013-07-06
That is great to hear, exploder...welcome back to ubuntu with unity (my favorite!)...Not surprising that your daughter likes unity coming from a mac...yeah, i think anyone who has used and liked the mac interface usually tends to like unity a lot...I used the mac for about a year after i left windows (but before discovering linux and ubuntu) so i kind of liked it right away and now i really love using it...
My experience has been that the open source drivers are less problematic in the long run so always better to use them if you can...

Also, Intels (and my current new toshiba 17 laptop/desktop replacement has intel i3 processor and intel graphics) are very linux friendly and in fact there is no proprietary driver option for me because it is identical to the open source version...and have never had any problem with it...so i try to stay with intel when buying a new computer...I think the newer kernels coming in 13.10 will probably be even more favorable for those of you with amd in terms of lessening the need for optional drivers as there are many improvements for the open source version)...

Glad to hear it's running well and you are enjoying it...I'm going to probably do an upgrade for my 13.04 to 13.10 when it arrives and once 14.04 LTS gets here, do a fresh install and go on a 2 year LTS to LTS cycle from that point on (it would be nice to do less re-installing...lol) :D

---

### Post by exploder on 2013-07-06
Hi craig10x! Really nice to hear from you! I agree with you about Intel graphics. My wife picked out my laptop, it was a Christmas gift and she really did not know much about hardware under Linux. I think I will stay with 12.04 for some time since everything is working now but I will take a look at the next LTS release and go from there. Unity seems alright and I like the way I have it set up now. This is the third day for using Unity and I do like it on the laptop now. 

Work has been so slow this year and I have been laid off twice now. I have been considering selling my desktops just to catch up my bills. I hate to do it but things have been pretty bad and I have my family to think about. I was off work 4 months last year too for my seventh eye surgery... I am really lucky I can still see. The year before I was off for three months to have my right foot reconstructed. Things have been really tough.

My laptop really was not of any use to me until a few days ago when I got 12.04 working on it. You are right about the open source drivers and I keep reading about how they are advancing along with the newer kernels. I think HP messed up with the branding on my HP DV6, I think it is really an HP 666 laptop! This thing was a total nightmare! 

Really great to hear from you craig10x and nice to see you so enthusiastic about Unity. Take care my friend!

---

### Post by exploder on 2013-07-07
I have added some ppa repos and updated, VLC, Gimp, LibreOffice, Audacity and probably a couple of other things I am forgetting. I installed minitube 2.1 yesterday after reading about it on OMG Ubuntu and I am extremely happy with the software I have running in 12.04 now! I never would have imagined myself enjoying this so much! Ubuntu 12.04 is really working fantastic on my laptop and I am really glad I gave it another try. PCLinuxOS will always be on my desktop because of it's high quality and I love the fact that it is a rolling release but Unity is really winning me over on my laptop!

Ubuntu 12.04 is working better than anything I have ever tried on the laptop now that I am going with the right kernel and graphics drivers. The laptop boots really quick, plymouth is displaying nice, application start time is great, graphics and fonts look great and everything is working perfectly now! I was so happy to get the new version of minitube, it is one of my favorite applications. I can do just about anything I can think of now with music thanks to all of the applications I was able to get from the ppa repos.

I just can't believe how well things turned out! My laptop just sat around doing nothing for a long time, now I am using it a lot and really enjoying it!

---

### Post by mastablasta on 2013-07-07
tried similar thing, but ralink wasn't supported by 12.04 so we had to go with 13.04 where it is somewhat supported.still not working as it should. it would have worked in OpenSUSE and it worked in the default preinstalled SUSE. but (K)Ubuntu is just easier for beginners.

---

### Post by exploder on 2013-07-07
@ mastablasta, I ended up with problems with the Ralink WiFi in OpenSuse too. At first it worked fine but an update messed it up to where I had to log off and back on to connect. My WiFi is working fine with 12.04 x64, I even get a decent signal from across the house and it stays connected all the time.

I looked up some of the tweaks for 12.04 today and got all of the start up apps to display. I turned off some things I do not need running at start up and it made things even better! I tested the battery life last night and for not having the screen dim all the time the battery life is pretty decent. The battery lasts about 4 hours, not bad for running Firefox and playing videos. Processor usage is great! All 4 cores stay between 0-3% at idle, I thought that was awesome! Memory use is 375 MB on start up at idle and after running apps and closing them out memory use has been around 425 MB, not bad at all for a 64 bit OS in my opinion.

I am definitely staying with the LTS release on my laptop. All the problems I have had are solved and it is running great! :D

---

