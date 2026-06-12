---
title: "Laptop questions"
date: 2006-10-09
forum: System76 Support
---

### Post by Nangineer on 2006-10-09
I'm interested in either a Gazelle or a Pangolin, but I have a few questions. I welcome anyone to comment.

I noticed S-video isn't mentioned in the description of the Gazelle Value, but the images show what looks like an S-video port. So does that one have it?

Also, what sound chipset is in the Gazelles? How do they sound with PC speakers (or the Pangolin)? I've got a 2.1 ITrigue system (w/subwoofer) that I would like to use when I'm using the laptop at home.

If I get one with Intel graphics, will I need extra RAM for compiz/beryl, screensavers, multimedia? I will be using many programs at once, but I don't do any video editing or 3D gaming. I'm just not sure under what circumstances more than 512 MB would be necessary on a Linux laptop.:confused: 

Thanks in advance!

---

### Post by Frak on 2006-10-09
All I can say is, Ram-as much as you can afford, speakers-included, S-Video-mine came with one,Graphics-Need to have.

---

### Post by crichell on 2006-10-09
I'm a fan of accelerated graphics but I use a Gazelle Value and it's all that I need.  Multimedia and screensavers work perfectly on Intel's chip.  I play around with graphics without any issues either.  Video editing, gaming, and some apps require accelerated graphics (google earth only flows w/ accelerated graphics).  It's a short list though.

I always recommend customers working within a budget go for more processor and less memory - you can always add a stick memory later on but changing the processor is expensive.

---

### Post by Frak on 2006-10-10
Yeah but without ram theres nothing to backup the proccessor. The proccessor need the ram to load off and on to.

---

### Post by Nangineer on 2006-10-11
Thanks for the replies!

I'd still like to know which sound chipset is in the Gazelles though (I know Realtek is used on many System76 systems--I'm just curious as to which one it is exactly.)

And I know it comes w/speakers, but I was just wondering how external speakers would sound w/one of these. (Of course, if they're loud enough and have a subwoofer, I won't need them.)

---

### Post by Frak on 2006-10-11
Intel 802.11 abg

---

### Post by crichell on 2006-10-11
I missed that one (sound chip).  I have a Gazelle value and I regularly plug it into 2.1 speakers (as you know - two sattelites and a sub).  The sound is great.

The chipset in the Gazelle Value is Intel HDA Generic 14f1 ID 5045.  What makes this sound chip particular nice is how alsa controls it.  Instead of separate channels for front, headphone, etc you have only one master that controls everything.  One mic volume control as well for built in or plug in mic,

The Pangolin uses the Realtek ALC 882 chipset.  Also a good chip.

---

### Post by Nangineer on 2006-10-15
Do you know if the Intel chips produce native 44.1 kHz sound output, or do they resample to 48? I couldn't find any info. (I know the Realtek ALC 882 doesn't resample. Yes, I'm paranoid about sound quality.)

---

### Post by crichell on 2006-10-16
I don't know about resampling - is there an easy way to tell?

---

### Post by stmiller on 2006-10-18
I have never heard of any onboard laptop sound chip that resamples from 44.k to 48k. Or why it would do that. Some Creative sound devices are fixed at 48k (which is why audio folks avoid consumer Creative-crap!).

---

### Post by Nangineer on 2006-10-25
Just to be clear--the S-video-out port _does work_ on the Gazelle Value, right?

---

### Post by crichell on 2006-10-25
Yes it does work; however, there isn't a good GUI app (that we've been able to find) for manipulating X output through the s-video port.  It requires tinkering around in the xorg.conf file.

---

