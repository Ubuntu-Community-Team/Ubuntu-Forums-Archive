---
title: "Disappointed so far"
date: 2008-04-04
forum: Testimonials &amp; Experiences
---

### Post by brento73 on 2008-04-04
Having used linux in the past, I decided to try setting up an audio workstation and leave WinXP behind forever. The idea of not having to pay hundreds, even thousands, for software and plugins is very appealing, as is sticking it to the man. I wanted to run something 64bit, feeling that would take advantage of my system more completely, and found a few possible choices.

I tried 64Studio, but couldn't get the x-server to run, at all, making anything multimedia completely impossible. Since a friend is running Ubuntu 7.10, and there was a 64bit Ubuntu Studio, I figured I'd give it a shot. The install went smooth and quick, and the x-server actually ran without hesitation, making it instantly more impressive that 64Studio had been. It even gave me a little icon to click which would install the NVidia drivers for my 8600gt, and that all worked fine as well.

Then I decided to install some updates. I didn't think to note which one it was, but something caused to updater to hang, and after rebooting I got no screen at all. There wasn't any signal going to the monitor, and nothing seemed to change that. I reinstalled and decided to ignore the updates for now.

So I fire up Ardour, and after figuring out the basics, loaded some tracks I'd recorded in the past. At first it seemed great, then it locked up. It took several reboots before it would run at all, and only occasionally was I able to get any sound to actually come out of my speakers. The same sound issue seemed to plague Totem, which is my default audio/video player. All the while, the system sounds work fine, as do all 'Test' buttons in the sound menu. Sometimes it would work, but after stopping and hitting Play again it would stop working.

In the midst of all this, my mouse/keyboard began to suffer horrible, for lack or a better word, lag. I had to reboot to fix the issue, and it seemed to happen at random times, with no connection to how hard the system was working.

The only thing that I have had any luck with is getting Flash working in Firefox, which I did do(and very easily) thanks to a post on these forums.

Understand that I want this to work out. I want to like linux, and be a champion for open source in general. I really, really want to tell MS they can stick it, and never have to pay an arm and a leg(or resort to piracy) again just so I can have the software I need. I think that making a self-produced album on open source software would be about as 'indie' as one can possibly get. I also need to not spend all my time playing computer tech when I should be creating art(or something close to art).

Convince me that I belong on a linux system; that I can do everything I could ever need without XP. Please.

---

### Post by misfitpierce on 2008-04-04
No one can convince you but yourself. I use only Ubuntu 64 bit and no other OS. In fact I had a Intel apple and have not touched windows since before Vista on XP. I run fine without it but only you can decide which OS is right for you.

---

### Post by Gen2ly on 2008-04-04
First off brento73 I can assure you that what you are experiencing is a bug.  The system shouldn't and usually doesn't hang like that.  Judging from the evidence it sounds like there are some driver conflicts.  I haven't used Studio so I can't be as much help as I like but take a look at the syslog and look for errors.  Also if it helps, there are other distros that tailor to multimedia.  For instance, I hear that Linux Mint is good at it.

[http://www.linuxmint.com/about.php](http://www.linuxmint.com/about.php)

---

### Post by brento73 on 2008-04-04
Thanks for the link, I'll look into it.

I was able to use asoundconf to convince Ubuntu to ignore my on-mobo sound(BIOS lacks the option to disable), which seems to have helped at least some of my sound issues. Ardour still doesn't make any sound, but Audacity does, so that's a start.

Any ideas on the mouse/keyboard 'lag'? Right now I consider that my main issue, since it makes figuring anything else out much more difficult. I've confirmed with system monitor that my system isn't working much at all, and yet the problem persists. Both keyboard and mouse are wired USB, so my first guess is some issue with the USB drivers?

Thanks in advance for any ideas.

---

### Post by DJiNN on 2008-04-04
Hey brento73, i know what you mean about the whole Windows based studio thing, and i really hope that you find an answer. I use all flavours of Linux on several machines here, but in my studio i've resigned to still using XP..... Why? Because i've still not found a Linux distro that "Does it all" the way that XP does. 

I use Cubase (VST 32) everyday for work, and also use Reason and several other apps for original stuff. There are some really great apps out there for a Lin based system (Ardour, RoseGarden etc) and i've read stories about many people using them successfully on a regular (Daily) basis..... but i haven't reached that "Studio Nirvana" yet! :)

