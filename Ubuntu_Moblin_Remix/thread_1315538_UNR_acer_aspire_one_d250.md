---
title: "UNR acer aspire one d250"
date: 2009-11-05
forum: Ubuntu Moblin Remix
---

### Post by Stevie B on 2009-11-05
Hi

I switched to linux 2 months ago, im running UNR on my acer aspire one D250
I updated it to 9.10 via the update option.
[LEFT]Now I want to download drivers for my netbook, especially for the grapics card
because I feel it's needed. But I don't know howto .. im totally new to this operating system, so please help this newbie out ):P

Thanks for your time.

- Stevie B
 [/LEFT]

---

### Post by Stevie B on 2009-11-05
Bump

---

### Post by SushiR on 2009-11-05
Why do you feel to download graphics driver? Blank display? Flickering?

---

### Post by StewartG on 2009-11-05
> **Stevie B said:**
> Hi

I switched to linux 2 months ago, im running UNR on my acer aspire one D250
I updated it to 9.10 via the update option.
[LEFT]Now I want to download drivers for my netbook, especially for the grapics card
because I feel it's needed. But I don't know howto .. im totally new to this operating system, so please help this newbie out ):P

Thanks for your time.

- Stevie B
 [/LEFT]
You won't need new drivers - ubuntu will provide you with driver updates. they are just part of the OS - unless you have some ati or nvidea card don't worry about it.

---

### Post by Stevie B on 2009-11-05
> **SushiR said:**
> Why do you feel to download graphics driver? Blank display? Flickering?
It's so buggy when scrolling on websites, don't know how to say
When I scroll down or up on a webpage it doesn't flow normally, it's in parts
I hope u understand what I mean...

---

### Post by Jayferd on 2009-11-05
Stevie,

With ubuntu, things are a little different.  When you're running Windows, you do need to go download lots of drivers from your hardware manufacturer; or more often, they come pre-loaded with Windows.  With ubuntu, the install process detects your hardware and installs either a community-developed driver or a driver from the manufacturer.  Either way, the concept of "downloading a driver" doesn't usually apply unless you have some really specialized hardware from a particularly linux-friendly vendor.

As for the scrolling lag, I would guess Firefox is a bit much for the Aspire One's teensy processor and RAM.  I would recommend Google Chrome or Chromium (Chrome is more stable at this point, even though they say it's still a "Developer Preview"); they have much better memory handling than the current version of Firefox.  Also, you may try disabling visual effects (compiz) from your System->Appearances window.

If the desktop is still being laggy, you can set it to low graphics mode by pressing Alt+F2 and typing "gconf-editor".  Locate the folder apps > netbook-launcher, highlight it, and in the window on the right, check the box titled "force_low_graphics".  It won't be as flashy, but it won't make things lag either.

Finally, we may be able to help you locate a better driver for your video card if you let us know what kind of card you have.  Open a terminal, type "cd ~", then 
```

sudo lshw > lshw.txt

```
Find the file lshw.txt (it will be in your home folder), and upload it here; that'll give us more info about your hardware.

...or if you know the make and model of your graphics card, just tell us, we'd be happy to point you in the right direction.

Peace,
--Jay

---

### Post by Stevie B on 2009-11-05
First of all thank you for your detailed answer Jay!

Here's the info:

---

### Post by Stevie B on 2009-11-06
Google Chrome is only for windows at this moment ...

---

### Post by Jayferd on 2009-11-06
Nonsense.  I'm on Chrome right now.  I find it indispensable for the small netbook screens.  Check out the so-called "unstable" version: [http://dev.chromium.org/getting-involved/dev-channel#TOC-Linux](http://dev.chromium.org/getting-involved/dev-channel#TOC-Linux)

EDIT: Alternatively, you can install Chromium, the open source browser that looks exactly the same; but that one's really unstable right now.  I can't get it to open Google reader.

---

### Post by Stevie B on 2009-11-06
> **Jayferd said:**
> Nonsense.  I'm on Chrome right now.  I find it indispensable for the small netbook screens.  Check out the so-called "unstable" version: [http://dev.chromium.org/getting-involved/dev-channel#TOC-Linux](http://dev.chromium.org/getting-involved/dev-channel#TOC-Linux)

EDIT: Alternatively, you can install Chromium, the open source browser that looks exactly the same; but that one's really unstable right now.  I can't get it to open Google reader.

Okay thanks, ill check it out.
What about my lshw.txt?

-Stevie B

---

### Post by Jayferd on 2009-11-06
Well, I'm not a hardware guru, I was sort of just letting you know what sort of info to give on the boards if you want to talk about hardware.  To me, who again knows very little about hardware and drivers and such, it looks like you just have the sort of standard onboard video from Acer.  I don't know of any special drivers for it.

...but someone more knowledgeable than me might come along and say something different.

Peace,
--Jay

---

### Post by Stevie B on 2009-11-07
> **Jayferd said:**
> Well, I'm not a hardware guru, I was sort of just letting you know what sort of info to give on the boards if you want to talk about hardware.  To me, who again knows very little about hardware and drivers and such, it looks like you just have the sort of standard onboard video from Acer.  I don't know of any special drivers for it.

...but someone more knowledgeable than me might come along and say something different.

Peace,
--Jay

Okay thanks for helping me out and pointing me in the right direction!

-Stevie B

---

### Post by vexorian on 2009-11-11
> As for the scrolling lag, I would guess Firefox is a bit much for the Aspire One's teensy processor and RAM This is nonsense. Firefox 3.5 works just fine even in my eee 701 (with its 800x480 resolution, 600 Mhz processor and 1GB RAM, and the D250 is a powerhorse in comparison to it :) .

Edit: hmnn, I have not experienced scrolling LAG in firefox and I have the D250 as well.

Could it actually be related to the touchpad rather than firefox  performance? The D250 touchpad feels a little "odd" to me in comparison to my old eee.

---

### Post by goldblumer on 2009-11-22
Hello all,

I am using UNR 9.10 on this platform and have an issue that I could not find resolved elsewhere.

Straight out of the restart after the install, the wireless is active and I can connect to my home network; the LED even works just fine.  My issue is that if I deactivate my wireless using the switch on the front of the netbook, I can not reactivate the wireless.  The LED remains off and the network manager reports my wireless as deactivated.  No amount of holding the wireless switch to the "ON" position does any better.

If there is any more information needed, please let me know.  Any help pointing in the direction of a fix would be most appreciated!

EDIT:  After a more careful look at this page; I may not have posted this in the best place (see "Moblin").  I was brought here from a search and the thread was for my particular platform.  I apologize and will hold off of cross-posting elsewhere unless instructed.  Thank you still!

---

### Post by iamgeniusrnti on 2009-11-25
Just felt like piping in--I installed UNR 9.10 on this same netbook and it worked perfectly execpt for the LED, switch and mic.  I also installed Puppy and Kubuntu Netbook without issues.  I also know BT3 will run on a thumdrive o this netbook as well.
 
There are a lot of treads out there regarding how to fix the mic on the D250... I'd leave it alone... people say their mic works after following a "few simple steps"... I followed those "few simple steps" and then I spent the next three days at war with Ubuntu trying to get my sound working again at all.  
 
Just speak into the mic and pretend it works; you'll be fine!

---

### Post by vexorian on 2009-11-26
mic worked for me in karmic UNR without tweaks. 

At first I thought it didn't but somehow I then noticed that mic volume in sound recorder was low. nothing else.

---

