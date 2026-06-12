---
title: "ALSA or OSS?"
date: 2010-01-19
forum: The Cafe
---

### Post by Grifulkin on 2010-01-19
I know that this is the ubuntuforums and I will assume that the majority use Ubuntu and it turn probably use Pulse-Audio.

Anyways, my question is do you prefer ALSA or OSS?  I like the fact that OSS works and if I have XMMS and Opera open at the same time if I want to pause XMMS to watch a Youtube video with sound, it works.  I find that with ALSA you have one program that has sound and one that does not.

So yes, OSS or ALSA?

-Grif

EDIT:  Another question, is OSS dead?

---

### Post by Rhapsody on 2010-01-19
I personally prefer OSS. To me, it feels more stable and more complete than ALSA. I used it for a long time, but ended up dumping it after having sound problems with the OSS output on MPlayer, where the response from the developers was "OSS is depreciated, we only support ALSA". My only option was to return to ALSA, and I've had no end of sound problems since.

The traditional problem with OSS and Ubuntu is that it's not available from the repositories (though that [may be changing soon](http://packages.debian.org/sid/oss4-base)). A more serious problem is the above, where application developers stick to the kernel developer line of "OSS is depreciated, use ALSA instead". I'm increasingly thinking to just ignore both the application and kernel developers and use OSS anyway. If enough people use it, the application developers will start to support OSS, and the kernel developers can effectively be ignored (OSS works well enough without their approval).

Also, OSS is [definitely not dead](http://www.opensound.com/linux.html). The latest release from 4Front right now is 4.2 Build 2002 and was released just two months ago. It's also GPLed, so I say if it works, use it!

---

### Post by anagor on 2010-01-20
Alsa too can mix either in software or in hardware, so there should be no problem pausing xmms to watch some youtube video.
Besides I think that OSS pretty much dead, it's not included in the main kernel by default any more, and none of the biggest distros use it or install it by default, (ubuntu, debian, mandriva, suse, redhat/fedora).
Any advantage oss had on alsa 4-5 years ago is pretty much gone now, and with the spread of pulseaudio no one really cares what runs beneath it.

It looks like a question from 2004 :)
why won't you use pulseaudio?

---

### Post by Grifulkin on 2010-01-20
> **Rhapsody said:**
> I personally prefer OSS. To me, it feels more stable and more complete than ALSA. I used it for a long time, but ended up dumping it after having sound problems with the OSS output on MPlayer, where the response from the developers was "OSS is depreciated, we only support ALSA". My only option was to return to ALSA, and I've had no end of sound problems since.

The traditional problem with OSS and Ubuntu is that it's not available from the repositories (though that [may be changing soon](http://packages.debian.org/sid/oss4-base)). A more serious problem is the above, where application developers stick to the kernel developer line of "OSS is depreciated, use ALSA instead". I'm increasingly thinking to just ignore both the application and kernel developers and use OSS anyway. If enough people use it, the application developers will start to support OSS, and the kernel developers can effectively be ignored (OSS works well enough without their approval).

Also, OSS is [definitely not dead](http://www.opensound.com/linux.html). The latest release from 4Front right now is 4.2 Build 2002 and was released just two months ago. It's also GPLed, so I say if it works, use it!

Thank you for clearing up whether it was dead or not.  And also I much prefer OSS to ALSA, it seems much better than ALSA.

---

### Post by Grifulkin on 2010-01-21
bump

---

### Post by MaxIBoy on 2010-01-21
Almost all Linux desktop users think of OSS3 when they think of OSS. OSS3 is included with the Linux kernel, but it is obsolete mid '90s technology and sucks even worse than ALSA does. 

For a while, OSS4 was closed source and so the version in the kernel was left at OSS3. This is where ALSA became commonly used as it was better than OSS3. 

However, OSS4 is now totally open-source again, being licensed under three open-source licenses (CDDL, GPL, and a BSD variant.) And it really is superb compared to ALSA. 

It's not at all hard to checkout the OSS4 source code from Mercurial, compile it, and install it. (Or you can just download a stable release, but that hasn't worked *quite* as well for me.) If anyone here is having sound issues (especially sound loss on resume from suspend or high CPU usage when playing lots of sound sources at once,) I highly recommend trying OSS4 out. Your mileage may vary, but it fixed all my sound problems on two different computers (Realtek AC97 and Intel HDA.)

---

### Post by siimo on 2010-01-21
AFAIK OSS in kernel is deprecated.

---

### Post by k64 on 2010-01-21
I don't prefer either. I personally prefer PulseAudio, and will support it more once it supports more hardware. It's a really useful audio tool.

As for an audio editor? Probably Audacity.

---

### Post by Icehuck on 2010-01-21
> **Grifulkin said:**
>  I find that with ALSA you have one program that has sound and one that does not.



I haven't run into this issue for a long long time.


I always use ALSA and I never use Pulse Audio.

---

### Post by MaxIBoy on 2010-01-21
> **k64 said:**
> I don't prefer either. I personally prefer PulseAudio, and will support it more once it supports more hardware. It's a really useful audio tool.PulseAudio runs on top of either ALSA or OSS, usually ALSA these days. So if you use PulseAudio you are probably also using ALSA.

