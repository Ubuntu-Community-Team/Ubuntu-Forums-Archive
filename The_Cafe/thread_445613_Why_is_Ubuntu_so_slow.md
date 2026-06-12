---
title: "Why is Ubuntu so slow?"
date: 2007-05-16
forum: The Cafe
---

### Post by PrimoTurbo on 2007-05-16
I have been using and trying Ubuntu and it's various versions since 5.10, the one problem I have always had is the slow responsiveness of the GUI and the slow speed at which applications start.

My computer specs are old, but should be enough to run Ubuntu.

Pentium 4 1.6GHz
768 DDR RAM
ATI 9700 Pro 128Mb
Western Digital 250GB 7200RPM

Even under XUbuntu 7.04 I have noticed general GUI sluggish performance.

I used both the Open Source video drivers that come with Ubuntu and various versions of the ATI Restricted drivers, there is almost no difference in their performance on the 2D desktop. Except of course that the Restricted drivers allow me to run 3d applications. I similar but a few fps lower performance in 3D games like Warsow and Tremulous, compared to Windows so it's not a video issue.

I have spent a bit of time trying to figure out if it's a hardware issue with the help of #ubuntu IRC channel but no one has been able to identify any particular problem or to provide any fix that had any significant speed increase. I have checked my hard drive configuration with out finding any problem, my read/write speeds are normal.

I'm also using little system memory, however I get high CPU usage when rendering the GUI compared to windows. I reach around 60-70% when dragging a window around, while around 40-50% on Windows.

XUbuntu is significantly faster, especially when moving around windows and minimizing but still there is an obvious redrawing effect that I see and everything is a little slow.

Firefox is significantly slower, for example switch tabs is a lot slower compared to windows.

Any help or suggestions are welcome.

I have tried other distros like Vector Linux, which is **a lot** faster then Ubuntu. Why is Ubuntu so slow? Under any environment? Gnome, KDE, XFCE? Beryl runs pretty good on my computer and I notice moving windows is smoother but the overall desktop still feels a bit slow.

---

### Post by steven8 on 2007-05-16
I have near the same specs as you, and have no sluggishness.  The only diference, really, is my vid card.  Nvidia FX 5500. 128mbs.

---

### Post by Tom Mann on 2007-05-16
Are you using the ATI official drivers? I have nVidia myself, but it makes a huge difference to have the official drivers turned on for me :)

---

### Post by steven8 on 2007-05-16
> **Tom Mann said:**
> Are you using the ATI official drivers? I have nVidia myself, but it makes a huge difference to have the official drivers turned on for me :)

I use the open source driver.

---

### Post by kvonb on 2007-05-16
My spare system is a P4 1.6, it is quite slow compared to my server which is an AMD 2000 (1.6 real speed).

I think it is the main board, the P4 is a cheap and nasty all in one heap of junk, but the video card is an nvidia gf2/mx 400.

Have a look in your BIOS and try tweaking your RAM speed settings etc', also make usre your onboard video is disabled if it has one!

Although I do believe the old P4 chips are still on a par with a top end P3 to tell you the truth, not much faster at all!

---

### Post by WalmartSniperLX on 2007-05-16
most likely its the video drivers and the X server. Ati is notorius for bad drivers (open source drivers arent great either). High cpu usage can be a result of bad video drivers as it puts more load on the cpu and less on the gpu with all video processiing (both 2D and 3D).

Ubuntu ran VERY slow on my system with an ATI Radeon x1600pro with fglrx drivers (good specs too) and ran faster on a radeon 9250 simply because ati drivers work better with older cards (well at the time at least). And, now that Im running a GeForce 7300 I noticed the performance on the desktop is even smoother. 

You can also stop certain damons (sp) or services/processes that you don't need to help speed things up. Gentoo has a very fast interface but it also doesn't have many processes (like 73MB RAM usage in Gnome on boot).

---

### Post by PrimoTurbo on 2007-05-16
I doubt it's the graphics drivers, because video rendering is very very fast on Ubuntu compared to Windows. Also like I said before I run 3d games with nearly the same FPS, over 100FPS on most Quake engine based games.

I think there is a setting problem with Ubuntu, other Linux distros preform much better like Vector Linux, PCLinuxOS, Debian, SLAX...All using modern desktop environments like Gnome/KDE.

---

### Post by WalmartSniperLX on 2007-05-16
> **PrimoTurbo said:**
> I doubt it's the graphics drivers, because video rendering is very very fast on Ubuntu compared to Windows. Also like I said before I run 3d games with nearly the same FPS, over 100FPS on most Quake engine based games.

I think there is a setting problem with Ubuntu, other Linux distros preform much better like Vector Linux, PCLinuxOS, Debian, SLAX...All using modern desktop environments like Gnome/KDE.

Then its probably services. However having high FPS in a 3D game and fast video rendering doesnt justify it isn't your gpu. Ive worked with many linux distros and with ati/nv hardware and ati has horrible *2D support *

Fedora is just as slow as Ubuntu. I used Slax and it did run a litle faster than ubuntu but it is also a live distro inwhich runs in your ram and fsb. And, it's lightweight.

