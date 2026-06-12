---
title: "[SOLVED] Why I still dislike Ubuntu"
date: 2009-01-17
forum: Testimonials &amp; Experiences
---

### Post by ssj4Gogeta on 2009-01-17
Hi

I installed Ubuntu a few months ago. I was excited about trying something other than Windows. There were some problems with some drivers, but I got some of them fixed with some help and the rest were fixed by the new 8.10 release, on which everything worked out of the box and I'm really thankful to Ubuntu developers for that.:)


I like the idea of a free and open source OS, with all the functionality of Microsoft's expensive ones. But there are certain things which just annoy me. They are small things, mainly related to the GUI, but they are enough to make me use Windows as my regular OS instead of Ubuntu.


First, the GUI is LAGGY. There's a lag of 0.5 to 1 seconds whenever I switch tabs in dialog boxes, open new windows, etc. not only in apps, but also the native dialog boxes. It's like when I click on a tab, first the tab header will become live, then some of the contents of the window change and then the text changes, etc. Basically it's not as snappy as it's in windows.

By the way, I'm running this on Pentium 4, 3 GHz, 2GB DDR2 667MHz, 7200 rpm HDD and GeForce 8600GT. Yes, this computer doesn't have the latest hardware. But Windows XP, even Vista, works just fine, without any such lags and pauses.

Second, the interface is "unpredictable" (sorry I can't find the right word, I think). Sometimes when I right click, the menu won't appear. I have to try again and it appears the second time. This doesn't happen always, but it does happen, like 20% of the time. (And the mouse is OK, it works fine with Windows). Sometimes, a setting that I've set changes itself to something else. This happens rarely, but it does happen. Sometimes it won't let me mount my disks, then I restart and it works just fine. If I encounter any such problem, I just restart and it starts working just fine. But this annoys me a lot. Sometimes a keyboard shortcut works, sometime it doesn't, sometimes it changes itself to dvorak layout. Lol imagine you just typed a whole paragraph without looking on the screen and then when you look at it, you find it's all messed up cause the keyboard changed itself to dvorak layout. :lol: At first I thought I might have pressed the keyboard shortcut accidentally, but it happens even when I disabled the shortcut.


Third, Firefox: Freezes for like 3-5 seconds everytime on startup, everything from tab switching to moving the mouse cursor across my Live bookmarks feed list lags. When I move it across the list, the highlighting bar lags behind the cursor. Firefox freezes for a second or two once every 20 minutes. Sometimes even the keyboard input lags. Yes, I do have 42 addons installed. That's quite a lot, you might think, but I share the same Firefox profile with Windows, both XP and Vista and the interface is snappy, no lags and no freezes/pauses at all, with all those extensions and much more running (like 20 tabs or more). When I open more than 10 tabs in Ubuntu, the whole system slows down to a crawl.


Fourth, flash: takes up huge amount of processor power, doesn't work at all. It lags like hell. Flash games are completely unplayable. I can even make them lag by repeatedly clicking on them. Flash videos lag as well.


Fifth, compiz fusion: Again, "unpredictable". Sometimes a setting works, sometimes, it doesn't and sometimes it'll change itself. Restarting the system fixes this, but I hate it. Someone told me compiz is in beta, if so, it's OK.


Sixth, GUI: The GUI isn't as good as in Windows - I don't even have a right-click->run as admin (or sudo, or whatever it's called here) option.


Seventh, processor usage: It's always around 30-50%. I can't see which process is using it in the system monitor. Firefox uses around 10%, but where the rest goes, I don't know. In XP, it remains at, well, 0-2% when the system is idling.

RAM usage is extremely low when compared to XP and Vista. Doesn't even use 400 MiB. XP uses around 600-700, with all the background processes that I have running on it, and Vista uses around 1 GiB. But I'd rather have my system USE what resources are available and be responsive, than try to save them and waste the money I bought them with and be laggy.


Eighth, games: I've never seen a game like Crysis, Far Cry 2, Prince of Persia, etc. which runs on Linux. But that's not Linux's fault. Developers will start making more games for the platform once it becomes popular.

Thank you for reading this long post. I'm not a Windows fanboy. Rather, I'll be really grateful if the developers can fix these things up and rid the world of expensive MS software.:) I've already convinced my friends to install Ubuntu and I also helped them set their systems to multiboot with the other OS'es they have.:) They were really happy to try something different, and are willing to learn more about Linux commands, just like I am.

