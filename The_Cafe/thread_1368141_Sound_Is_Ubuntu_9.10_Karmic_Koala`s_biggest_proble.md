---
title: "Sound Is Ubuntu 9.10 Karmic Koala`s biggest problem ?"
date: 2009-12-30
forum: The Cafe
---

### Post by premamotion on 2009-12-30
Hi there to all!

I`m using Ubuntu (and loving it) since version 8.04. I have tryied many other distros, like Fedora, openSuse, Mandriva, Linux Mint... but no one is better than Ubuntu.

I loved so much 8.04 and 8.10 and I`m so happy that during the time many things got implemented, many beautiful ideeas and a lot of problems got resolved. I never had problems in 8.04 and 8.10 but with 9.04 and now, with current version, Karmic Koala... I hear, and it seams that the sound is the most used word in Lauchpad bugs...

 It`s true? Why this happens... I have a lot o f problems with the sound now...

---

### Post by VertexPusher on 2009-12-30
> **premamotion said:**
> Why this happens...
One word: PulseAudio.

The good news: If you remove PulseAudio, most of those problems will go away.

The bad news: Some people believe that "PulseAudio is the future of Linux audio". I doubt it because there are some conceptual problems in PulseAudio that keep it from ever working properly for the majority of users. Nothing can become a standard that doesn't work for the vast majority of users. Some bugs have not been fixed for months because the developers simply don't know how to fix them. The concept is flawed; the one-size-fits-all approach doesn't work. In the end, PulseAudio will go the way that ESD and aRts went before. ALSA and JACK are going to stay with us for many, many years, because in 99% of all cases they just work.

---

### Post by LuisGMarine on 2009-12-30
I haven't had any issues with sound on either my laptop or desktop.  However, Karmic installs great on the desktop.  When I try to do the same here on this laptop, it is a complete different story. 

Hopefully all these issues will be fixed with 10.04.

---

### Post by premamotion on 2009-12-31
> **VertexPusher said:**
> One word: PulseAudio.

The good news: If you remove PulseAudio, most of those problems will go away.

The bad news: Some people believe that "PulseAudio is the future of Linux audio". I doubt it because there are some conceptual problems in PulseAudio that keep it from ever working properly for the majority of users. Nothing can become a standard that doesn't work for the vast majority of users. Some bugs have not been fixed for months because the developers simply don't know how to fix them. The concept is flawed; the one-size-fits-all approach doesn't work. In the end, PulseAudio will go the way that ESD and aRts went before. ALSA and JACK are going to stay with us for many, many years, because in 99% of all cases they just work.

Tryed to remove Pulse Audio... but it seams that it has very deep roots into Gnome... in fact I`m not able to purge it completely, because with Pulse Audio goes also Gnome applets... indicators... etc...

I tryed 

[B]sudo apt-get purge pulseaudio gstreamer0.10-pulseaudio
sudo apt-get autoremove
sudo apt-get install alsa-base alsa-tools alsa-tools-gui alsa-utils alsa-oss linux-sound-base alsamixergui
sudo apt-get install esound esound-clients esound-common libesd-alsa0 gnome-alsamixer[/B]  

but there is no way to remove it completely... any suggestins?
Why this version of Ubuntu comes with PulseAudio?

---

### Post by VertexPusher on 2009-12-31
> **premamotion said:**
> I tryed 

[B]sudo apt-get purge pulseaudio gstreamer0.10-pulseaudio
sudo apt-get autoremove
sudo apt-get install alsa-base alsa-tools alsa-tools-gui alsa-utils alsa-oss linux-sound-base alsamixergui
sudo apt-get install esound esound-clients esound-common libesd-alsa0 gnome-alsamixer[/B]  

but there is no way to remove it completely... any suggestins?
There's no need to remove it completely. You can leave libpulse installed; it won't do anything unless the PulseAudio daemon is running.

Many of the ALSA packages you installed were already there because PulseAudio uses them, too. Installing esound packages doesn't really make sense. I don't know any application still using them. Gnome won't even launch esound any more, so these packages will just occupy space and do nothing.

I recommend installing gstreamer0.10-alsa, gnome-alsamixer, and removing gstreamer0.10-pulseaudio, vlc-plugin-pulse, pulseaudio. Open gstreamer-properties, choose ALSA as its default audio plugin, and you're done.

You know, there is this rumour dating back to maybe 2003 which says that ALSA does not allow multiple applications to use a sound card simultaneously. But that's nonsense. ALSA allows complete control over the way sound cards are used. It does sample format conversion, rate conversion, channel routing, up- and downmixing, shared playback, shared recording etc. It can turn a PCI sound card and a USB webcam microphone into a single device, and it can turn a single 7.1 surround onboard audio interface into four separate stereo playback devices, running at latencies below 4ms. It combines all the features of the various sound systems of Windows (MME, DirectSound, WDM kmixer, ASIO) under one programming interface which PulseAudio will never replace.

The only major achievement of PulseAudio in the past two years is to completely destroy the reputation of Linux as a platform for any kind of audio-related application. In a significant number of cases, including mine, PulseAudio just doesn't work out of the box. It crashes, it crackles, it uses too much CPU, it leaks memory, it messes up mixer settings etc. The bug tracker is full of PulseAudio bug reports. Some of these bugs have not been fixed for months and probably never will.

---

### Post by kblandfo on 2009-12-31
> **VertexPusher said:**
> There's no need to remove it completely. You can leave libpulse installed; it won't do anything unless the PulseAudio daemon is running.

Many of the ALSA packages you installed were already there because PulseAudio uses them, too. Installing esound packages doesn't really make sense. I don't know any application still using them. Gnome won't even launch esound any more, so these packages will just occupy space and do nothing.

I recommend installing gstreamer0.10-alsa, gnome-alsamixer, and removing gstreamer0.10-pulseaudio, vlc-plugin-pulse, pulseaudio. Open gstreamer-properties, choose ALSA as its default audio plugin, and you're done.

You know, there is this rumour dating back to maybe 2003 which says that ALSA does not allow multiple applications to use a sound card simultaneously. But that's nonsense. ALSA allows complete control over the way sound cards are used. It does sample format conversion, rate conversion, channel routing, up- and downmixing, shared playback, shared recording etc. It can turn a PCI sound card and a USB webcam microphone into a single device, and it can turn a single 7.1 surround onboard audio interface into four separate stereo playback devices, running at latencies below 4ms. It combines all the features of the various sound systems of Windows (MME, DirectSound, WDM kmixer, ASIO) under one programming interface which PulseAudio will never replace.

The only major achievement of PulseAudio in the past two years is to completely destroy the reputation of Linux as a platform for any kind of audio-related application. In a significant number of cases, including mine, PulseAudio just doesn't work out of the box. It crashes, it crackles, it uses too much CPU, it leaks memory, it messes up mixer settings etc. The bug tracker is full of PulseAudio bug reports. Some of these bugs have not been fixed for months and probably never will.

I have the same problem.  No sound... I had sound and then suddenly one day, much to my dispair nothing... not even a crackel.  The question is how do you remove gstreamer0.10-pulseaudio, vlc-plugin-pulse, pulseaudio and then how do you install gstreamer0.10-alsa, gnome-alsamixer?  Bit of a novis with Linux ams I.  Thanks for the help.

---

### Post by premamotion on 2010-01-01
> **VertexPusher said:**
> There's no need to remove it completely. You can leave libpulse installed; it won't do anything unless the PulseAudio daemon is running.

Many of the ALSA packages you installed were already there because PulseAudio uses them, too. Installing esound packages doesn't really make sense. I don't know any application still using them. Gnome won't even launch esound any more, so these packages will just occupy space and do nothing.

I recommend installing gstreamer0.10-alsa, gnome-alsamixer, and removing gstreamer0.10-pulseaudio, vlc-plugin-pulse, pulseaudio. Open gstreamer-properties, choose ALSA as its default audio plugin, and you're done.

You know, there is this rumour dating back to maybe 2003 which says that ALSA does not allow multiple applications to use a sound card simultaneously. But that's nonsense. ALSA allows complete control over the way sound cards are used. It does sample format conversion, rate conversion, channel routing, up- and downmixing, shared playback, shared recording etc. It can turn a PCI sound card and a USB webcam microphone into a single device, and it can turn a single 7.1 surround onboard audio interface into four separate stereo playback devices, running at latencies below 4ms. It combines all the features of the various sound systems of Windows (MME, DirectSound, WDM kmixer, ASIO) under one programming interface which PulseAudio will never replace.

The only major achievement of PulseAudio in the past two years is to completely destroy the reputation of Linux as a platform for any kind of audio-related application. In a significant number of cases, including mine, PulseAudio just doesn't work out of the box. It crashes, it crackles, it uses too much CPU, it leaks memory, it messes up mixer settings etc. The bug tracker is full of PulseAudio bug reports. Some of these bugs have not been fixed for months and probably never will.


Thank you so much, VertexPusher!
Your point is very very clear and mature... I`ve done what you said and now Alsa is doing great.. everything with my sound, from playing to recording got resolved!

Thank you so much for your intervention, and best wishes for the new year!

---

### Post by premamotion on 2010-01-01
And... I want to say that lately more and more people are complaining about PulseAudio... more and more... I think that`s not possible for so many people to be wrong...

In fact, more and more people agree that PulseAudio is "the black sheep" of Linux...

---

### Post by kblandfo on 2010-01-01
Act I
Scene 5

Indeed, however, having very little knowledge of how anything works with Linux, I admit my lowly state of ignorance as to how I might execute VertexPusher's council.  Help me I would so very much like to have my sound back, and rid myself of the bonds of Microsoft monopoly.  (Curtain falls)

---

### Post by leorolla on 2010-01-06
> **VertexPusher said:**
> There's no need to remove it completely. You can leave libpulse installed; [FONT=Arial Black]**[COLOR=Red]it won't do anything unless the PulseAudio daemon is running[/COLOR]**[/FONT].

Many of the ALSA packages you installed were already there because PulseAudio uses them, too. Installing esound packages doesn't really make sense. I don't know any application still using them. Gnome won't even launch esound any more, so these packages will just occupy space and do nothing.

I recommend installing gstreamer0.10-alsa, gnome-alsamixer, and removing gstreamer0.10-pulseaudio, vlc-plugin-pulse, pulseaudio. Open gstreamer-properties, choose ALSA as its default audio plugin, and you're done.

You know, there is this rumour dating back to maybe 2003 which says that ALSA does not allow multiple applications to use a sound card simultaneously. But that's nonsense. ALSA allows complete control over the way sound cards are used. It does sample format conversion, rate conversion, channel routing, up- and downmixing, shared playback, shared recording etc. It can turn a PCI sound card and a USB webcam microphone into a single device, and it can turn a single 7.1 surround onboard audio interface into four separate stereo playback devices, running at latencies below 4ms. It combines all the features of the various sound systems of Windows (MME, DirectSound, WDM kmixer, ASIO) under one programming interface which PulseAudio will never replace.

The only major achievement of PulseAudio in the past two years is to completely destroy the reputation of Linux as a platform for any kind of audio-related application. In a significant number of cases, including mine, PulseAudio just doesn't work out of the box. It crashes, it crackles, it uses too much CPU, it leaks memory, it messes up mixer settings etc. The bug tracker is full of PulseAudio bug reports. Some of these bugs have not been fixed for months and probably never will.

Thanks!!!

Now how do I get PulseAudio daemon not running?

ps: btw, anyone knows why Ubuntu chose to come with PA?

---

### Post by markbuntu on 2010-01-06
Well, there is certainly a lot of dismay about pulseaudio in Ubuntu and some of it is deserved but this dismay has less to do with pulseaudio than many people are willing to accept.

Pulseaudio uses the low level alsa drivers, many of which get broken all the time by the alsa devs updates. Somehow this becomes pulseaudios fault.

The drivers themselves have moved into the kernel recently so, to insure kernel security, many of the old alsa API calls have been deprecated and are no longer valid. Applications are no longer allowed to access and control the alsa drivers directly. This was not a decision of the pulseaudio devs but the kernel team. If you have a problem with that take it up with Linus.

Pulseaudio strictly enforces the new protocols so many applications which previously used them fail. Application devs were told about this a long time ago by the kernel team, ALSA, and the pulseaudio devs who even published a list of the new "safe API set". Many application devs chose to ignore this, including the wine devs.
This also somehow became the fault of pulseaudio.

In light of this many distribution rushed to adopt pulseaudio which even the pulseaudio devs thought was not a good idea at the time. Some distributions implemented pulseaudio very well and it integrated deeply into their sound management schemes (Fedora, Mandriva) but some did not and Ubuntu was, and still is, first among distros with problematic pulseaudio implementations.

Ubuntu does not update pulseaudio versions except at distribution release. Because of this much of the progress of pulseaudio, and many bug fixes, do not find themselves in updates. Intrepid used the same pulseaudio release as Hardy and Jaunty was released with a version that the pulseaudio devs explicitly announced as not ready for distribution release. Karmic was released with a very recent pulseaudio release but gnome was also upgraded and the new gnome volume control which implements pulseaudio was released incomplete. A history of grievous missteps.

On top of all this the actual guis to control pulseaudio, pavucontrol and paman have never been included in the Ubuntu desktop seed leading many users with no way to actually control pulseaudio. Along with that they made pulseaudio run at startup but did not include all the libs or defaults necessary for pulseaudio to actually take control of the sound scheme and applications seeking to use sound.

In addition the Ubuntu team did not make other accomodations necessary for pulseaudio to function properly, like kernel scheduling, udev rules, console kit activities, etc.

There is a sea change in linux with many old protocols being abandoned and new ones adopted. hal is deprecated in favor of console kit and udev. esound oss dmix and much of the old kludged alsa API are deprecated in favor of pulseaudio and phonon. KDE3 is deprecated for KDE4 despite all the KDE devs who were not ready for the change.

Just because something worked before does not mean it ever worked properly or that it will be able to work once everything else is made to work properly. It has been decided that now is the time for linux to get many of its kludged together systems in order. As a result many things will be broken and many users subject to a long period of grief as this works itself out but the result will be a more robust system that will serve everyone well for a long time into the future.

So, everyone is faced with a choice. Participate in making the future better or undermining progress in favor of your own personal immediate need.

Linux is not a corporation, it is people. You can talk to them and influence the direction of progress. What you cannot do is impel people to reverse direction just because you are unhappy with the changes or find yourself in a distribution with a less than stellar implementation.

---

### Post by Bakudan00 on 2010-01-07
Oh Ubuntu, some days I love you, and on others, I *love* you...

