---
title: "Ubuntu - In My Own Words"
date: 2008-06-12
forum: Testimonials &amp; Experiences
---

### Post by 91004 on 2008-06-12
I have used almost all of the version of Ubuntu at some point and time since I first read about it on Distrowatch a few years back.  Seemed like the right thing to do.  But every time I ended up going back to Windows XP because of the Media and codec support because quite frankly they just weren't there.  

Let me validate my statement above that my wife and children were the main reason for the switch back.  They insisted that they wanted it to be painless.  They liked the way XP was layed out and although they only used about 1% of the features of XP I was overruled.  

So here I sat on my computer chair in my underwear one day, very dissatisfied with XP and all of the errors that come with it.  Even doing the simplest tasks seemed daunting.  I don't know why, but it seems if the hard drive was filled up around 50% the machine became unstable and everything I did from trying to defrag, cleaning up the file system, etc didn't seem to fix it.  With a AMD 64 processor and 2 gigs of ram, along with a 128meg video card, and a 200gig hard drive running SATA,  that computer shouldn't be running like this.  Finally on this day it was the last straw.  The Operating System and I were going to have some words.  I was tired of having to ask if I could run a program without it telling me that the programs were closing because some Kernel Exception over-ruled the processor at location x0000ef0000123 or something like that.

I had been checking out the latest release of Hardy and heard a lot of good things about it from this forum and from other online sources.  My future brother-in-law who hates Microsoft as much as I do said he was really impressed with 8.04 and that I should download it and give it a try.  Well that did it.   Windows XP was coming off and 8.04 was going on.  I don't like to do things half-a$$ed so I backed up the files I needed and burnt a copy of Ubuntu and let it loose....

I am very happy I did.  Finally with Hardy I am able to do everything I need to do with two exceptions which I will get to.  The first thing I noticed is that Hardy didn't seem as slow at boot-up as in the past releases.  Having installed Ubuntu and other Linux flavors I knew what to expect and Ubuntu paid out at the finishline.

Without having to do anything, it recognized all of my devices right away.  I didn't have to hunt for the drivers disk as I have in XP.  Everything just worked right out of the box.  I was very very happy for this.

Of course who is going to run Linux without sound and video?  Having had past dealings with Ubuntu I was really surprised that right off the bat the sound system was recognized.  This was a definite plus for me.  I just installed mediabuntu and I was off and running.

Over the course of about three hours I was drooling as I downloaded from the non-free repositories and everything.... well just worked.   Even things that seemed to be a challenge in earlier releases worked right away.

Although I had played around with WINE before I always became upset trying to download everything I needed for it to work.  This time around..... It worked.

Compwiz - I believe it was the 7.10 edition I still had to install everything by hand.  8.04 it was already there.

The benefits of the positives outway the negatives, but there are some things that I still seem lacking, and its not Ubuntu's fault...

**Logitech Headset**  This is a big one for me.  I have a USB Logitech headset and if Logitech could supply support for Linux it would be a wonderful thing.  Sometimes it works, but most times it doesn't.  I use it for SKYPE, Amateur Radio "Echolink", and several other programs.  I just need this to work.  It's pretty annoying to the family when I sit here and listen to Bubba or Howard Stern and they hear it through the speakers.  Likewise I don't like to sit and listen to Thomas The Tank Engine Youtube videos blaring over the sound of the television.    The computer and tv are fairly close to each other and being competitive over the volume often ends up in shouting.... This is not needed in my household.  

**DELL AIO 962 PRINTER**  Enough said.  Everyone that has a Dell has tried drivers for their "Lexmark" printers, and just like me failed miserably.  I had hoped that running it under Virtual Box I could get it to run, but I'm still having trouble with it...... Dell should be commended for their usage of Ubuntu on their systems as a option, but they should also supply support for printers as well....

I'm pretty happy otherwise with my system.  There is only one problem that I have right now that I can't resolve and it is Remote-Desktop and VNC issues...... Hopefully I'll be able to solve that....

BTW here is a picture of my son and a friend at the local lake..... I just think this is a great photo....

[IMG]http://www.cyberlancaster.com/lancasterfire/20080513001.jpg[/IMG]

---