---

### Post by quinnten83 on 2009-01-17
yeah,...
you might want to read [this]("http://people.redhat.com/blizzard/evolution.txt").
and in tradition of being helpful:
Linux is not windows and the things you are talking about, don't seem to affect everybody, so it might be a problem on your end.
sounds like your hardware is not fully compatible with ubuntu or linux.
Try running a different window environment like KDE or XFCE to see if menus are more responsive. About your resources, I can't tell you much, but if I am not mistaken Linux is optimized to use as much processor power as possible (I believe), so that might be the difference.
Besides, this is not the place for a bug report. If you need help fixing some of the issues than by all means, ask. If you want to report a bug, you can try launchpad. If you only wanted to rant, than a warning would have been nice. Rants are allowed here.

---

### Post by Allochtoon on 2009-01-17
Hmm, only the first problem i encountered myself; mostly when DR is off meaning you run vesa driver, when u run "glxgears" in console, what does it give? And "glxinfo | grep direct"?

Other issues i can't say much about.

---

### Post by quinnten83 on 2009-01-17
> **Allochtoon said:**
> Hmm, only the first problem i encountered myself; mostly when DR is off meaning you run vesa driver, when u run "glxgears" in console, what does it give? And "glxinfo | grep direct"?

Other issues i can't say much about.
*offtopic*
Funny name, allochtoon.
Fellow countryman?
*back to the ontopic*

---

### Post by ssj4Gogeta on 2009-01-17
> **Allochtoon said:**
> Hmm, only the first problem i encountered myself; mostly when DR is off meaning you run vesa driver, when u run "glxgears" in console, what does it give? And "glxinfo | grep direct"?

Other issues i can't say much about.

> 5239 frames in 5.0 seconds = 1047.750 FPS
4285 frames in 5.0 seconds = 856.904 FPS
4197 frames in 5.0 seconds = 838.642 FPS
4606 frames in 5.0 seconds = 921.169 FPS
4569 frames in 5.0 seconds = 913.741 FPS
4717 frames in 5.0 seconds = 943.349 FPS
6297 frames in 5.0 seconds = 1259.291 FPS
6473 frames in 5.0 seconds = 1294.488 FPS
6378 frames in 5.0 seconds = 1275.483 FPS
6446 frames in 5.0 seconds = 1289.184 FPS
6422 frames in 5.0 seconds = 1284.393 FPS


It opened a window with three gears running. When I closed it, it said in the terminal:
> XIO:  fatal IO error 22 (Invalid argument) on X server ":0.0"
      after 36 requests (36 known processed) with 0 events remaining.


on glxinfo|grep direct, it said
> direct rendering: Yes


> **quinnten83 said:**
> yeah,...
you might want to read [this]("http://people.redhat.com/blizzard/evolution.txt").
and in tradition of being helpful:
Linux is not windows and the things you are talking about, don't seem to affect everybody, so it might be a problem on your end.
sounds like your hardware is not fully compatible with ubuntu or linux.
Try running a different window environment like KDE or XFCE to see if menus are more responsive. About your resources, I can't tell you much, but if I am not mistaken Linux is optimized to use as much processor power as possible (I believe), so that might be the difference.
Besides, this is not the place for a bug report. If you need help fixing some of the issues than by all means, ask. If you want to report a bug, you can try launchpad. If you only wanted to rant, than a warning would have been nice. Rants are allowed here.

I do not know what to say. It wasn't supposed to be a rant. I'm new to Linux and I was just mentioning some of the problems that I faced. It might be a problem at my end, though. Thank you for taking time to reply.

EDIT: @alochtoon: I already have nvidia drivers installed.

---

### Post by billgoldberg on 2009-01-17
> **ssj4Gogeta said:**
> It opened a window with three gears running. When I closed it, it said in the terminal:


on glxinfo|grep direct, it said




I do not know what to say. It wasn't supposed to be a rant. I'm new to Linux and I was just mentioning some of the problems that I faced. It might be a problem at my end, though. Thank you for taking time to reply.

EDIT: @alochtoon: I already have nvidia drivers installed.

You can remove the "might", it's a problem on your end.

If everyone had the problems you had, not much people would use it.

