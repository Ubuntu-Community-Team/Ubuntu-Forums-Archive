---
title: "Brand new Pangolin beeps and won't start :|"
date: 2010-05-24
forum: System76 Support
---

### Post by compu73rg33k on 2010-05-24
I just received my new Pangolin 30 minutes ago. I immediately unpackaged it and plugged in the power cord so I could set it up. It booted up fine and I went through the initial 4-step setup.

When I finally logged in, I was disappointed to find the system running a bit sluggish. It would take ~20 seconds for the widget dialog box to pop up after I selected "Add to Panel". I figured it was still doing set up stuff so I excused it. I add some widgets to the panel and started firefox, which took about 2 minutes to load. Things were going pretty slow. I added the mouse directives or w/e that mouse widget is to the panel and clicked around. I then got a dialog that I had to restart my session to enable this functionality, so I did. When I logged back in I had some crash messages about some gnome processes and my panels/icons were the fall back ones when things in gnome crash. Gray, boxy, etc - if you don't understand what I mean by this I can find a pic. So I rebooted.

When I started up again, I got the System76 bios screen then after that disappeared I was met with a black screen with a white blinking underscore. Then the numlock and capslock started beeping.

I restarted again and went into the BIOS. After a few seconds, the beeping and blinking started again. I set the system time to the proper time and enabled the diagnostic info at the beginning. The computer restarted on its own before I had a chance to save these settings.

I restarted a few more times but I've been met with the blinking LEDs, beeping, and the black screen with the blinking underscore. The computer restarts own its own after a minute or so.

What is going on!? x(

---

### Post by robtg on 2010-05-24
This isn't much help and I could be wrong but I think the blinking numlock/capslock keys mean you've got a kernel panic.  

Can you create a 64-bit Ubuntu install CD and try reinstalling?   Maybe something went wrong with the disk imaging process before your machine was shipped.  With the machine being brand new I'm not sure you're going to want to salvage what was originally installed.

Rob

---

### Post by compu73rg33k on 2010-05-25
> **robtg said:**
> I think the blinking numlock/capslock keys mean you've got a kernel panic.
I thought the same thing but the beeping/LED blinking happens sometimes even when I'm in the BIOS! Obviously that's before Linux has even booted up. And I installed a Ubuntu image to a USB and booted from it but it beeped/blinked as the image was booting up and restarted before it even had a chance to load.

Man, this is bad. :(

EDIT: I successfully booted up on a live USB session and after a minute into the install (i was at the partitioning phase) the computer just shut off. I guess it was good that it didn't beep and have blinking LEDs this time but it's kinda irrelevant since it still shut off.

Definitely thinking I need to return this. What are the steps to get this replaced? :(

---

### Post by Lee_Machine on 2010-05-25
Sometimes during shipping a computers parts can get slightly dislodged. I would try reseating the Hard Drive, and RAM. 

This is rare with laptops but I'm sure it happens.

---

### Post by jml on 2010-05-25
compu73rg33k, since this is a new laptop and presumably under warranty, you may want to contact System 76 support directly.  E-mail your information to:  [email]support@system76.com[/email]

When I needed to contact them for an issue, I included the purchase/order number (it will be on your recept,)  This allows them to look up the specific configuration of laptop that they shipped to you.  

Tom may answer your question on the forum, but he often requests that this type of problem (rare as they are,) be directed to him via the e-mail address I included.  Good luck.

Joe

---

### Post by thomasaaron on 2010-05-25
I received your email and will help you out via that venue.

Best,
Tom

---

### Post by betrunkenaffe on 2010-05-25
Remove bottom plate where fan is, ensure it is turning properly and close panel back up.

Pretty sure that's the light sequence for fan not working/overheating.

---

### Post by shell-fu on 2010-11-25
My best guess is that Lee_Machine is right. After having the problem go away and come back again, I went through a lot of trial and error and can only guess that something inside wasn't seated properly and was getting nudged out of place if I moved or touched the machine in the wrong way. At one point, I placed the bottom panel back on for the 10th time, put in all of the screws and the problem stopped. It hasn't shown up again since.

---

