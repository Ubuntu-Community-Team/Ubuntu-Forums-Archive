---
title: "My ubuntu 10.10 does not recognize my Diablo 2 disc"
date: 2011-02-13
forum: Wine
---

### Post by Foxjin on 2011-02-13
Hello to my new fellow Linux Users! 

I recently installed Ubuntu 10.10 on my laptop in an effort to make it run more smoothly. Long story short, mission accomplished! 

Now the problem is this: A few days ago I tried to install Diablo 2 on the system just to see if I could (Regular version, not expansion) and I have never run into such a major pain in all my years of computing!

Everything is up to date (both Wine and PlayonLinux) I've tried every command I can find from my searches on the internet and I have yet to tackle this beast so I finally broke down and am specifically asking for help. 

The main headache is that when I pop in my Diablo 2 CD, the system just refuses to recognise it. For the life of me I cannot figure out where the disc and it's files are supposed to show up.

Now, I'm wondering, is it something to do with the way 10.10 detects discs (I've tried DVD movies and they detect perfectly) or is it something to do with my drive? My drive shows up under computer, and again when I run dmesg. It does NOT get detected when I have the disc in BEFORE I booth the computer. In that case my drive isn't detected at all and requires a complete reboot in order for the system to detect it. 

For the love of all that is sacred in computing, please help!

---

### Post by Foxjin on 2011-02-13
The biggest issue is that my Diablo 2 disc is not being mounted anywhere on the system as far as I can tell, so Wine does not have a path to it. I'm using the latest everything. Anybody have any ideas?

---

### Post by Unguidedone on 2011-02-13
I had the same probelm but i could not solve it :(

In the end to work around the probelm i installed d2 on windows copyed the folder and pasted it in the wine virtual c drive.

---

### Post by Foxjin on 2011-02-15
Yeah, I finally had to give up and download the game from battle.net. It installed perfectly but now I have a new problem. 

When I load it up, the game goes through the first two Blizzard intros before it moves on to the next and just hangs with a bright white screen. I have no idea how to fix this. Is anyone going to help? Please?

---

### Post by Foxjin on 2011-02-15
These are the two lines I get in the terminal when Diablo 2 gets the "white screen"

err:ddraw:ddraw_surface7_Flip Can't find a flip target
err:ddraw:ddraw_surface7_Flip Can't find a flip target
fixme:d3d:swapchain_init Add OpenGL context recreation support to context_validate_onscreen_formats

What does it mean? Someone out there has got to know an answer to this...

---

### Post by Foxjin on 2011-02-15
Nevermind. I finally fixed it myself. Thanks for all the help, jerks.

---

### Post by Sobster on 2011-02-22
<- Linux Newbie here. I'm scared to try and get this game running. Just looked at your post. Gonna try and do what you did and see if i cant get it running. ](*,)

---

### Post by Dopetastic on 2011-03-07
I was recently able to get this all to work for both Diablo and Diablo II. A few details that may help a few folks (this isn't a tutorial for using Ubuntu...minor instruction has omitted =/ ):

- Be sure that you have the latest version of wine installed
- Configure wine (winecfg), and select the "Drives" tab
- Confirm that your cd-rom drive type is set to "CD-Rom" (under "Advanced", "Type"-drop)
- Insert the install disc for the Diablo flavor of your choice
- Now, for the "Path" setting click "Browse" and select the actual Diablo disc as your mount point (i.e. rather than just "/media" select "media/INSTALL" -- Diablo II's root directory in this example)
- Run the appropriate setup .exe from the CD via wine (or Q4wine like I did) and you *should *be golden

Again, I ran the setups using q4wine...but to me it seems that the problem was just mounting the "right" directory as the cd drive. I was able to play both Diablo I & II full-screen (so far) with next-to zero issues.

I've seen a few threads in various forums that didn't seem to indicate an actual resolution to this situation. I hope this helps someone!

-------------

Some details that may be pertinent:
nvidia  9600 GT
wine 1.2.2
Linux 2.6.35-27-generic -- x86_64

---