You can try a different DE or WM like xfce, kde, enlightenment or fluxbox.

---

### Post by ssj4Gogeta on 2009-01-17
> **billgoldberg said:**
> You can remove the "might", it's a problem on your end.

If everyone had the problems you had, not much people would use it.

You can try a different DE or WM like xfce, kde, enlightenment or fluxbox.

Thank you. I'll try Kubuntu. But is there a way to change the environment without reinstalling the OS? Is it OK to ask here or should I start a new thread in one of the support forums?

---

### Post by billgoldberg on 2009-01-17
> **ssj4Gogeta said:**
> Thank you. I'll try Kubuntu. But is there a way to change the environment without reinstalling the OS? Is it OK to ask here or should I start a new thread in one of the support forums?

you don't need to reinstall to use a new DE.

Just install it, then log out and in the login screen you can select KDE.

Just do a 

sudo apt-get install kubuntu-desktop

Note that KDE is at least as resource heavy as gnome.

xfce, e17, fluxbox, ... are more lightweight.

---

### Post by ssj4Gogeta on 2009-01-17
So is it that my computer doesn't meet the minimum system requirements?

P4, 3GHz (overclocked to 3.4), 2 GiB DDR2 667MHz, nvidia 8600GT. If so, I'll try installing it on another rig instead. By the way, this one runs Vista just fine.


EDIT: Thanks for your help.

---

### Post by C0pac3t1c on 2009-01-17
> **ssj4Gogeta said:**
> It opened a window with three gears running. When I closed it, it said in the terminal:


ssj4Gogeta, thats hard to believe...I have an older machine with Pentium 3 -- 512 mb of memory and it still runs faster and much more efficiently than windows xp and other rivals, which i might add lags like an old man on death bed.

---

### Post by billgoldberg on 2009-01-17
> **ssj4Gogeta said:**
> So is it that my computer doesn't meet the minimum system requirements?

P4, 3GHz (overclocked to 3.4), 2 GiB DDR2 667MHz, nvidia 8600GT. If so, I'll try installing it on another rig instead. By the way, this one runs Vista just fine.


EDIT: Thanks for your help.

You pc meets the min requirements, and exceeds them.

A friend of mine runs Ubuntu on a PIII with 512mb or ram.

--

If you want to stick with gnome, try disabling compiz fusion.

It can help a lot.

You can still use metacity compositing if you want some eyecandy. It's more light-weight.

---

### Post by Joeb454 on 2009-01-17
Moved to Testimonials & Experiences :)

---

### Post by benmoran on 2009-01-17
Wow, that 30%+ processor sounds really high to me. Mine never even approaches that unless i'm running something processor intensive. I'm currently running Firefox and Transmission (plus a few apps sleeping in the background), and i'm running between 10% ~ 20%.. And this is with a crappy 1.8ghz Mobile Sempron. Try turing off desktop effects (system, preferences, appearance) and see if it has a noticeable effect. 

I hope you get it sorted out! I've had a few growing pains also since switching from XP about 1.5 years ago, but overall i'm much happier using GNU/Linux.

---

### Post by sjnovick on 2009-01-17
It sounds like you may not have installed the nvidia video drivers.  Did you go to the menu:  System -> Administration -> Hardware drivers ?

If not, try it out and I think that you'll have a great working system afterwards.

---

### Post by ssj4Gogeta on 2009-01-17
Thank you for all the help guys.


Yes, I have the nvidia drivers installed. This is the screenshot of the CPU utilization tab and the processes tab in system monitor:

---

### Post by ssj4Gogeta on 2009-01-17
The CPU usage in the processes tab doesn't total to the CPU usage shown in the CPU tab. This is very strange. I'll try turning of compiz fusion and see if it helps. I'll also Google metacity and try to find a guide on how to install and use it.

---

### Post by wolfen69 on 2009-01-17
these problems are not typical for most people. please buy compatible hardware (like you did with windows) or stay with windows. problem solved.

---

### Post by jrusso2 on 2009-01-17
I don't think this has anything to do with "Hardware".  If he is running 30% on his cpu I would look at top and see whats using so much CPU and try to fix that.

I am running a 2 ghz P4 with Kubuntu 8.04 and I am not running anywhere near that unless I am using Flash or something intense.

---

