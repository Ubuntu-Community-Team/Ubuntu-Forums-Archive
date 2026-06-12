---
title: "The backwards step of Ubuntu professional audio"
date: 2008-07-12
forum: Ubuntu Studio
---

### Post by badmotor on 2008-07-12
My biggest concern is what I have seen with the development of Ubuntu (namely Hardy). I used to record with it and Ubuntu Studio, and Linux Mint Daryna. Since the latest has come out (Ubuntu 8.04, Ubuntu Studio 8.04, Linux Mint Elyssa - and I have tried all of these), I have found that setting up hardware inputs and latency is a major pain in the butt! (and I suspect this is to do with Pulse Audio). I thought SURELY Ubuntu Studio would work well - trying to do a simple task like enable the mic input (failed!) or setup a decent latency ... what a nightmare - and I have tested this on a number of computers.

Low and behold (as I suspected) I installed Ubuntu Studio 7.10 and automatically the inputs are all there, latency is setup fine and it sounds great. 

I definitely tested this on a couple of different machines with the same results (before you all cry "... it's your hardware..."). I really think Ubuntu has taken a big leap backwards as far as audio is concerned. Leap forward for normal desktop - leap backwards for semi/professional audio.

---

### Post by Stochastic on 2008-07-13
Are you using Jack?  Pulse audio is killed as qjackctl starts up, from what I remember.  I do think that for general purpose applications Pulse Audio may not quite be ready, but it's very promising with all of its capabilities (fixes many issues that were constant pains in the audio system).

I personally love the improvements to ardour in the new version, and can't wait for MIDI to show up.  There are some apps that are plagued by buggs in Hardy, but from what I hear the UbuntuStudio devs are concentrating on bug squashing for Intrepid.

---

### Post by badmotor on 2008-07-14
> **Stochastic said:**
> Are you using Jack?  Pulse audio is killed as qjackctl starts up, from what I remember.  I do think that for general purpose applications Pulse Audio may not quite be ready, but it's very promising with all of its capabilities (fixes many issues that were constant pains in the audio system).

I personally love the improvements to ardour in the new version, and can't wait for MIDI to show up.  There are some apps that are plagued by buggs in Hardy, but from what I hear the UbuntuStudio devs are concentrating on bug squashing for Intrepid.

Yeah, I guess - roll on Intrepid. Interesting to see what happens to Ubuntu Studio there.

---

### Post by badmotor on 2008-07-20
Actually, I would like to hear from anyones experience with recording audio with Ubuntu Studio 8.04...

---

### Post by wkulecz on 2008-07-22
> **badmotor said:**
> Actually, I would like to hear from anyones experience with recording audio with Ubuntu Studio 8.04...

Recording?  I'd be happy if playback worked correctly in 8.04.

--wally.

---

### Post by arthursucks on 2008-07-23
I had little issue with running Jack on my desktop in 8.04, but on my laptop I had to uninstall Pulse.  I did it through synaptic and restarted, everything works find now.

---

### Post by zipperback on 2008-07-23
If Ubuntu 7.10 was working great for you, and 8.04 isn't working great for you in your specific situation, then just stick with 7.10 for now until the issues with Pulseaudio are resolved that are causing you problems.

As far as my needs go, I would say that Hardy is a major step in the right direction.

- zipperback
:popcorn:

---

### Post by russo.mic on 2008-07-26
I'm recording with Ubuntu Studio 8.04.  In fact, my studio is 3 presonus firepods sync'ed up under freebob as a mobile recording rig with ardour. Runs great for me.

I'm also using Jack sync to have video sync to MIDI timecode with Open Movie editor for video playback for ADR and post sessions.

8.04, no complaints here.

Russo

---

### Post by badmotor on 2008-07-26
> **russo.mic said:**
> I'm recording with Ubuntu Studio 8.04.  In fact, my studio is 3 presonus firepods sync'ed up under freebob as a mobile recording rig with ardour. Runs great for me.

I'm also using Jack sync to have video sync to MIDI timecode with Open Movie editor for video playback for ADR and post sessions.

8.04, no complaints here.

Russo

Wow.... really?

---

### Post by lapcat66 on 2008-07-26
For me, on three different computers, 7.10 (gutsy) Ubuntu Studio is rock solid, but 8.04 (hardy) US doesn't play nicely.  I can't eliminate the xruns.

I just set up an intrepid alpha 3 partition to experiment, from which I am writing.  First issue was all sounds were coming out the computer speaker only!

---

### Post by russo.mic on 2008-07-26
> **badmotor said:**
> Wow.... really?

