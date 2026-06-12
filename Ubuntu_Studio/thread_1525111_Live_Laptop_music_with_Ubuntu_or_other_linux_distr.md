---
title: "Live Laptop music with Ubuntu or other linux distro"
date: 2010-07-06
forum: Ubuntu Studio
---

### Post by kokoshmusun on 2010-07-06
I have a Phonic Firefly 302 USB audio card that I was unsuccessful at getting to work with Ubuntu.  I have some experience making music in Windows and I was quite happy with the available software at the Win platform.  However, I really don't want to use Windows for anything ever again after having discovered Ubuntu.  I'm committed to the FOSS idea and really dislike the idea of being locked up in the Win environment for music.

BUT, I have ambitious-ish music projects.  I want to be able to use a Linux laptop for making live music.  After failing to make my audio card recognized in Ubuntu though, I have doubts.  I'm willing to buy a new audio card that is compatible with Linux.  But I haven't even been able to try any of the software.

While I'm not expecting to see Ableton Live-quality software, I'm hopeful that there is decent music software in Linux.  Can I expect to be able to make live music on a linux laptop and do it stably (i.e., it won't let me down in the middle of a gig)?  Or would you recommend that I go back to Windows for this purpose?

The type of music we'll be making will rely on loops, sampler/synth, and I'm also intending to get into generative or algorithmic music (cSound, supercollider, etc.).  We want to make something that is very weird and experimental but still manages to be pretty at times.  I don't have any other specific ideas at this point. 

I would really like to hear from some linux musicians.  Is there a specific forum for linux musicians?  I have tons of other questions beginning with which audio card should I buy for linux?

thanks in advance.

---

### Post by AutoStatic on 2010-07-06
> **kokoshmusun said:**
> I have a Phonic Firefly 302 USB audio card that I was unsuccessful at getting to work with Ubuntu.Hello kokoshmusun, isn't that Phonic a Firewire card? If so, it's reported to work: [http://ffado.org/?q=node/80](http://ffado.org/?q=node/80)

> **kokoshmusun said:**
> While I'm not expecting to see Ableton Live-quality software, I'm hopeful that there is decent music software in Linux.  Can I expect to be able to make live music on a linux laptop and do it stably (i.e., it won't let me down in the middle of a gig)?Yes you can.

> **kokoshmusun said:**
> The type of music we'll be making will rely on loops, sampler/synth, and I'm also intending to get into generative or algorithmic music (cSound, supercollider, etc.).  We want to make something that is very weird and experimental but still manages to be pretty at times.  I don't have any other specific ideas at this point.Then Hydrogen will probably suit you best. Or Qtractor.

> **kokoshmusun said:**
> I would really like to hear from some linux musicians.Unfortunately there aren't many active Linux Musicians yet, especially when it comes to doing stuff live.

> **kokoshmusun said:**
> Is there a specific forum for linux musicians?Yes there is: [LinuxMusicians]("http://forum.linuxmusicians.com/index.php")

> **kokoshmusun said:**
> I have tons of other questions beginning with which audio card should I buy for linux?Maybe we can get your Phonic to work with Ubuntu. What did you try already to make it work?

Best,

Jeremy

---

### Post by kokoshmusun on 2010-07-06
Hi, those are great answers, thanks a lot.  My audio interface is unfortunately a USB, **not** a firewire.  Since I'm not very familiar with Linux music jargon (ALSA, JACK, etc.) I can't explain precisely what I did to try to make it work, but I got some help from this forum to get to the point where my Ubuntu would recognize the card if it could (doing all those Jack, ALSA, whatever things), but it didn't and nobody knew how to go from there.  It seems like there's no info on whether this card works with Linux or not. 

I vaguely remember your name and face, maybe you were one of those trying to help, so I don't wanna double-waste your time.  But the other answers are very promising for me to try to stick with Linux for Live music situation.

cheers!

---

### Post by AutoStatic on 2010-07-06
Your card is an USB2 audio card: [http://www.phonic.com/en/firefly-302-usb.html](http://www.phonic.com/en/firefly-302-usb.html)

In [this thread]("http://ubuntuforums.org/showthread.php?t=1463701") you already posted some info and aplay -l doesn't return any USB soundcard so your Phonic card doesn't even get recognized :( So it's most probably unsupported.

Unless you really want to record at 192Khz a nice replacement candidate could be the Edirol UA-25EX: [http://www.roland.com/products/en/UA-25EX/](http://www.roland.com/products/en/UA-25EX/)

---

### Post by kokoshmusun on 2010-07-06
Thanks, I appreciate your help.  I will have to sell my USB interface and look into the Roland device you mentioned.  Cheers!

---