### Post by ssj4Gogeta on 2009-01-17
> **jrusso2 said:**
> I don't think this has anything to do with "Hardware".  If he is running 30% on his cpu I would look at top and see whats using so much CPU and try to fix that.

I am running a 2 ghz P4 with Kubuntu 8.04 and I am not running anywhere near that unless I am using Flash or something intense.

Like I said, I have no idea what is causing this, because if I add up the CPU usage for all the processes in the processes tab, it still doesn't add up to the amount of CPU usage shown in the Resources tab. Please look at the screenshots that I attached in my last post.

> **wolfen69 said:**
> these problems are not typical for most people. please buy compatible hardware (like you did with windows) or stay with windows. problem solved.

Now that wasn't really helpful.:rolleyes: So you're saying that Pentium 4 and ASUS P5GC-MX and GeForce 8600GT isn't compatible with Linux? I wonder what is then. Can you guide me?

And I didn't have to pick compatible hardware for Windows. I just went out and bought whatever I felt like. It worked. And since all the component's drivers are available for Linux too, it should work here too.

---

### Post by Martje_001 on 2009-01-17
Press ALT + F2 and type:
```
gksudo gnome-system-monitor
```
Also, make sure you choose 'Show All Processes'.

Do you see anything now?

---

### Post by ssj4Gogeta on 2009-01-17
Ahh yes! It's a process called Xorg (It's constantly taking up around 20-30% and shoots up to 50-60% every 5 seconds or so). I think that's the GUI process?? So is my processor not capable of handling the compiz fusion eye candy?

---

### Post by zero244 on 2009-01-17
Im running Hardy Heron, I havent used Intrepid except from the live cd. Which by the way ran quite fast compared to past live cd's.
You must have something going on that is using your cpu.
Sitting idle the cpu should not be above 20 percent.
Even with compiz running.

Im running Hardy on a machine that has one third less horsepower than what your running and Hardy is very responsive.

I would look in the area of power management.

I have to use a few augments in my menu.lst file on the kernel line to get Hardy to remain stable.


Here is what my kernel line looks like.

title		Ubuntu 8.04.1, kernel 2.6.24-22-generic
root		(hd0,9) 
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=4bfb1e7d-4d9c-4ee6-ad7e-f2be641ee7f8 ro quiet splash apic=off highres=off nohz=off irqpoll 

Since doing the tweaks on boot up I haven't had any problems. I was having random lockups.
Knock on wood.

Bottom line your machine should be giving you better performance.

If you do some searching Im sure your not the only one.

There should be a fix for your situation, its just a matter of finding it.

Good luck.

---

### Post by ssj4Gogeta on 2009-01-17
I really have no idea what the problem is. That stupid Xorg is taking up all the processing power. Even if I turn off all the eye candy, it's the same. System monitor itself also takes around 20% or more but Xorg takes another 50%. I think I'll just buy a cheap Allendale for this rig. I'm thinking e2200.

---

### Post by ssj4Gogeta on 2009-01-17
Sorry for the double post. I've just installed KDE. It's looks sooo cool. It's still laggy though, so I think buying a new processor is the only option. The Xorg process eats up upto 80% when I move the widgets. I really want to be able to run KDE. Do you think it'll work with e2200? My parents aren't ready to give me more money atm. I'll probably overclock the processor as well.

---

### Post by emshains on 2009-01-17
You know, I don't have these lags with worse hardware. I mean, there is a lag, but even with 1.6ghz sempron/768mb/7300Gt and compiz/awn it doesn't lag that much. 

The flash is a different story, you see, adobe is not trying hard enough to make normal drivers for linux. And you may not be using the real flash, just an open-source alternative. To get flash, check the ubuntu faq's. 

And, you could try openbox or KDE. They may run faster/slower.

You could try to delete all the bloaters. Google for "ubuntu speed-up"!
And were these lags there the whole time ? Or just now ? If you have a spare HDD, or some free space left for another partition, you could try a fresh install, and check the speed of that. What have you installed on your machine ? 

But the xorg stuff sounds really strange, because as far as I know, it should never go over 20% on old computers, not to mention 30% on a p4 with 3.0ghz !!!

---

### Post by jrusso2 on 2009-01-17
> **ssj4Gogeta said:**
> Ahh yes! It's a process called Xorg (It's constantly taking up around 20-30% and shoots up to 50-60% every 5 seconds or so). I think that's the GUI process?? So is my processor not capable of handling the compiz fusion eye candy?