In an attempt to get my internal mic to work I followed VertexPusher's instructions and switched to ALSA. It still wouldn't happen, plus Rhythmbox and anything else that uses sound got really crashy. So I reversed my steps and wouldn't you know it? Now I have no sound at all, except on Youtube, oddly enough. Rhythmbox and VLC won't even play the media. I'm guessing Synaptic got rid of some dependencies that didn't get reinstalled when I tried to undo what I did. Any ideas on how to get my sound back?

I swear, after I fix this, I'm just going to leave it alone!

---

### Post by VertexPusher on 2010-01-08
> **Bakudan00 said:**
> In an attempt to get my internal mic to work I followed VertexPusher's instructions and switched to ALSA. It still wouldn't happen, plus Rhythmbox and anything else that uses sound got really crashy.
I call BS.

Rhythmbox uses GStreamer, not ALSA. You forgot to replace gstreamer0.10-pulseaudio with gstreamer0.10-alsa, so Rhythmbox, Totem etc. locked up trying to connect to the missing PulseAudio daemon. In other words: You did not follow my instructions.

Sorry about your mic not working, but if it doesn't work with ALSA, your only remaining option is OSS4. Good luck with that.

---

### Post by chessnerd on 2010-01-08
Ironically Karmic is the first version of Ubuntu where the sound worked perfectly out of the box for me. 

