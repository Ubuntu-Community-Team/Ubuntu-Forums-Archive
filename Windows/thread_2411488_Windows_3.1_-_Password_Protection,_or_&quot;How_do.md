---
title: "Windows 3.1 - Password Protection, or &quot;How do I get network features without one?&quot;"
date: 2019-01-30
forum: Windows
---

### Post by ioixd on 2019-01-30
[I]Preemptive note: I'm dumb. Now that that's out of the way:
[/I]
I set up a Windows 3.1 via DOSBox on Raspberry Pi and I've been having some fun messing around on it recently. I'd like to set up password protection for the device, but so far I haven't had any luck. All I've got is the password on the screensaver - I'd like to set it similar to modern Windows, where you need to enter the password at the start to access the rest of the system. I downloaded Visual Basic 3.0 and created a simple mock login screen, and it works, but it won't let me set the program to appear on top of every other program, which means its useless because the Program Manager and everything else opens over it. So I asked around and I found out that Windows 3.1 DOES come with password protection on startup, but only if you have a network. I got WfW 3.11 (because I plan on setting up Internet later), so there's no trouble upgrading. The trouble is that I don't have the money or time to buy and set up a network for one simple feature. I tried installing a network without an adapter, and it worked, but I get an error on startup informing me that none of the network features will work because (no duh) the installation didn't go so well.

**TL;DR: How can I password protect Windows 3.1 or get all the other network features without setting up a network?**

One last thing I saved til the end (since it's long and off topic): I did password protect my Raspberry Pi, and it worked, but it's a bit more annoying because I use a bluetooth keyboard, meaning I have to remember to click the bluetooth button during startup every single time; this may not seem annoying, but when you're me you forget to do the most basic of tasks and you end up having to manually restart the Pi because you forgot to do it the first time. Also the cronjob I set up to automatically connect the keyboard has a two second time frame. But I digress, I like being able to get straight to the Raspberry Pi because if I forget to sync my keyboard, there's a little .sh file I created on my desktop that does it for me, so I can save time. So if possible, I'd like to leave password protection to the Windows 3.1. **If this sounds stupid and easily fixable, it is, but I'm making this post anyway since I couldn't find anything on Google about password protecting the system.**&#8203;

---

