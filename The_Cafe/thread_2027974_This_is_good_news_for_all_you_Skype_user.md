---
title: "This is good news for all you Skype user"
date: 2012-07-17
forum: The Cafe
---

### Post by irv on 2012-07-17
[SIZE="3"]**Skype Release Bugfix Update**[/SIZE]
[http://www.omgubuntu.co.uk/2012/07/skype-push-out-new-bug-fix-update?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+d0od+%28OMG%21+Ubuntu%21%29&utm_content=FaceBook]("http://www.omgubuntu.co.uk/2012/07/skype-push-out-new-bug-fix-update?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+d0od+%28OMG%21+Ubuntu%21%29&utm_content=FaceBook")

---

### Post by Linuxratty on 2012-07-17
Would not work for me but it was worth trying.

---

### Post by irv on 2012-07-17
I just saw this in an article on the new MS office coming out.
> The Office suite also comes with Skype Internet-calling, which Microsoft gained in its $8.5 billion purchase of Skype Technologies SA last year.

By the way I don't use Skype, I use Google + for hanging out with kids and grandkids.

---

### Post by palimmo on 2012-07-18
This second 4.0 release doesn't work for me.
I can't see any icon (and therefore its menu) in the notification area and in some strange way skype makes unity launcher crash...

---

### Post by irv on 2012-07-18
Every time MS buy up a company like Skype, Linux user will suffer. They make it harder to try and run on a Linux machine. They want to set a standard that is not compatible with other OS's. Open Source is the only way to go when it come to compatibility. That is why I use Google + and not Skype.

---

### Post by palimmo on 2012-07-18
> **palimmo said:**
> This second 4.0 release doesn't work for me.
I can't see any icon (and therefore its menu) in the notification area and in some strange way skype makes unity launcher crash...

After several reinstalling/unistalling now it works.
I don't know why, but I had to reinsert skype in the notification area whitelist.

---

### Post by Lyfang on 2012-07-18
Skype 4.0 works great now! Unfortunately the microphone doesn't work for me with Skype 4.0.0.8 & other applications on my Lubuntu 12.04 LTS netbook. I'm trying to adjust the recording volume with PulseAudio Volume Control (pavucontrol) with no success.

```
skype --version
```
Skype 4.0.0.8
Copyright (c) 2004-2012, Skype

```
audacity --version
ALSA lib pcm.c:2217:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.rear
ALSA lib pcm.c:2217:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.center_lfe
ALSA lib pcm.c:2217:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.side
ALSA lib pcm_dmix.c:957:(snd_pcm_dmix_open) The dmix plugin supports only playback stream
Cannot connect to server socket err = Filen eller katalogen finns inte
Cannot connect to server socket
jack server is not running or cannot be started
Expression 'ret' failed in 'src/hostapi/alsa/pa_linux_alsa.c', line: 1670
Expression 'AlsaOpen( &alsaApi->baseHostApiRep, params, streamDir, &self->pcm )' failed in 'src/hostapi/alsa/pa_linux_alsa.c', line: 1830
Expression 'PaAlsaStreamComponent_Initialize( &self->capture, alsaApi, inParams, StreamDirection_In, NULL != callback )' failed in 'src/hostapi/alsa/pa_linux_alsa.c', line: 2092
Expression 'PaAlsaStream_Initialize( stream, alsaHostApi, inputParameters, outputParameters, sampleRate, framesPerBuffer, callback, streamFlags, userData )' failed in 'src/hostapi/alsa/pa_linux_alsa.c', line: 2764
ALSA lib pcm_dsnoop.c:612:(snd_pcm_dsnoop_open) unable to open slave
ALSA lib pcm_dsnoop.c:612:(snd_pcm_dsnoop_open) unable to open slave
ALSA lib pcm_dsnoop.c:612:(snd_pcm_dsnoop_open) unable to open slave
ALSA lib pcm_dsnoop.c:612:(snd_pcm_dsnoop_open) unable to open slave
ALSA lib pcm_dsnoop.c:612:(snd_pcm_dsnoop_open) unable to open slave
ALSA lib pcm_dsnoop.c:612:(snd_pcm_dsnoop_open) unable to open slave
ALSA lib pcm_dsnoop.c:612:(snd_pcm_dsnoop_open) unable to open slave
ALSA lib pcm_dsnoop.c:612:(snd_pcm_dsnoop_open) unable to open slave
ALSA lib pcm_dsnoop.c:612:(snd_pcm_dsnoop_open) unable to open slave
ALSA lib pcm_dsnoop.c:612:(snd_pcm_dsnoop_open) unable to open slave
ALSA lib pcm_dsnoop.c:612:(snd_pcm_dsnoop_open) unable to open slave
ALSA lib pcm_dsnoop.c:612:(snd_pcm_dsnoop_open) unable to open slave
ALSA lib pcm_dsnoop.c:612:(snd_pcm_dsnoop_open) unable to open slave
ALSA lib pcm_dsnoop.c:612:(snd_pcm_dsnoop_open) unable to open slave
ALSA lib pcm_dsnoop.c:612:(snd_pcm_dsnoop_open) unable to open slave
ALSA lib pcm_dsnoop.c:612:(snd_pcm_dsnoop_open) unable to open slave
ALSA lib pcm_dsnoop.c:612:(snd_pcm_dsnoop_open) unable to open slave
ALSA lib pcm_dsnoop.c:612:(snd_pcm_dsnoop_open) unable to open slave
ALSA lib pcm_dsnoop.c:612:(snd_pcm_dsnoop_open) unable to open slave
ALSA lib pcm_dsnoop.c:612:(snd_pcm_dsnoop_open) unable to open slave
ALSA lib pcm_dsnoop.c:612:(snd_pcm_dsnoop_open) unable to open slave
ALSA lib pcm_dsnoop.c:612:(snd_pcm_dsnoop_open) unable to open slave
ALSA lib pcm_dsnoop.c:612:(snd_pcm_dsnoop_open) unable to open slave
ALSA lib pcm_dsnoop.c:612:(snd_pcm_dsnoop_open) unable to open slave
ALSA lib pcm_dsnoop.c:612:(snd_pcm_dsnoop_open) unable to open slave
ALSA lib pcm_dsnoop.c:612:(snd_pcm_dsnoop_open) unable to open slave
ALSA lib pcm_dsnoop.c:612:(snd_pcm_dsnoop_open) unable to open slave
ALSA lib pcm_dsnoop.c:612:(snd_pcm_dsnoop_open) unable to open slave
ALSA lib pcm_dsnoop.c:612:(snd_pcm_dsnoop_open) unable to open slave
ALSA lib pcm_dsnoop.c:612:(snd_pcm_dsnoop_open) unable to open slave
ALSA lib pcm_dsnoop.c:612:(snd_pcm_dsnoop_open) unable to open slave
ALSA lib pcm_dsnoop.c:612:(snd_pcm_dsnoop_open) unable to open slave
ALSA lib pcm_dsnoop.c:612:(snd_pcm_dsnoop_open) unable to open slave
ALSA lib pcm_dsnoop.c:612:(snd_pcm_dsnoop_open) unable to open slave
ALSA lib pcm_dsnoop.c:612:(snd_pcm_dsnoop_open) unable to open slave
ALSA lib pcm_dsnoop.c:612:(snd_pcm_dsnoop_open) unable to open slave
ALSA lib pcm_dsnoop.c:612:(snd_pcm_dsnoop_open) unable to open slave
ALSA lib pcm_dsnoop.c:612:(snd_pcm_dsnoop_open) unable to open slave
ALSA lib pcm_dsnoop.c:612:(snd_pcm_dsnoop_open) unable to open slave
ALSA lib pcm_dsnoop.c:612:(snd_pcm_dsnoop_open) unable to open slave
ALSA lib pcm_dsnoop.c:612:(snd_pcm_dsnoop_open) unable to open slave
ALSA lib pcm_dsnoop.c:612:(snd_pcm_dsnoop_open) unable to open slave
ALSA lib pcm_dsnoop.c:612:(snd_pcm_dsnoop_open) unable to open slave
ALSA lib pcm_dsnoop.c:612:(snd_pcm_dsnoop_open) unable to open slave
ALSA lib pcm_dsnoop.c:612:(snd_pcm_dsnoop_open) unable to open slave
ALSA lib pcm_dsnoop.c:612:(snd_pcm_dsnoop_open) unable to open slave
ALSA lib pcm_dsnoop.c:612:(snd_pcm_dsnoop_open) unable to open slave
ALSA lib pcm_dsnoop.c:612:(snd_pcm_dsnoop_open) unable to open slave
ALSA lib pcm_dsnoop.c:612:(snd_pcm_dsnoop_open) unable to open slave
ALSA lib pcm_dsnoop.c:612:(snd_pcm_dsnoop_open) unable to open slave
ALSA lib pcm_dsnoop.c:612:(snd_pcm_dsnoop_open) unable to open slave
ALSA lib pcm_dsnoop.c:612:(snd_pcm_dsnoop_open) unable to open slave
ALSA lib pcm_dsnoop.c:612:(snd_pcm_dsnoop_open) unable to open slave
ALSA lib pcm_dsnoop.c:612:(snd_pcm_dsnoop_open) unable to open slave
ALSA lib pcm_dsnoop.c:612:(snd_pcm_dsnoop_open) unable to open slave
ALSA lib pcm_dsnoop.c:612:(snd_pcm_dsnoop_open) unable to open slave
ALSA lib pcm_dsnoop.c:612:(snd_pcm_dsnoop_open) unable to open slave
ALSA lib pcm_dsnoop.c:612:(snd_pcm_dsnoop_open) unable to open slave
ALSA lib pcm_dsnoop.c:612:(snd_pcm_dsnoop_open) unable to open slave
ALSA lib pcm_dsnoop.c:612:(snd_pcm_dsnoop_open) unable to open slave
ALSA lib pcm_dsnoop.c:612:(snd_pcm_dsnoop_open) unable to open slave
ALSA lib pcm_dsnoop.c:612:(snd_pcm_dsnoop_open) unable to open slave
ALSA lib pcm_dsnoop.c:612:(snd_pcm_dsnoop_open) unable to open slave
ALSA lib pcm_dsnoop.c:612:(snd_pcm_dsnoop_open) unable to open slave
ALSA lib pcm_dsnoop.c:612:(snd_pcm_dsnoop_open) unable to open slave
ALSA lib pcm_dsnoop.c:612:(snd_pcm_dsnoop_open) unable to open slave
ALSA lib pcm_dsnoop.c:612:(snd_pcm_dsnoop_open) unable to open slave
ALSA lib pcm_dsnoop.c:612:(snd_pcm_dsnoop_open) unable to open slave
ALSA lib pcm_dsnoop.c:612:(snd_pcm_dsnoop_open) unable to open slave
ALSA lib pcm_dsnoop.c:612:(snd_pcm_dsnoop_open) unable to open slave
ALSA lib pcm_dsnoop.c:612:(snd_pcm_dsnoop_open) unable to open slave
ALSA lib pcm_dsnoop.c:612:(snd_pcm_dsnoop_open) unable to open slave
ALSA lib pcm_dsnoop.c:612:(snd_pcm_dsnoop_open) unable to open slave
ALSA lib pcm_dsnoop.c:612:(snd_pcm_dsnoop_open) unable to open slave
ALSA lib pcm_dsnoop.c:612:(snd_pcm_dsnoop_open) unable to open slave
ALSA lib pcm_dsnoop.c:612:(snd_pcm_dsnoop_open) unable to open slave
ALSA lib pcm_dsnoop.c:612:(snd_pcm_dsnoop_open) unable to open slave
ALSA lib pcm_dsnoop.c:612:(snd_pcm_dsnoop_open) unable to open slave
ALSA lib pcm_dsnoop.c:612:(snd_pcm_dsnoop_open) unable to open slave
ALSA lib pcm_dsnoop.c:612:(snd_pcm_dsnoop_open) unable to open slave
ALSA lib pcm_dsnoop.c:612:(snd_pcm_dsnoop_open) unable to open slave
ALSA lib pcm_dsnoop.c:612:(snd_pcm_dsnoop_open) unable to open slave
ALSA lib pcm_dsnoop.c:612:(snd_pcm_dsnoop_open) unable to open slave
ALSA lib pcm_dsnoop.c:612:(snd_pcm_dsnoop_open) unable to open slave
ALSA lib pcm_dsnoop.c:612:(snd_pcm_dsnoop_open) unable to open slave
ALSA lib pcm_dsnoop.c:612:(snd_pcm_dsnoop_open) unable to open slave
ALSA lib pcm_dsnoop.c:612:(snd_pcm_dsnoop_open) unable to open slave
ALSA lib pcm_dsnoop.c:612:(snd_pcm_dsnoop_open) unable to open slave
ALSA lib pcm_dsnoop.c:612:(snd_pcm_dsnoop_open) unable to open slave
ALSA lib pcm_dsnoop.c:612:(snd_pcm_dsnoop_open) unable to open slave
ALSA lib pcm_dsnoop.c:612:(snd_pcm_dsnoop_open) unable to open slave
ALSA lib pcm_dsnoop.c:612:(snd_pcm_dsnoop_open) unable to open slave
ALSA lib pcm_dsnoop.c:612:(snd_pcm_dsnoop_open) unable to open slave
ALSA lib pcm_dsnoop.c:612:(snd_pcm_dsnoop_open) unable to open slave
ALSA lib pcm_dsnoop.c:612:(snd_pcm_dsnoop_open) unable to open slave
ALSA lib pcm_dsnoop.c:612:(snd_pcm_dsnoop_open) unable to open slave
ALSA lib pcm_dsnoop.c:612:(snd_pcm_dsnoop_open) unable to open slave
ALSA lib pcm_dsnoop.c:612:(snd_pcm_dsnoop_open) unable to open slave
ALSA lib pcm_dsnoop.c:612:(snd_pcm_dsnoop_open) unable to open slave
ALSA lib pcm_dsnoop.c:612:(snd_pcm_dsnoop_open) unable to open slave
ALSA lib pcm_dsnoop.c:612:(snd_pcm_dsnoop_open) unable to open slave
Expression 'ret' failed in 'src/hostapi/alsa/pa_linux_alsa.c', line: 1670
Expression 'AlsaOpen( &alsaApi->baseHostApiRep, params, streamDir, &self->pcm )' failed in 'src/hostapi/alsa/pa_linux_alsa.c', line: 1830
Expression 'PaAlsaStreamComponent_Initialize( &self->capture, alsaApi, inParams, StreamDirection_In, NULL != callback )' failed in 'src/hostapi/alsa/pa_linux_alsa.c', line: 2092
Expression 'PaAlsaStream_Initialize( stream, alsaHostApi, inputParameters, outputParameters, sampleRate, framesPerBuffer, callback, streamFlags, userData )' failed in 'src/hostapi/alsa/pa_linux_alsa.c', line: 2764
Expression 'stream->playback.pcm' failed in 'src/hostapi/alsa/pa_linux_alsa.c', line: 4541
Expression 'stream->playback.pcm' failed in 'src/hostapi/alsa/pa_linux_alsa.c', line: 4541
Okänd command line option: --version
```

---

### Post by mr john on 2012-07-19
> **irv said:**
> Every time MS buy up a company like Skype, Linux user will suffer. They make it harder to try and run on a Linux machine. They want to set a standard that is not compatible with other OS's. Open Source is the only way to go when it come to compatibility. That is why I use Google + and not Skype.

I don't think so.  They have actually improved it on the Linux platform. The problem the users had here was a Unity issue, not a Microsoft one. So next time don't be so quick to attack Microsoft.

---

### Post by Lars Noodén on 2012-07-19
> **irv said:**
> Every time MS buy up a company like Skype, Linux user will suffer. They make it harder to try and run on a Linux machine. They want to set a standard that is not compatible with other OS's. Open Source is the only way to go when it come to compatibility. That is why I use Google + and not Skype.

This is also why you owe it to yourself to keep trying SIP along side any other VoIP tools you might be using.  The sound quality is better even if there are other shortcomings.  Ekiga is one example, but all the SIP tools can talk with eachother so it does not matter which one(s) you try.

---

### Post by Dry Lips on 2012-07-19
By going here: [http://www.skype.com/intl/en/get-skype/on-your-computer/linux](http://www.skype.com/intl/en/get-skype/on-your-computer/linux)
it seems as if the download only is packaged for Ubuntu 10.04. Would this download work for 12.04?

(I guess you also could compile it, though.)

---

### Post by markbl on 2012-07-19
> **Dry Lips said:**
> By going here: [http://www.skype.com/intl/en/get-skype/on-your-computer/linux](http://www.skype.com/intl/en/get-skype/on-your-computer/linux)
it seems as if the download only is packaged for Ubuntu 10.04. Would this download work for 12.04?
Yes, that package installs fine on 12.04. Why the linux skype people don't fix this confusion on the download page just baffles me.

---

### Post by Wirephire on 2012-07-19
> **Dry Lips said:**
> By going here: [http://www.skype.com/intl/en/get-skype/on-your-computer/linux](http://www.skype.com/intl/en/get-skype/on-your-computer/linux)
it seems as if the download only is packaged for Ubuntu 10.04. Would this download work for 12.04?

(I guess you also could compile it, though.)
Yes, it works on  Ubuntu 12.04. And no, it can't be compiled since its not open source (I wonder what craps are hidden in the source). 
Only some binaries are available.

---

### Post by irv on 2012-07-26
There is some bad news for Skype users also.
Big Brother is watching.
This was in the ars technica. 
[Skype handing over more chat data to law enforcement]("http://arstechnica.com/tech-policy/2012/07/skype-handing-over-more-chat-data-to-law-enforcement/")
And this was in the Washington Post.
[Skype makes chats and user data more available to police]("http://www.washingtonpost.com/business/economy/skype-makes-chats-and-user-data-more-available-to-police/2012/07/25/gJQAobI39W_story.html")

---

### Post by kostkon on 2012-07-26
> **Dry Lips said:**
> By going here: [http://www.skype.com/intl/en/get-skype/on-your-computer/linux](http://www.skype.com/intl/en/get-skype/on-your-computer/linux)
it seems as if the download only is packaged for Ubuntu 10.04. Would this download work for 12.04?

(I guess you also could compile it, though.)
Actually, they mean 10.04 or older.

---

### Post by AllRadioisDead on 2012-07-26
> **wirephire said:**
> Yes, it works on  Ubuntu 12.04. And no, it can't be compiled since its not open source (I wonder what craps are hidden in the source). 
Only some binaries are available.

Of course. It's proprietary, surely it must be evil.

---

### Post by irv on 2012-07-26
> **AllRadioisDead said:**
> Of course. It's proprietary, surely it must be evil.

Now that MS owns it we will never see the source. :twisted:

---

### Post by AllRadioisDead on 2012-07-26
> **irv said:**
> Now that MS owns it we will never see the source. :twisted:

You would have never seen the source regardless ;)

---

### Post by irv on 2012-07-26
> **AllRadioisDead said:**
> You would have never seen the source regardless ;)

Your right! But I felt like it was in a locked box now the locked box is in another locked box and MS has the keys to both boxes.
I am glad I don't use Skye so it really doesn't bother me.

---

### Post by irv on 2012-07-29
The new Skype is now in the software center

[**[SIZE="3"]Latest Skype Release Added to Ubuntu Software Center[/SIZE]**]("http://www.omgubuntu.co.uk/2012/07/latest-skype-release-added-to-ubuntu-software-center?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+d0od+%28OMG%21+Ubuntu%21%29")

> But a new upstream release of Skype – though not the most recent – has been added to the Ubuntu Software Center, meaning a new, stable release of Skype is but a few clicks away.

---

### Post by markbl on 2012-07-29
> **irv said:**
> But a new upstream release of Skype – though not the most recent – has been added to the Ubuntu Software Center, meaning a new, stable release of Skype is but a few clicks away.

I just don't see the point when it is not the current version? :-?

---

### Post by t0p on 2012-07-29
> **markbl said:**
> I just don't see the point when it is not the current version? :-?

Won't the non-current version be able to communicate with the current version?  I'm not a Skype user, but I find it difficult to believe you won't be able to use the version in the repos to talk to people using the latest-greatest-bells-n-whistles version.

I find it hard to understand people who consider anything but the latest version as lame.  Heck, it was good 6 months ago or whatever - what makes it a bunch of crap *now*?

---

### Post by markbl on 2012-07-29
> **t0p said:**
> 
I find it hard to understand people who consider anything but the latest version as lame.  Heck, it was good 6 months ago or whatever - what makes it a bunch of crap *now*?
Er, I was commenting that I don't see the point of Ubuntu (finally) adding linux version 4.0.0.7 of skype to the repositories after skype already have released fixes and tweaks to that version recently in linux version 4.0.0.8. The point of the repositories is so you have the current version - but clearly here you are still better off just downloading the deb from the skype site. Why would Ubuntu announce this and make it a news item but not use the current version? Skype don't release many updates for linux after all.

---

### Post by brashley46 on 2012-07-29
> **markbl said:**
> Er, I was commenting that I don't see the point of Ubuntu (finally) adding linux version 4.0.0.7 of skype to the repositories after skype already have released fixes and tweaks to that version recently in linux version 4.0.0.8. The point of the repositories is so you have the current version - but clearly here you are still better off just downloading the deb from the skype site. Why would Ubuntu announce this and make it a news item but not use the current version? Skype don't release many updates for linux after all.

WEll,heck, at least we are up to version 4.xx now ... I presume we will get an update in *buntu 12.10 .    :popcorn:

---