Under Jaunty I had sound issues on my laptop ---> [http://ubuntuforums.org/showthread.php?t=1265116](http://ubuntuforums.org/showthread.php?t=1265116)

Under Hardy I had sound issues on my desktop ---> [http://ubuntuforums.org/showthread.php?t=1120340](http://ubuntuforums.org/showthread.php?t=1120340)

I basically skipped over Intrepid so, yeah. Karmic sound is great for me. 

Note: Both of those threads had no replies until after it was fixed. Seems like the bigger problem is the support for sound issues from the community...

---

### Post by VertexPusher on 2010-01-08
> **markbuntu said:**
> Many application devs chose to ignore this, including the wine devs.
Linux is not a corporation, it is people. You can talk to them and influence the direction of progress. What you cannot do is impel people to drop a working implementation in favor of a non-working one.

> Ubuntu does not update pulseaudio versions except at distribution release.
Ubuntu has never been a rolling release distro. If there is no stable snapshot of PulseAudio available yet, why is it deployed with a stable distro at all? As always, the Debian devs seem to be the only ones who get it right: They have PA in their repository but don't install it by default. Because it is not ready to be deployed as part of a stable distro.

> esound oss dmix and much of the old kludged alsa API are deprecated in favor of pulseaudio and phonon.
Please quote the ALSA developer who said that dmix is deprecated.

> It has been decided that now is the time for linux to get many of its kludged together systems in order.
Linux is not a corporation, it is people. You can talk to them and influence the direction of progress. What you cannot do is tell them that things "have been decided".

> As a result many things will be broken and many users subject to a long period of grief as this works itself out but the result will be a more robust system that will serve everyone well for a long time into the future.
The only people subject to a period of grief are the newbies. But that period of grief may turn out much shorter than you expect, because there's always a Windows install CD around. What you have to understand is that many Linux distros come on live CDs these days. Guess what happens when a new user pops in such a live CD, boots up Linux and then figures out that there is no sound? For most of those people, the period of grief ends right there.

This is what PulseAudio does to Linux adoption.

> Linux is not a corporation, it is people. You can talk to them and influence the direction of progress. What you cannot do is impel people to reverse direction just because you are unhappy with the changes or find yourself in a distribution with a less than stellar implementation.
We have had less than stellar implementations of pretty much anything, including sound daemons. Look where they are now. Management decisions are irrelevant because Linux is not a corporation, it is people. You can scare newbies away from Linux, but you can't force people to use a less than stellar implementation as long as there is a superior alternative.

Lennart believes that everybody and the dog is using PulseAudio today. But the truth is that he is only scaring away the newbies. The number of application developers who have dropped ALSA is exactly zero. GStreamer, OpenAL, SDL, libao, PortAudio, MPlayer and VLC won't deprecate their ALSA back ends any time soon because they realize that PulseAudio will be gone as soon as Lennart and his crew run out of steam.

Note that I am not dismissing the sound daemon concept in general. There's one sound daemon that I use frequently: JACK.

---

### Post by worseisworser on 2010-01-08
I fully agree with you VertexPusher.

Users who need an advanced sound daemon like PulseAudio or JACK (all 0.0001% of the total Linux user-base) can add this themselves. The poor normal users (all 99.9999% of them) just want/need the simple ALSA already included with the Linux kernel (for good reason...).

All this is very unfortunate and wrong, and I believe the decision to introduce PulseAudio into Gnome/Ubuntu was one made in childish excitement ("Vista has pr. application volume controls!!11"), perhaps even fear or greed and, well, ignorance (lack of high-level overview of the situation).

---

### Post by llawwehttam on 2010-01-08
> **VertexPusher said:**
> One word: PulseAudio.

The good news: If you remove PulseAudio, most of those problems will go away.

The bad news: Some people believe that "PulseAudio is the future of Linux audio". I doubt it because there are some conceptual problems in PulseAudio that keep it from ever working properly for the majority of users. Nothing can become a standard that doesn't work for the vast majority of users. Some bugs have not been fixed for months because the developers simply don't know how to fix them. The concept is flawed; the one-size-fits-all approach doesn't work. In the end, PulseAudio will go the way that ESD and aRts went before. ALSA and JACK are going to stay with us for many, many years, because in 99% of all cases they just work.

I agree 100%. That's all I can say.

---

### Post by Jose Catre-Vandis on 2010-01-08
KISS !!

Sound should work at a basic level out of the box. It doesn't have to be clever, it just has to work.

We are starting to expect things to just work when we install Ubuntu, so it is surprising when it doesn't, especially when it worked in the previous release. That's progress I guess. But alsa and oss etc have been around long enough, and are deep rooted enough to just work. Provide the fancy stuff as an option to try/test/resolve as a part of the release process. It would be good if Ubuntu pushed this approach a little more, rather than relying on committed users to run pre-release versions and bug-fix (or ignore problems and release anyway).

Pulse has never worked for me, properly, on any hardware setup, I have always had to work around it and get back to alsa to get sound working.

---

### Post by shortsightedPenguin on 2010-01-08
What exactly should I do to make the sound work on a Karmic?

---

### Post by VertexPusher on 2010-01-08
> **shortsightedPenguin said:**
> What exactly should I do to make the sound work on a Karmic?
```
sudo apt-get install gstreamer0.10-alsa gnome-alsamixer
sudo apt-get purge gstreamer0.10-pulseaudio vlc-plugin-pulse pulseaudio
```Then log out and log in again. Use alsamixer to adjust your sound card volume levels.

Run this if you want to get PulseAudio back:
```
sudo apt-get install ubuntu-desktop
```Using these commands, you can switch from PulseAudio to a pure ALSA setup and back within minutes. Try both setups and see which one works better for you.

---

### Post by manco on 2010-01-08
> **VertexPusher said:**
> One word: PulseAudio.

The good news: If you remove PulseAudio, most of those problems will go away.
How do I remove PulseAudio?  I have 9.10 running on my family's desktop and the audio is sketchy.

---

### Post by leorolla on 2010-01-08
> **VertexPusher said:**
> ```
sudo apt-get install gstreamer0.10-alsa gnome-alsamixer
sudo apt-get purge gstreamer0.10-pulseaudio vlc-plugin-pulse pulseaudio
```Then log out and log in again. Use alsamixer to adjust your sound card volume levels.

Run this if you want to get PulseAudio back:
```
sudo apt-get install ubuntu-desktop
```Using these commands, you can switch from PulseAudio to a pure ALSA setup and back within minutes. Try both setups and see which one works better for you.

```
sudo apt-get purge gstreamer0.10-pulseaudio
```tells me that it must then remove ubuntu-desktop

That doesn't feel so good. Is it really safe to do it?

I have Ubuntu 9.10

Thanks!

----

About the discussion I agree:

KISS, have everything working Out of The Box.

I didn't study mechanical engineering to drive a car. The same way, I should be able to use Linux without being a hacker.

I use the computer to work, not as a toy.

It is really disappointing to have something working preety well on a given release and being replaced by a beta buggy version on the next one.

I don't mean only sound, but basic stuff like kdvi removed from repos and replaced by something that does not accomplish the same tasks, kile being switched to an officially beta version, karmic-medibuntu skype not working but hardy-medibuntu skype doing great, wireless driver working out of the box during 3 consecutive releases and then broken on Karmic, and so on...

---

### Post by Shazaam on 2010-01-08
"tells me that it must then remove ubuntu-desktop"
ubuntu-desktop is a metapackage. If you remove it you will only have a problem when you upgrade Ubuntu versions (Hardy to Intrepid, Intrepid to Jaunty, Jaunty to Karmic, etc). If you plan on upgrading versions in the future, reinstall ubuntu-desktop before you upgrade. That said, I have been removing ubuntu-desktop (to get rid of apps/services that I don't use/want) without any ill effects during day to day use since Dapper.

[https://help.ubuntu.com/community/MetaPackages](https://help.ubuntu.com/community/MetaPackages)

---

### Post by Bakudan00 on 2010-01-08
> I call BS.

Rhythmbox uses GStreamer, not ALSA. You forgot to replace gstreamer0.10-pulseaudio with gstreamer0.10-alsa, so Rhythmbox, Totem etc. locked up trying to connect to the missing PulseAudio daemon. In other words: You did not follow my instructions.

Sorry about your mic not working, but if it doesn't work with ALSA, your only remaining option is OSS4. Good luck with that.I got sound back. All I had to do after reinstalling was reboot. >_<

But no, I did exactly what you said, and to double check I did it again, and restarted this time. No sound at all -- except for in my headphones. Sound levels in alsamixer are all high and unmuted. In System > Preferences > Sound all I get is a dialog that says, "Waiting for sound system to respond." Oh, and my mic works. -_-

Suggestions, before I screw it all and go back to PulseAudio defeated? I don't think I'm comfortable with getting rid of ubuntu-desktop.

---

### Post by Linktwo on 2010-01-09
(I moved from windows 3 days ago, and I still like Ubuntu despite the problems with video and sound)
Thank you for your support so far. My sound files can play without any problems so far.
In this process I lost my sound default volume controller,<<< related to this discussion. My question is: Where do I find another one that can be directed thought a digital volume wheel? I think I might done something wrong with the directions. My temporarily solution is  using the GNOME ALSA-mixer, I would not recommend this unless you can't control your volume.

Thanks in advance!

---

### Post by VertexPusher on 2010-01-09
> **Bakudan00 said:**
> No sound at all -- except for in my headphones. Sound levels in alsamixer are all high and unmuted.
Enter this command in a terminal window:
```
amixer
```
This will print a list of all available mixer controls. Send me the list, and I'll figure out which mixer setting needs to be changed. Usually there is a headphones jack sense switch which turns the speakers off when headphones are plugged in. Some people see this as a feature, not a bug, but if there is a way to switch it off, we'll find it.

> In System > Preferences > Sound all I get is a dialog that says, "Waiting for sound system to respond."
This is normal. The sound control panel is in fact a control panel for PulseAudio. It is unable to control ALSA settings. Use alsamixer or gnome-alsamixer for that.

> Oh, and my mic works. -_-
See?

One thing is 100% certain: If sound does not work with ALSA alone, it won't work with PulseAudio either because PulseAudio uses ALSA to access the sound card. It cannot use any sound card features unless they are exposed by ALSA in the first place.

> I don't think I'm comfortable with getting rid of ubuntu-desktop.
I don't think you understand the purpose of ubuntu-desktop.

---

### Post by Telecaster72 on 2010-01-09
> **Bakudan00 said:**
>  I swear, after I fix this, I'm just going to leave it alone!

If i got a penny everytime i said this and later wished i would have followed my own advice...;)

---

### Post by Bakudan00 on 2010-01-09
@VertexPusher

Hmm... I followed the instructions a third time in order to send you the output of amixer under ALSA, and now everything works perfectly. So far all my audio problems - no mic, awful game sound, everything - are gone. This suggests I *did* do something wrong before, twice, but I honestly have no clue where. Oh well, many, many thanks for your help since I've been pulling my hair out over this stuff since Nov. when I installed Ubuntu for the first time.

I'm going to bookmark this in case the PulseAudio bugs aren't resolved in April with Ubuntu 10.

---

### Post by cesium62 on 2010-01-09
@vertex pusher

Thanks for the clear concise instructions.  I now have sound output.

I still don't have a microphone working.  I debug this using skype, make a test call, echo server.  But that's kinda slow.  What's a better way to quickly test the mike after making a change?  Also, what are the troubleshooting steps to figure out why the mike isn't working?  I've been to the alsa mixer panel and unmuted everything and moves the sliders around.  I checked the microphone mute on my headphones.

---

### Post by cesium62 on 2010-01-09
For my own reference, since I run into these problems once a quarter since I make my three kids use Linux as well as myself, and I'm the sysadmin:


I removed pulseaudio per VertexPushers instructions and logged out and in.

I reinstalled pulseaudio per VertexPushers instructions and logged out and in.

I right-clicked on the speaker icon at the top-left of the gnome panel, and opened preferences.  I selected the 'input tab', and set my microphone to microphone 2.  (I used the Applications>Sound>Recorder [check spelling] application to test which setting would record sound.)  I played around with the microphone amplification and output levels using the recorder to find a good gain with low hiss.  (I set amplification to about 2x unamplified, and I set output level to about 80% of the dotted line.)

I started skype and set the sound options to reference pulse.  Clicked on Apply.  Used 'generate test sound' to verify basic settings.  I disabled "allow skype to set my mixer levels".  Used 'generate test call' to prove all settings.

I quit skype, logged out, logged into my wife's account and set up skype again.


[This is the short version.  I dicked around with a bunch of other stuff, but this appears to be the important path.  I think I personally prefer to use pulseaudio [there are aspects of the control panel I like better].  Removing it and reinstalling it seemed to help, and I very much appreciate VertexPushers posting on the bottom of page 2 of this thread.  I believe it is very important that only one user account run skype at a time; I had problems when it was running under multiple accounts.]

---

### Post by Papabravo on 2010-01-09
I had sound on my system with the preinstalled Ubuntu 9.04.  It went away after I upgraded to Ubuntu 9.10.  I've been following this thread with no success

I cannot run eithe alsamixer or amixer.  What I get is the following

amixer: Mixer attach default error: No such file or directory

Never mind,  I blew away the upgrade to karmic and returned to jaunty

---

### Post by Goklagie on 2010-01-10
Hello guys,

i need a bit of help right here...
Once upon a time, i was a happy user of an 8.04lts desktop. At my first attempt to upgrade to 8.10 the network manager wasn't working so i stayed happy with 8.04 until yesterday.

Unfortunately i became jealous of the shiny stuff 9.10 has and i attempted 3 consecutive:o:o upgrades. I really am thrilled that everything apart from sound, an ntfs automount setting and static ip settings works really fine. The first two stopped working since 9.04.

Right now i have sound from amarok and vlc by manually setting them to alsa. Due to the fact that gstreamer-properties is set to alsa, totem, rythmbox and flash aren't working. I followed VertexPusher's steps with a slight difference. At first i did //sudo apt-get remove gstreamer... vlc-plugin..  instead of purge but i don't believe it makes any difference.

I would appreciate any help because i am really desperate...

---

### Post by kellemes on 2010-01-10
Never had problems with sounds on my desktop.. Well, not with Karmic anyway.

---

### Post by radard on 2010-01-10
Hi all,

I also had a problem with sound, as soon as I had two apps which needed to use the sound card.

The solution proposed in post [#20]("http://ubuntuforums.org/showpost.php?p=8630967&postcount=20")
worked well for me.

I also learned on post [#23]("http://ubuntuforums.org/showpost.php?p=8631987&postcount=23") that I have to reinstall ubuntu-desktop before my next Ubuntu upgrade.

Thanks all and a special one to VertexPusher and Shazaam :)

---
I have a Dell Mini 12'

---

### Post by cyboreal on 2010-01-10
I have an Acer Aspire Timeline 1810t and I tried the method in post #20:
```
sudo apt-get install gstreamer0.10-alsa gnome-alsamixer
sudo apt-get purge gstreamer0.10-pulseaudio vlc-plugin-pulse pulseaudio
```
I logged out and in and both Skype and Sound Recorder were finally able to pick up input. It was a little scratchy and not very loud, but usable.

The problem now is that the system tray icon for volume control is gone and the Fn-UpArrow/Fn-DownArrow volume control does not work. Apparently they are tied pretty tightly to PulseAudio. Any clues as to how to get the volume control applet and hotkeys working again?

---

### Post by Jammet2 on 2010-01-10
Is it pulseaudio as well, that's causing these annoying problems with sound in Vice (the C64 emulator)? Sound's stuttering and then drops out. The current Teamspeak 3 beta also bombs out after a while of testing the mic.

---

### Post by ratcheer on 2010-01-10
I had a minor sound problem when I upgraded from 9.04 to 9.10. After some poking around, all I had to do was raise the PA volume, which for some reason was defaulted to zero. The painful thing was that I had to do this for every individual application that uses sound. I thought this was very weird.

But, I agree that sound seems to be the greatest problem for the most users in Karmic. The standard sound configuration is very confusing because so many components interact with each other. Specifically, Pulse Audio on top of ALSA. Both sets of components have to be configured just so for sound to work.

To add to the confusion, there is also OSS.

I wish I could understand all of this stuff and learn how to confidently configure my setup for the "best" way to do things. But, I am afraid that it would be next to impossible to even determine what that would be. "Pulse Audio is the future." "No, ALSA is better." "No, no. You should ditch all that and use OSS."

????????????????

Tim

---

### Post by Goklagie on 2010-01-11
> **Goklagie said:**
> Hello guys,

i need a bit of help right here...
Once upon a time, i was a happy user of an 8.04lts desktop. At my first attempt to upgrade to 8.10 the network manager wasn't working so i stayed happy with 8.04 until yesterday.

Unfortunately i became jealous of the shiny stuff 9.10 has and i attempted 3 consecutive:o:o upgrades. I really am thrilled that everything apart from sound, an ntfs automount setting and static ip settings works really fine. The first two stopped working since 9.04.

Right now i have sound from amarok and vlc by manually setting them to alsa. Due to the fact that gstreamer-properties is set to alsa, totem, rythmbox and flash aren't working. I followed VertexPusher's steps with a slight difference. At first i did //sudo apt-get remove gstreamer... vlc-plugin..  instead of purge but i don't believe it makes any difference.

I would appreciate any help because i am really desperate...


Hell yeah. A reset of gconf was the big step! I can hear now.

---

### Post by toddr on 2010-01-11
Thanks Vertexpusher. That did the trick!:D

---

### Post by sphyg04 on 2010-01-11
> **VertexPusher said:**
> Enter this command in a terminal window:
```
amixer
```This will print a list of all available mixer controls. Send me the list, and I'll figure out which mixer setting needs to be changed. Usually there is a headphones jack sense switch which turns the speakers off when headphones are plugged in. Some people see this as a feature, not a bug, but if there is a way to switch it off, we'll find it.


This is normal. The sound control panel is in fact a control panel for PulseAudio. It is unable to control ALSA settings. Use alsamixer or gnome-alsamixer for that.


See?

One thing is 100% certain: If sound does not work with ALSA alone, it won't work with PulseAudio either because PulseAudio uses ALSA to access the sound card. It cannot use any sound card features unless they are exposed by ALSA in the first place.


I don't think you understand the purpose of ubuntu-desktop.
So, I get sound. But sound disappears after a suspend. Any way to fix this? After a restart, sound is back, but I don't wanna have to restart everytime my computer comes back from suspend!

$ amixer
Simple mixer control 'Master',0
  Capabilities: pvolume pswitch pswitch-joined
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 74
  Mono:
  Front Left: Playback 74 [100%] [0.00dB] [on]
  Front Right: Playback 74 [100%] [0.00dB] [on]
Simple mixer control 'PCM',0
  Capabilities: pvolume
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 245 [96%] [-2.00dB]
  Front Right: Playback 245 [96%] [-2.00dB]
Simple mixer control 'IEC958',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'IEC958 Default PCM',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'IEC958',1
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'Digital',0
  Capabilities: cvolume
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 120
  Front Left: Capture 117 [98%] [28.50dB]
  Front Right: Capture 117 [98%] [28.50dB]
Simple mixer control 'Docking Mic',0
  Capabilities: volume pswitch
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 80
  Front Left: 0 [0%] [-74.00dB] Playback [off]
  Front Right: 0 [0%] [-74.00dB] Playback [off]
Simple mixer control 'External Mic',0
  Capabilities: volume pswitch
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 80
  Front Left: 0 [0%] [-74.00dB] Playback [off]
  Front Right: 0 [0%] [-74.00dB] Playback [off]
Simple mixer control 'Internal Mic',0
  Capabilities: volume pswitch
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 80
  Front Left: 0 [0%] [-74.00dB] Playback [off]
  Front Right: 0 [0%] [-74.00dB] Playback [off]

---

### Post by cebif on 2010-01-12
> **kblandfo said:**
> I have the same problem.  No sound... I had sound and then suddenly one day, much to my dispair nothing... not even a crackel.  The question is how do you remove gstreamer0.10-pulseaudio, vlc-plugin-pulse, pulseaudio and then how do you install gstreamer0.10-alsa, gnome-alsamixer?  Bit of a novis with Linux ams I.  Thanks for the help.
Just do as vertexpusher has shown:
```
sudo apt-get install gstreamer0.10-alsa gnome-alsamixer
sudo apt-get purge gstreamer0.10-pulseaudio vlc-plugin-pulse pulseaudio
```
Copy and paste those commands into gnome terminal. Press enter after each. You will be asked for your login password and need to have root privileges with your account.
After that logout then login. Open System, preferences, Multimedia Systems Selector and choose alsa for default output and input.
I myself have only partial success.
What is now working is openal sound in flightgear. What is not working is my microphone in skype and sound recorder.
When I open soundrecorder and click on record button this message comes up:
"Could not capture using the 'Voice, Lossless' audio profile. Please verify its settings.
You may be missing the necessary plug-ins".

---

### Post by saharian on 2010-01-12
Hi everyone.
i have just installed ubuntu 9.10  (64 bit). I know very little about the OS.
my microphone is not working.  motherboard DG965WH, Processor: intel pentium D.
please anyone tell me how to make my mic work.

---

### Post by leorolla on 2010-01-12
> **saharian said:**
> Hi everyone.
i have just installed ubuntu 9.10  (64 bit). I know very little about the OS.
my microphone is not working.  motherboard DG965WH, Processor: intel pentium D.
please anyone tell me how to make my mic work.

Hi Saharian,

If you open a thread explaining what is not working you should get specific help for your case.

Good luck :-)

---

### Post by imakeart on 2010-01-14
I'm not sure if my sound issue is related to what everyone else is experiencing, but I wanted to go ahead and throw it into the mix.

I installed Ubuntu 9.10 as a fresh install on my Acer Aspire 3680. Everything worked perfectly (I loves Ubuntu!). But then I started having a small issue with the sound in Firefox.

Sound works in everything else, playing music, watching videos from files on my laptop. But going to Youtube, nothing.

But...if I reboot then the sound comes back - till it goes out again. I'm wondering if this has something to do with my Power Management settings; which I have set to put the laptop to sleep after 1 hour of inactivity. (My model of Acer has heat issues so I like to have it sleep.)

Anyone experience anything like this or have heard about it?


Thanks!

---

### Post by utannheim on 2010-01-14
I have removed pulse now and ALSA works fine. The only problem that remains for me is the internal laptop mic works, but when I plug in a headset the internal mic keeps recording and nothing is recorded via the headset. I was playing around with alsamixer to try to find the right settings to change this around but I have not been successful. I know that reducing the volume or muting Internal 1 stops the laptop mic from recording. Does anyone have tips or suggestions on getting the headset mic working. (Oh and the headset does work, just tested it on another machine). 

Thanks in advance.

---

### Post by manco on 2010-01-14
> **VertexPusher said:**
> ```
sudo apt-get install gstreamer0.10-alsa gnome-alsamixer
sudo apt-get purge gstreamer0.10-pulseaudio vlc-plugin-pulse pulseaudio
```Then log out and log in again. Use alsamixer to adjust your sound card volume levels.

Run this if you want to get PulseAudio back:
```
sudo apt-get install ubuntu-desktop
```Using these commands, you can switch from PulseAudio to a pure ALSA setup and back within minutes. Try both setups and see which one works better for you.
Thanks! ALSA works great!

---

### Post by abrazafi on 2010-01-14
Hi,

Running desktop kubuntu 9.10. Spent a lot of time to figure out why youtube/dailymotion does not have any sound coming out of my USB headset.
Tried many instructions from:
[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)
without any success. So I need help.

Herewith my sound devices

> cat /proc/asound/modules
1 snd_usb_audio
2 saa7134_alsa
3 snd_hda_intel

I want to use the above "snd_usb_audio" for Youtube/dailymotion. Note that the sound is working fine with amarok and skype (separatly or at the same time).
I am using firefox version 3.5.6
Adobe Flash player version 10,0,42,34
Samething happened with the browser konqueror

any suggestion will be welcomed and many thanks,

Abdon.

====================== herewith some outputs from my system

I'm using Pentium P5W Deluxe HD motherboard with the USB Logitech Headset.

> uname -a
Linux antec 2.6.31-17-generic #54-Ubuntu SMP Thu Dec 10 16:20:31 UTC 2009 i686 GNU/Linux

> aplay -l

**** List of PLAYBACK Hardware Devices ****
card 1: Headset [Logitech USB Headset], device 0: USB Audio [USB Audio]
Subdevices: 0/1
Subdevice #0: subdevice #0
card 3: Intel [HDA Intel], device 0: ALC882 Analog [ALC882 Analog]
Subdevices: 1/1
Subdevice #0: subdevice #0
card 3: Intel [HDA Intel], device 1: ALC882 Digital [ALC882 Digital]
Subdevices: 1/1
Subdevice #0: subdevice #0

---

### Post by dalee on 2010-01-14
> **cyboreal said:**
> I have an Acer Aspire Timeline 1810t and I tried the method in post #20:
```
sudo apt-get install gstreamer0.10-alsa gnome-alsamixer
sudo apt-get purge gstreamer0.10-pulseaudio vlc-plugin-pulse pulseaudio
```
I logged out and in and both Skype and Sound Recorder were finally able to pick up input. It was a little scratchy and not very loud, but usable.

The problem now is that the system tray icon for volume control is gone and the Fn-UpArrow/Fn-DownArrow volume control does not work. Apparently they are tied pretty tightly to PulseAudio. Any clues as to how to get the volume control applet and hotkeys working again?

Hi,

Yup switching to ALSA will kill the tray button and any keyboard control. But I was able to regain some control with the key board by using this little tutorial I found around here. I didn't save the attribution, (I wish I had), but to who ever figured this out Thanks!

To get audio volume control: "But what I did for volume control is to go to System > Preferences > Keyboard shortcuts, and then made a Volume Up shortcut (add button), with the command line "amixer -q set PCM 3+" (you can also use Master instead of PCM.. I used PCM because it went all the way down to mute, unlike Master). Then make another shortcut, Volume Down, with the command "amixer -q set PCM 3-"... again, you can change to Master if you want.

edit: You can use any keys you like, but I used XF86AudioRaiseVolume and XF86AudioLowerVolume which is basically "Fn+Left" and "Fn+Right" on my laptop.

It doesn't show the volume in the gnome panel, but you can still see it by running "amixer". It should change under PCM (or Master, whichever).
edit: There is probably a non-GUI way to do this".

dalee

---

### Post by alexfish on 2010-01-14
hi

I have install the pulse audio device chooser, now having great fun with pulse, don't see the point of removing pulse . its a sound server for your sound system , usually using Alsa as the core

so I have voted

---

### Post by cebif on 2010-01-15
> **imakeart said:**
> I'm not sure if my sound issue is related to what everyone else is experiencing, but I wanted to go ahead and throw it into the mix.

I installed Ubuntu 9.10 as a fresh install on my Acer Aspire 3680. Everything worked perfectly (I loves Ubuntu!). But then I started having a small issue with the sound in Firefox.

Sound works in everything else, playing music, watching videos from files on my laptop. But going to Youtube, nothing.

But...if I reboot then the sound comes back - till it goes out again. I'm wondering if this has something to do with my Power Management settings; which I have set to put the laptop to sleep after 1 hour of inactivity. (My model of Acer has heat issues so I like to have it sleep.)

Anyone experience anything like this or have heard about it?


Thanks!
I'm not experiencing anything exactly like this but watching youtube uses adobe flash player in firefox. Have you tried seeing if anything else that uses this will play when youtube stops. For instance:
[http://www.nasa.gov/multimedia/nasatv/](http://www.nasa.gov/multimedia/nasatv/)
On this page you can also try other players to see if they will play the same if adobe flash stops. For playing windows mediaplayer encoded you could use Totem (Movie Player) if you've got all the right codecs downloaded.
If these work when adobe flash doesn't, I would say its more an adobe flash or firefox problem. If adobe flash works at nasa tv, then it is probably a firefox problem.

---

### Post by pirron on 2010-01-15
Thanks VertexPusher I follow your instructions on #20 and finally the sound works!

---

### Post by imakeart on 2010-01-16
> **cebif said:**
> I'm not experiencing anything exactly like this but watching youtube uses adobe flash player in firefox. Have you tried seeing if anything else that uses this will play when youtube stops. For instance:
[http://www.nasa.gov/multimedia/nasatv/](http://www.nasa.gov/multimedia/nasatv/)
On this page you can also try other players to see if they will play the same if adobe flash stops. For playing windows mediaplayer encoded you could use Totem (Movie Player) if you've got all the right codecs downloaded.
If these work when adobe flash doesn't, I would say its more an adobe flash or firefox problem. If adobe flash works at nasa tv, then it is probably a firefox problem.

Thanks for replying cebif. No problems watching any of the media. The problem is intermittent, so I know it's difficult to pinpoint what might be wrong. 

And like I said, when the problem does occur if I reboot the laptop it fixes itself, at least temporarily. :???:

---

### Post by alldaylong on 2010-01-16
hey switching to alsa from pulseaudio fixed EVERYTHING. Thank you so much.

For anyone having problems with skype on a laptop with karmic - just do what is advised on page 1 of this thread, and then run alsamixer and you will be all set.

Thanks so much!

---

### Post by munchkinmunchkin on 2010-01-16
My sound is fine on 9.10 but I did have a few sound hiccups with 8.04LTS.

The volume and mute buttons on my keyboard never worked right in 8.04 but work fine in 9.10.

---

### Post by imakeart on 2010-01-16
I've discovered another issue with my sound. After installing I noticed that the sound volume was too low, so I went into Sound Preferences and moved the slider over to increase the output volume.

This worked, but if I then adjust the volume slider from the panel it resets the volume back down in Sound Preferences. I have to change it again to have adequate volume.

It's not a huge problem, but there are times when I have to turn the volume down and would like to be able to then turn it back up without the extra steps.

---

### Post by Kat of Zion on 2010-01-18
I vote yes on this.  Granted, I am running the 32 bit version of Karmic.  Does that make a difference?

Things I  cant get to work:
[LIST]
[*]Audio on embedded video will only play from Firefox.  Opera, Konqueror, and Flock only let me see the visuals from sites like Ustream, YouTube, Daily Motion, etc...
[*]Cant record from my webcam except visuals.  Audio will not record from front mic (internal webcam and internal mic).
[*]Cant do voice chat in SecondLife (but that may be more Lindens' issue than mine).
[/LIST]

---

### Post by Kat of Zion on 2010-01-23
Ugh.  Karmic's sound issue has been the bane of my existance.  I have a slew of problems despite that Pulse audio is not set to the highest preference.  I have the HDA Intel

My biggest problem seems to be with recording sound.  I have a front mic and I can hook up an external one.  Same goes for my webcamming.  Sometimes an external one is better.  Cheese (and any program like it) cannot record anythign but visual on a webcam.  I cant stream audio by webcam either.

Not sure what to do.

---

### Post by ynaidoo on 2010-01-25
Thanks Vertexpusher, your instructions worked for my laptop. I spent many hours trying various things as suggested by others...until I tried your instructions.

---

### Post by ratcheer on 2010-01-26
I got quite a few PulseAudio-related updates, yesterday. Does anyone know what was fixed or improved?

Tim

---

### Post by pmlxuser on 2010-01-26
I removed Karmic from my acer aspire one 750h because of the sound problem,I tried the poulseAudio and instaling alsa, worked fine but i didn't like the fact that my fn + key stoped working on reducing or increasing sound....

will hope 10.04 will be better, i will install that one.

---

### Post by cebif on 2010-01-27
> **ratcheer said:**
> I got quite a few PulseAudio-related updates, yesterday. Does anyone know what was fixed or improved?

Tim
I tried those updates but they never solved any problems. I still cannot use the microphone with sound recorder and skype. flightgear and second life sound is still intermittent or scratchy.
I think the updates were meant to solve a memory leak. I was not 100% certain what a memory leak is but did a search for anyone interested:
[http://en.wikipedia.org/wiki/Memory_leak](http://en.wikipedia.org/wiki/Memory_leak)

---

### Post by VertexPusher on 2010-01-27
> **pmlxuser said:**
> hope 10.04 will be better
It won't.

Removing PulseAudio from Ubuntu will always be possible, but if you want a non-crippled Gnome install out of the box, your only option is Debian.

---

### Post by Yellow Pasque on 2010-01-27
> **pmlxuser said:**
> worked fine but i didn't like the fact that my fn + key stopped working on reducing or increasing sound...

> Removing PulseAudio from Ubuntu will always be possible, but if you want a non-crippled Gnome install out of the box, your only option is Debian.

Get the reconfigured gnome packages here and lose the crutches ;) [https://launchpad.net/~dtl131/+archive/ppa](https://launchpad.net/~dtl131/+archive/ppa)

> I got quite a few PulseAudio-related updates, yesterday. Does anyone know what was fixed or improved?
Changelogs are often informative. Update manager displays them nicely (if it can retrieve them) and they're also accessible in Synaptic with a few clicks. Failing that: [http://changelogs.ubuntu.com/changelogs/pool/main/p/pulseaudio/pulseaudio_0.9.19-0ubuntu4.1/changelog](http://changelogs.ubuntu.com/changelogs/pool/main/p/pulseaudio/pulseaudio_0.9.19-0ubuntu4.1/changelog)

---

### Post by trustnobody13 on 2010-01-27
Judging by the results of the poll i must be the few that has never had a problem with the sound in Ubuntu since i started using it way back in the days of 7.10.

---

### Post by leorolla on 2010-01-27
> **alexfish said:**
> hi

I have install the pulse audio device chooser, now having great fun with pulse, don't see the point of removing pulse . its a sound server for your sound system , usually using Alsa as the core

so I have voted


It happened with me too.

After removing Pulse Audio everything as fine...
But... I dind't have my Fn+Up increasing volume, nor the audio control on the panel. Amixer is horrible and Gnome mixer is akward. I cound't play sound from simultaneous applications... so talking through skype to a friend and watching a youbute video to comment with that friend was not possible.

Then I tried the following, just for the sake of it.

Install everything related to PulseAudio: pavumeter paman paprefs padevchooser etc.
Reboot.
Open Device Chooser, Configure Local Server, Simultaneous Output, there was only one item "Add virtual outpout...", I checked it.
Open either Volume Control or Sound Preferences and choose Internal Audio, not Simultaneous Output. Play with other volume controls, up and down, mute and unmute.

For my surprise, it worked. Including the newest skype. Now I have full control on the sound, with good quality, I can play multiple sounds perfecly, and I can even direct the output to the input so I can either record it or stream music to my frineds through skype.

One problem: my internal mic is no longer recognized, but it happened both with ALSA and PulseAudio, even when the latter is removed. (Edit: surprising enough it is actually the case that the Input source is automatically changing from internal to external mic, with the exception that for Skype the internal one is not working)

---

### Post by VertexPusher on 2010-01-27
The most convenient way to make PulseAudio work as expected is to lower your expectations. If you take a closer look at the poll, you'll notice that the author of a multi-page PulseAudio repair tutorial voted "No, the sound works perfectly!".

I guess this is what psychologists call the "Stockholm syndrome".

---

### Post by leorolla on 2010-01-27
> **VertexPusher said:**
> The most convenient way to make PulseAudio work as expected is to lower your expectations. If you take a closer look at the poll, you'll notice that the author of a multi-page PulseAudio repair tutorial voted "No, the sound works perfectly!".

I guess this is what psychologists call the "Stockholm syndrome".

multi-page PulseAudio repair tutorial ?

Could you post the link?

Thanks! :-)

---

### Post by Robbyx on 2010-01-27
I gave up on Pulse because I could not keep the settings from one reboot to the next. I would get it to work and then after a system suspend there would be no sound or mic working.

I went back to alsa and now skype works consistently but I can not get the Ringing button in the sound devices option to work. Mic and Speakers are set to the headset. Ringing I wanted to go to the monitor speakers. I think I know the correct device name. Any ideas to make the ringing work?

---

### Post by VertexPusher on 2010-01-28
> **Robbyx said:**
> I went back to alsa and now skype works consistently but I can not get the Ringing button in the sound devices option to work. Mic and Speakers are set to the headset. Ringing I wanted to go to the monitor speakers. I think I know the correct device name. Any ideas to make the ringing work?
"aplay -l" will return the list of sound cards available for playback. If card 0 is your main sound card and card 1 is your USB headset, the following PCM names should work for Skype:

Voice capture: "plughw:1"
Voice playback: "plughw:1" or "plug:dmix:1" (the latter allows shared access)
Ringing: "default" (equivalent to "plug:dmix:0" unless you have redefined it)

---

### Post by Telecaster72 on 2010-01-28
I never had an issue with sound since i started using linux with Edgy, i have done some distro-hopping (Zenwalk, Lenny, Mint, PCLinuxOS), never had sound issues there either, if it wasn't for pulse audio i would be pretty happy with Karmic, but now all of a sudden my music randomly skips and stutters, sometimes goes almost quiet except for some weird low volume static noise for a minute and returns. This is unacceptable as i use my computer as my main music source except for my vinyl records ;-). If the Ubuntu devs want to experiment with pulse, why dont leave the default to ALSA (that works and is well tested and debugged) and make it optional to install Pulse for those adventurous enough to try?

Ofcourse i could remove Pulse and deal with eventual problems that arises, spend a night or two. But i dont have the time or the will to try different workarounds when they would not be neccecary if ALSA was default.
IF Ubuntu aspires to be the common mans OS, why include experimental software that completely hijacks the system, is complicated (for the "windows refugee") to remove and change. If Ubuntu wants to "Just Work", why not just keep to what just works?

Pulse Audio and it's possibilities is interesting and may well prove to be great once it is stabilized, but as i mentioned earlier i cant understand why it is the default in Ubuntu when clearly a lot of people have major problems with it. Sound is an essential part in a system and should "just work (tm)", no workarounds needed.

Sorry for the rambling ;-)

---

### Post by Robbyx on 2010-01-28
> **VertexPusher said:**
> "aplay -l" will return the list of sound cards available for playback. If card 0 is your main sound card and card 1 is your USB headset, the following PCM names should work for Skype:

Voice capture: "plughw:1"
Voice playback: "plughw:1" or "plug:dmix:1" (the latter allows shared access)
Ringing: "default" (equivalent to "plug:dmix:0" unless you have redefined it)

Thank you. I need a bit more help if you do not mind.

```
rob@rob-desktop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC888 Digital [ALC888 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: default [C-Media USB Headphone Set  ], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
rob@rob-desktop:~$ 

```

I can see pcm in the volume control but that is one of the sliders for the device such as the HDA Intel (Alsa Mixer)


My sound devices in skype do not show PCM as an option. How do I use it?

Robin

---

### Post by VertexPusher on 2010-01-28
> **Robbyx said:**
> My sound devices in skype do not show PCM as an option. How do I use it?
Did I say you should look for an option called "PCM"? I don't think so.

---

### Post by Robbyx on 2010-01-28
> **VertexPusher said:**
> Did I say you should look for an option called "PCM"? I don't think so.

I agree. Unfortunately as set up,  none of the names you suggested  appear in the skype available devices. Is there a way to include them?

Robin

---

### Post by Robbyx on 2010-01-29
> **Robbyx said:**
> I agree. Unfortunately as set up,  none of the names you suggested  appear in the skype available devices. Is there a way to include them?

Robin

I now understand a bit more. It seems the make a test sound button  will not come out of the HDA intel ALC888 Analog device, if the mic and speakers are set to the USB headphone set. Does anyone know a work around this block?

---

### Post by Robbyx on 2010-01-29
I wonder if anyone has a solution to this additional problem:

I put my computer regularly into suspend mode. When it wakes up the ALSA sound settings for my USB headphone set are changed so that the mic is muted. Each time it restarts from suspend I have to switch on the mic sound. Tedious, especially if it coincides with an incoming  skype call.

---

### Post by mrz80 on 2010-02-02
I am just about ready to chew nails and spit staples!  I had no audio on a fresh 9.10 install, and so did what I always do when confronted with a recent Ubuntu with sound problems - I attempted to strip pulseaudio out.  Herein lies a tale of woe...

[edit - tale of woe stripped... found the problem... it was a stale .asoundrc config file accidentally copied over from my previous machine that referenced pulse.]

---

### Post by spiritofelric on 2010-02-02
Although i have some sound problems... overall... it works.  That's all i need.  I'm impressed it picked it up on install.

I'm fine with doing some tweaking for my one in a million sound card.  It's would be helpful to have a sound manual for Ubuntu rather than expecting it to work for every card automatically.

---

### Post by Ric_NYC on 2010-02-03
"Yes, there are problems with the sound"... 201..** 82.38%**


A lot of people.

"You are not alone".

---

### Post by monsoongroover on 2010-02-03
Didn't work. I've tried many fixes gleaned from the forums. None of them work.

---

### Post by scouser73 on 2010-02-03
Sound works perfectly for me on Karmic.

---

### Post by The Toxic Mite on 2010-02-03
I don't have any problem with the sound in Karmic. I would prefer to have it on the sound card than on the integrated chip, but I don't really care.
 
:>

---

### Post by dabrowsa on 2010-02-03
Kubuntu 9.10
pulse expunged
intel HDA card

Sound now mostly works correctly.  Just one problem: I can't find a good way to get the line-in to play through my speakers.  Is there a way to set up my asoundrc to do this?  Would aloop help?

Two methods that almost work:

(1) Running jack.  I can use jack_connect to hook up the line-in to the line-out.  But this breaks sound in my web browsers.

(2) command line pipe:
arecord -f cd -D hw:0 | aplay -f cd
Works but latency is unacceptable.

Any suggestions?

---

### Post by Kixtosh on 2010-02-07
I recently installed Karmic Koala in the two older laptops in my signature. The results were:

_For the Toshiba Portégé_, no issues whatsoever, including a Netgear PC Card wireless card and sound. In fact, the only thing that remains for me to fix is how to use an external LCD monitor.

_For the Dell Latitude CPi_ series laptop, everything worked with no issues, except for sound. I had a horrible clicking noise every time a sound was supposed to play. Sometimes you could still hear the correct sound being played in the background, sometimes, just the clicking. I described my issue (and the solution) in this thread:

 [http://ubuntuforums.org/showthread.php?t=1391973](http://ubuntuforums.org/showthread.php?t=1391973)

In the end, I solved it (almost entirely, but not quite) in this way:

1) Updated ALSA to 1.0.22.
2) Removed PulseAudio: *sudo apt-get purge gstreamer0.10-pulseaudio vlc-plugin-pulse pulseaudio*
3) Reinstalled PulseAudio: [I]sudo apt-get install ubuntu-desktop

[/I]To be fair to Karmic Koala, I also tried installing 8.04 **Hardy Heron** (since it's  the current LTS release) and had the **same problem**, so in my case, this is not 9.10 specific. However, I had **no such issues **using** Puppy Linux** 4.3.1.

The only thing that remains to be solved now on this machine is the same clicking sound, which now only occurs during the "ubuntu" splash screen when first starting up. As soon as the desktop first appears, the default musical "jungle" theme (I'm not sure of the "official" title for this) plays normally, and so does everything else thereafter.

---

### Post by l-x-l on 2010-02-07
My problems with sound only happen when I upgrade kernels. So when I find a kernel where sound works perfectly I decided to stick with it and block all kernel updates/upgrades.

---

### Post by shortsightedPenguin on 2010-02-08
> **VertexPusher said:**
> ```
sudo apt-get install gstreamer0.10-alsa gnome-alsamixer
sudo apt-get purge gstreamer0.10-pulseaudio vlc-plugin-pulse pulseaudio
```Then log out and log in again. Use alsamixer to adjust your sound card volume levels.

Run this if you want to get PulseAudio back:
```
sudo apt-get install ubuntu-desktop
```Using these commands, you can switch from PulseAudio to a pure ALSA setup and back within minutes. Try both setups and see which one works better for you.

I dont get what you mean by switching from PulseAudio to a pure ALSA setup?

I have done the former steps. It works. But alsamixer doesn't allow me to adjust my volumes. It's just a piece of empty window box when I open it. Now, I have sound playing without control volume.

Any fix for this?

---

### Post by Robbyx on 2010-02-08
> **shortsightedPenguin said:**
> I dont get what you mean by switching from PulseAudio to a pure ALSA setup?

I have done the former steps. It works. But alsamixer doesn't allow me to adjust my volumes. It's just a piece of empty window box when I open it. Now, I have sound playing without control volume.

Any fix for this?


Applications--sound and video. Right click volume control and add launcher to panel.

---

### Post by ETbluez on 2010-02-08
Switched to Xubuntu and loving it.the problem that came up  sound was muted on every boot .removed PulseAudio problem solved. Thank's _Vertexpusher._

---

### Post by ETbluez on 2010-02-08
> **ETbluez said:**
> Switched to Xubuntu and loving it.the problem that came up  sound was muted on every boot .removed PulseAudio problem solved. Thank's _Vertexpusher._
I had to reinstall pulseaudio cause without it the sound in a game im playing was crackling
Think i can live with mute on boot. game is  Rise of the triad

---

### Post by chriswyatt on 2010-02-08
This release (Karmic) fixed a previous sound issue but did introduce one, I eventually found a fix for it though so I'm very happy with sound in Karmic.  With the fix it's great, have had no problems.  I think the only issue is sound being out-of-sync in Flash which has been an issue for me ever since PulseAudio was introduced.

Other than that, great :popcorn:

---

### Post by pickarooney on 2010-02-08
I've run the commands in post #20 but I still get audio in smplayer even though the audio driver is set to pulse there. Is smplayer automatically picking the next available driver/sound engine or has pulse not gone away?

ps has

```

/usr/bin/pulseaudio --start --log-target=syslog

```

---

### Post by Kixtosh on 2010-02-09
Well, I've actually switched my old DELL to Xubuntu 9.10, and my one remaining sound issue (clicking noise during the startup splash screen) has been entirely solved. _I did not have to do anything with Xubuntu to get the sound working_, neither upgrading ALSA nor fiddling around with PulseAudio in the Terminal Console. It worked flawlessly (so far) out of the box.

---

### Post by Mr. Picklesworth on 2010-02-09
> **markbuntu said:**
> Well, there is certainly a lot of dismay about pulseaudio in Ubuntu and some of it is deserved but this dismay has less to do with pulseaudio than many people are willing to accept.

You, sir, are excellent.

"ALSA is good enough and developers should leave mah audio alone" evangelists: try to set up bluetooth audio without studying documentation or manually editing configuration files.

...

Personally, I chose to be patient with PulseAudio and can do it in three clicks. I can keep my music playing on the big speakers and VOIP stuff going through Bluetooth, to boot.

Yes, there has been much breakage. Yes, I, too, suffered an Ubuntu release in which Pulse + ALSA on my sound card just fell to bits and I realize it still happens in Karmic, but it has been totally worth it for the amazing system in place now. I think it's a real shame that people choose to discourage this kind of progress and actively insist on mediocrity. Yes, go ahead and implement the workarounds you personally need to make things happen, but there is no denying that the old audio system *was not going to work* in the long run and was really showing its age as soon as we threw inexperienced end users (and pluggable sound hardware) into the mix.
Some day soon it will all work better and the world will be a happier place because of it.

On a related note, both Maemo 5 (Nokia N900) and the completely mass-market focused WebOS (Palm Pre) use PulseAudio *by choice* and have been quite well regarded with no audio issues that I'm aware of.

---

### Post by Nevon on 2010-02-09
The only sound problems I have experienced in Ubuntu 9.10 are related to zsnes and Flash. The former I have solved (though I can't remember how...). The latter is, of course, impossible for me to do anything about.

---

### Post by unknownencryption on 2010-02-09
i have no sound i need help please!! on xp sound works fine but on ubuntu it doesnt work
i remember someone asking for my lspci's output so here it is

:


00:00.0 RAM memory: nVidia Corporation MCP61 LPC Bridge (rev a1)
00:01.0 ISA bridge: nVidia Corporation MCP61 LPC Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP61 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3)
00:02.1 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3)
00:04.0 PCI bridge: nVidia Corporation MCP61 PCI bridge (rev a1)
00:06.0 IDE interface: nVidia Corporation MCP61 IDE (rev a2)
00:07.0 Bridge: nVidia Corporation MCP61 Ethernet (rev a2)
00:08.0 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)
00:08.1 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)
00:09.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0b.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0c.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:08.0 Multimedia audio controller: Creative Labs SB0400 Audigy2 Value
02:00.0 VGA compatible controller: nVidia Corporation G92 [GeForce 8800 GT] (rev a2)
knives@knives-desktop:~$ 

--------------------------------------------------------
someone please help me out i neeedddddd sounddd ohhh keep in mind im verrryy new to ubuntu

---

### Post by ETbluez on 2010-02-09
> **Kixtosh said:**
> Well, I've actually switched my old DELL to Xubuntu 9.10, and my one remaining sound issue (clicking noise during the startup splash screen) has been entirely solved. _I did not have to do anything with Xubuntu to get the sound working_, neither upgrading ALSA nor fiddling around with PulseAudio in the Terminal Console. It worked flawlessly (so far) out of the box.
I to am useing Xubuntu which this version to me is better than gnome.Iwasn't have a sound problen.just the sound would be at zero on every boot.Xubuntu 9.10 is great.

---

### Post by Kixtosh on 2010-02-09
> **ETbluez said:**
> I to am useing Xubuntu which this version to me is better than gnome.Iwasn't have a sound problen.just the sound would be at zero on every boot.Xubuntu 9.10 is great.I am really liking Xubuntu Karmic also, although I really liked the regular install of Ubuntu too (especially on the Toshiba, where I didn't have the clicking sound on startup). 

Given the very limited resources of the two machines I have installed (in my signature below), Xubuntu is supposed to be the better choice anyway (suited to machines with slower processors and less memory). I can't say that I've noticed a big difference between the two versions in speed however, but I do find Xubuntu easier to feel your way around as a first time user. Many of the menus seem more intuitive to find and navigate correctly to me. Of course, Puppy Linux is most certainly the easiest of them all so far, and had no sound issues either, but I really want a hard drive install and a few more features.

I **do not have muted sound on every start** up on either of my laptops. It remains where I set it prior to shutting down. Either way, I am extremely happy with the performance of these old machines compared to W2K previously, and neither of them have the resources available to use any of the advanced features mentioned in the post above by Mr. Picklesworth. I'm just happy that the wireless cards worked out of the box, which is the only reason I didn't change to Linux in 2005, when I first tried a Live CD of Knoppix 3.7 (on the same machines).

---

### Post by phrostbyte on 2010-02-09
Wine ***KILLS*** sound in Ubuntu. Everything else works fine.

---

### Post by MacDuff on 2010-02-09
Brand New Acer Aspire One. New installation of Ubuntu 9.10 Netbook Remix -- Seemed to work pretty well until I installed Skype.  

I spent 2 frustrating days trying to get the microphone to work with Skype. Acting on advice from users I tried un-installing Pulse, Installing Alsa etc. etc.  I ended up breaking the sound entirely so I did another clean installation and just played around with sound settings.

The solution turned out to be simple and I hope it helps someone else.  I will describe it in detail for newbies that may be having a problem.

Right click on the sound volume icon on the task bar.

Click "sound preferences"

Check all the tabs to make sure that nothing is muted and that all the volume sliders are near the top.

THEN the final thing I found that was necessary was to select the "OUTPUT" tab and move the "Balance" control ALL THE WAY TO THE LEFT.

Skype should now work.  If you have changed the Skype "sound devices" settings, make sure you check the box to "Allow Skype to automatically adjust mixer levels". 

When you are done using Skype, if you want to listen to music in stereo, re-set the output balance on your pulse audio control. 

An annoying bug that I hope gets addressed soon.  From the number of posts on the Internet it has frustrated quite a few people.

---

### Post by pickarooney on 2010-02-09
(following earlier post after copying commands in post 20)
After I rebooted pulse no longer worked in smplayer and pulse was not in ps aux
ALSA doesn't work in smplayer either - I have to use OSS. 

This is not right...

---

### Post by restless on 2010-02-09
I also had problems after the latest kernel update

but this solved it

sudo apt-get install gstreamer0.10-alsa gnome-alsamixer
sudo apt-get purge gstreamer0.10-pulseaudio vlc-plugin-pulse pulseaudio

thanx to VertexPusher

thank you
lor

---

### Post by jdash1 on 2010-02-10
> **phrostbyte said:**
> Wine ***KILLS*** sound in Ubuntu. Everything else works fine.

we are on the same case men

---

### Post by buddyd16 on 2010-02-10
scratch that a alsa or pulseaudio update installed at the same time as my kernel update and is now continually setting all alsamixer channels to mute on reboot. saving the alsamixer settings does not seem to work. 

I will say that once I reset the alsamixer settings though sound quality is much better than it was before the latest update.

---

### Post by pickarooney on 2010-02-12
I've lost all sound in all media players after the .19 kernel upgrade although flash still has sound. Karmic is a fecking joke! For crying out loud, is working sound too much to ask for?

---

### Post by Kixtosh on 2010-02-12
I have not experienced any new sound issues with the kernel .19 update. Everything has continued to function normally on my two laptop-o-saurs, so I'm quite a happy camper right now. 

I will update both to Lucid Lynx when it is released however, and then just stick with LTS versions, but for how long is anyone's guess. After all, how much more than ten years of use can one reasonably expect from a laptop?

I even tried Puppy Linux 431 on both, and it works great, including sound, but I don't seem to really get much of a performance boost from using it when compared to Xubuntu (at least that I have noticed) other than another twenty to thirty seconds less time waiting for start-up.

---

### Post by swoll1980 on 2010-02-12
There are something like 6 million people using Ubuntu. If a million people had sound issues (which isn't the case), it's still less than 20%. This is not "the majority" I have installed Ubuntu on several machines and still have yet to have a sound problem.

---

### Post by Riverside on 2010-02-12
I have one odd sound issue however I suspect that it is a bug in Totem rather than an Ubuntu issue per se.

I installed 9.10 on my Dell Inspiron 6400 laptop last weekend, everything worked perfectly after a standard new install.  Sound is good and crystal clear, working in all applications as it should.

My desktop is a reasonably high specification self-build machine:

[http://www.yoyo.org/~anthony/riverside_hardware.html](http://www.yoyo.org/~anthony/riverside_hardware.html)

Post-installation sound (again, a standard new install not an upgrade from a previous Ubuntu version) didn't work solely due to being muted, I un-muted it using the Gnome panel applet (which didn't work the first time, I had to do it twice) and after that had perfect sound.

However, Totem will play a DVD (I have tried several DVDs, same result for each) with sound during the DVD intro and whilst the root menu is being viewed but selecting actual content results in continued playback with video only.

Rather odd, Kaffeine plays DVDs perfectly with sound throughout so this can only I think be a Totem issue.

---

### Post by prodigy_ on 2010-02-13
> **Mr. Picklesworth said:**
> Yes, there has been much breakage. Yes, I, too, suffered an Ubuntu release in which Pulse + ALSA on my sound card just fell to bits and I realize it still happens in Karmic, but it has been totally worth it for the amazing system in place now. I think it's a real shame that people choose to discourage this kind of progress and actively insist on mediocrity.
Your own signature is "help, don't preach." And still you come here preaching pulseaudio "superiority" to people who were able to solve their problems by getting rid of it? Talk about hypocrisy... :-)

---

Personally I voted "there are problems". But I must add that in 9.10 the only issue I still have is sound disappearing occasionally. It doesn't happen often and usually goes away after a reboot, so I consider it a minor issue.

In 7.10, 8.04 and 8.10 sound didn't work at all (I have a Toshiba laptop with Conexant CX20549 audio) and in 9.04 it was less stable than now.

---

### Post by Mr. Picklesworth on 2010-02-13
To be clear, I'm not denying that there are problems (because there are). However, every "PulseAudio isn't working for me" thread hereabouts seems to end in people trashing the entire thing with no investigation (the unsuspecting user follows suit by enabling OSS and missing out on cool stuff), then somebody else jumps in to complain about progress and the GNOME project's awesome cohesiveness, only furthering the backwards tug. As someone who cares about Linux having a good audio experience, I think that sucks.

I don't think I'm preaching here, since I do recognize the issue and I absolutely realize this thing isn't immortal; I just think the eventual gain (Lucid?) outweighs the loss and I want to make that point of view known. Also, if you follow the link in my sig, you'll find it's about a fairly different topic. Thanks for the pinch anyway, though.

Basically, I'm not saying "torture yourselves with broken audio because it misfunctions through bluetooth." I'm saying: please look at all sides here before telling people that the *only* solution to any audio problem is to revert their audio system to bare ALSA. In the long run, that approach will sting.

---

### Post by Ric_NYC on 2010-02-13
The majority has spoken: There are problems with the sound.

---

### Post by pickarooney on 2010-02-13
Nox I keep having to run **sudo alsa force-reload** in order to get sound back and the system, for the first time since I installed Ubuntu abotu 4 years ago, keeps freezing. 

What a nightmare.

---

### Post by nsacco on 2010-02-17
My sound has been fine in most programs (XMBC, Firefox w/ Flash), but it has been a huge pain in the *** for me when it comes to NES and SNES emulators.

* ZSNES, an SDL-based emulator, worked
* Mednafen, which could use ALSA or SDL, was a mess
* fceu(x), an SDL-based emulator, could play sound, but very poorly and choppy

So I did what was suggested in this thread by [VertexPusher]("http://ubuntuforums.org/member.php?u=917567") in this thread, in the #20 post, and purged Pulseaudio. I'm running straight ALSA through my HDMI, now. Here's where I'm at now:

* XMBC sound works, but only after manually changing the sound device in it from default to hdmi
* Mednafen works perfectly, again, after telling it the sound device is 'hdmi'
* ZSNES has gone completely silent
* And since Mednafen works, I'm not gonna even bother with fceu(x)
* Firefox /w Flash has gone silent

It seems to me that since getting rid of Pulseaudio, I've killed SDL sound, and I can only do ALSA. How can I get SDL sound working without Pulseaudio. Plus, how do I get the rest of my system sound back? I don't have the desktop sounds (login sound, error alerts, etc) nor is Firefox sounding off.

---

### Post by BbUiDgZ on 2010-02-17
gave up and went back to 8.04  (ubuntu studio) due to the m-audio 2496 no analoge sound outputs.

---

### Post by Yellow Pasque on 2010-02-17
> **nsacco said:**
> Plus, how do I get the rest of my system sound back? I don't have the desktop sounds (login sound, error alerts, etc) nor is Firefox sounding off.
This [https://launchpad.net/~dtl131/+archive/ppa](https://launchpad.net/~dtl131/+archive/ppa) should fix the event sound thing. Make sure sound works properly in the *gstreamer-properties* dialog

> since getting rid of Pulseaudio, I've killed SDL sound, and I can only do ALSA. How can I get SDL sound working without Pulseaudio.
The ALSA backend for SDL is known to be problematic in Ubuntu (there's a really good Launchpad bug showing this, but I'm too lazy to look it up). I'm not sure whether that's something particular to Ubuntu's configuration  or the backend itself. You can try using the OSS backend for SDL (make sure you have alsa-oss package installed), but the drawback there is that ALSA can't mix OSS apps properly and you lose the ability to have sounds from multiple sources.

---

### Post by nsacco on 2010-02-17
> **Temüjin said:**
> 
The ALSA backend for SDL is known to be problematic in Ubuntu (there's a really good Launchpad bug showing this, but I'm too lazy to look it up). I'm not sure whether that's something particular to Ubuntu's configuration  or the backend itself. You can try using the OSS backend for SDL (make sure you have alsa-oss package installed), but the drawback there is that ALSA can't mix OSS apps properly and you lose the ability to have sounds from multiple sources.

Yeah, that would be a problem for me, since I want to launch NES and SNES games from XBMC.

---

### Post by Objekt on 2010-02-17
Yes, Pulseaudio is a problem for me.  But in an indirect sort of way.

You see, there's an app I'd REALLY like to use, Teamspeak 3, that does not play nice with Pulseaudio.  By "not play nice" I mean "consumes 100% of available CPU resources, making everything else run like crap and causing audio artifacts even within TS3 itself."

The TS3 devs blame it on a bug in some library that they use to interface with Pulseaudio.  They are apparently content to wait on the devs of that library to fix the bug.  Accordingly, I project this bug will get fixed some time between the release of Teamspeak 4, and heat death of the universe.

Unfortunately, I'm stuck with Pulseaudio as long as I stick with Ubuntu.  I don't know how to set up any other kind of audio support, so while I could use a different desktop, I would do so without sound.

---

### Post by quequotion on 2010-02-17
Two-cents more:

I found a little oddity, which may shed some light on the sound issues in Karmic.

If you open "Volume Control" from padevchooser (or "Pulseaudio Volume Control" from the Appplications menu, or "pavucontrol" in terminal) and leave it running while using some application that employs sound (I tried ePSXe linux & wine, mupen64 plus, fceux, totem-xine playing video), magically things start to sound just fine.

I interpret that to mean that pulseaudio isn't getting enough priority to process sound in sync with the applications unless one of it's own applications is open. It could also be that since pavucontrol captures and processes the sound (to show the volume bar) somehow the redundant processing fixes things up....

If this happens for anyone else, post and hopefully it will catch a developer's attention. In the meantime, I'm off to search for bug reports that this might help...

---

### Post by quequotion on 2010-02-17
> **VertexPusher said:**
> Nothing can become a standard that doesn't work for the vast majority of users.

That just made me laugh. Not so sound too critical, you have a good point... but in the nineties, the linux kernel didn't work for the vast majority of users either.

---

### Post by XubuRoxMySox on 2010-02-18
Ubuntu isn't a good choice for newcomers to Linux anymore, since they started using Beta software by default in their "ready" releases. Grub2 is Beta. PulseAudio is Beta. 

Beta testing is fun for experienced Linuxers who enjoy taking some risks and uncovering bugs and helping to fix them! But imposing high-risk default Beta stuff on newbies is a mistake, and I fear it will hurt Ubuntu in the long run.

-Robin

---

### Post by VertexPusher on 2010-02-18
> **quequotion said:**
> That just made me laugh. Not so sound too critical, you have a good point... but in the nineties, the linux kernel didn't work for the vast majority of users either.
OK, I should have said:

Nothing can become a standard *until* it works for the vast majority of users.

As dixiedancer said, deploying beta software, especially as core elements of the system, will only hurt Ubuntu's reputation.

---

### Post by elsalvadorbali on 2010-02-18
> **VertexPusher said:**
> There's no need to remove it completely. You can leave libpulse installed; it won't do anything unless the PulseAudio daemon is running.

Many of the ALSA packages you installed were already there because PulseAudio uses them, too. Installing esound packages doesn't really make sense. I don't know any application still using them. Gnome won't even launch esound any more, so these packages will just occupy space and do nothing.

I recommend installing gstreamer0.10-alsa, gnome-alsamixer, and removing gstreamer0.10-pulseaudio, vlc-plugin-pulse, pulseaudio. Open gstreamer-properties, choose ALSA as its default audio plugin, and you're done.

You know, there is this rumour dating back to maybe 2003 which says that ALSA does not allow multiple applications to use a sound card simultaneously. But that's nonsense. ALSA allows complete control over the way sound cards are used. It does sample format conversion, rate conversion, channel routing, up- and downmixing, shared playback, shared recording etc. It can turn a PCI sound card and a USB webcam microphone into a single device, and it can turn a single 7.1 surround onboard audio interface into four separate stereo playback devices, running at latencies below 4ms. It combines all the features of the various sound systems of Windows (MME, DirectSound, WDM kmixer, ASIO) under one programming interface which PulseAudio will never replace.

The only major achievement of PulseAudio in the past two years is to completely destroy the reputation of Linux as a platform for any kind of audio-related application. In a significant number of cases, including mine, PulseAudio just doesn't work out of the box. It crashes, it crackles, it uses too much CPU, it leaks memory, it messes up mixer settings etc. The bug tracker is full of PulseAudio bug reports. Some of these bugs have not been fixed for months and probably never will.


Hi Vertex and All!

I have had problem with removing PulseAudio for a while. I was happy to read your post and tried to do what you just suggested.
Yet when I tried to remove the "gstreamer0.10-pulseaudio" packageat Synaptic, it told me that as dependency it will bring ubuntu-desktop with itself.
I already did this, and I had a reeealy hard time after to recover my GNOME, which collapsed already two times because of this.
Anyone knows how to remove/deactivate PulseAudio without getting ubuntu-desktop deleted and GNOME collapsed? :(

I really would like to get rid of this garbage PulseAudio.


Thanks!

SalvadorBali

---

### Post by Objekt on 2010-02-18
> **dixiedancer said:**
> Ubuntu isn't a good choice for newcomers to Linux anymore, since they started using Beta software by default in their "ready" releases. Grub2 is Beta. PulseAudio is Beta. 

Beta testing is fun for experienced Linuxers who enjoy taking some risks and uncovering bugs and helping to fix them! But imposing high-risk default Beta stuff on newbies is a mistake, and I fear it will hurt Ubuntu in the long run.

-Robin

Excellent point.  I don't feel the need to keep up with a new release every 6 months; chiefly, I started over with 9.10 a few months ago so that my version would be supported for a good while.  Lately I have considered starting over with 8.04.4 LTS.  There have just been too many things in 9.10 that have broken for no reason.  I don't know that 8.04.4 will fix them, but it seems worth a try.

As I've mentioned in other threads, 9.10 or 9.04 are not what I use when building a machine for someone.  Too many problems, too many unstable beta versions.  Too many unexplained and unfixed bugs, like Xserver locking up on some machines for no apparent reason, Nautilus not retaining filetype associations, and being unable to do Internet connection sharing.

The last machine I sent out had Ubuntu 8.04.3 LTS.  While older versions of Ubuntu will have older versions of key apps (OpenOffice, Firefox, etc.) by default, this is easily corrected.  One can use Ubuntuzilla, or install from a more recent .deb or .run package.

---

### Post by Arthur_D on 2010-02-18
Yes, I have OpenAL issues, causing sound to crackle and drop completely. Jaunty and Lucid alpha2 which I've tested, works with no hiccups. /me can't wait for 10.04!

---

### Post by VertexPusher on 2010-02-18
> **elsalvadorbali said:**
> I had a reeealy hard time after to recover my GNOME, which collapsed already two times because of this.
What do you mean by "collapsed"?

ubuntu-desktop is an empty package. Removing it will do exactly nothing to Gnome. I've been running Karmic without ubuntu-desktop for months, and Jaunty before that, all the way back to Hardy, the first release to come with PulseAudio. Others have done the same. We certainly would have noticed if Gnome had "collapsed" at some point.

---

### Post by Objekt on 2010-02-18
That's funny, when I removed PulseAudio entirely, I lost my Gnome desktop completely.  Trying to log in with Gnome after purging PA resulted in a blank desktop.

I had LXDE available, but didn't find it very useful without any sound support.  I guess one could configure something else (ALSA?) but I had no idea how to do so.  I gave up & reinstalled PulseAudio.

---

### Post by VertexPusher on 2010-02-18
> **Objekt said:**
> That's funny, when I removed PulseAudio entirely, I lost my Gnome desktop completely.  Trying to log in with Gnome after purging PA resulted in a blank desktop.

I had LXDE available, but didn't find it very useful without any sound support.  I guess one could configure something else (ALSA?) but I had no idea how to do so.  I gave up & reinstalled PulseAudio.
OK, I've posted this many times before, but here it is again:
```
sudo apt-get install gstreamer0.10-alsa gnome-alsamixer
sudo apt-get purge pulseaudio gstreamer0.10-pulseaudio vlc-plugin-pulse
```
These commands will uninstall PulseAudio from Ubuntu 9.10. They will not remove anything else; your Gnome desktop will work just as it did before. The PulseAudio volume control will be gone of course, but that's why we install gnome-alsamixer as a replacement. You can put its icon near the notification area for easy access like this:
[img]http://img715.imageshack.us/img715/5892/volumex.png[/img]

If you want PulseAudio back for some reason, this command will do the job:
```
sudo apt-get install ubuntu-desktop
```
You see, that's what the package "ubuntu-desktop" is useful for: it's a system restore point. And that's why it makes perfect sense to remove it along with PulseAudio. ubuntu-desktop itself does not contain any software; it's a metapackage.

---

### Post by nsacco on 2010-02-18
I followed those instructions, and got rid of ubuntu-desktop, and I had nothing happen to GNOME.

> **quequotion said:**
> Two-cents more:

I found a little oddity, which may shed some light on the sound issues in Karmic.

If you open "Volume Control" from padevchooser (or "Pulseaudio Volume Control" from the Appplications menu, or "pavucontrol" in terminal) and leave it running while using some application that employs sound (I tried ePSXe linux & wine, mupen64 plus, fceux, totem-xine playing video), magically things start to sound just fine.

I interpret that to mean that pulseaudio isn't getting enough priority to process sound in sync with the applications unless one of it's own applications is open. It could also be that since pavucontrol captures and processes the sound (to show the volume bar) somehow the redundant processing fixes things up....

If this happens for anyone else, post and hopefully it will catch a developer's attention. In the meantime, I'm off to search for bug reports that this might help...

This has sorta happened to me, but it's in no way a 'fix'. I was having issues with mednafen, an emulator compliation, couldn't get sound to work in it's NES emulator. But if I set my sound device to 'pulse', the emulator would just freeze when launched.

When I had Volume Control running, it was like... it loosened gears that were* completely* stuck, but the gears still ran terribly and uncontrollably. Most of the time I would still freeze within seconds, soemtimes sound would SORTA work. But it did do SOMETHING.

---

### Post by litemirrors on 2010-02-18
This is why in the future I"ll build a PC specifically for Ubuntu. You can also buy an Asus eeebox which is fully compatible from what I've seen (I'm on a B202) soo yea, Ubuntu rocks!

---

### Post by Yellow Pasque on 2010-02-18
VertexPusher, is there a reason you do not recommend the audiohacks PPA? : [https://launchpad.net/~dtl131/+archive/ppa](https://launchpad.net/~dtl131/+archive/ppa)

It is very useful in restoring the GNOME audio functionality (media keys, GNOME mixer, etc.) Most users probably won't need gnome-alsamixer if they have the classic gstreamer-based GNOME mixer.

---

### Post by Robbyx on 2010-02-19
> **Temüjin said:**
> VertexPusher, is there a reason you do not recommend the audiohacks PPA? : [https://launchpad.net/~dtl131/+archive/ppa](https://launchpad.net/~dtl131/+archive/ppa)

It is very useful in restoring the GNOME audio functionality (media keys, GNOME mixer, etc.) Most users probably won't need gnome-alsamixer if they have the classic gstreamer-based GNOME mixer.

1. I have removed Pulse and now have alsa sound working. I use skype and have been unable to divert the ringing tone away from the usb headphones to the speakers attached to the sound card. No sound comes out of the speakers under skype if the mic and speakers are set to the headphones.

2. As a result of removing Pulse I do not have the instant slider for sound. I have to click on the volume control and then the sound control screen opens. Is there an applet that will bring back the pop up volume slider?

---

### Post by VertexPusher on 2010-02-19
> **Robbyx said:**
> 1. I have removed Pulse and now have alsa sound working. I use skype and have been unable to divert the ringing tone away from the usb headphones to the speakers attached to the sound card. No sound comes out of the speakers under skype if the mic and speakers are set to the headphones.
Choose "default" for ringing and "plughw:1" for sound in/out in Skype preferences.

> 2. As a result of removing Pulse I do not have the instant slider for sound. I have to click on the volume control and then the sound control screen opens. Is there an applet that will bring back the pop up volume slider?
Yes. The link was in Temüjin's post that you quoted.

---

### Post by Objekt on 2010-02-19
OK, I think I have some idea now of how to purge PulseAudio while still retaining a useful system.  Sort of.  

What I don't understand is, how do I go about installing an alternative sound handler (or whatever it's called)?  As I mentioned previously, my problem the last time I tried to go without PA was that I then had no sound at all.

---

### Post by kio_http on 2010-02-19
It is more likely that people with sound problems will view, post and vote in this thread. Most people who don't have problems won't come here, this makes the poll quite inaccurate.

---

### Post by mikewhatever on 2010-02-20
> **kio_http said:**
> It is more likely that people with sound problems will view, post and vote in this thread. Most people who don't have problems won't come here, this makes the poll quite inaccurate.

Why is it more likely? What's wrong with the 26% who voted for 'the sound works perfectly'?

---

### Post by caglar sekmen on 2010-02-20
> **restless said:**
> I also had problems after the latest kernel update

but this solved it

sudo apt-get install gstreamer0.10-alsa gnome-alsamixer
sudo apt-get purge gstreamer0.10-pulseaudio vlc-plugin-pulse pulseaudio

thanx to VertexPusher

thank you
lor

I tried that but still no sound. However *sudo alsa force-reload* helped me to hear amsn message alerts :).. Cant get sound from youtube/flash though ..

---

### Post by ETbluez on 2010-02-20
Maybe you need more.
[http://www.johannes-eva.net/index.php?page=2009_10_useful_ubuntu_guide_karmic#mediacodecsandmore](http://www.johannes-eva.net/index.php?page=2009_10_useful_ubuntu_guide_karmic#mediacodecsandmore)

---

### Post by Rhemat on 2010-02-20
I have had problems with pulseaudio, and I thought a patch/update had fixed it.  It worked for a while, but now, it goes back to the habit of breaking every so often.  In fact, I was just playing around for a couple of hours on this machine, and sound worked fine.  Then pulseaudio decided to break, just in the middle of websurfing, and I had to uninstall it, and then reinstall.  I want to just get rid of it, because there is no reason that a person should have to do that.  What is worse, is that the Ubuntu-Desktop package, is labeled as a dependency of pulseaudio (which makes no sense to me).
I think Pulseaudio needs to go.  If people new to linux have to deal with this, they'll label LINUX as junk.  They won't know that it was a buggy sound package.  If any of the Ubuntu developers are reading this; dump PulseAudio.  Please bring back ESD.  I had no problems with it, and I certainly didn't have to reinstall it every two days, just to keep it functioning.

---

### Post by Robbyx on 2010-02-20
> **VertexPusher said:**
> Choose "default" for ringing and "plughw:1" for sound in/out in Skype preferences.


Thank you for responding. I am not seeing the plughw:1 option in my sound devices within skype. I see a lot of HDA,ALC888 entries including Analog and digital. There seems to be a clash between using the USB headphones and HDA, ALC888 entries. I can not mix them in skype.

---

### Post by VertexPusher on 2010-02-20
> **kio_http said:**
> It is more likely that people with sound problems will view, post and vote in this thread. Most people who don't have problems won't come here, this makes the poll quite inaccurate.
Oh really? What about the people who don't come here **because they wipe Linux off their hard disks and tell their friends what a pile of junk it is?**

---

### Post by Kixtosh on 2010-02-21
Just for clarity, the poll question is: 
 
"Do you have sound problems in Ubuntu 9.10 ?" with possible answers:
 
*- Yes, there are problems with the sound.*
- No, the sound works perfectly!
 
Compare this to the title of the thread:
 
"Sound Is Ubuntu 9.10 Karmic Koala's biggest problem".
 
Those are two slightly different points IMO. I did have some problems with the sound, which have been solved, but I would have had the same problems with 8.04, as well as a few others besides (my particular wireless cards did not work out of the box with the earlier versions I tried). I naturally voted "yes, there are problems" in the poll.
 
To admit that there are some problems with the sound in the poll, however, is not to vote (or agree) that sound is actually Karmic Koala's biggest problem. In my case, I wouldn't consider myself even remotely experienced enough to offer an opinion on the latter point, and also, these problems don't even manifest themselves at all on my systems with the Xubuntu version of Karmic Koala.

---

### Post by markinf on 2010-02-23
> **wilbuntu said:**
> [B]Ubuntu 9.10 Karmic Koala doesn't have big problems at all. Just a few small annoyances 
[/B]

You must be joking... right?

---

### Post by Objekt on 2010-02-23
> **wilbuntu said:**
> [B]Ubuntu 9.10 Karmic Koala doesn't have big problems at all. Just a few small annoyances 
[/B]

Oh please.  Random lockups are hardly "small annoyances," even if they don't always happen.  In fact it is the bugs which only happen to some users which are the worst, because they cannot be worked around as long as it is not understood why they happen.

---

### Post by Robbyx on 2010-02-24
> **Robbyx said:**
> 
Quote:
[COLOR="DarkOrange"]Per response from VertexPusher 
Choose "default" for ringing and "plughw:1" for sound in/out in Skype preferences.[/COLOR]

Thank you for responding. I am not seeing the plughw:1 option in my sound devices within skype. I see a lot of HDA,ALC888 entries including Analog and digital. There seems to be a clash between using the USB headphones and HDA, ALC888 entries. I can not mix them in skype.

I am still wondering how I can get the sound in and out to go to the usb headphones and the ringing to go to my sound card and thens to speakers. Choosing the USB device seems to block the sound to the soundcard. I think this is an ALSA problem. Is there a way of having two devices working?

---

### Post by Objekt on 2010-02-24
> **Robbyx said:**
> I am still wondering how I can get the sound in and out to go to the usb headphones and the ringing to go to my sound card and thens to speakers. Choosing the USB device seems to block the sound to the soundcard. **I think this is an ALSA problem. Is there a way of having two devices working?**

Digging around, I found a HOWTO here that may be of help:
[http://ubuntuforums.org/showthread.php?t=539819]("http://ubuntuforums.org/showthread.php?t=539819")

However, due to its age (2007) I'm not sure it is still relevant.

A while back, when I was still using Kubuntu 8.10, I simply could not have more than one application produce sound at one time.  Whatever app I started first would dominate the sound card.  This was a big problem, because I wanted to play an online game & use a voice chat app at the same time.  

A few people actually suggested that I buy a second sound card to "solve" this problem.  Ridiculous!  

I never did find a solution.  I had to give up on Ubuntu/Kubuntu until 9.04.  With Ubuntu 9.10, sound now works in most respects.  Some applications simply do not play nicely with Pulseaudio.

I am interested in whether you can get hardware mixing to work, as I would like to ditch PulseAudio in favor of ALSA.

---

### Post by Robbyx on 2010-02-24
> **Objekt said:**
> Digging around, I found a HOWTO here that may be of help:
[http://ubuntuforums.org/showthread.php?t=539819]("http://ubuntuforums.org/showthread.php?t=539819")

However, due to its age (2007) I'm not sure it is still relevant.

A while back, when I was still using Kubuntu 8.10, I simply could not have more than one application produce sound at one time.  Whatever app I started first would dominate the sound card.  This was a big problem, because I wanted to play an online game & use a voice chat app at the same time.  



Using the skype options it did not make any difference. I can only get the ringing tone to come out of the usb headphones, if the recorder and sound are via USB. It seems that I can not get the sound from one source and the riging tone from another, within skype.

---

### Post by Objekt on 2010-02-24
It seems I misunderstood your problem.  Absent options present in Skype, I don't think you are going to find a way to direct some of its output to one sound device, the rest to another.  That is not an ALSA (or PulseAudio for that matter) problem at all.  ALSA is just a means of delivering the sound put out by Skype.

---

### Post by Robbyx on 2010-02-24
> **Objekt said:**
> It seems I misunderstood your problem.  Absent options present in Skype, I don't think you are going to find a way to direct some of its output to one sound device, the rest to another.  That is not an ALSA (or PulseAudio for that matter) problem at all.  ALSA is just a means of delivering the sound put out by Skype.


Under the skype sound set up options there are three buttons. One for the speaker, another for the mic and the third for the ringing tone. Each button is a drop down menu with the sound devices showing. I can choose any device listed but as explained if I choose another device when the speaker and mic is set to usb headphones, no ringing tone is heard. So it seems to me that skype is written to enable the ringing tone to be heard on a different device to the headphones, but it does not work in Ubuntu Karmic.

---

### Post by Objekt on 2010-02-24
Neat.  I've never used Skype, but that arrangement would make a lot of sense...if it worked.  I would probably set it up so that the ringing came through the external speakers, with the talking done through the headset.  That's more or less how a regular telephone is arranged.

Unfortunately this does not give me insight into your problem. :P

But maybe the extra bumping to the top will catch the attention of someone more knowledgeable.

---

### Post by click4851 on 2010-02-24
FIX SOUND for any application, for any sound card, or codec......It should just work right. I've been futzing with sound since Breezy....

---

### Post by d3v1150m471c on 2010-02-24
I voted yes because of the initial trouble I had after an update in [COLOR=Red]kubuntu[/COLOR][COLOR=Black]. Fixed with alsamixer.[/COLOR]

---

### Post by prodigy_ on 2010-02-25
> **Objekt said:**
> Oh please.  Random lockups are hardly "small annoyances," even if they don't always happen.  In fact it is the bugs which only happen to some users which are the worst, because they cannot be worked around as long as it is not understood why they happen.

Not everyone experiences lockups with with 9.10. For instance, I don't. 

When bugs happen only to some users, they might be caused by faulty HW or wrong config files. That's not necessarily true but you need to consider the possibility.

---

### Post by Ozor Mox on 2010-02-25
I had to vote yes for this. Sound is literally the only problem I have with Ubuntu 9.10, and the symptoms are identical on both my laptop and my desktop, with the former being a fresh installation. It's quite frustrating, because in 9.04 the problems had all gone away.

The most obvious problem is the classic only one application seems to be able to process sound at once. Listening to my music and playing a game for example, means the music plays and the sound in the game will either not work at all, or will cut out after a short time.

Just this minute I've found out that another problem I had is directly related to the sound issues. A lot of the games I have installed would work perfectly, but then crash when closing them. In every single game, without fail, if I disable all the sound and music options and then quit, it closes perfectly. Re-enable sound, it crashes on close again, requiring me to Ctrl+Alt+F1, kill -9, Ctrl+Alt+F7 to get my desktop back again.

It's not the end of the world, but I really hope Ubuntu get this sorted out soon.

---

### Post by quequotion on 2010-02-26
> **nsacco said:**
> This has sorta happened to me, but it's in no way a 'fix'.

You are right about that. It can get some things going, but for some programs things are still out of sync or the audio is really crackly....

---

### Post by quequotion on 2010-02-26
> **litemirrors said:**
> This is why in the future I"ll build a PC specifically for Ubuntu. You can also buy an Asus eeebox which is fully compatible from what I've seen (I'm on a B202) soo yea, Ubuntu rocks!

a pc built for ubuntu.... that just seems strange to me somehow :/

not in a bad way, but i thought the point was to engineer ubuntu to run on anything...

---

### Post by quequotion on 2010-02-26
> **Ozor Mox said:**
> Ctrl+Alt+F1, kill -9, Ctrl+Alt+F7 to get my desktop back again.

It's not the end of the world

but figuring out that sequence would be the end of a lot of people ever bothering to use ubuntu again...

sometimes i wonder how bugs get their priority status... 
[URL="https://bugs.launchpad.net/ubuntu/+source/libsdl1.2/+bug/203158"]
Here's our bug by the way![/URL]

The sound issues with SDL in Karmic have been rated "Medium".... 

Problems like this are the kind of thing that makes linux completely inaccessible to the myriad Windows-junkies who can not understand why anything doesn't "just work" and don't understand why "Ubuntu doesn't just release an update to fix it" within a week.

Sound functionality is essentially less important than say, a kernel bug, but they have the same effect on linux's market share.

---

### Post by leorolla on 2010-02-26
> **quequotion said:**
> but figuring out that sequence would be the end of a lot of people ever bothering to use ubuntu again...

sometimes i wonder how bugs get their priority status... 
[URL="https://bugs.launchpad.net/ubuntu/+source/libsdl1.2/+bug/203158"]
Here's our bug by the way![/URL]

The sound issues with SDL in Karmic have been rated "Medium".... 

Problems like this are the kind of thing that makes linux completely inaccessible to the myriad Windows-junkies who can not understand why anything doesn't "just work" and don't understand why "Ubuntu doesn't just release an update to fix it" within a week.

Sound functionality is essentially less important than say, a kernel bug, but they have the same effect on linux's market share.

Sure!!!

Telling somebody to go to a Forum or to open a Terminal should be the exception and not the rule.

I can't reasonably convince anyone to use an OS that frequently requires editing files and runnin commands from the terminal, in order just to have it accomplishing ordinary tasks.

Before, Linux was too "under development" for things to "just work".

But at present, I honestly have the impression that things don't "just work" not for the lack of available drivers/software that do just work, but because of political decisions.

These are decisions of promoting this or that alternative, deprecating the ones that "just work", thus leaving behind everyone who prefers something that Works to something that is Free. Or perhaps the policy of having an OS that is amenable only for people who have really a lot of free time or for companies who pay for professional support.

It is of course a question of priority. Either you want to have it more and more shiny, doing a lot of kung fu, transparent windows that move smoothly, modern but not-yet-stable sound systems etc., or you stick to what works and develop solutions rather than new special effects.

---

### Post by Objekt on 2010-02-26
I'm probably repeating myself, but I agree with the opinion, expressed elsewhere, that PulseAudio (and the whole sound server concept in general) is broken.  It needs to die.

The video problem is just about licked.  Well, unless you use an Intel integrated graphics solution, in which case you're sort of left out of the 3D game (no pun intended).  But, if you have an Nvidia or ATI (although yeah, their Linux drivers suck, another issue for another thread), drivers do exist, which largely parallel the functionality available under Windows.  That's a sign of hope.


Why can't this happen for sound?  Is it a question of manufacturer support, or rather lack thereof?  While the vast majority of gaming PCs will have one brand of GPU or the other (ATI or NVidia), there are lots of different sound setups out there, so perhaps this is the root of the problem.  What about ALSA?

I don't know which manufacturers do/don't support Linux users by providing Linux drivers for their sound hardware.  My Creative Labs Audigy 2 ZS seems perfectly happy under Ubuntu 9.10 and Pulseaudio, but I may be the exception.  I haven't tried using my motherboard's built-in sound, which is some sort of Analog Devices chipset.

That's probably enough disjointed ramblings for now. :P

---

### Post by quequotion on 2010-02-26
> **Objekt said:**
> Why can't this happen for sound?

Somehow, video development has continuously evolved, branched, re-merged, and maintained a measure of consistent improvement without too much chaos over the years (excepting fglrx/ati/radeon/radeonhd/etc)... Audio development however is a different story entirely. For some reason linux audio developers are compulsively creating new APIs and layering them over, under and through each other.... 

Pulseaudio *could actually be a great idea* if the development goes a little further (more portability, getting more applications to use a the native API, wrapping other systems without breaking them, midi support, etc) and I would like to see pulseaudio become the all-encompassing, multipurpose, multi-platform, local and network audio server it intends to be. Unfortunately the Ubuntu audio team may have killed it's chances by including pulse before it was ready. It's so unpopular now because Ubuntu has been getting so much attention and exposing lots of would-be users to a shattered audio system (keep in mind that many people trying linux for the first time don't really care *why* something doesn't work).

I am actually afraid that it will become so hated that it will get superseded by *yet another new API*. That is something that must be avoided at any cost. leorolla has a good point about how linux development has changed... I don't know how much it's politicized, but now that linux has reached a level of development that can seriously compete in the home pc market, things have shifted from stabilization to expermintation. Experimentation is fun, but not acceptable for releases intended to increase linux awareness and userbase, [which is very specifically what ubuntu was made to do]("https://launchpad.net/bugs/1").

Of course, it may be impatient to complain too much about a transitional release just before an upcoming Long Term Support... Lucid will have several improvements and have more chances to get it's own bugs fixed than Karmic ever will.

Bottom line: *You want it to work right now?* Ok, kill pulseaudio and go back to alsa or oss4, but you're going to lose some cool functions which you probably don't know you have. *Want things to get better?* Post (in) bug reports like mad, get involved in fixes if you can, and don't give up.

---

### Post by TurnOfTide on 2010-02-26
Pulse audio was one of the first things to make noise in my error files on my Karmic install. I also have big problems with playing streaming audio from the internet. Need to refer back to this post when I have time to see if anything here offers a solution.

---

### Post by prodigy_ on 2010-02-27
> **quequotion said:**
> but figuring out that sequence would be the end of a lot of people ever bothering to use ubuntu again...
I don't know about the others but personally I'm sick of hearing this. Let them leave. Why should we care about people who don't want to do **anything** to help themselves? 

A PC isn't Aladdin's lamp and never will be. It requires at least some basic knowledge. Otherwise you'll feel uncomfortable regardless of the OS you use. Not everything in Windows can be configured/fixed via GUI. So why searching for some obscure value in the registry is OK and typing a couple of commands in bash is the end of the world?

---

### Post by Objekt on 2010-02-27
> **prodigy_ said:**
> I don't know about the others but personally I'm sick of hearing this. Let them leave. Why should we care about people who don't want to do **anything** to help themselves? 

A PC isn't Aladdin's lamp and never will be. It requires at least some basic knowledge. Otherwise you'll feel uncomfortable regardless of the OS you use. Not everything in Windows can be configured/fixed via GUI. So why searching for some obscure value in the registry is OK and typing a couple of commands in bash is the end of the world?

I have to agree with you there.  When Windows XP/Vista/7 requires command-line intervention, or other tinkering with obscure settings, people make excuses.  When Ubuntu requires a teeny bit of command-line tinkering, or hardware doesn't work simply because of manufacturer non-cooperation, it's all "DURRR LINUX SUX0R WINDOWS GOOD IMA GO BACK TO WINDOWS LOL."

Maybe I'm just a little bitter.

---

### Post by Queue29 on 2010-02-27
> I don't know about the others but personally I'm sick of hearing this. *Let them leave*. Why should we care about people who don't want to do anything to help themselves? 

And I'm sick of elitist users like you. It's people like you who turn away newcomers. It's people like you who perpetuate the 1970's ways of doing things. It's people like you who stifle progress by assuming everybody sits in front of the computer for 12 hours a day like you do.

---

### Post by andy_spoo on 2010-02-28
> **Queue29 said:**
> And I'm sick of elitist users like you. It's people like you who turn away newcomers. It's people like you who perpetuate the 1970's ways of doing things. It's people like you who stifle progress by assuming everybody sits in front of the computer for 12 hours a day like you do.

I completely agree. There are those that never want Ubuntu to be fully accepted by the masses because if it just worked, then they wouldn't be needed and they'd just be an average Joe. If they were actually as clever as they like to think, then they would help with the Ubuntu distro and make it better, rather than making sarcastic comments.

---

### Post by leorolla on 2010-02-28
> **Objekt said:**
> I have to agree with you there.  When Windows XP/Vista/7 requires command-line intervention, or other tinkering with obscure settings, people make excuses.  When Ubuntu requires a teeny bit of command-line tinkering, or hardware doesn't work simply because of manufacturer non-cooperation, it's all "DURRR LINUX SUX0R WINDOWS GOOD IMA GO BACK TO WINDOWS LOL."

Maybe I'm just a little bitter.

An average Windows user will be in such situation after a year or perhaps never.

An average Linux user necessarily must be comfortable with running terminal commands and editing non-intuitive text files.

Unless she is at a Department with an admin, support team etc, or their company has bought professional support from Canonical.

---

### Post by prodigy_ on 2010-03-01
> **Queue29 said:**
> And I'm sick of elitist users like you. It's people like you who turn away newcomers. It's people like you who perpetuate the 1970's ways of doing things. It's people like you who stifle progress by assuming everybody sits in front of the computer for 12 hours a day like you do.
/yawn 
I'm sorry, but you've just failed at trolling. Too obvious. Try better next time.

> **leorolla said:**
> An average Windows user will be in such situation after a year or perhaps never.
Now that's called wishful thinking. For instance, ping and tracert are command-line tools in any version of Windows. And practically everyone uses them occasionally **even** if nothing is wrong with the OS. And when something **is** wrong, anything can be required to fix it - from netsh or regedit to recovery console.

> **leorolla said:**
> An average Linux user necessarily must be comfortable with running terminal commands and editing non-intuitive text files.
You need to stop living in the 1990s.

---

### Post by leorolla on 2010-03-02
> **prodigy_ said:**
> 
Now that's called wishful thinking. For instance, ping and tracert are command-line tools in any version of Windows. And practically everyone uses them occasionally **even** if nothing is wrong with the OS. And when something **is** wrong, anything can be required to fix it - from netsh or regedit to recovery console.


I said **average**.

You can do **average** yourself. Go to the city center and stop 10 people at random, from all ages etc. Then ask them if they know the meaning of these:

1. when you buy a computer it has sound
2. when you buy a computer it has wireless
3. ping
4. tracert
5. netsh
6. regedit
7. recovery console

> **prodigy_ said:**
> You need to stop living in the 1990s.

I have 3 laptops:
2 of them had problems with wireless
3 of them had problems with sound, sometimes easier to solve, sometimes hard, sometimes unsolved

When I managed to fix them I had to use terminal commands and I edit text files that have no meaning for a non-linux-geek

So, how should I have done it in the 2010s?


Anyway this is leaving the topic... my point is that in the present-day state-of-art we could have such **basic** devices like wireless and sound working out-of-the-box, and this is not the case due to differente priorities ans policies taken into account when releasing a distro.

I'm not saying that Ubuntu nerver works and Mac/Windows always work.
I'm not saying that 100% of Ubuntu users need terminal and file-editing to have basic things working and 0% of Mac/Windows users have to run tracert, netsh and regedit.
I am saying that what should be an exception, still in the 2010's is a rule. Unfortunately.

---

### Post by Mr. Picklesworth on 2010-03-02
> **leorolla said:**
> 'm not saying that Ubuntu nerver works and Mac/Windows always work.
I'm not saying that 100% of Ubuntu users need terminal and file-editing to have basic things working and 0% of Mac/Windows users have to run tracert, netsh and regedit.
I am saying that what should be an exception, still in the 2010's is a rule. Unfortunately.

Well, I can disprove that right away. My computer's Intel WiFi adapter has worked perfectly since Jaunty, and it's the only thing on here that ever gave me trouble. I use the terminal to get convoluted things working because I'm crazy that way, but I have never needed to fix basic stuff on this machine.
I have also gone to a person's house and helped him through some Ubuntu problems (all of which were entirely GUI things). He had installed it himself and had been happily using it for over a year.

So, I agree there are a number of people who have trouble with low level stuff and that sucks, but it is definitely not everyone. Running on [certified hardware]("http://www.ubuntu.com/partners/hardwareprogramme") should get you the ideal results. And if that doesn't seem reasonable, consider why Apple's operating system succeeds with such a small slice of the market.

---

### Post by prodigy_ on 2010-03-03
> **leorolla said:**
> I said **average**.
The problem is that you say "average" when you mean "a complete lamer." If we were still in 1995, you'd even be somewhat right.


> **leorolla said:**
> I have 3 laptops:
2 of them had problems with wireless
3 of them had problems with sound
And of course Windows PCs are free from either?
/sarcasm off

[http://www.google.com/search?hl=en&newwindow=1&safe=off&q=windows+7+wireless+problems](http://www.google.com/search?hl=en&newwindow=1&safe=off&q=windows+7+wireless+problems)
[http://www.google.com/search?hl=en&newwindow=1&safe=off&q=windows+7+sound+problems](http://www.google.com/search?hl=en&newwindow=1&safe=off&q=windows+7+sound+problems)

Enough?

---

### Post by prodigy_ on 2010-03-07
The reason why I believe that pulseaudio will continue to fail indefinitely:
[http://pulseaudio.org/wiki/PulseAudioStoleMyVolumes](http://pulseaudio.org/wiki/PulseAudioStoleMyVolumes)

And no, I don't care if what they say on this page is true. The problem is that pulseaudio is being ruined by its own developers arrogance. FOSS or not, you don't talk to your users like this if you want your software to be popular.

---

### Post by emanuel t. on 2010-03-07
what's Karmic Koala's biggest problem? it's a linux distro, i.e. a "cool" game geeks like us play when we're bored of having things the easy way.

;P

---

### Post by hhh on 2010-03-07
The only sound issue I had was the crackling noise that occurs with HDA audio cards (fixed with a quick edit of alsa-base.conf)...
[http://www.ubuntugeek.com/ubuntu-tip-how-to-fix-crackling-noise-on-hda-audio-cards-in-ubuntu-9-10.html#more-3112](http://www.ubuntugeek.com/ubuntu-tip-how-to-fix-crackling-noise-on-hda-audio-cards-in-ubuntu-9-10.html#more-3112)

I absolutely love the new Sound Preferences>Applications tab.

---

### Post by Raeven0 on 2010-03-13
I registered for the sole purpose of contributing this nugget of wisdom:
Yes, I had multiple sound problems with Ubuntu, which were resolved by removing PulseAudio and compiling ALSA myself.
*smokebomb*

---

### Post by quequotion on 2010-03-23
> **prodigy_ said:**
> I don't know about the others but personally I'm sick of hearing this. Let them leave. Why should we care about people who don't want to do **anything** to help themselves? 

A PC isn't Aladdin's lamp and never will be. It requires at least some basic knowledge. Otherwise you'll feel uncomfortable regardless of the OS you use. Not everything in Windows can be configured/fixed via GUI. So why searching for some obscure value in the registry is OK and typing a couple of commands in bash is the end of the world?

Allow me to respectfully disagree.

Not that I don't feel the same way from time to time, but Ubuntu is not the right distribution for this attitude. This way of thinking applies to distros intentionally more complex and more geek-friendly, like Fedora or CentOS or Gentoo.

Ubuntu is *intended* to bring those helpless millions over to linux and make them feel at home.

Ubuntu's community and development team certainly contains a fair number of real wizards, but one should not feel "733+" for being competent in using it. The Ubuntu user experience is very specifically targeted at people who have no idea what linux is or how to use it.

---

### Post by vnc on 2010-03-27
> **prodigy_ said:**
> I don't know about the others but personally I'm sick of hearing this. Let them leave. Why should we care about people who don't want to do **anything** to help themselves? 

A PC isn't Aladdin's lamp and never will be. It requires at least some basic knowledge. Otherwise you'll feel uncomfortable regardless of the OS you use. Not everything in Windows can be configured/fixed via GUI. So why searching for some obscure value in the registry is OK and typing a couple of commands in bash is the end of the world?

Select a random kernel hacker.  Watch him spend hours trying to figure out how to get his 10 years old sound card working---or at least keep pulseaudio from randomly using 100% CPU when an application outputs some sound.

Expect a huge smile on his face.

--Vincent

---

### Post by vnc on 2010-03-27
Or picture a mechanic, whispering sweet words as his car breaks down on his way to work.

---

### Post by SwedishWings on 2010-05-30
I just can't understand why Ubuntu simply drop Pulse-Audio. 

Apart from using Ubuntu at my office (since 7.10), I've been helping several friends installing Ubuntu on different makes of PC's and laptops, but NOT A SINGLE TIME did audio work out of the box. Embarrassing!

How many users will just try and forget Ubuntu due to sound issues? 

Ubuntu: Please think again - and let Pulse-Audio rest in piece!

/Mike

---

### Post by cebif on 2010-05-30
Well after all that time, at April just before the official Ubuntu 10.04, sound started working with pulse audio in Ubuntu 9.10. It started working for me but I don't know how many other users it started working for.
I have Ubuntu 10.04 lucid now and it is working in that to.

---

### Post by earlneath on 2010-06-26
Not working for me. If you want audio out through HDMI it's a nightmare. I say burn pulse

---

### Post by Timmer1240 on 2010-06-26
Mines working flawlessly love 9.10 runs nice!

---

### Post by ubunterooster on 2010-06-26
Usually the biggest problem is the user...

---