It's still something to consider because like many users, I noticed a great increase in video performance (2D, 3D, and video) by just switching to NV.


But you can also try replacing the Ubuntu Gnome desktop with gnome-core. I believe there are several posts on the forum about doing this. But, you will lose a lot of the programs that come with Ubuntu that don't normally come with the Gnome package. But, it will run faster because you wont have as many processes going on that ubuntu's desktop usually has to allow super user friendliness :P resulting in a faster desktop. I did this with Kubutnu; I removed the kubuntu desktop and intsalled kde-core from the repos.

**gnome-core is the basic gnone desktop env. package without all the Ubuntu mods and tweaks.

---

### Post by misfitpierce on 2007-05-16
glxinfo | grep 'direct rendering' in console = does it say yes?

---

### Post by ssam on 2007-05-16
system -> administration -> service.
disable anything you don't need.

run
```
top
```
in a terminal and see if anything in particular is slowing you down.

try different themes. i am sure once i found one to be slower than others.

try enabling desktop effects (system->preferences->desktop-effects), and disable cube and wobble. this may speed up moving windows around, and take some work off the cpu (by moving it to gpu)

install
```
preload
```
it tries to keep useful files cached in RAM, based on watching your usage patterns.

---

### Post by mips on 2007-05-16
Try another distro, you might be pleasantly surprised.

Or try one of the ubuntu derivitives like Fluxbuntu.

---

### Post by curuxz on 2007-05-16
debian is  VERY VERY fast compared with ubuntu duno why...

---

### Post by sup on 2007-05-16
I also use (mobility) ati radeon 9700 and when using opensource windows, the gui was slow. With the closed source drivers, the speed is just fine. So i would advice to try those drivers. If you do not mind them being closed source.

---

### Post by lyceum on 2007-05-16
I have the same specks, but ATI 9200 and it is quick, very quick. And I use beryl.

---

