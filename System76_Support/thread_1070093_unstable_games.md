---
title: "unstable games"
date: 2009-02-14
forum: System76 Support
---

### Post by mysteriousdarren on 2009-02-14
I have been playing several games including Alien Area, Assault Cube, Nexuiz, Urban Terror, World of Padman, Wolfstein:Enemy Territory, Sauerbraten, and Warsow. I have been having trouble with staying in full screen mode, then after I'm going to town on somebody and it goes to a small box on the side of the screen. It doesnt let me do anything, I have tried to lock the screen, that sometimes works to help the problem, but it keeps happening. I have restarted, but it keeps happening. 

Thanks.

---

### Post by ctsdownloads on 2009-02-15
> **mysteriousdarren said:**
> I have been playing several games including Alien Area, Assault Cube, Nexuiz, Urban Terror, World of Padman, Wolfstein:Enemy Territory, Sauerbraten, and Warsow. I have been having trouble with staying in full screen mode, then after I'm going to town on somebody and it goes to a small box on the side of the screen. It doesnt let me do anything, I have tried to lock the screen, that sometimes works to help the problem, but it keeps happening. I have restarted, but it keeps happening. 

Thanks.

Which video card is being used and also, what applications are running in the background? This includes instant messengers, clipboards, etc.

---

### Post by mysteriousdarren on 2009-02-16
I am using a nVidia GeForce 8600M GT for a video card. The only applications in the background have been firestarter, sometimes MozillaFirefox. I usually just have the game though.

---

### Post by ctsdownloads on 2009-02-16
> **mysteriousdarren said:**
> I am using a nVidia GeForce 8600M GT for a video card. The only applications in the background have been firestarter, sometimes MozillaFirefox. I usually just have the game though.

Hmm, unless you have the browser open to something that actively changes the webpage ongoing like Gmail, it should not be browser related. Have you tried lesser resolutions with the video card?

---

### Post by xakh on 2009-02-16
Just going to chime in, I've had these issues too. I've tried other resolutions, it only happens in 3D games in full screen mode, no matter the resolution. However, there are exceptions. 2D games, of course, as well as RuneScape in its full screen mode, I don't know its secret, but it works fantastically. Anyway, if the game is windowed, it still suffers the catastrophic crash sometimes, but I can get out of the window and kill the process. It happens fairly quickly sometimes, and other times it seems like it won't happen, which makes it all the more depressing, when in fact, it does. Just chiming in with my two cents.

---

### Post by mysteriousdarren on 2009-02-17
I tried other resolutions and none of them seemed to work. I always seemed to leave each of the games in full-screen mode, and even when in the windows are maximized. I was wondering if there is a fix for it.

Thanks for the two cents.

---

### Post by ctsdownloads on 2009-02-17
Which System76 PC is having these issues?

---

### Post by mysteriousdarren on 2009-02-18
I have a Serval Laptop, if that helps. I bought it Sept-Oct of last year.

---

### Post by jcoaster2008 on 2009-02-21
This same problem is happening to me. When I am playing a full screen game, it often switches to a window, and renders the computer completely unresponsive. The only way I can do anything is to shut off the computer and turn it back on. This makes it very difficult to play a game.

---

### Post by xakh on 2009-02-21
I have the current pangolin, with the following specs:
 	Pangolin Performance
Options
*Bluetooth : Bluetooth
+ $0.00
*Car AC Adapter : no car AC adapter
+ $0.00
*Display Resolution : 15.4" WXGA Super Clear Glossy LCD (1280 x 800)
+ $0.00
*Extra AC Adapter : no extra AC adapter
+ $0.00
*Extra Battery : no extra battery
+ $0.00
*Hard Drive : 320 GB 5400 RPM SATA II
+ $55.00
*Hardware Warranty : 1 Yr. Ltd. Warranty and Technical Support
+ $0.00
*Laptop Bag : no bag
+ $0.00
*Memory : 4 GB - DDR2 800 MHz - 2 DIMMs
+ $70.00
*Operating System : Ubuntu 64 Bit 8.04 (Hardy Heron) Linux
+ $0.00
*Optical Drive : CD-RW / DVD-RW
+ $0.00
*Processor : Core 2 Duo P8400 2.26 GHz 1066 MHz FSB 3 MB L2 (25 Watt)
+ $125.00
*Wireless : 802.11 agn
+ $0.00

Just copied from the page from shipping last october/november.

---

### Post by mysteriousdarren on 2009-02-22
Ya I have a Serval Performance. I hope we get some help on this, especially not liking when the computer becomes unresponsive after it becomes a window.

---

### Post by thomasaaron on 2009-02-23
I'm sorry, but I really have no way of supporting these games.

Did you try disabling your desktop effects to see if that helps? (System > Prefs > Appearances > Visual Effects > None)

---

### Post by xakh on 2009-02-24
I had once, it still happened. Also, really, no effects is a sorry work around, as I use some of the Compiz effects for productivity reasons, and it would just make my desktop kind of lame.

---

### Post by thomasaaron on 2009-02-24
Several people have said they've experienced similar problems, and your hardware is pretty common, so I'd be surprised if someone on the WineHQ forums hasn't encountered and fixed them. 

Have you tried posing your question there?

Wine just requires too much specialized tweaking for us to support it.

---

### Post by xakh on 2009-02-25
It's not on wine that the issue crops up. OpenArena, Sauerbraten and that weird game Powermanga, all deliver this issue when played for too long.

---

### Post by moster on 2009-02-27
Try disable screensaver and maybe other power saving things... It help with similar problem.

---

### Post by 3Miro on 2009-03-02
My perhaps worthless opinion on the issue:

One problem could be the heat. When I play Planet Penguin Racer, I get at least an extra 10 degrees Celsius on the thermal monitor. Alien Arena would be worse. I would try and monitor that.

A note on Powermanga: this game has ridiculous requirements to play. I sometimes have trouble running it on my desktop, especially on a 64-bit Linux.

---

### Post by eyecreate on 2009-03-04
I have a serp4 and have had this happen before too. I googled it and it seems that gnome-screensaver doesn't detect that your mouse/keyboard is giving input when a fullscreen game takes control. I fixed this temporarily by making a shortcut in my menu to(gnome-screensaver-command --inhibit) and executed it every time I started a game, no problems after that. This was a big problem discussed when the game World of Goo was ported to linux and since nobody working on Gnome Screensaver has found/fixed this bug yet, they put the same hack I told you into the game to prevent what is happening to you from happening. You could also try using xscreensaver instead of gnome's one, but in your situation, it may be more than you want to do right now. I finally fixed my issue by using the compiz screensaver plugin and turning gnome-screensaver off.

---