Ubuntu Studio is probably one of the best ones that you can work with, because there are so many resources available and if you get a problem there's a good chance that you'll get it fixed fairly fast. 

If you do manage to get good results with a particular setup then please share your results because i'm sure there are many others here who would be interested. 

Oh, and you might like to have a look at Zenwalk, because the guy that develops Ardour uses Zenwalk as his main platform..... can't say better than  that for a distro eh? :)
Good luck.

---

### Post by ubuntu-freak on 2008-04-04
Have you tried plugging them into different USB ports? That has helped some with your issue. A kernel upgrade helps others, but then your graphic driver may also need updating after a kernel upgrade.
 
Nathan

---

### Post by Thelasko on 2008-04-04
From [Wikipedia ]("http://en.wikipedia.org/wiki/Ubuntu_Studio") I found out that Ubuntu Studio has a different kernel with a different scheduler than normal Ubuntu.  What this means is that your computer is going to give priority to making graphics and audio perform in real time at the expense of things such as your keyboard.

If you don't like that and can live with some latency, I suggest you install the regular Ubuntu 64-bit OS and add and remove programs to suit your needs.  The amount of latency you will experience really depends on your system hardware.

---

### Post by brento73 on 2008-04-04
I may have to do that, just install a normal Ubuntu kernel. Can someone point me to a how-to for getting a normal kernel without reinstalling everything?

---

### Post by ubuntu-freak on 2008-04-04
> **brento73 said:**
> I may have to do that, just install a normal Ubuntu kernel. Can someone point me to a how-to for getting a normal kernel without reinstalling everything?

 
The 32-Bit Ubuntu Studio may work better actually, give that a try. 
 
Regarding the kernel, try searching Synaptic (System>Administration) and see what kernels are available to you. You may be after the low latency one, but I'm not completely sure. Once installed, you can decide which to boot with at the GRUB menu.
 
Nathan

---

### Post by steveneddy on 2008-04-04
I always had issues with the -rt kernel in 64 bit.

Maybe Hardy will fix these issues.

---

### Post by prostar on 2008-04-04
Hopefully I am catching you before you re-install...  The "lag" you feel may just be a problem with your graphics not using hardware acceleration.  I had this problem twice (each time I "upgraded" my ATI graphics).  There are a few choices for configs, but I think (some one chime in if you know for sure) that you want to end up with fglrx-xorg.  Also just for comparison, make sure that your System -> Preferences -> Appearance has no advanced effects on for starters.  You can try a tool called "envy", that will get you spanking fresh drivers.  I didn't have good luck with it, but most people do.

If your only remaining problem is the sound, make sure you install "pulse audio".  Theres a thread on here somewhere, but you need to install most of the things in synaptic related to pulse audio.

Good luck!

Oh and just for motivation, I use my x64 to encode video with 64 bit stuff (tovid) and it's close to 2X faster than a 32 bit.

---

### Post by brento73 on 2008-04-05
Thanks for the suggestion, but I actually do have hardware acceleration enabled. I'm pretty sure that it's not a graphics issue, because it's not simply a matter of the movement not displaying properly, the system isn't registering it. If I type, for instance, at a normal pace(for me only about 30-40 wpm) it will only catch about every 3rd key press. That seems deeper than a video driver.

I'm thinking I'll try getting the normal x64 kernel and booting that up. In reality, the super low latency isn't a big deal to me anyway. I long ago gave up recording tracks direct to my computer and just got an 8-track Tascam DP-01. I then export the tracks to my computer for mixing/mastering. It's worked great with Sound Forge in WinXP, and I've already been successful with getting the tracks exported over to linux as well. Mostly what I need is a way to apply effects to a track and hear the effects without too much delay. Running several virtual instruments and listening to a dozen tracks with effects on them while I track a couple more isn't something I really see myself doing in the near future.

I've had good luck with Audacity, which should suffice for the mixing part, and does have access to all the plugins, but I can't listen to a track WHILE I'm making adjustments to the effect, so it doesn't flow as well as I'd like.

---

