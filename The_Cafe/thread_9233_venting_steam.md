---
title: "venting steam"
date: 2004-12-26
forum: The Cafe
---

### Post by snipes420 on 2004-12-26
im so sick of x-windows crashing on me all the freakin time.ill be recieving some important files from someone then BAM! everything just shuts down. its so hard to say what could be causing it because it seems so random and I usually have more than a dozen different things going at once.
sure linux itself is still running but since everything I use is in xwindows when it goes everything goes. *deep breath*
*exhale*
Does any one else find there xwindows dissapearing or shutting down randomly or at times that it shouldent be?

Edit: I also want to say I have complete confidence in the ubuntu team that this will be fixed in the final release, unless it is a problem in a different package.(gnome?)
Thank you Ubuntu team for this fine OS

---

### Post by ankitmalik on 2004-12-26
Strange!

Although I do have X hanging sometimes due to my 128 MB RAM but never had it restart itself.

Try using the free drivers from Scitech. They work gr8 for me!

---

### Post by orion_114 on 2004-12-26
I have also had the whole GUI freeze when I am running lots of windows at once. Again I think it is more due to my lack of RAM in my PC.

---

### Post by KiwiNZ on 2004-12-26
Snipes , it could be usefull if you can provide some more detail , 
 EG your machine spec's?, your Ubuntu config , is it out of the box or modified.
 what typically do you have running when this occurs, is there a trend common to events?.
 Are you overclocking?
 
 etc etc etc

---

### Post by swerner on 2004-12-26
Also snipes, what does your /var/log/XFree86.0.log say? The reason for the shutdown is often given in the last few lines of the file. Also are there any errors reported in this file, search for (EE) to find the errors.

---

### Post by snipes420 on 2004-12-27
It an AMD Athlon XP 2500+
A7N8X-X Asus Motherboard
with nForce Chipset
256 + 512 DDR  RAM 
nVidea Geforce FX 5200
nForce NIC and onboard sound

My ubuntu config. hmmm
it was a expert install and it went well because it was the third install I did and it was smooth as butter.
And I have done a bunch of modifications I guess but mostly only on tips from the forums here. like the nvidea drivers and media player and codec setup.
[here is my XFree86 file from /etc/X11](http://snipes.undergroundcanada.net/etc/snipesXF86Config-4)
I'm going to try to reproduce it so I can get a copy of the XF86 log file.
There is an error in my current log and the old log but I dont think it is related. 
```
(II) LoadModule: "GLcore"
(WW) Warning, couldn't open module GLcore
(II) UnloadModule: "GLcore"
(EE) Failed to load module "GLcore" (module does not exist, 0)
```
Im usually running gaim 1:1.1.0-1-warty+backportedfrom-ubuntu-hoary1,
firefox 1.0, 
gkrellm 2.2.2-1, 
azureus 2.2.0.2, 
gnome terminals 2.7.3-1, 
and gftp 2.0.17-6,

and possibly xmms 1.2.10-1, 
gmplayer  1.0pre6-3.3.4, 
xine 0.99.1,
and xchat 2.4.1-0.1ubuntu-warty+backportedfrom-ubuntu-hoary1.

Ill do a double check to make sure im not overclocked. this mobo is great for that.

It mostly happens when Im doing something important. talking on gaim or ftping files   to my webspace or from the internet or something.

I dont know if it related but my computer won't boot after a warm boot anymore for some reason. It freezes on the entry "Starting Hotplug Services" and wont continue. I have to physically switch off the power switch on my power supply and cold boot it to get it to pass that point.

Oh well it hasen't happened yet today so Im happy now. but we willl see and Ill remember that file to get a copy of it next time.

---

### Post by snipes420 on 2004-12-27
ok it just did it again. I wasn't able to get X going again without completely powering down and then back up. but before i shut down I swtiched to a virtual term and got copies of XFree86.0.log and XFree86.0.log.old. (just in case)
but is doesnt look like my problem is in there. (im not very fluent in this though)
but there a few extra lines in XFree86.0.log that aren't in XFree86.0.log.old.
the last 2 lines.

[XFree86.0.log](http://snipes.undergroundcanada.net/etc/XFlog) 
[XFree86.0.log.old](http://snipes.undergroundcanada.net/etc/XFlog.old) 

seeing as the last 2 lines mention fonts I should add that I have installed the microsoft truetype fonts in the system.

I was running xchat, xmms, gaim, azureus, firefox, gedit, and a gnome-terminal running a script that was compiling a game at the time of the crash. [the script is from here](http://icarus.uic.edu/~ssenne1/)

it crashed as soon as i issued a wget command in the gnome-terminal.

Its driving me crazy

---

### Post by shimon on 2004-12-27
sound like your gfx card is stuffed but then again i know nothing about gfx card besides ....

---

### Post by snipes420 on 2004-12-27
im thinking its possible its a hardware problem too. But I was thinking ram. but then why would X crash and not the whole kernel?

---

### Post by machiner on 2004-12-27
In your X86Config-4 file comment out GLCore. It's not supposed to be loaded when using the Nvidia 3-d drivers.

---

### Post by jadm5000 on 2004-12-27
[QUOTE=swerner]Also snipes, what does your /var/log/XFree86.0.log say? The reason for the shutdown is often given in the last few lines of the file. Also are there any errors reported in this file, search for (EE) to find the errors.[/QUOTE]
 i agree there - mines done it a couple times but told me why

---

### Post by farnsworth on 2005-04-12
I've had X crash a few times, in warty and hoary, when azureus is running between 250 - 300 kB/s.  At those speeds, if I so much as hit the refresh button in my browser, BOOM.  If you think this might be the problem, switch to the official bittorrent client (and say goodbye to leeching).

---

