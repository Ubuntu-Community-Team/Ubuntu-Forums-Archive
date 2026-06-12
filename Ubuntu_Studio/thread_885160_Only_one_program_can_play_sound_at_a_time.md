---
title: "Only one program can play sound at a time?"
date: 2008-08-09
forum: Ubuntu Studio
---

### Post by Envergure on 2008-08-09
It seems that some programs prevent others from using my computer's audio out.  When Firefox is open, LMMS can't secure an audio context.  Firefox and Rhythmbox can cooperate, but either alone can prevent Synesthesia (my own program, which is destined to be a softsynth) from opening an audio output stream (using SDL).  It's very frustrating because if i listen to music while i'm coding i have to close everything to test my app.

Is it my hardware or a problem in Ubuntu?  Is there anything I can do to fix it?

My audio hardware is an Intel AC'97 integrated motherboard audio thingy.

I have no such problems in Windows XP Home.

---

### Post by dhimate on 2008-08-09
I am also facing the same issue. I can't open any media file if firefox is running.

---

### Post by eye208 on 2008-08-09
The Flash browser plug-in doesn't work properly with PulseAudio. To fix it, either install "libflashsupport" or remove PulseAudio as described [here](http://ubuntuforums.org/showpost.php?p=5354773&postcount=6).

---

### Post by Roasted on 2008-08-10
For me, I had to adjust my sound preferences in my music program. I use Amarok, and Amarok was set to auto detect, while sys-pref-sounds was set to ALSA. With this setup, oddly enough I had issues with sound, just like you dsecribed.

Once I set Amarok to ALSA, which is the same as my sound preferences, suddenly everything worked. I was watching youtube videos and listening to Amarok at the same time without any issues.

note - I don't have libflashsupport installed. I found I only had more frequent crashes. :confused:

---

### Post by markbuntu on 2008-08-10
You can fix all your problems with multiple applications playing sound by following this guide I wrote here:


[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

---

### Post by Roasted on 2008-08-10
> **markbuntu said:**
> You can fix all your problems with multiple applications playing sound by following this guide I wrote here:


[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

Everything works fine without libflashsupport, as long as my music player is set to ALSA. That's what's weird. Everybody always praises libflashsupport as it solves this problem, yet, I don't have that problem.

Here, read this thread. I just posted it with a lot of details about what I've done and what I've experienced in hopes of somebody offering an idea as to why I have zero issues without libflashsupport, but others need it.

[http://ubuntuforums.org/showthread.php?t=885840](http://ubuntuforums.org/showthread.php?t=885840)

---

### Post by markbuntu on 2008-08-10
Do you have flash 10b perhaps, or flash 8?

Flash 10 works without libflashsupport. In fact, libflashsupport causes problems for flash10.

What caused the crashes with firefox and flash was that flash would rapidly open and close streams in pulseaudio until the stream limit was passed somewhere around 900-1,000, then the system would crash or lock up completely. Libflashsupport was to fix that problem, and it does, but it is strictly a flash/ pulseaudio problem. If you are not running pulse audio then you won't have that problem.

---

### Post by Roasted on 2008-08-10
I have flash 9, however, I'm looking to install flash 10 beta as we speak.

Then, I've been under a false notion based on what talk I've heard in other pulseaudio threads. I've been told time and time again that the reason people want to go to pulseaudio is so they can watch youtube and listen to music at the same time. And I've been sitting here staying then why the fk am I any different? I'm running alsa and my system is perfectly fine.

But, alas, it sounds like the reasoning behind pulseaudio wasn't to run youtube + amarok at the same time, but it had other network related tendencies. Eh?

---

### Post by eye208 on 2008-08-10
> **Roasted said:**
> I've been told time and time again that the reason people want to go to pulseaudio is so they can watch youtube and listen to music at the same time.
Yes, it's a common myth that PulseAudio introduced software mixing. Any application using ALSA's default device will run side by side with others. The same goes for apps using ESD. Only those hogging ALSA's "hw" devices or /dev/dsp will occupy the sound card. Fortunately this is a thing of the past. Flash 9 works fine with ALSA.

---

### Post by Roasted on 2008-08-10
Oh, so flash 9 fixed the problem with music/youtube... I knew something along the line did. Everything I read just suggested pulse would fix it, when it wasn't a problem with me in the first place... but hey, I had flash 9! So I guess that'd be why.

---

### Post by markbuntu on 2008-08-10
Pulse fixed a number of issues for me, like using two of my sound cards at the same time, but yeah, it seems to be all about network streaming. The fact that hal can only detect the first device on any card is a real issue that has not been addressed even though the devs have known about it for almost a year. There is a way around it, but it only partly works.

Nonetheless, I have figured out how to get it all to work, even with jack.

---

### Post by Roasted on 2008-08-10
Hm, for me, I can't imagine having the need of using two sound cards at once... I'm still blown away by how good this PCI card is I just bought! 

Maybe with Intrepid we'll have a solid pulse option here for us. Until then, I'll steer clear of it...

Also - How would you even hook up two sound cards? Do you just have two sets of speakers? Or do you somehow wire each card together?

---

### Post by eye208 on 2008-08-10
> **Roasted said:**
> Hm, for me, I can't imagine having the need of using two sound cards at once...
Two sound cards make sense if you produce music. You can have a cheap onboard one hooked up to a headset for Skype, games etc. and an expensive, maybe external one for music production. Software mixers and sample rate converters degrade sound quality, so you want to bypass these. This can be done easily with two separate cards. I had two cards in my PC when I was using Cubase on Windows several years ago.

---

### Post by Roasted on 2008-08-10
> **eye208 said:**
> Two sound cards make sense if you produce music. You can have a cheap onboard one hooked up to a headset for Skype, games etc. and an expensive, maybe external one for music production. Software mixers and sample rate converters degrade sound quality, so you want to bypass these. This can be done easily with two separate cards. I had two cards in my PC when I was using Cubase on Windows several years ago.

So I guess when I read about these individuals who are hardcore into pulse audio, it's really people who are pretty much audiophiles and not your typical websurfing/email/occasional song type of person?

---

### Post by markbuntu on 2008-08-10
Just people who want better sound than those crappy chips on the motherboards. I have one of mine hooked up through my high quality speakers and use the other for my headphones. 

So, when am doing audio work and want a break, I don't have to change any settings on my audio/recording/jack setup to look at some youtube videos. 

I can just switch to another desktop and put on the headphones.

---

### Post by Roasted on 2008-08-10
> **markbuntu said:**
> Just people who want better sound than those crappy chips on the motherboards. I have one of mine hooked up through my high quality speakers and use the other for my headphones. 

So, when am doing audio work and want a break, I don't have to change any settings on my audio/recording/jack setup to look at some youtube videos. 

I can just switch to another desktop and put on the headphones.

I'm still failing to see the beneficial point of this.

Why not just get a decent sound card, kick your shoes off, and call it a day?

---

### Post by eye208 on 2008-08-11
> **markbuntu said:**
> Just people who want better sound than those crappy chips on the motherboards.
Fun fact: Many "pro" sound cards use the same chips you can find on motherboards. For example the whole M-Audio line of interfaces is based on VIA's "Envy" controller. You will find the same chip on motherboards and some $15 PCI sound cards.

The days when onboard sound meant 16bit locked at 48kHz are long gone. Intel's HDA standard has largely replaced the previous AC97. This new breed supports up to 24bit/192kHz/2.0ch and 24bit/96kHz/7.1ch. All modern motherboards have digital outputs, so cheap onboard D/A converters are no longer an issue.

Right now I see only three reasons for buying a separate audio interface: recording, multi I/O, and latency. If you record audio in a studio setup, you want decent A/D conversion and many separate inputs and outputs. This is beyond the scope of onboard sound cards.

Latency is an issue only on Windows. With ALSA/Jack and a realtime kernel you can get ~10ms out of the cheapest cards. The ALSA developers have no incentive to cripple their drivers in order to sell separate "pro" sound cards at a premium. This is both a blessing and a curse because it keeps the commercial pro audio world from adopting Linux (except as an embedded OS for synthesizers). This is why we won't see Cubase on Linux any time soon.

---

### Post by Roasted on 2008-08-11
I just spent 60 dollars on a PCI 7.1 sound card.

Why?

Because my onboard one on my motherboard absolutely sucked. I couldn't stand listening to distortion, so I had to do something about it.

Then again, my motherboard is a solid 3 years old. Maybe onboard audio has significantly improved since then??

Plus, I can see people spending money on sound cards if they have big audio setups and want the surround sound capabilities... But I wouldn't ever just get a standard PCI sound card for the sake of replacing onboard. If onboard works, it works. If it sucks, upgrade. Mine sucked, I upgraded.

But, in the end, I look at upgrading a sound card now like most people look at upgrading a video card from onboard. You speak of chipsets and whatnot being the same, yeah, that may be true... but there's something else there that is kicking the pants off of my onboard sound card. For the same reason that my PCIE 6600 256mb graphics card is kicking the pants off of my onboard video card too. But, hey, if integrated does what you need, great. But I like video gaming and listening to badass gunshots. So I had to do what I had to do. :)

---

### Post by eye208 on 2008-08-11
> **Roasted said:**
> Then again, my motherboard is a solid 3 years old. Maybe onboard audio has significantly improved since then??
The HDA specification was released in 2004. You probably have AC97 onboard sound.

---

### Post by Roasted on 2008-08-11
> **eye208 said:**
> The HDA specification was released in 2004. You probably have AC97 onboard sound.

Whiiiich is the crappier one, right? I was going to say, my audio in XP and Ubuntu wasn't bad, but it wasn't good. I didn't realize how good things could get till I got this sound card. 

But, when I build a new system, I'll give the onboard a shot. I hear a lot of conflicting things going in either direction, though. Some swear that onboard audio will suffice, others are convinced that sound cards have their place.

So far, I'm opting for numero dos.

---

### Post by eye208 on 2008-08-11
There's another thing that defines audio quality, and I mentioned it before: D/A (digital-to-analog) converters.

However if you use the digital-out of your motherboard, you bypass the onboard converters and their quality becomes irrelevant.

---

### Post by fbuchele on 2008-08-21
I found a fix for that a while ago, I don't remember where. 

System > Preferences > Sound > Change everything from autodetect to ALSA

It should work now.

---

### Post by f1r31c3r on 2008-10-06
system > preferences > sound and setting all to ALSA solved the problem including crash problems with audio indicants to me to set the default devices correctly if you suffer from this problem great thread rock on


I then decided to set my default device to intel ac97 audio ICH4 device and all work perfect still so there is solution i am sure if there is prob continuing there is deeper problem


hope this helps

---

