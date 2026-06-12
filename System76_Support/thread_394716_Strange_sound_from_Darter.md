---
title: "Strange sound from Darter"
date: 2007-03-27
forum: System76 Support
---

### Post by madcitybrit on 2007-03-27
I just received my Darter, it's a nice looking machine. Everything appears to be working perfectly (wi-fi, bluetooth, suspend and hibernate etc.). I was surprised to find the function button working for the volume controls too, although Fn and screen settings (brightness) don't seem to work right now. Service was also excellent (I originally ordered a Gazelle Performance but changed my mind post-order and the sales rep couldn't have made the process any easier or quicker!).

However, the machine seems to be making a strange noise, every 20-30 seconds or so, regardless of load (even with nothing running after a fresh boot and left sitting idle). It doesn't seem to be fan related (the fan is extremely quiet, but when it does come on, which is rarely right now, it's completely separate from this other noise). I have had the CD/DVD tray open, so it's nothing there either. The sound is a little hard to explain, but it sounds a little like a mechanical drop of water, if that makes any sense. Oh, and it's not coming from the speakers, which I have also muted. Has anyone else experienced a similar thing? Overall the system is really nice, but the noise, and the regularity of it, is already becoming quite annoying.

Additional...
The sound seems to be coming from the right hand side (possibly right front). I'm guessing it's hard-drive related, but can't say for sure (+ I don't know if this is where the hd is located!). Also it's quite loud, in that I don't need to be in front of the machine to hear it, I can still hear the noise from the other side of my desk at work. I can hear when the hard drive spins, and that sounds normal (and quiet), but I've never before heard the 'droplet' type sound I'm getting right now.

Thanks.

---

### Post by thomasaaron on 2007-03-27
That does sound strange. We've not heard of that symptom before.
The hard drive does make a distinct noise when booting or recovering from suspend, but not every two or three seconds.

If the problem continues and you'd like to replace the drive, send us an email at support(AT)system76.com, and we will make the appropriate arrangements.

Best,
Tom

---

### Post by madcitybrit on 2007-03-27
I'll monitor it over the next few days, see how it goes, and let you know. Thanks.

---

### Post by iMav on 2007-03-27
> **madcitybrit said:**
> although Fn and screen settings (brightness) don't seem to work right now.
They were working previously but now do not?  (I assume so as I am under the impression that all hardware is supported and functional "out of the box"...hence the big benefit of buying from the great folks at System76!)  :)

---

### Post by Rotarychainsaw on 2007-03-27
I get a kind of light screeching from the right front when I drag windows with beryl turned on. Maybe related?

---

### Post by madcitybrit on 2007-03-27
> **iMav said:**
> They were working previously but now do not?  (I assume so as I am under the impression that all hardware is supported and functional "out of the box"...hence the big benefit of buying from the great folks at System76!)  :)

The sleep, email, web, LCD toggle, touchpad disable/enable, mute, and volume up/down all work with Fn. Nothing happens when I use Fn and the brightness or contrast keys (F6 and F5 respectively). Not sure about F2 at this point (I'm currently at work and don't know what the F2 symbol is for except for maybe an innacurate guess!). Oh, Fn and Num Lk works too.

Perhaps someone else with a Darter could clarify the above for me, and whether Fn and brightness/contrast controls are supported at this time (and what I might need to do if they should work). Thanks.

---

### Post by madcitybrit on 2007-03-27
> **Rotarychainsaw said:**
> I get a kind of light screeching from the right front when I drag windows with beryl turned on. Maybe related?

Hmm, a light screeching doesn't sound right! I just got my Darter and I'm not setup to use Beryl as of yet. The noise I get is likely my hard drive, and it's certainly not a screeching sound (nor is it related to anything I'm doing on screen). Is it coming from your speakers?

---

### Post by Rotarychainsaw on 2007-03-27
well maybe screeching wasn't the right word. It doesn't sound mechanical whatever it is, and its really quiet. I also think my main computer makes a different kind of hum when a window is dragged in Beryl.

---

### Post by madcitybrit on 2007-03-28
Okay, so perhaps "mechanical drop of water" wasn't the best description. More of a click...click every 20 to 30 seconds. 

Seems it's something to do with the hdd heads parking, power management related. I found another post here (which also has links to other related posts)...

[http://ubuntuforums.org/showthread.php?t=269938](http://ubuntuforums.org/showthread.php?t=269938)

Quote from above thread:
"I've since found out that this is a known issue with my Western Digital hd in laptops. The drive is incorrectly interpreting a signing from the laptop's power management. Western Digital has a firmware update on their site. However, when I attempted to use it, it said that I already have the latest firmware."

As a temporary solution I can use "sudo hdparm -B 255 /dev/hda" which turns off power management (and stops the clicking). Not the best when running off of battery though.

Does anyone know of a permanent fix for this?

Also, I didn't check what the PM level was (sudo hdparm -i /dev/hda) before running the above to switch it off. Does anyone know?

Thanks.

---

### Post by crichell on 2007-03-28
> More of a click...click every 20 to 30 seconds. 

Oh - I know what you're talking about now.  It is power management related (you probably don't here the sound when the laptop is plugged in).  It looks like this is fixed in Feisty.

> although Fn and screen settings (brightness) don't seem to work right now.

Fixed in the upcoming Feisty.

---

### Post by madcitybrit on 2007-03-29
> **crichell said:**
> Oh - I know what you're talking about now.  It is power management related (you probably don't here the sound when the laptop is plugged in).  It looks like this is fixed in Feisty.

Is this bad for the hard disk?

Also, since turning power management off with "sudo hdparm -B 255 /dev/hda", do you know what the original setting would have been, or should be, so I can turn it back on? Looks like I can use any number from 1 - 255, I just don't know what!


> **crichell said:**
> Fixed in the upcoming Feisty.

Looking forward to its release. Hopefully an upgrade shouldn't be too difficult. Btw, so far I am loving my Darter. Great computer, great company and support.

Cheers.

---

### Post by crichell on 2007-03-30
> Is this bad for the hard disk?

I don't think it's stressing the drive.

> 
Also, since turning power management off with "sudo hdparm -B 255 /dev/hda", do you know what the original setting would have been, or should be, so I can turn it back on?

That's a good question.  I haven't found a default setting scouring the forums.  We'll keep looking.

---

