---
title: "64 Studio / Ubuntu Studio"
date: 2009-06-05
forum: Ubuntu Studio
---

### Post by SyL on 2009-06-05
I'm just starting to get interest on what it the best way to build up a home studio for record some music.

Honestly, i did not expect to find so much on the Linux world, but there is actually a lot of different options! It's great!
So, just would like to get some input on two serious distribution: [64 Studio]("http://www.64studio.com/") and of course Ubuntu Studio. 

Did someone tried both?
Any input?

I'm also interesting on any advice for choose a correct sound card. I have read [this]("http://www.linux.com/archive/feature/39751"), but it's quite old now. 

Cheers!

---

### Post by jrlii on 2009-06-05
Well. . . that depends on what you want to do.

The requirements for producing podcasts are very different than if you want to produce CDs which are also a bit different than doing movie/TV soundtracks.

I'll assume you are working on CDs for demos, if not release, and from acoustic sources, since that is what I'm used to dealing with.

Installing Ubuntu Studio will pretty well cover you for software: Ardour with Jack will give most of the commercial audio programs a run for their money. 

As for hardware, get a fast hard disk. 7200RPM is good, 10,000 or 15,000RPM is better. The faster the hard disk the more channels you can handle simultaneously. If you can dedicate a disk (or even a RAID) to audio, so much the better. Processor-wise, you don't need that much unless you need real-time effects. I was able to record 8 tracks simultaneously with a 350 MHz Pentium II back in 1999. Now, applying compression, equalization or mixing down those tracks just didn't happen in real time with that old computer, but nowadays even a netbook will have several times its speed and RAM. 

When it comes to audio hardware, google to see if the device is supported in Linux. I prefer audio interfaces which keep the analog signals outside the noise-filled environment of the PC.

As I understand it, there is a standard for USB2.0 sound interfaces, so that should help, but none the less there is prone to be stuff which still needs to be futzed with. If it is the latest & greatest, and the manufacturer does not specifically support Linux (I'm not sure anyone does) you may have to be the one figuring out what tweeks are required. 

In the analog world, there are two places not to skimp: Microphones and preamps. If you are running mediocre mics into a cheap preamp, it doesn't matter if your audio interface is the best, you just aren't likely to sound that good. (Yes, yes more platinum records have had $100 SM57s used on 'em than anything else, but they weren't the only mics. . .)

I only have hands-on experience with two audio interfaces: The old 20 bit Echo Layla and the M-Audio Fast Track Pro. The former required compiling the ALSA driver to get it to load the firmware so it would work, and I'm still putzing with getting the latter to work right. (Despite it being allegedly USB audio compliant.)It is capturing the audio, but not playing it. . . Better than the other way around, I guess.

---

### Post by SyL on 2009-06-08
Thanks for your complete answer.
You assumption was totally correct. I would like to record acoustic instruments to get working on demos, mainly for fun ;-)

I think i understood your recommendation regarding the disk access criticality. So i guess that RAID 0 will be great, right? 

I'm still puzzled concerning which audio hardware, i'm going to spend money on... but you are right i should also keep in mind to invest in good mics -i only got crappy stuff now- and buy a good mic preamp - i don't even got one. 
Well, though it's quite off-topic here, for the mic's preamp, would have any affordable recommendation?  

Cheers mate.

---

### Post by StudioDave on 2009-06-08
> **SyL said:**
> I'm still puzzled concerning which audio hardware, i'm going to spend money on... 

You might find some relevant information here:

[http://www.linuxjournal.com/content/little-boxes-audio-production-hardware-studio-dave](http://www.linuxjournal.com/content/little-boxes-audio-production-hardware-studio-dave)

You might also find some helpful information in the other articles listed here:

[http://www.linuxjournal.com/user/800764/track](http://www.linuxjournal.com/user/800764/track)

Btw, I use 64 Studio 2.1 routinely and am testing the beta release of 3.0. I'm also testing Ubuntu Studio 9.04, which happens to be the subject of my latest article.

HTH,

dp

---

### Post by SyL on 2009-06-12
> **StudioDave said:**
> 
 
Btw, I use 64 Studio 2.1 routinely and am testing the beta release of 3.0. I'm also testing Ubuntu Studio 9.04, which happens to be the subject of my latest article.
 

 
 
Thanks for the links, will check it out asap.
As you have used both distrib, which would you recommend for basic acoustic recording? 
Few words on the pros and cons, would be much appreciate!
Maybe a link to your article would answer my questions ;-)
 
Cheers

---

### Post by Stochastic on 2009-06-12
Well I'm a fan of Ubuntu Studio but I keep an install of 64studio on a different partition.

Ubuntu Studio: 
[INDENT]-cutting edge software gives newest features
-large distro behind it allows users to install almost any other software
-very user friendly (compared to some other distros)
-the RT kernel (best for audio work) is sometimes buggy[/INDENT]

64Studio (I haven't tried 3.0 yet):
[INDENT]-based on debian up until this latest release (3.0 - it's still beta) when it switched to Ubuntu
-not as up-to-date programs (the Ubuntu version that 3.0 is based on is 8.04)
-large distro behind it allows users to install almost any other software (though with the 64studio mods to some packages, it can be trickier)
-the debian system is a little bit less user friendly, but the Ubuntu-based release should be nicer
-VERY stable[/INDENT]

In general, I prefer to work in Ubuntu Studio when I can, but if the current release is acting poorly on my box for any reason I head to 64studio during any mission-critical recording sessions, then pop back into Ubuntu Studio to do the editing/mixing/mastering.

---

### Post by SyL on 2009-06-15
Thanks Stochastic!
Sounds like the RT kernel is going to be a strong advantage for UbuntuStudio, once it will be stable. 
I will do my best to try both. My only issue is the time ...
Very nice blog BTW!

---

### Post by SyL on 2009-06-16
> **StudioDave said:**
> You might find some relevant information here:

[http://www.linuxjournal.com/content/little-boxes-audio-production-hardware-studio-dave](http://www.linuxjournal.com/content/little-boxes-audio-production-hardware-studio-dave)

You might also find some helpful information in the other articles listed here:

[http://www.linuxjournal.com/user/800764/track](http://www.linuxjournal.com/user/800764/track)

Btw, I use 64 Studio 2.1 routinely and am testing the beta release of 3.0. I'm also testing Ubuntu Studio 9.04, which happens to be the subject of my latest article.

HTH,

dp


Hi Dave,

I have read your article regarding your amazing studio!
Well that's impressive :-)
And also the one related to UbuntuStudio ([http://www.linuxjournal.com/content/judgement-day-studio-dave-tests-ubuntu-studio-904](http://www.linuxjournal.com/content/judgement-day-studio-dave-tests-ubuntu-studio-904)).   

Though, you are not using it, would you know if the [M-AUDIO PROFIRE with a FIREWIRE]("http://en.woodbrass.com/M-AUDIO+PROFIRE+610+INTERFACE+AUDIO+FIREWIRE+6X10+HAUTE+DEFINITION+AVEC+PREAMLIS+OCTANE") interface is working with Linux?
It suits my budget, and looks adapted to my needs... 

Cheers

---

### Post by SyL on 2009-07-02
> **SyL said:**
> 
Though, you are not using it, would you know if the [M-AUDIO PROFIRE with a FIREWIRE]("http://en.woodbrass.com/M-AUDIO+PROFIRE+610+INTERFACE+AUDIO+FIREWIRE+6X10+HAUTE+DEFINITION+AVEC+PREAMLIS+OCTANE") interface is working with Linux?



The [M-AUDIO PROFIRE]("http://en.woodbrass.com/M-AUDIO+PROFIRE+610+INTERFACE+AUDIO+FIREWIRE+6X10+HAUTE+DEFINITION+AVEC+PREAMLIS+OCTANE") 610 is NOT supported. I found out this very interesting website about firewire audio hardware stuff: [http://www.ffado.org]("http://www.ffado.org/?q=devicesupport%2Flist&filter0=&filter1=&op2=OR&filter2")
[http://www.ffado.org/?q=node/735](http://www.ffado.org/?q=node/735)

The Roland Edirol FA101 looks very nice, and top quality: &#26085;&#26412;&#12398;&#12391;&#12377;&#12424;&#65281;
[http://www.rolandus.com/products/productdetails.php?ProductId=702&ParentId=114](http://www.rolandus.com/products/productdetails.php?ProductId=702&ParentId=114)

---

### Post by luisaf on 2010-05-03
The [M-AUDIO PROFIRE]("http://en.woodbrass.com/M-AUDIO+PROFIRE+610+INTERFACE+AUDIO+FIREWIRE+6X10+HAUTE+DEFINITION+AVEC+PREAMLIS+OCTANE") 610 is Reported to work:
[http://www.ffado.org/?q=node/735](http://www.ffado.org/?q=node/735)

My profire 610 works very well with latest ffado-trunk, jackd (updated), Ardour/Audacity in Ubuntu Studio [B][B]8.04 LTS 

[/B][/B]Ffado installation (use the SVN *trunk*):
[http://subversion.ffado.org/wiki/InstallingFfadoFromSource](http://subversion.ffado.org/wiki/InstallingFfadoFromSource)

   For compile:
   $ scons ENABLE_MAUDIO=True PREFIX=/usr

---

