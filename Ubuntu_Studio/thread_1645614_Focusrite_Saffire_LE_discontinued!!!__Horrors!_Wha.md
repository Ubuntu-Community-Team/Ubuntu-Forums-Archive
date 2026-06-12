---
title: "Focusrite Saffire LE discontinued!!!  Horrors! What to do now?"
date: 2010-12-14
forum: Ubuntu Studio
---

### Post by jukingeo on 2010-12-14
Hello all...

I know I been talking about this audio interface for a while now in these forums and I figured I was going to get one when I finally update my system with Lucid.

Much to my amazement, Focusrite has discontinued the Saffire LE and it is no longer available in stores :(.

I have looked at some of the new interfaces that Focusrite puts out and while they look cool, the problem is that they are 'new'.   Just about anything 'new' seems to have a habit of not working in Ubuntu (Studio).

I was wondering if anyone knows if any of these 'new' Focusrite products work in Ubuntu, or if they don't could they recommend a similar firewire interface that DOES work.

Thanx,

Geo

---

### Post by prokoudine on 2010-12-14
> **jukingeo said:**
> 
I have looked at some of the new interfaces that Focusrite puts out and while they look cool, the problem is that they are 'new'.   Just about anything 'new' seems to have a habit of not working in Ubuntu (Studio).

I was wondering if anyone knows if any of these 'new' Focusrite products work in Ubuntu, or if they don't could they recommend a similar firewire interface that DOES work.

I got my Saffire Pro 24 working on 10.04. However I still have to somehow update firmware. Not sure if it's related, but I had to patch one file to get FFADO to live with current old firmware, and after some 5 or 6 hours of work FFADO's D-Bus server starts sending weird messages to stdout and then turns off. The mixer looks somewhat ugly too (24 is a dice based device). But hey — it works.

---

### Post by Fer Servadu on 2010-12-14
> I was wondering if anyone knows if any of these 'new' Focusrite products work in Ubuntu

I'll add my voice to this question. Specifically, I'm curious if anyone has gotten a Saffire Pro 14 (which seems to be the successor to the Saffire LE) working in Linux. There's no mention of the device at ffado.org, although support for the older and rather high-end Pro 24 and 40 looks good.

> the Saffire LE... is no longer available in stores

Well, there are a few around, but most of what I've found is being offered at $200-250, which is awfully close to what a Saffire Pro 14 is going for right now.

Anyone?

---

### Post by AutoStatic on 2010-12-15
The Saffire Pro 24 and 40 work (I use them both). The 14 should work by now or will do so shortly.
Working FFADO packages for 10.04: [https://launchpad.net/~autostatic/+archive/ffado](https://launchpad.net/~autostatic/+archive/ffado) (no support for Saffire Pro 14 yet)

Prokoudine, did you get the mixer to work?

Best,

Jeremy

---

### Post by prokoudine on 2010-12-15
> **AutoStatic said:**
> Prokoudine, did you get the mixer to work?

To tell the truth I barely understand the point of this puzzling matrix in the first tab, so I don't even bother with it. Default values seem to be ok, front panel knobs for controlling input volume work, capture and playback work — beyond that I don't care much. Of course as soon as the mixer starts looking like something designed for humans I'll be diving deeper (it's entirely possible, of course, that everybody but me is happy with that matrix) and maybe even discovering some bugs I distinctly remember reading about in ffado-user@:)

---

### Post by jukingeo on 2010-12-22
> **Fer Servadu said:**
> I'll add my voice to this question. Specifically, I'm curious if anyone has gotten a Saffire Pro 14 (which seems to be the successor to the Saffire LE) working in Linux. There's no mention of the device at ffado.org, although support for the older and rather high-end Pro 24 and 40 looks good.


Well, there are a few around, but most of what I've found is being offered at $200-250, which is awfully close to what a Saffire Pro 14 is going for right now.

Anyone?


That does seem to be the trend with Ubuntu (or Linux in general), that newer stuff is harder to get to work.  I held off on getting the Saffire LE because I knew that the longer I would wait, the better the support.  Also because I am still running Hardy, Jack isn't set up with FFADO.  If you want FFADO, you have to endure a long tedious installation process.

When Lucid came along, it offered full FFADO support in Jack, but the OS was buggy when it was first released.   Now it seems like a great time to upgrade to Lucid and low and behold, I can no longer get the Saffire LE.

I did see the Pro14, but like yourself I have my doubts if it will work in Ubuntu studio.

