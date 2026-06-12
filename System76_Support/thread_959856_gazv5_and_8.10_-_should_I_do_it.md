---
title: "gazv5 and 8.10 - should I do it?"
date: 2008-10-26
forum: System76 Support
---

### Post by ctsdownloads on 2008-10-26
So I own a gazv5 and am considering upgrading Ubuntu 8.10 once it goes live (not RC).


I am enjoying 8.10 on of my test desktops, watched it fail **badly** on my old Averetec notebook thanks to "dynamically creating Xorg.conf and the apparent mismatch with VIA Unichrome video chipset. No screen detected with zero means of reconfiguring the xorg.conf makes for "big trouble in little china", let me tell ya.

My main desktop will as always, remain stable using the older release (8.04) as this is how I keep myself out of trouble. I also do a lot of SSH to access my mail on that machine, too. So I like to leave it alone. :)

So Tom, what's the word on Intrepid - am I going to smell "burning firmware" coming out of my Intel ethernet port (kidding) or do you see any challenges with regard to things working well. Last I heard, ubuntu disabled the bad Intel driver that was hosing chipsets, or something to that effect.

Thanks!

---

### Post by thomasaaron on 2008-10-27
Well, I've not tried it on our GazV5 yet. I'm sure I will by weeks end, though. I'm getting antsy too!

Personally, I'd recommend letting us hose our machines before you hose yours.:lolflag:

But, hey! It's a free country, right?:popcorn:

---

### Post by ctsdownloads on 2008-10-27
> **thomasaaron said:**
> Well, I've not tried it on our GazV5 yet. I'm sure I will by weeks end, though. I'm getting antsy too!

Personally, I'd recommend letting us hose our machines before you hose yours.:lolflag:

But, hey! It's a free country, right?:popcorn:

Thanks Tom. Yeah, I would feel better knowing how the networking hardware is going to stand-up with that issue I sent you awhile back still being a bit of a mystery. Please let me know what you find out.

Thus far I am really impressed with 8.10 as it has done well with improving NM speed/responsiveness while also not regressing natively supported wifi chipsets - rt73usb (*Edimax ew-7318usg*) & ZD1211 (*Zyxel Zyair G-220 v1 or 2*). So knowing that it will not do the same or worse (remember the bug I fwd'd ya) is going to be key for this Intel based machine.

Thanks!:)

---

### Post by thomasaaron on 2008-10-27
I guess I need to keep my trap shut! I was hoping you'd go first! :popcorn:

---

### Post by ctsdownloads on 2008-10-27
> **thomasaaron said:**
> I guess I need to keep my trap shut! I was hoping you'd go first! :popcorn:

Heh. I might if I was sure it would be a software hosing and not that of the hardware variety. :) Software can be reinstalled while the latter means sending my notebook in for repair help from you guys. ;)

---

### Post by ctsdownloads on 2008-10-27
In all seriousness, if you want me to try it I will over the weekend. I just need assurances with regard to that firmware bug that we addressed some time back. It has me spooked, not sure if I am able to take that kind of risk. You think I am safe to try it? :confused:

---

### Post by thomasaaron on 2008-10-27
Probably. But I was just joking.

I'm imaging a GazV5 now for testing. I should be done by tomorrow.

---

### Post by ctsdownloads on 2008-10-27
> **thomasaaron said:**
> Probably. But I was just joking.

I'm imaging a GazV5 now for testing. I should be done by tomorrow.

Tom, you continue to be a gentleman and a scholar. :)

Thanks! I am looking forward to it.

---

### Post by thomasaaron on 2008-10-27
> Tom, you continue to be a gentleman and a scholar. 

Could I get you to put that in writing and mail it to my wife! :lolflag:

I just checked with R&D on this issue. They say that:

1. We've never used the e1000e nic, so we are not subject to that bug
2. Ubuntu has blocked that problem
3. They will be patching it in 8.10

So, if you do want to tinker with 8.10, you should be fine.

---

### Post by ctsdownloads on 2008-10-27
> **thomasaaron said:**
> Could I get you to put that in writing and mail it to my wife! :lolflag:

Heh, I hear ya there. My wife and your wife ought to go bowling to discuss what it is like being married to Linux geeks. :) 

> I just checked with R&D on this issue. They say that:

1. We've never used the e1000e nic, so we are not subject to that bug
2. Ubuntu has blocked that problem
3. They will be patching it in 8.10

So, if you do want to tinker with 8.10, you should be fine.

Sweeeet - thanks again. Will see about doing some testing this weekend.

---

### Post by thomasaaron on 2008-10-30
Finished testing the GazV5. 
No problems.

Well, to record sound, you have to go to System > Prefs > Sound and set stuff to Pulse Audio.

Then, the set up in sound controls is a bit different than in Hardy. But it works fine once you figure it out. I imagine I'll be posting screenshots of it.

On Intel GazV5 machines, cloning and extending with an external monitor is much slicker and easier than in Hardy. It auto-inserts virtual resolution lines in your xorg.conf if they are needed. I believe that was a manual process in Hardy.

---