Seems like that version maybe bugged if you installed the Nvidia drivers.

I might consider trying Hardy Heron thats what I am running and not getting that kind of cpu usage.

Your capable or running compiz fusion with that video card.  I know a lot of people were complaining about Intrepid and Nvidia not sure if that's still a problem or not but something is not right, and your hardware looks fine.

---

### Post by ssj4Gogeta on 2009-01-17
Thanks jrusso, but my onboard ethernet doesn't work with Hardy. :( I tried many drivers and instructions, but none of them worked. Then I tried Ibex when it was released and the ethernet worked out of the box.

---

### Post by emshains on 2009-01-18
You could try installing the beta drivers from jaunty. People say, that it has great performance improvements in both 2d and 3d.

---

### Post by gfg on 2009-01-18
It's probably some issues with the nvidia drivers as mentioned. Try installing the 180 drivers, by issuing sudo apt-get install nvidia-glx-180 in the terminal. This might require that you enable proposed and testing repositories in System-->Administration-->Software sources.

---

### Post by ssj4Gogeta on 2009-01-18
I'll try and report back. :)

---

### Post by Perfect Storm on 2009-01-18
> **gfg said:**
> It's probably some issues with the nvidia drivers as mentioned. Try installing the 180 drivers, by issuing sudo apt-get install nvidia-glx-180 in the terminal. This might require that you enable proposed and testing repositories in System-->Administration-->Software sources.

+1
The 180 driver is a lot better. The previous drivers had some odd performance problems.

---

### Post by ssj4Gogeta on 2009-01-18
Thank you sooo much everyone, the drivers made all the difference. I had 177 before and the interface was really laggy and I couldn't even drag the KDE widgets properly. Now everything works flawlessly. And Xorg generally remains in single digit and always remains below 20%. :) It was really silly of me to assume that the problems I was facing were general problems with Ubuntu.

(Do I need to mark this thread as "solved"? How do I do that?)

---

### Post by gfg on 2009-01-18
> **ssj4Gogeta said:**
> 

(Do I need to mark this thread as "solved"? How do I do that?)

Should be under thread tools at the top of the page. If it's not there it's probably disabled temporarily for some reason.

---

### Post by ssj4Gogeta on 2009-01-18
It's not there. Anyways, thank you all.:)

---

### Post by wolfen69 on 2009-01-18
cool as the other side of the pillow. glad you got it sorted. :-)

---

### Post by ssj4Gogeta on 2009-01-18
I still have a problem about Firefox tabs not rendering properly in KDE, and some questions. But I'll start a new thread for that.

---

### Post by solwic on 2009-01-18
> **ssj4Gogeta said:**
> I still have a problem about Firefox tabs not rendering properly in KDE, and some questions. But I'll start a new thread for that.

They didn't render properly for me, either.

---

### Post by Perfect Storm on 2009-01-19
Marked thread SOLVED as requested.


Also try Opera in KDE instead, they go very nice together IMHO.

---

### Post by ssj4Gogeta on 2009-01-19
I do use Opera sometimes like when I have to open multiple google accounts, but I can't live without FF addons (have over 45 of em installed). Besides, I share my FF profile with Windows.
By the way, is there a way to run chrome in wine? It installs and opens fine, but crashes when I try to open a web page in it. I hope Google do the Linux port fast. It's a really nice browser and very fast too.

---

### Post by solwic on 2009-01-19
> **ssj4Gogeta said:**
> I do use Opera sometimes like when I have to open multiple google accounts, but I can't live without FF addons (have over 45 of em installed). Besides, I share my FF profile with Windows.
By the way, is there a way to run chrome in wine? It installs and opens fine, but crashes when I try to open a web page in it. I hope Google do the Linux port fast. It's a really nice browser and very fast too.

Dude if you get Chrome to work in wine I wanna know about it.  I can't wait for the Linux port to come through.  

Chrome looks really nice.  :)

---

### Post by ssj4Gogeta on 2009-01-19
Take a look here:
[http://www.codeweavers.com/services/ports/chromium/](http://www.codeweavers.com/services/ports/chromium/)

It's NOT the official port from Google but an unofficial one. I haven't tried it yet. By the way, if you don't know, Chromium is the name of the open source project for Google Chrome. :)

---

