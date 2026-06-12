---
title: "Stuttering Playback"
date: 2008-03-23
forum: Virtualisation
---

### Post by SyCo123 on 2008-03-23
In virtual box streaming video such as netflix is very choppy, audio is fine.

I have XP in virtual box. I can see this on megavideo  too but it plays fine on ubuntu. Of course I can't watch netflix on ubuntu without virtual box.

Going legit is hard work!!

---

### Post by veratyr on 2008-06-08
I have the same problem using 8.04 32bit and virtualbox 1.6. My video memory configuration in virtualbox is set to 128MB and it still stutters even with compiz disabled.

---

### Post by redcharlie on 2010-06-24
I had issues with choppy netflix playback with the following setup:

Gigabyte ma78gpm-d2sh (micro atx, ATI Radeon 3200 integrated video)
Athlon X2 4450e (2.3 GHz dual core "Brisbane")
2GB DDR2 800
Cool and Quiet disabled in Bios, AMD-V enabled in bios

Ubuntu 9.04 "Jaunty" hostOS, 32 bit
Windows XP Guest, 32 bit (using Virtual Box) 512MB base memory, 64MB video memory, and AMD-V extensions enabled.

Everything I read indicated I should be able to run Netflix in my VM without any problem. But when I did playback was very poor, stuttering and stopping so often it was quite unwatchable.

Then I accidentally started up the VM with the "null" audio driver, and noticed that Netflix worked fine, no stuttering or dropping frames (although of course I had no sound).

Googling around, I read that pulseaudio has issues here:
[http://ubuntuforums.org/showthread.php?t=1168194](http://ubuntuforums.org/showthread.php?t=1168194)

Sure enough, switching from pulseaudio to OSS (system->preferences->sounds, change to OSS for "music and movies") did the trick, along with changing the sound driver in the VM to OSS. Now netflix works great!

BTW, I also got netflix working w/o any issues on the following:

Asus m4a785td evo-m (micro atx, ATI Radeon 4200 integrated video)
Athlon II X3 435 (Triple core "Rana" 2.9 GHz, 4th core unlocked)
4GB DDR3 1333
Cool and Quiet disabled in bios
Ubuntu 10.04 "Lucid" HostOS, 32 bit
Windows XP 32 bit guest, with Virtual Box, 1024MB base mem and 64 MB video mem

At first I thought that the Brisbane just wasn't powerful enough, since I had no trouble with the Rana.  But now I'm thinking that it may be that there are fewer issues with sound in Lucid

---

### Post by xtremesupremacy3 on 2010-06-24
I want to just point out that you replied to a post from 2 years ago, I doubt there will be a reply.

Arthur

---

### Post by SyCo123 on 2010-06-24
Oh no, I monitor my email :) It is a bit like stepping out of a time machine though!

I gave up in the end and have been dual booting but your info about the problem is well timed. I've been thinking about trying again as I hate dual booting. Just yesterday I moved all the files off my laptop ready for a total do-over. Curiously well timed post, are you part Jedi? :guitar:

---

### Post by SyCo123 on 2010-07-06
So XP into virtual box was very easy as was getting wireless network to play along. They've done a great job improving that experience.

Netflix is running but it stutters at full screen still. I tried dffernt OSS, Pluse and Alsa but it ran the same. 

Before, when I was dual booting, Netflix ran in XP full screen fine but Hulu stuttered full screen. Now Hulu does the same thing in Xubuntu while Netflix full screen in VBox(3.2) might just be too much for this machine. I can live without full screen and the wife has an XP laptop for times we want full screen Netflix. Shame to have to keep an XP box around for something that Xubuntu/VBox/XP can't do though.

---