I know that there are other options available to me such as the Lexicon Omega and the Edirol (now Cakewalk) UA-25a.   But I have already found a couple shortcomings with each divice.  The Omega can only do 48k sample rate (YUK!) and while that is fine for regular (games, system sounds) audio work, it isn't good enough for "studio" work.   The Edirol/Cakewalk UA-25a  can go to 96k, which his acceptable for me, but the interface only allows recording for TWO inputs.    As it is my current M-Audio Delta 44 which has FOUR ins and FOUR outs.

Another unit that is known to work in Ubuntu is Presonus Firepod...a firewire device, but at $500...that is a bit out of my pocketbook.

The Saffire LE would have come in on a nice level with everything.   Maybe I might find one used.,  we will see.

Thanx,

Geo

---

### Post by trulan on 2010-12-23
> **jukingeo said:**
> Another unit that is known to work in Ubuntu is Presonus Firepod...a firewire device, but at $500...that is a bit out of my pocketbook.
Unfortunately, these have also been discontinued.  They indeed do work excellently - I have two of them.  They're a bit low on hardware features maybe, with only a preamp knob for each channel.  But they do 8 inputs at 96kHz (Bonus points:  It is possible to daisy-chain two of them at 96kHz in linux - in Windows or Mac they limit you to 48kHz if you use more than one)  I picked up my second one off ebay for around $300.

---

### Post by AutoStatic on 2010-12-23
> **jukingeo said:**
> If you want FFADO, you have to endure a long tedious installation process.Hello Geo,

With Lucid 10.04 you only have to install the **jackd** and **ubuntustudio-controls** packages that will also install the FFADO packages. Then follow the steps [here]("https://help.ubuntu.com/community/FireWire") and you should have a working FireWire device.

> **jukingeo said:**
> I did see the Pro14, but like yourself I have my doubts if it will work in Ubuntu studio.Yes it will. FFADO from svn trunk now also supports the Saffire Pro 14: [http://subversion.ffado.org/changeset/1942](http://subversion.ffado.org/changeset/1942)
I can cook up a package, I already have [updated FFADO packages]("https://launchpad.net/~autostatic/+archive/ffado") available, and help out setting it up eventually.

Best,

Jeremy

---

### Post by jukingeo on 2010-12-29
> **AutoStatic said:**
> Hello Geo,

With Lucid 10.04 you only have to install the **jackd** and **ubuntustudio-controls** packages that will also install the FFADO packages. Then follow the steps [here]("https://help.ubuntu.com/community/FireWire") and you should have a working FireWire device.

Yes it will. FFADO from svn trunk now also supports the Saffire Pro 14: [http://subversion.ffado.org/changeset/1942](http://subversion.ffado.org/changeset/1942)
I can cook up a package, I already have [updated FFADO packages]("https://launchpad.net/~autostatic/+archive/ffado") available, and help out setting it up eventually.

Best,

Jeremy

So it STILL has to be installed?  I am surprised, I thought FFADO would run out of the box with Lucid. 

> **trulan said:**
> Unfortunately, these have also been discontinued.  They indeed do work excellently - I have two of them.  They're a bit low on hardware features maybe, with only a preamp knob for each channel.  But they do 8 inputs at 96kHz (Bonus points:  It is possible to daisy-chain two of them at 96kHz in linux - in Windows or Mac they limit you to 48kHz if you use more than one)  I picked up my second one off ebay for around $300.

It was cost that initially strayed me away from the Firepod, but I do know that it is a good unit.   It was shortly after I discovered the Saffire LE and thought that would be a good buy for when I upgrade to Lucid.   Now I am ready to put a new computer together, go with Lucid AND the Saffire LE is discontinued. 

As for Ebay, I no longer use the site.   Their practices have become unfair for the small time seller and they require the use of Paypal for payments....Paypal, a company Ebay owns, need I say more?  Ebay WAS fun years ago, but not anymore.

Besides I would rather buy new.   Many times when I buy 'old' audio pieces, I always get stuck with scratchy controls and/or loose jacks.

Oh, well, I guess either I go with the limited input Cakewalk UA-25 or the limited sample rate Lexicon Omega.   The trouble with the Omega though, is that I seriously cannot archive my vinyl collection at a 48k sample rate.

I DO have a beautiful Alesis IO-26 Firewire interface that goes to a whopping 192k, BUT it isn't supported in Linux AND it probably never will be.

More then likely I am probably just going to have to archive using Windows and the Alesis unit and use something like the Omega for everyday use.

Or maybe I get lucky with something on Craigslist....We will see.

Thanks for the input folks!

Geo

---

