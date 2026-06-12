---
title: "Mixxx not working with JACK, but ok with ALSA"
date: 2008-07-11
forum: Ubuntu Studio
---

### Post by jukingeo on 2008-07-11
[Since I wrote this post based on an older version of Mixxx and Ubuntu Studio, I have since upgraded to Lucid and I am using the latest version of Mixxx which I got from the site.  DO NOT USE THE SYNAPTIC VERSION!  It is seriously out of date.

The new version of Mixxx I am using is 1.10.0 and it has changeable skins as well the graphic display problems in the old version are now over. Sound issues in Alsa are also over. Seriously get this version of Mixxx, it works great!]




Hello all,

I looking to work with Mixxx in Ubuntu Studio, however, I have a bit of a problem with the audio side of the program.  If I open Jack and tell Mixxx to use Jack, it responds with an error message that says "Cannot Open Audio Device".  If I select the ALSA direct, Mixxx WILL work, but the audio is crackly and distorted.  Turning up the latency does minimize the distortion, but never gets rid of it.  However, turning up the latency that high causes the program to be very slow and unresponsive.

The bottom line though is that I wanted to use Mixxx BECAUSE of it's ability to use Jack.  I like Mixxx's functionality and layout, but it doesn't have much in terms of additional mixing capabilities (add a microphone or drum machine).  So in order to the most out of it, I have to get it to work with Jack.

Jack is working on my system right now and I am using Ardour, Hydrogen, Audacity, and TerminatorX with it and I have no problems with audio response with these programs.

I have tried to check the problem out over at the Mixxx website, but there is very little information about the problem.  I left a message in the troubleshooting forum and it has gone unanswered for 3 days.

So I am wondering if anyone here has run into the same problem and perhaps has a solution to the dilema.

Any assistance would be much appreciated.

I am on Ubuntu Studio Hardy and Mixxx version 1.6.0 Beta 2.

EDIT:  [Solved (partially)].  

Ok, I was told that the problem with Mixxx is that the sample rates have to match in both Mixxx AND Jack.  That is why I gave me the error.   I did make a notice in the Mixxx forum that the error message should be changed to "Couldn't load audio device:  Check to see that sample rates match".  With a message like that, it would be a no-brainer as to what to do next.

However, now I have different issue within Jack.   Mixxx causes ALOT of xruns when both of the decks are playing.   But I guess now that becomes another issue.

Thank You,

Geo

---

### Post by Stochastic on 2008-07-11
I can confirm this issue on my system.  I've even tried the beta3 version from their website and it has the same problem.  I don't have time to file a Launchpad bug right now, could you do it and I'll post my findings on it too.

For now, if you have turntable and a timecoded vinyl, XWAX has a jack branch that is fully functional.  It doesn't have all the features of MIXXX, but will work very similar.

---

### Post by jukingeo on 2008-07-11
> **Stochastic said:**
> I can confirm this issue on my system.  I've even tried the beta3 version from their website and it has the same problem.  I don't have time to file a Launchpad bug right now, could you do it and I'll post my findings on it too.

For now, if you have turntable and a timecoded vinyl, XWAX has a jack branch that is fully functional.  It doesn't have all the features of MIXXX, but will work very similar.

Out of all the programs I tested thusfar, MIXXX does offer the most promise and probably has a good amount of interest behind it, but considering what you said that it is indeed a bug and it was carried over from one beta to another does make it seem that MIXXX's problem solving is SLLOOOWW.

I am still going to play with it some more, but the thing is without Jack I can't use it with my other applications.

I am wondering if I should perhaps seek out an older version.  Would you know if an older version works with Jack and which one that may be?

I took your offer up and checked out the XWAX site you recommended.  There seems to be a lack of screenshots there, so I don't know what the program looks like.  It also seems like that you NEED the vinyl rig in order for it to work.  The main point is that I would like to get away from turntables even though I still do have them.  For me a scratch wheel is good enough.  When I saw that you could use Mixxx with the inexpensive Mixman DM2, that looked fine enough for me.

I guess perhaps I led on to that I may like a turntable scratching system because I made a comment earlier about how I liked the scratch function on Terminator-X.  Now THIS is a program that has serious potential IF they work on it a bit more.   All it needs is separate outputs for Jack, so if you want to you can hook it up to a hardware (analog) mixer or mix withing a program like Ardour.   It needs more transport controls so you can move the files back and forth.  It also needs tempo or fixed key control.  But I like the stacked waveform approach and all the plug in capabilities.

In terms of features, DJ Play comes the closest as it does have the multiple outputs and even a cue system.  It is set up in a traditional dual CD player (like a Numark or Denon).   However, it too lacks tempo control.  But the bad thing about DJ Play is that it gives Jack the worst case of the XRuns I have seen!  Talk about a digital laxative! 

