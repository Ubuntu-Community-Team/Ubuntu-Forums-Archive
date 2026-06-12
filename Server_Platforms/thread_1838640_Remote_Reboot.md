---
title: "Remote Reboot"
date: 2011-09-04
forum: Server Platforms
---

### Post by TripleD on 2011-09-04
Here's the low-down: before moving to China I set up a dynamic dns with my ubuntu server at home. I tried it out before I left (ssh, web access, etc.) and everything seemed to be fine. When I arrived in China I tried out these same tests and, to my delight, everything was peachy keen.

Then all of a sudden I was cut off. My website was unreachable, ssh requests went ignored, and for all intents and purposes it was as if my server no longer existed.

At first I thought it might be my ddns, but the service was running fine. Then I thought maybe my server had gone offline, but when I logged into my router it showed it was connected. Finally I mused that I was being blocked by the Great Firewall of China (I hear they're not to keen on ssh) but I traced a packet and it was making it to Canada just fine.

Finally I looked at my router info and noticed that it said that the connection had only been up for a few hours, which leads me to suspect there was a power outage back home. What I think is happening is that Ubuntu is stuck on that step where, after a cold boot, it asks you to select which mode you want to boot in.

Is there anyway for me to remote in and tell ubuntu to start up normally? Or will I have to get someone to go over to my place, manually plug in a keyboard, and press spacebar? If so, is there any setting I can tweak or service I can install to stop this from happening in the future?

---

### Post by lisati on 2011-09-04
Annoying, isn't it? A few weeks back, my server machine went down because of glitches in the power supply due to bad weather. Anyway, to get to the point: My server machine has a setting in BIOS that lets the machine turn on automatically after a power outage (which I'd forgotten to set after resetting BIOS a few months back).

If you're using a "standard" installation of Grub and haven't changed its setting, it shouldn't get stuck at the stage where it asks which OS you want to load; there's usually a count down until it automatically chooses for you. If it *is* getting stuck at grub and it didn't before, there could be other issues to address.

---

### Post by TripleD on 2011-09-04
Hmmm, I don't think I ever messed around with grub. It's was a pretty vanilla installation of ububtu server (the only non-default option I recall going with was the swap memory). 

I remember once before when, in a fit of impatience, I hard booted the machine only to have it stop responding. When I hooked a monitor and keyboard back up (I had been doing pure ssh at the time) I saw that it was stuck at the grub screen.

Problem is, I can't remember if that was this installation or a previous (and much more ill-formed) one. What I'm going to do is e-mail my dad and ask him to hard boot the machine and see if that helps. With the time difference I may have the results in twelve hours or so.

---

### Post by TripleD on 2011-09-04
Well we tried a reboot and things have gone from bad to worse. Now I am unable to even log into my  router back home (which makes little if any sense). Even a basic ping on the IP address is turning up nada. There are three possibilities I'm nursing right now:

1) There was another power outage. My Canadian home is in a rural area, so multiple power outs (both planned and unplanned) within a single month are not unheard of.

2) Internet at this university is slow at the best of times, so it could be that my connections are legitimately timing out. But I have trouble believing that a simple ping packet could be such a bandwidth hog.

3) Someone/Something within China detected that I was using ssh and blocked my dynamic dns ip. I tried to avoid something like this by using a non-standard port number, but it may have been in vain. 

I'll play around and see what I can do to fix this.

---

### Post by CharlesA on 2011-09-04
Try a different network - internet cafe or whatever.

If it's not responding still, then it's likely it's either powered off or network connectivity is down. Guessing it's likely that power went out if you can't even get to your router.

---

### Post by BkkBonanza on 2011-09-05
Another possibility is that your IP changed (perhaps due to power outage) and your router did not correctly update your DNS.

You also need to make sure the BIOS on your computer is set so that on power cuts it will resume with power on. The default is to just stay off when power is cut and resumed.

Lastly, if there was a problem with a previous boot then the grub menu will wait for a response before continuing. This is an option that can be turned off - but I don't recall what you do to set that option now. 

So for example if power got cut and and disk was corrupted then it would try to do an fsck upon power up. But if that fsck had some problem and another reboot/power outage occurred then grub would wait for you at the prompt. I believe that behavior can be disabled and it can be told to continue if at all possible.

Anyway at this stage you probably need someone local who has some linux ability to go and look into it. I know if I tried to talk my Dad thru it there would be much gritting of teeth.

Also to rule out China Wall interference you could ask me or someone else to ping/traceroute/connect from outside China.

---

### Post by TripleD on 2011-09-05
> **BkkBonanza said:**
> 
Anyway at this stage you probably need someone local who has some linux ability to go and look into it. I know if I tried to talk my Dad thru it there would be much gritting of teeth.


I'm actually pretty lucky in that my dad's an IT guy. He doesn't do much in the way of linux or hacking, but at he's got a good repertoire of computer terms and is quick at figuring things out.

---

