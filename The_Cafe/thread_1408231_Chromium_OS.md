---
title: "Chromium OS"
date: 2010-02-16
forum: The Cafe
---

### Post by BslBryan on 2010-02-16
Has anyone here built it?  Pros/cons?  Thinking of something to do over the next week, in my free time I may build and install it.  What does everyone think of it so far?

---

### Post by mkvnmtr on 2010-02-16
I installed it in a virtual box. Lasted about an hour before I grew bored and removed it. It does not seem to do anything interesting.

---

### Post by Queue29 on 2010-02-16
Open Chrome. Maximize. Pretend the "x" button is not there. 

You now have a ChromeOS emulator w/ 99% of the real functionality.

---

### Post by NormanFLinux on 2010-02-16
Its basically Google's Chrome web browser with apps on the cloud. I'd recommend installing a DE operating system. You want to work offline, not just when you're connected to the Net.

---

### Post by arnab_das on 2010-02-16
used it in virtualbox quite a few times. verrry buggy and slooooow. :) hence never stuck with it.

---

### Post by user1397 on 2010-06-03
Two days ago I somehow built it and compiled it successfully, and tried the 'live' environment on my netbook.

Like some others said, basically just the chrome browser with a few must haves (such as battery and network indicators on the top right), but that's about it.

Really fast, cool how they removed so many steps from the boot up as compared to a regular linux distro.

Wouldn't install it though, seems like you *have* to be connected to the net to do anything.

---

### Post by Shining Arcanine on 2010-06-03
I think that the idea is that on Chrome OS, the internet is your application, so all of the devices running Chrome OS are supposed to be connected to the internet all the time.

---

### Post by stmiller on 2010-06-03
It's not really an operating system. There is no file system. No desktop. No applications. You have: Chrome browser, full screen. That is it.

It's basically a modified ubuntu to be chrome full screen. There was a long thread on this forum analyzing it.

---

### Post by Shining Arcanine on 2010-06-03
> **stmiller said:**
> It's not really an operating system. There is no file system. No desktop. No applications. You have: Chrome browser, full screen. That is it.

It's basically a modified ubuntu to be chrome full screen. There was a long thread on this forum analyzing it.

It is an operating system. It does have a file system. Having a desktop or a GUI was never a requirement for something to be called an operating system. It runs web applications.

Chrome OS has very little in common with Ubuntu. While Ubuntu and Chrome OS share the Linux kernel, some system libraries, chromium, and possibly X, considering Chrome OS to be Ubuntu would be like saying that Gentoo Linux is basically Ubuntu Linux, which is absurd. Linux distributions are usually defined by their package managers and their repositories. On Google Chrome OS, all applications are web applications, so there really is no notion of a package manager or repository. The closest things to those on Chrome OS are Google's updater mechanisms.

By the way, run [COLOR="Green"]sudo /etc/init.d/xdm stop[/COLOR] and you will very quickly discover that having a desktop is not a requirement for something to be an operating system.

---

### Post by seanelly on 2010-06-03
I put Hexxeh's build on a usb stick, had fun for 20 minutes, and never used it again.

---

### Post by smellyman on 2010-06-04
No interst in it at all.
 
Only point I see to it is have it as an optional boot on a laptop to quickly get online at an airport or something. 
 
Other than that it seems useless.

---

### Post by Johnsie on 2010-06-04
For us techies it's no good because it's just a browser and we like to play around with stuff. For everyone else it will be quite good because it will be quick and simple. The down side is that every single thing you do in that OS will be sent to Google.

Will it catch on? I don't know. Android caught on because there was no 'standard' for smartphones, but computer users are different because they are very set in their ways.

---

### Post by Paqman on 2010-06-04
> **NormanFLinux said:**
> You want to work offline, not just when you're connected to the Net.

The devices running it are unlikely to be offline, ever. I'm sure Google have considered the (exceedingly) rare case when you can't get either a wifi or mobile connection. 

Previously the solution was Gears, but it looks like they've dropped that, so it'll be interesting to see what the solution is in the release version of Chrome OS.

---

### Post by kevpatts on 2010-06-04
I've successfully built it and built the image.

Is it possible to do a "single user boot" (i.e. into init 1), chroot into chromium's image and "startx" or "/etc/init.d/xdm start" to get it running locally off my drive instead of running off a slow USB key or VMWare machine?

I'd like to see it's native performance on my hardware.

---

### Post by madnessjack on 2010-06-04
> **NormanFLinux said:**
> Its basically Google's Chrome web browser with apps on the cloud. I'd recommend installing a DE operating system. You want to work offline, not just when you're connected to the Net.
HTML5 lets you work offline. Problem solved :P

---

