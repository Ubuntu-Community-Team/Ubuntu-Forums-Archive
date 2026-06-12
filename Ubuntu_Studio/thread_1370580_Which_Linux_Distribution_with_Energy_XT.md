---
title: "Which Linux Distribution with Energy XT?"
date: 2010-01-02
forum: Ubuntu Studio
---

### Post by groovebrother on 2010-01-02
Hello!

Which Linux distribution do you recommend when working with Energy XT 2.5? 

Thanks!

---

### Post by sgx on 2010-01-02
> **groovebrother said:**
> Hello!

Which Linux distribution do you recommend when working with Energy XT 2.5? 

Thanks!
I assume you will use the windows version with wine, wineasio,
jackd, and qjackctl, to use vst instruments and effects in a secure
linux setting. You must be prepared to create your own luck, by testing several linux setups, and buying specific hardware, if yours is unsupported. some + and - on a few distros:

ubuntu studio: 8.04 usually works, RT kernel usually works
64studio: best up-to-date audio-centric distro, active mailing list,
lousy xorg implementation.
Fedora 11 CCRMA: possibly the best RT kernel support, security in disarray
is problem for newbies. Good for experienced penguins.
Suse 10.2 JAD abandoned, but works on some hardware, and good for experienced upgraders 
pclinuxos: best installer/dual-boot/partioning, extremely stable, but
realtime kernel is not in the latest repositories, stock kernel is good for around one plugin per 300 mhz of cpu  with 2 gig system ram. Minime
version (300 meg) is great basis to add the audio apps.
Mepis antiX/ubuntu Mint: nicely polished debians, good foundations to  build on.
Puppy: small, fast, really small, really fast, great foundation, worth
learning the few non-standard approaches. lashstudio.sfs is a good
incentive for serious recording musicians.
pure-dyne: (dyne:bolic) (dhoruba) great live distro, RT out of the box,
lots of audio apps ready to rumble. Drag the 'nest' to C:\ to finish
booting from hard-disk, to free up the cd/dvd 

 When I get a new motherboard, this will be the order of testing for me.
Cheers

---

### Post by groovebrother on 2010-01-04
Thanks for this comprehensive answer!!!

---

### Post by danflash on 2010-01-04
Depends on the system...

Energy XT screams on any system really, but my best experiences for a bog-standard desktop pc was 64Studio or Sabayon w/ RT Kernel (good dual-monitor support, which is a must for my studio needs).

If it's a laptop or netbook you're after, Ubuntu Studio can sometimes be OK if you've got a good sound card and only simple needs.  But for serious work, i'd shell out for the Indamixx (Transmission) OS - I use it on my AAO netbook as a portable studio (w/ small usb 2in/2out sound card, nanokey + nanokontrol) and it really is the dog's ******** (the OS comes with Energy XT installed, along with other must-haves like Ardour, Zynaddsubfx and Hydrogen).  I could brag about it all day (but won't).

If you don't fancy paying for an OS though, and you're system is strong enough, try out 64Studio.

---

### Post by bebox on 2010-01-09
did anybody get his energyxt to work on ubuntu 64bit with qjackctl...please help me.

---

### Post by bebox on 2010-01-09
i had to run qjackctl as super user...and also run energyxy as super user...and than it works...but not for long...and than i get this message in terminal ..zombified - calling shutdown handler

---

### Post by bebox on 2010-01-09
i think it has to do something with the latency.

---

### Post by thomasjw on 2010-01-21
i'm starting to get sufficiently fed up with ubuntu to start shopping around (after a promising start, audio in wine has broken and no amount of tinkering or reinstalling seems to make it any better, and that is a deal-breaker).  i just tried pure-dyne (which is really just ubuntu wearing different clothes so i figured it would be a comfortable switch), but was unable to get myself connected to my wireless router... and no internet is also a deal-breaker.  i have a 64studio livecd around here somewhere which i'll try, and also i'm d/ling the 'zenmini' version of pclinuxos (i don't mind having to scrounge up all my own audio apps if it means they'll actually work).  I'll report on how it goes, though of course YMMV.  

the pervasiveness of pulseaudio in ubuntu is like opening every drawer in your house and finding tampons in all of them.  i just keep thinking 'yeah, this is a fine idea for people who need such a thing, but i am not one of those people, so i'd rather not have all these tampons...'

---

### Post by AutoStatic on 2010-01-22
Start sending mails to [XT Software]("http://www.energy-xt.com/index.php?id=0500") to ask for an optimised download for Ubuntu! The more noise Linux Energy XT users make, the more the devs will bear their wishes in mind.

---

### Post by mrufino1 on 2010-01-23
I started using avlinux a few weeks ago and it is awesome. Ubuntu Studio was good for me but AV is great. I don't use energy xt, but wine, wineasio, etc is all preinstalled.

---

### Post by danflash on 2010-01-25
the pervasiveness of pulseaudio in ubuntu is like opening every drawer in your house and finding tampons in all of them.  i just keep thinking 'yeah, this is a fine idea for people who need such a thing, but i am not one of those people, so i'd rather not have all these tampons...'[/QUOTE]

Quite simply the most amazing analogy ever.  And I couldn't agree more.
Maybe try Fedora/CCRMA?  Or, dare I say, remortgage your house + sell your soul to the devil himself (Steve ******* Jobs) and shell out for a mac.
I never had any luck with Ubuntu as a audio system.

---