---

### Post by Psumi on 2010-01-21
I prefer ALSA, I tried OSS before (including OSS4) but I ended up going back to ALSA because OSS made my static more prevelant as well as more scrappy sounds.

---

### Post by Xbehave on 2010-01-21
I don't like the idea of complex in kernel mixing, so ALSA+userspace mixing FTW (ofc you can do that with OSS too, but i think ALSA is the way to go in terms of design)

[probably FUD]I also heard (so it may be wrong) that OSS doesn't limit audio gain to 0db, so you can damage your soundcard using it.[/FUD]

edit: I've found [the post]("http://linux.slashdot.org/comments.pl?sid=1409057&cid=29792279") that gave me the impression but it doesn't seam to justify the claim.

---

### Post by Grifulkin on 2010-01-21
> **Xbehave said:**
> I also heard (so it may be wrong) that OSS doesn't limit audio gain to 0db, so you can damage your soundcard using it.

That doesn't even sound right, software damaging hardware?  That doesn't make sense to me.

---

### Post by Zoot7 on 2010-01-21
Alsa, given that pretty much all audio applications work perfectly with it.
> **Grifulkin said:**
> I find that with ALSA you have one program that has sound and one that does not.
Strange, I've found using just plain Alsa and Alsa alone I've never had a problem where one application steals the sound from the others.

> **k64 said:**
> I don't prefer either. I personally prefer PulseAudio, and will support it more once it supports more hardware. It's a really useful audio tool.
IMO PulseAudio is one of the most problematic tools of all given that few enough applications actually work with, and worse it then steals Alsa away from everything else.

---

### Post by Simian Man on 2010-01-21
ALSA and Pulseaudio "just work" for me and always have, so I never saw a reason to try replacing them with OSS.  Also Alsa/Pulse are the way forward, so I doubt I will ever have the need for OSS.

> **Grifulkin said:**
> That doesn't even sound right, software damaging hardware?  That doesn't make sense to me.

It can definitely happen, though I have never heard that of OSS specifically.

---

### Post by Psumi on 2010-01-21
> **Zoot7 said:**
> Strange, I've found using just plain Alsa and Alsa alone I've never had a problem where one application steals the sound from the others.

Since 7.10, I had to deal with this at times (and now, all the time.) ALSA will not let me play a music file in totem without stealing the sound system for totem, which means I can't play flash sound at the same time as the music file in totem. I first have to quit totem, (Quit firefox if it is already on a flash), open firefox on a flash page with sound, then flash sound will work. I have to do this every time. Oh and, if I play a flash while totem is playing, and decide to quit totem, flash sound never plays, and it causes firefox to crash when I do anything.

---

### Post by Zoot7 on 2010-01-21
> **Psumi said:**
> Since 7.10, I had to deal with this at times (and now, all the time.) ALSA will not let me play a music file in totem without stealing the sound system for totem, which means I can't play flash sound at the same time as the music file in totem. I first have to quit totem, (Quit firefox if it is already on a flash), open firefox on a flash page with sound, then flash sound will work. I have to do this every time. Oh and, if I play a flash while totem is playing, and decide to quit totem, flash sound never plays, and it causes firefox to crash when I do anything.
That's because Flash wants to use Alsa which gets hogged by Totem with Pulseaudio. You have to everything use the same thing, you can do this with Alsa, not yet with Pulse.

---

### Post by Roasted on 2010-01-21
Never had any problems with Alsa, though at one point I did kind of get sucked into OSS4 fanboys telling me it was better. So I followed the official guide to install OSS4 and it completely FUBAR'd everything. When I went to uninstall it, I found I couldn't. After further research some people were telling me that I couldn't uninstall OSS4 and I had to reinstall.

Went back to Alsa, things work great. No issues. Love it.

---

### Post by Icehuck on 2010-01-21
> **Grifulkin said:**
> That doesn't even sound right, software damaging hardware?  That doesn't make sense to me.

Poorly written drivers are a recipe for disaster.

---

### Post by MaxIBoy on 2010-01-21
Any computer with support for ACPI can *potentially* allow software to overclock the CPU into oblivion and things like that, but this never happens.


> **Roasted said:**
> Never had any problems with Alsa, though at one point I did kind of get sucked into OSS4 fanboys telling me it was better. So I followed the official guide to install OSS4 and it completely FUBAR'd everything. When I went to uninstall it, I found I couldn't. After further research some people were telling me that I couldn't uninstall OSS4 and I had to reinstall.That's ridiculous, of course you can. You just reinstall the ALSA packages you removed, reinstall/dpkg-reconfigure the kernel, and *maybe* you need to edit /etc/modules. Ought to work fine.

---

### Post by Psumi on 2010-01-21
> **Zoot7 said:**
> That's because Flash wants to use Alsa which gets hogged by Totem with Pulseaudio. You have to everything use the same thing, you can do this with Alsa, not yet with Pulse.

No, I had the issue in reverse of what you said: I have normal ALSA, no pulse. But if I use pulse, both flash and totem can play without issues.

---

