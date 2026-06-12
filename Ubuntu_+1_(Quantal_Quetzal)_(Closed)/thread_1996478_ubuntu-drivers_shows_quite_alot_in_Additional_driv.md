---
title: "ubuntu-drivers shows quite alot in Additional drivers"
date: 2012-06-04
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by mc4man on 2012-06-04
Hadn't had occasion to use add. drivers till new install so guess I missed the new view. Was a little surprised to see all the drivers shown & settable, 23 here.
This certainly could be useful though seems a bit against Ubuntu's way of not exposing such options to the general user

---

### Post by dino99 on 2012-06-04
get a similar list here too, its a bit too much. The first tweak i've done is only installing the needed packages inside synaptic, but we should not get the list from the kernel.

---

### Post by zika on 2012-06-04
Where does Jockey keep changes made through it?
I know how to blacklist certain drivers...
What is interesting for me is following:
If  I go and disable some drivers and Jockey get changed back not to show these drivers how am I to reactivate drivers that I did disable with Jockey...
Boy, I did put this question as complicated as I could but I do hope that it can be understood somehow... ;)

---

### Post by mc4man on 2012-06-04
There was something about jockey being set to be removed? this dev, if so maybe this is an in-between stage.

The other interesting question would be  - if you disable or disable/remove some fairly important driver in the current jockey window, does it actually disable it. 
I'm tempted to think that most of the ones I see won't be, though there would be an easy way to find out..

Edit: ubuntu-drivers-common contains a number of bin files, haven't looked what they do - Ex.
ubuntu-drivers -h

---

### Post by zika on 2012-06-04
> **mc4man said:**
> The other interesting question would be  - if you disable or disable/remove some fairly important driver in the current jockey window, does it actually disable it. I tried and it actually does. I would not call them important (sp5100, k10,...)
What made me ask what I've asked is the fact that it does not list them in blacklist.conf of any kind I've been able to find, even though it honors them (at least /etc/modprobe.d/blacklist.conf that I've tried) in the sense that blacklisted drivers can not be enabled through Jockey... (to be honest I did not spend too much time on that)...

---

### Post by mc4man on 2012-06-04
Not being exactly up on some of What's shown in the screen, would any of these be an issue if disabled/removed or enabled?

---

### Post by zika on 2012-06-04
> **mc4man said:**
> Not being exactly up on some of What's shown in the screen, would any of these be an issue if disabled/removed or enabled?Is this a question for me?
(Are You talking to me? [img]http://www.sherv.net/cm/emo/funny/1/bush-shoe-emoticon.gif[/img])
If You enable, for example, PCSpeaker, where that fact would be written?
If Jockey seize to provide that opportunity, would it be enough to restore „blacklist pcspkr“ (or whatever is the name) in /etc(modprobe.d/blacklist.conf?
Or the other way around, if You disable some driver, will You be able to enable it after Jockey seize to provide that opportunity...? Where will Jockey write that fact...?
Some of these drivers could invoke trouble if disabled and You're not able to enable them back, HID, and some other, not to mention video and similar which I expect to remain in Jockey, because without them it looses any sense of existence...

---

### Post by ventrical on 2012-06-04
I just got this with the daily-build. Fascinating.

---

### Post by VinDSL on 2012-06-04
> **ventrical said:**
> I just got this with the daily-build.
Dittos!  UbuQQ A1 daily .iso

I'm gonna go try to clean things up...

---