Anyway, thanx again for the tip off.  So far I am hoping they do fix Mixxx as I still like that one overall.  But if Terminator X improves on it's features...then that would be the way to go.  I think I will drop a line in their suggestion box!

G'Night

Geo

---

### Post by Stochastic on 2008-07-12
> **jukingeo said:**
> I am wondering if I should perhaps seek out an older version.  Would you know if an older version works with Jack and which one that may be?

Mixxx 1.5.0 worked fine with jack in Gutsy, so if it doesn't work ok in Hardy, then the problem may be a Hardy/mixxx issue rather than a jack/mixxx1.6.0 issue.  I'm primarily interested in timecoded vinyl control, as I love my vinyl, so XWAX works for me (and is nice and stable, though the current file browser could use a lot of improvements).

---

### Post by jukingeo on 2008-07-12
> **Stochastic said:**
> Mixxx 1.5.0 worked fine with jack in Gutsy, so if it doesn't work ok in Hardy, then the problem may be a Hardy/mixxx issue rather than a jack/mixxx1.6.0 issue.  

I wonder if version 1.5 may work with Hardy.  But I wouldn't doubt if the problem was in Hardy.  There seems to be quite the amount of problems with Hardy.  

> I'm primarily interested in timecoded vinyl control, as I love my vinyl, so XWAX works for me (and is nice and stable, though the current file browser could use a lot of improvements).

Heh, heh.  Yeah, I gathered that by your avatar :).  Oh, I like my old records as well.  I have TONS of old freestyle and dance music from the 80's into the early 90's.  Much of it was never pressed to CD.

In some cases vinyl CAN sound better than CD's.  That is why I was waiting for a long time until a good recording frequency became available, so it could more accurately capture the signal.  I had a 48k recording studio and nixed it because I wasn't happy with that frequency.  96k to me is the absolute minimum standard for recording, but not vinyl archiving.  192k...Ok, now were are here.  The trouble is this format does take up alot of hard drive space (you don't want to EVER archive vinyl with MP3's).  But now that terrabyte harddrives are out there, the project is feasible.  Luckily, I was very judicious about my vinyl purchases when I was a DJ.  Either the song was very good, had long term popularity, or I personally liked it, then I bought it.   If it was something that I knew would be flash in the pan, I didn't buy it.  I either recorded it to cassette or later to Mini-disk.

While I did think vinyl control was cool I just don't have the room any more for it.  I may still play around with the concept because I always still need one turntable hooked up.  But my goal is to make mixed recordings again for parties.  Who knows, I may start to DJ again, but this time for a niche market.  I don't particularly care for the new stuff that is out now, but I like anything from the 50's to the early 90's.

I am going to poke around to see if anyone managed to get Mixxx version 1.5 operational on Hardy.  Because right now I am really without a good DJ mixing program.   DJ Play would suffice and hold me over if it wasn't for the large xrun problem it has.   Terminator X would be FAR superior to Mixxx if it had the control and output features that DJ Play has.

So for now I really don't know what I would use.  But if version 1.5 of Mixxx does work with Jack, then I would be good to go for a while.  Even though Mixxx lacks in/out features, with Jack I can push it into Ardour and add other sound sources in the mix from there.

Geo

---

### Post by jukingeo on 2008-07-15
Boomp

---

### Post by Stochastic on 2008-07-15
> **jukingeo said:**
> Boomp

Is this a way of saying you tried to get mixxx 1.5 up and running, but it's acting weird too?

---

### Post by jukingeo on 2008-07-16
> **Stochastic said:**
> Is this a way of saying you tried to get mixxx 1.5 up and running, but it's acting weird too?

Boomp = Bump.

I tried to move the message up because when you edit it, it doesn't move. Yes, I was trying to be funny.

Anyway, I have read about a fix HERE in Ubuntu that may fix the problem.  So in a way that is funny too because the fix isn't listed on the Mixxx site.

I do believe...that the frames has to be moved to 512 and the captures (something like that, it is located below the frames setting) has to be changed from 2 to 3.  Supposedly that should take care of the xruns problem.  But I have not tested as of yet.

Thusfar I have not rolled back to 1.5 yet.  However, I been finding out that not necessarily applications can be buggy, but the OS can be as well.   I have noticed quite a few peculiar problems with Hardy.  Supposedly from what I heard it is the buggiest version of Ubuntu yet.  I am hoping that things will be massively corrected when Intrepid comes out.  But if I find that to be buggy also, then I am probably going to switch distributions and go to something more suited for audio work such as JackLab or 64Studio.

Geo

---

### Post by jukingeo on 2008-07-17
Ok all, I found a way to fix the xruns problem in Jack with Mixxx through another poster here in the Ubuntu forums.