### Post by 3rdalbum on 2008-06-13
I have a Logitech headset as well. Unfortunately, the problem you describe is a kind of limitation with Linux. Your headset is recognised by ALSA and can be used by ALSA-aware programs as long as they support switching output devices (Flash doesn't!). ESD-aware programs will be able to use it, as long as you use System > Preferences > Sound to switch the output device. OSS-only programs will ignore your headset.

Unfortunately, that's the state of audio in Linux. We're hoping that PulseAudio will fix things, or that proprietary programs like Flash will get smarter in their use of audio.

---

### Post by hyper_ch on 2008-06-13
teh OSS problem can be avoided by using AOSS.

---

### Post by ukripper on 2008-06-13
> **91004 said:**
> I have used almost all of the version of Ubuntu at some point and time since I first read about it on Distrowatch a few years back.  Seemed like the right thing to do.  But every time I ended up going back to Windows XP because of the Media and codec support because quite frankly they just weren't there.  

Let me validate my statement above that my wife and children were the main reason for the switch back.  They insisted that they wanted it to be painless.  They liked the way XP was layed out and although they only used about 1% of the features of XP I was overruled.  

So here I sat on my computer chair in my underwear one day, very dissatisfied with XP and all of the errors that come with it.  Even doing the simplest tasks seemed daunting.  I don't know why, but it seems if the hard drive was filled up around 50% the machine became unstable and everything I did from trying to defrag, cleaning up the file system, etc didn't seem to fix it.  With a AMD 64 processor and 2 gigs of ram, along with a 128meg video card, and a 200gig hard drive running SATA,  that computer shouldn't be running like this.  Finally on this day it was the last straw.  The Operating System and I were going to have some words.  I was tired of having to ask if I could run a program without it telling me that the programs were closing because some Kernel Exception over-ruled the processor at location x0000ef0000123 or something like that.

I had been checking out the latest release of Hardy and heard a lot of good things about it from this forum and from other online sources.  My future brother-in-law who hates Microsoft as much as I do said he was really impressed with 8.04 and that I should download it and give it a try.  Well that did it.   Windows XP was coming off and 8.04 was going on.  I don't like to do things half-a$$ed so I backed up the files I needed and burnt a copy of Ubuntu and let it loose....

I am very happy I did.  Finally with Hardy I am able to do everything I need to do with two exceptions which I will get to.  The first thing I noticed is that Hardy didn't seem as slow at boot-up as in the past releases.  Having installed Ubuntu and other Linux flavors I knew what to expect and Ubuntu paid out at the finishline.

Without having to do anything, it recognized all of my devices right away.  I didn't have to hunt for the drivers disk as I have in XP.  Everything just worked right out of the box.  I was very very happy for this.

Of course who is going to run Linux without sound and video?  Having had past dealings with Ubuntu I was really surprised that right off the bat the sound system was recognized.  This was a definite plus for me.  I just installed mediabuntu and I was off and running.

Over the course of about three hours I was drooling as I downloaded from the non-free repositories and everything.... well just worked.   Even things that seemed to be a challenge in earlier releases worked right away.

Although I had played around with WINE before I always became upset trying to download everything I needed for it to work.  This time around..... It worked.

Compwiz - I believe it was the 7.10 edition I still had to install everything by hand.  8.04 it was already there.

The benefits of the positives outway the negatives, but there are some things that I still seem lacking, and its not Ubuntu's fault...

**Logitech Headset**  This is a big one for me.  I have a USB Logitech headset and if Logitech could supply support for Linux it would be a wonderful thing.  Sometimes it works, but most times it doesn't.  I use it for SKYPE, Amateur Radio "Echolink", and several other programs.  I just need this to work.  It's pretty annoying to the family when I sit here and listen to Bubba or Howard Stern and they hear it through the speakers.  Likewise I don't like to sit and listen to Thomas The Tank Engine Youtube videos blaring over the sound of the television.    The computer and tv are fairly close to each other and being competitive over the volume often ends up in shouting.... This is not needed in my household.  

**DELL AIO 962 PRINTER**  Enough said.  Everyone that has a Dell has tried drivers for their "Lexmark" printers, and just like me failed miserably.  I had hoped that running it under Virtual Box I could get it to run, but I'm still having trouble with it...... Dell should be commended for their usage of Ubuntu on their systems as a option, but they should also supply support for printers as well....

I'm pretty happy otherwise with my system.  There is only one problem that I have right now that I can't resolve and it is Remote-Desktop and VNC issues...... Hopefully I'll be able to solve that....

BTW here is a picture of my son and a friend at the local lake..... I just think this is a great photo....

[IMG]http://www.cyberlancaster.com/lancasterfire/20080513001.jpg[/IMG]

Nice testimonial with pic:):KS

---

### Post by hyper_ch on 2008-06-17
btw, nice pic :)

---