### Post by graabein on 2007-05-16
Your previous avatar was much cooler **steven8**. :(

---

### Post by PrimoTurbo on 2007-05-19
I installed Debian Etch and it's noticeably faster compared to Ubuntu under Gnome, the menus are about twice as responsive, starting applications is also a little faster. However I dislike Debian because it's not as easy to use as Ubuntu, I couldn't install ATI drivers. I tried Envy and it failed to do things correctly, broke my x and I had to go back to a backup of xorg.conf.

What is the main difference between Debian and Ubuntu? Why is Ubuntu so slow? Is it misconfigured? My hardware is definitely capable of running Gnome and other desktop environments fast.

Any suggestions are welcome.

---

### Post by gp2x on 2007-05-21
I have an Athlon 64 3.2G/1G ram (from memory) machine at home running Feisty, and it is blindingly quick.

A bunch of us have intel core duo 1.8G/2G ram machines at work (HP Compaq boxen) with Intel 965Q video chipset etc, and they are as slow as mollasses.

Ubuntu has issues, and noone seems to be on top of it. Ive tried everything to get these machines to run ok, and altho Ive got improvement by changing the VideoRam setting in xorg.conf, changing network settings etc, nothing seems to fully resolve the issues. The machine I am using right now is sluggish, pauses for a few seconds randomly, scrolling artefacts, extremely slow app start (beryl-settings takes more than a minute!) etc etc etc

Dont get me wrong, these machines are pieces of crap, but Ubuntu just isnt cutting it. A multitude of bug reports surrounding mysterious performance issues have been raised, but this issue continues for many people.

I dont think this is a video driver issue, as I can run Beryl quite well now and 3D performance seems good. The main issue is that when I start an app, it takes ages to start, and CPU usage goes through the roof. I seem to recall (when we had the same issues with edgy) that gettimeofday calls were taking forever, but noone seems to have a solution......

---

### Post by Mazza558 on 2007-05-21
> **PrimoTurbo said:**
> I installed Debian Etch and it's noticeably faster compared to Ubuntu under Gnome, the menus are about twice as responsive, starting applications is also a little faster. However I dislike Debian because it's not as easy to use as Ubuntu, I couldn't install ATI drivers. I tried Envy and it failed to do things correctly, broke my x and I had to go back to a backup of xorg.conf.

What is the main difference between Debian and Ubuntu? Why is Ubuntu so slow? Is it misconfigured? My hardware is definitely capable of running Gnome and other desktop environments fast.

Any suggestions are welcome.

Are you running Beryl?

---

### Post by Mazza558 on 2007-05-21
> **gp2x said:**
> I have an Athlon 64 3.2G/1G ram (from memory) machine at home running Feisty, and it is blindingly quick.

A bunch of us have intel core duo 1.8G/2G ram machines at work (HP Compaq boxen) with Intel 965Q video chipset etc, and they are as slow as mollasses.

Ubuntu has issues, and noone seems to be on top of it. Ive tried everything to get these machines to run ok, and altho Ive got improvement by changing the VideoRam setting in xorg.conf, changing network settings etc, nothing seems to fully resolve the issues. The machine I am using right now is sluggish, pauses for a few seconds randomly, scrolling artefacts, extremely slow app start (beryl-settings takes more than a minute!) etc etc etc

Dont get me wrong, these machines are pieces of crap, but Ubuntu just isnt cutting it. A multitude of bug reports surrounding mysterious performance issues have been raised, but this issue continues for many people.

I dont think this is a video driver issue, as I can run Beryl quite well now and 3D performance seems good. The main issue is that when I start an app, it takes ages to start, and CPU usage goes through the roof. I seem to recall (when we had the same issues with edgy) that gettimeofday calls were taking forever, but noone seems to have a solution......

Are you on an AMD processor with power scaling?

---

### Post by PrimoTurbo on 2007-05-21
> **Mazza558 said:**
> Are you running Beryl?

No I'm ***_NOT_*** running Beryl. I have tried it and it makes window movement a little faster and smoother but slows down other things, like how long it takes for a program to close. Plus I have no need for the fancy stuff, I find it's counter-productive.

I'm back on Xubuntu 7.04, general responsiveness is a bit slow especially in Firefox. Only thing that runs really well is video playback, there is no delay between moving around the playback.

---

### Post by gp2x on 2007-05-22
> **Mazza558 said:**
> Are you on an AMD processor with power scaling?

Not at work - Core Duo.....

I hate this machine. *Hate*. All the developers here are wanting to use Ubuntu on these machines, but we just cant get it to perform :( My Dell laptop is a similar spec to these machines and it *flies*.

---

### Post by crimesaucer on 2007-05-22
My xubuntu is so fast. I even use Beryl.

I followed this guide: [http://sidux.com/PNphpBB2-viewtopic-t-3484-start-0.html](http://sidux.com/PNphpBB2-viewtopic-t-3484-start-0.html)

and did most everything in there that applies to me. 

I also then re-did my Firefox about:config like this guide: [http://forums.mozillazine.org/viewtopic.php?t=53650](http://forums.mozillazine.org/viewtopic.php?t=53650)

...but using this guide for the newer settings and values: [http://kb.mozillazine.org/Category:Preferences](http://kb.mozillazine.org/Category:Preferences)

My pages load so fast now.

---

### Post by PrimoTurbo on 2007-05-22
crimesaucer: I really appreciate the help, I will definitely look over all the links you posted, if anyone else knows any resources in order to speed up ubuntu / xubuntu / linux then please post them here.

I have switched to swiftfox, initially no difference but I noticed swiftfox performs much better under heavy load when you have 20-30 tabs open compared to regular firefox.

---

### Post by crimesaucer on 2007-05-22
No problem, I hope it helps to make things faster.

---

### Post by gp2x on 2007-05-22
finally got my work machine to behave. I ended up dist upgrading to Gutsy, installed kernel 2.6.22-4, and upgraded everything to the most recent dev version (X, Gnome etc). 

It still boots kinda slow (hangs on preliminary keymap) but the desktop is quick now. 

Seems X mightve had some issues?

---

### Post by PrimoTurbo on 2007-05-22
Also I noticed something interesting Gnome based applications and GUI rendering is whats slow, xubuntu's default file viewer is very responsive and has no delays. As soon as I run something that uses GTK I can feel the menu sluggishness, even if it's a small and low resource using application.

---

### Post by gp2x on 2007-05-22
Yeh, looks that way - Ill hunt around upstream.

Thanks

---

### Post by NJC on 2007-05-28
> **gp2x said:**
> The machine I am using right now is sluggish, pauses for a few seconds randomly, scrolling artefacts, extremely slow app start (beryl-settings takes more than a minute!) etc etc etc


My PIII/500Mhz w/ 640 megs mem is also running high octane molasses in 6.06. Most folks will easily brush off the lag as older hardware. Sure ... to an extent. But I also get these bizarro few second lags on cached programs. IE there really does not seem to be much speed increase once a program is cached. 

I may try Xubuntu instead of Gnome as I'm sure it would increase speed. 

Whereas navigating through Nautilus is very laggy, moving through folders in Audacity is fast and crisp with no lag. ??

---

### Post by kerry_s on 2007-05-28
> **NJC said:**
> My PIII/500Mhz w/ 640 megs mem is also running high octane molasses in 6.06. Most folks will easily brush off the lag as older hardware. Sure ... to an extent. But I also get these bizarro few second lags on cached programs. IE there really does not seem to be much speed increase once a program is cached. 

I may try Xubuntu instead of Gnome as I'm sure it would increase speed. 

Whereas navigating through Nautilus is very laggy, moving through folders in Audacity is fast and crisp with no lag. ??

You should also try the debian version of xfce4, i have it running pretty good on a 450mhz 256ram-> [http://mirrors.kernel.org/debian-cd/current/i386/iso-cd/debian-40r0-i386-xfce-CD-1.iso](http://mirrors.kernel.org/debian-cd/current/i386/iso-cd/debian-40r0-i386-xfce-CD-1.iso)

Also learning to use opera really helps, it really is lighter and faster if you take the time to set it up right.

---