Within the setup tab of Jack these changes have to be made:

1) Sample Frequency:  48000 (this must also be set in Mixxx too otherwise Jack will come up with the aforementioned "Audio Device Cannot Be Started" Error.

2) Frames: 512
3) Buffers: 4 (you may have to adjust this up or down depending on the speed of your system.

Now Mixxx is working fine.

---

### Post by Stochastic on 2008-07-17
AHHHH, now I see, the issue is in Mixxx not seeing the sample rate that Jack is set to, automatically.  It needs to be manually set in the Mixxx preferences to correspond with jack.  The other setting you're talking about will be user/soundcard dependent.  But without that matching audio sample rate the program says it cannot open the audio device.  Out of curiosity which thread did you find your information from?

---

### Post by jukingeo on 2008-07-19
> **Stochastic said:**
> AHHHH, now I see, the issue is in Mixxx not seeing the sample rate that Jack is set to, automatically.  It needs to be manually set in the Mixxx preferences to correspond with jack.  The other setting you're talking about will be user/soundcard dependent.  But without that matching audio sample rate the program says it cannot open the audio device.  Out of curiosity which thread did you find your information from?


No thread...I think I spoke to one of the Mixxx developers directly.  He said that if the sample rates do not match you get the "Cannot activate Audio Device" error.  I did inform him that perhaps changing the error message to read: "Cannot activate Audio Device: Application's sample frequency must match", or something like that.  At least it would tell the person where to go look to correct the problem.

The other information about changing the sample rate, frame and buffers I got right here in the Ubuntu Forum.

Geo

---

### Post by jocheem67 on 2008-08-04
I've got mixxx working ok with jack, I think.
Thing is it all depends on your hardware:


[[IMG]http://img231.imageshack.us/img231/9330/schermafdruksetupjackaubk2.th.png[/IMG]](http://img231.imageshack.us/my.php?image=schermafdruksetupjackaubk2.png)


These are the settings for a hercules rmx dj console, using jack obviously with pretty nice latency...

Now I just need to get midi working, aaarch!!!

I'll start a thread about that one.

---

### Post by Stochastic on 2008-08-05
> **jocheem67 said:**
> I've got mixxx working ok with jack, I think.
Thing is it all depends on your hardware:

No, it's not based on hardware.  Jukingeo had a software conflict between the jack sample rate and Mixxx's expected sample rate (set in mixxx's preferences).

---

### Post by motin on 2009-10-19
For those interested, I added instructions on how to get Mixxx working with JACK (in general) in Karmic:

Rebuild portaudio:
[https://bugs.launchpad.net/mixxx/+bug/360590/comments/16](https://bugs.launchpad.net/mixxx/+bug/360590/comments/16)

Then change mixxx configuration:
[https://bugs.launchpad.net/ubuntu/+source/mixxx/+bug/339537/comments/4](https://bugs.launchpad.net/ubuntu/+source/mixxx/+bug/339537/comments/4)

Cheers

---

### Post by jocampo on 2010-01-08
> **motin said:**
> For those interested, I added instructions on how to get Mixxx working with JACK (in general) in Karmic:

Rebuild portaudio:
[https://bugs.launchpad.net/mixxx/+bug/360590/comments/16](https://bugs.launchpad.net/mixxx/+bug/360590/comments/16)

Then change mixxx configuration:
[https://bugs.launchpad.net/ubuntu/+source/mixxx/+bug/339537/comments/4](https://bugs.launchpad.net/ubuntu/+source/mixxx/+bug/339537/comments/4)

Cheers

Thanks so much Motin, I've been looking for this during hours. But I&#7743; having problems finding and compiling these

```

sudo dpkg -i libportaudio2_19+svn20090620-0ubuntu1_i386.deb
sudo dpkg -i libportaudiocpp0_19+svn20090620-0ubuntu1_i386.deb
sudo dpkg -i portaudio19-doc_19+svn20090620-0ubuntu1_all.deb

```

where are those packages? My Ubuntu Studio can find them

---

### Post by hreichgott on 2011-08-31
Thank you! I was getting the "cannot load audio device" problem, using 11.04. 

I only had to change the sampling rate, periods and buffers to be the same in Mixxx and Jack, and I used the numbers suggested above (48000, 512 and 4.)

Did not have to muck about with editing configuration files manually.-

I also find that Mixxx does not list Jack as a sound option until the Jack server is started. So this is what I have to do
1. start Jack
2. start Mixxx
3. Mixxx complains that it can't use the soundcard since another application is using it
4. click "reconfigure"
5. THEN choose Jack
6. Mixxx appears as "Port Audio" in the Jack connections window.

Not a big deal, as this doesn't take very long, and it works great once it's done.

---

