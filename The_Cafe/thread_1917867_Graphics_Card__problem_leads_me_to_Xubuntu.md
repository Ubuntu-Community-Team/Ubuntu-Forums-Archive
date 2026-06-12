---
title: "Graphics Card  problem leads me to Xubuntu"
date: 2012-01-30
forum: The Cafe
---

### Post by cloyd on 2012-01-30
This isn't really a support question, but I'm just wondering why this is happening. I suspect that it is happening is simply because my netbook has an old, outdated graphics card.    (01:05.0 VGA compatible controller: ATI Technologies Inc RS690M [Radeon X1200 Series]
 ) Anyway, this is the story.  
 

 This is my netbook, a Gateway LT310l 3u.  Been running Ubuntu since 9.04.  After 9.10, I started having some problems with video crashes, but was able to find fixes . . . until the advent of Unity. This  is not an anti-Unity post . . . I'm running it on my work machine, and I love it. But this machine will not . . .  absolutely not run Unity. With a live USB, video crashes at the splash screen. (any version with Unity).   
 

 The other day, I tried to boot with a USB with Linux Mint. It wouldn't boot, and when I tried to reboot back to 11.04. It would not boot . . . just a flashing dash on the screen.  I got another torrent download and made another Linux Mint (latest Ubuntu version). Made fresh install  on machine.  Video crash. Tried Linux Mint Debian. Same thing. Tried Lubuntu. This seemed to work, however, video crashes seemed to happen at random times.  Tried Fedora. Video crashed about 2 minutes after logging in. All these were fresh installs. Tried Puppy Linux. This worked, but 1) I had a lot of relearning to do here, and I wasn't sure it would run all the programs I wanted. 2) I had to boot from a USB, even though I could save the session. I didn't like that.
 

 I tried 11.10 again. What if it would work in 2d?  So, installed and booted (no boot from live USB). I could log in, and it worked in 3d about 2 seconds after logging in. It worked in 2d about 2 minutes after logging in.
 

 I've burned about 2 days on this now, but I'm retired, so what? I've got the time. But my wife says I'm obsessed. I try one last thing. I fire up bit torrent again, download Xubuntu. Guess what? At 10:30 PM, the live USB boots perfectly.  The next morning, I do a fresh install, and it has run all day now, and no crashes.  I've been busy restoring all my favorite apps and learning how to customize it a bit. Still a bit to learn, but this looks like what I was looking for.  Found a thread,   
 [http://ubuntuforums.org/showthread.php?t=1909569&highlight=xubuntu&page=6](http://ubuntuforums.org/showthread.php?t=1909569&highlight=xubuntu&page=6)  and someone here said this was Ubuntu's best kept secret.  Maybe so.   
 

 Is this all because of an old, outdated card Gateway put in some netbooks? Is there any other way around it? If not, I do think I can live well with Xubuntu.  
 

 And, has anyone else had a similar experience?
 I really didn't want to use Puppy Linux, but that CD I had to burn may come in handy some day.


Note . . . video just started to crash. I closed some windows, and it cleared up.   ??????

---

### Post by 3Miro on 2012-01-30
Your video problems have nothing to do with Unity. AMD dropped the support for some of the older video cards for the latest kernels, I think your card was on the list. You will not be able to use 3D graphics with newer kernels on any distribution.

Xubuntu and Lubuntu will work great for you as they don't need 3D support and generally are designed to have low graphical requirements.

---

### Post by Khakilang on 2012-01-30
I don't have problem with Unity. But I find it a bit sluggish when processing hundreds of RAW images. With XFCE it is much swifter.

---

### Post by cloyd on 2012-01-30
> **3Miro said:**
> Your video problems have nothing to do with Unity. AMD dropped the support for some of the older video cards for the latest kernels, I think your card was on the list. You will not be able to use 3D graphics with newer kernels on any distribution.

Xubuntu and Lubuntu will work great for you as they don't need 3D support and generally are designed to have low graphical requirements.


Thanks. Like I said, this wasn't an anti-Unity thread . . . I like unity.

Lubuntu really didn't work very well. Video really was unpredictable.  Since posting this, have had some "partial" video problems . . . the top of the screen starts to deteriorate. I shut down all applications, and it goes away, and I can start again without rebooting.

Kind of like xubuntu.
__

---

### Post by 3Miro on 2012-01-31
I like XFCE myself and it is on a pretty powerful machine. Unfortunately in your case the graphics drivers will probably not get any better, reverting to an LTS or Debian 6 may work better for you.

---

### Post by mips on 2012-01-31
Googling 'RS690M linux' reveals a lot of issue with that chipset.

---

### Post by cloyd on 2012-01-31
I I knew how, I'd edit title of the thread and get unity out of it. I'd be using it if it would run on this machine.  Love the dash.  

This machine ran all day yesterday being used intensively. No crashes until last night. I did two things. I had enabled compositing, and installed and started conky. I have since turned off compositing. Don't really need it. If crashes continue, I'll get rid of conky. This might bother me a bit, because I like conky.  

And, if this continues, I may well revert to a previous release. 

I've learned something else. Installs are much easier when I do a completely clean install. Install to the entire drive, not just one partition.  When I get what I want, I'll probably have two partitions, one for media, and the rest for programs and documents.  Another thing is this. I've kept really crucial documents in dropbox.  There are things I don't want to lose, but could live without, and things I must not lose. Those things go to dropbox.

---

### Post by philinux on 2012-01-31
> **cloyd said:**
> I I knew how, I'd edit title of the thread and get unity out of it. I'd be using it if it would run on this machine.  Love the dash.  


Fixed that for you.

---

### Post by mips on 2012-01-31
cloyd, what driver are you using?

---

### Post by cloyd on 2012-01-31
I am not using any proprietary drivers.  I am simply using what  comes with the kernel at install.  I've thought I need to understand drivers n better in linux, so I may not be answering your question correctly.

No crashes so far this morning (yes, it is still morning here).

PS. Phiilinux, thanks for changing the title of the thread. I appreciate it.

---

### Post by 3Miro on 2012-01-31
> **cloyd said:**
> I am not using any proprietary drivers.  I am simply using what  comes with the kernel at install.  I've thought I need to understand drivers n better in linux, so I may not be answering your question correctly.

No crashes so far this morning (yes, it is still morning here).

PS. Phiilinux, thanks for changing the title of the thread. I appreciate it.

Only open drivers are included in the kernel, some companies make additional proprietary drivers that you have to get separately (from Additional Drivers).

Intel has only open drivers and hence Intel video cards work very well out of the box. Too bad that the Intel video cards are just not as powerful as the Nvidia or ATI.

ATI and Nvidia have both open and closed drivers. Before AMD took over, ATI wouldn't do drivers for Linux at all. Since AMD is in charge, both the open and closed drivers have seen great improvement, however, their main focus is the newer cards. What is bad for you is that you have an older video card, the prop drivers just dropped the support and the old open drivers for ATI were never good anyway.

Nvidia also has bad open drivers. They have made improvements lately, but the open Nvidia drivers are still lacking. The advantage of Nvidia is that they have excellent proprietary drivers, hence Nvidia + proprietary drivers gives you the best video performance on Linux. Just make sure to stay away from Optimus.

---

### Post by forrestcupp on 2012-01-31
> **3Miro said:**
> 
Intel has only open drivers and hence Intel video cards work very well out of the box. Too bad that the Intel video cards are just not as powerful as the Nvidia or ATI.The good thing is that Intel Graphics are getting better. The newest GPUs are better than AMD's low end stuff that comes in most computers, and I hear the next generation is going to step it up even more.

> **3Miro said:**
> Before AMD took over, ATI wouldn't do drivers for Linux at all.That's not true. We were using ATI's proprietary drivers well before they sold to AMD. They just wouldn't open up their specs for the open source drivers until AMD bought them. It *is* true that things got much better for open source and proprietary drivers after they became AMD, though.

---

### Post by mips on 2012-01-31
> **cloyd said:**
> I am not using any proprietary drivers.  I am simply using what  comes with the kernel at install.

I would try the proprietary drivers if I was you, from the little bit I have read that chipset is supported, R600 and newer (as of Catalyst 9.4)

[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)
[https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)

---

### Post by 3Miro on 2012-01-31
> **forrestcupp said:**
> 
That's not true. We were using ATI's proprietary drivers well before they sold to AMD. They just wouldn't open up their specs for the open source drivers until AMD bought them. It *is* true that things got much better for open source and proprietary drivers after they became AMD, though.

I know there was a period when ATI wouldn't provide Linux drivers at all. They probably started supporting Linux before AMD, but as you said AMD made the big difference.

---

### Post by BrokenKingpin on 2012-01-31
I switched to Xubuntu just because I liked Xfce far more than Unity.

---