Yeah, really.  I'm suprised to see all the negitave posts on 8.04 studio.  Not saying anybody is wrong, maybe I'm just lucky or something.  

It's been pretty good so far. I would def. say better than 7.10 for me.  I'm running on a MBP C2D, if that makes a difference. 

Russo

---

### Post by badmotor on 2008-07-26
> **russo.mic said:**
> Yeah, really.  I'm suprised to see all the negitave posts on 8.04 studio.  Not saying anybody is wrong, maybe I'm just lucky or something.  

It's been pretty good so far. I would def. say better than 7.10 for me.  I'm running on a MBP C2D, if that makes a difference. 

Russo

Maybe that IS what is making the difference...

---

### Post by Stochastic on 2008-07-28
> **badmotor said:**
> Maybe that IS what is making the difference...

I don't think it is, as I'm running on a Compaq Presario and I find 8.04 to be a much nicer recording system than 7.10.  However, I also have a Firepod as my pro soundcard - my inbuilt one works fine too though.

---

### Post by badmotor on 2008-07-29
Maybe it's my inbuilt laptop card. Although I tried on my desktop machine with the exact same results. I'm dreading I'm going to have to do what I have avoided in the last year, and that's install Windows for recording music.

---

### Post by SunnyRabbiera on 2008-07-29
Well pulse is still experimental, but at the same time it shows promise to surpass other audio servers in linux.

---

### Post by wkulecz on 2008-07-29
> Well pulse is still experimental, but

I'd prefer the experimental, not ready for prime time features be left out of LTS releases.  No sound issues for me in 6.06, my needs are modest, but big dissapointment that sound in 8.04 can't meet them.  If sound were mission critical I'd have already rolled back to 6.06.

--wally.

---

### Post by Stochastic on 2008-07-29
> **badmotor said:**
> Maybe it's my inbuilt laptop card. Although I tried on my desktop machine with the exact same results. I'm dreading I'm going to have to do what I have avoided in the last year, and that's install Windows for recording music.

Maybe if you posted a "please help me get this to work" thread rather than a "this software is bogus" thread then those who understand the audio server changes in 8.04 would be happy to help you fix the issues.  Try posting a new thread and see how far you get.  Besides, why go buy a copy of windows when you admitted 7.10 works fine for you.

---

### Post by badmotor on 2008-07-29
> **Stochastic said:**
> Maybe if you posted a "please help me get this to work" thread rather than a "this software is bogus" thread then those who understand the audio server changes in 8.04 would be happy to help you fix the issues.  Try posting a new thread and see how far you get.  Besides, why go buy a copy of windows when you admitted 7.10 works fine for you.

A. I think I will start a new help thread, sorry to come across negative
B. Don't need to buy Windows, I have a copy.
C. I'd like to use newer versions of Ubuntu (doesn't everyone?) because of the newer apps, all the bugs fixed, better looks etc.etc. I don't thank that is unreasonable?

And from the outside, and all the threads I have read - it does concern me that recording in Ubuntu/Studio seems to be getting harder not easier.

---

### Post by russo.mic on 2008-07-30
Oh,  thats your problem i suspect. I'm using Jack with a firepod.  The built in cards are prob. always going to have more problems as the latency will increase.  There just not made to record pro audio with.  

My firepods work great (the old ones, not the new fire studios, although they might work too, not sure) and they can be fetched on ebay for fairly cheap.  Works great with freebob through jack.

I don't even bother with pulse, I don't see the point...

Russo

---

### Post by badmotor on 2008-07-30
firepods ay? hmmmm  Might have to go do some research there.

---

### Post by zipperback on 2008-07-31
> **wkulecz said:**
> Recording?  I'd be happy if playback worked correctly in 8.04.

--wally.


Playback works fine for me. What application are you having a problem with?

- zipperback
:popcorn:

---

### Post by eye208 on 2008-07-31
[LIST=1]
[*]Disable Gnome system sounds.
[*]Remove package "pulseaudio", install "esound".
[*]Reboot.
[*]Enjoy fully operational audio in all applications.
[/LIST]

---

### Post by badmotor on 2008-07-31
> **eye208 said:**
> [LIST=1]
[*]Disable Gnome system sounds.
[*]Remove package "pulseaudio", install "esound".
[*]Reboot.
[*]Enjoy fully operational audio in all applications.
[/LIST]

You think that will work for recording purposes?

---

### Post by eye208 on 2008-08-01
> **badmotor said:**
> You think that will work for recording purposes?
Yes.

---

### Post by allmywebsite1 on 2008-08-02
My Dell Laptop automatically detect the sound in the ubuntu.So i don't have to waste my time to fix it.

---

