---
title: "How to power down screen when idle (JEOS)"
date: 2009-12-05
forum: Server Platforms
---

### Post by brettg on 2009-12-05
Hi

*Short Version:*

I've rebuilt my home server using hardy jeos (2.6.24-24-server). Prior to that it was running the "full" install of ubuntu server.

My minor problem is that the server does not power down the console screen when the console is idle. 

Obviously jeos doesn't install a power management package that installs with the full hardy install.

Does anyone know which package controls power management in ubuntu server?

More details follow for those who are interested.   

*Long Version:*

I have the server connected to the vga port on my LCD while my main PC is using the digital port. When the main PC goes to sleep, it shuts down the monitor interface, causing the LCD screen to "hunt" for another signal. Eventually it finds the server on the vga port and then sits there fully powered on at a black screen

This is a problem for two reasons. Firstly, the LCD never goes to sleep so uses more power. More importantly though, is that there are non geek users in the house who "have trouble turning on the computer" because when the PC powers up nothing comes up on the screen because the screen has parked itself on the server output.

Of, course, this is easily solved by pressing a button on the side of the monitor but that is a hassle and the other users keep forgetting or forget the correct button. 

Alternatively, I could unplug the server from the LCD panel but that becomes a hassle for the odd occasion that I need to get to the console although admittedly, this is rare.

I would prefer the proper, geeky fix to be sure.

So, I checked another server (2.6.24-25-server) that was running hardy and did dpkg -l on it.

I grepped the output for "power", "apm" and "acpi".

The only result I got was "pm-utils" and "powermgmt-base". 

I went and installed both packages.

I scanned the complete output of dpkg -l using the good old Mark-One Eyeball and looked for anything of interest.

I found nothing extra. 

There are a bunch of power management packages in the repos of course, but none of them are installed on a standard hardy build. I don't want to go installing packages at random because clearly there is a package on hardy server that give the correct result, but which one is it?

Or do I need to manually configure the two packages I installed earlier?

---

