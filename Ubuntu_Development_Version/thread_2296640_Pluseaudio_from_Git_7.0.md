---
title: "Pluseaudio from Git 7.0"
date: 2015-09-27
forum: Ubuntu Development Version
---

### Post by QDR06VV9 on 2015-09-27
A few new things 2.1 Channel is back among others.
[http://comments.gmane.org/gmane.comp.audio.pulseaudio.general/23989](http://comments.gmane.org/gmane.comp.audio.pulseaudio.general/23989)
> **[ANNOUNCE] PulseAudio 6.99.1**

Good evening, citizens of Earth!

The first release candidate for PulseAudio 7.0 is now ready. Testing
and reporting found issues would be greatly appreciated. These are the
most significant changes since 6.0 (according to some undefined
criteria):

  * LFE channel synthesis with low-pass filtering
  * New libsoxr based resamplers
  * Socket activation support for TCP
  * The "srbchannel" IPC mechanism enabled by default
  * More flexible jack detection support when using UCM
  * Exiting due to SIGTERM isn't considered a failure

The full release notes draft is available here:  [http://freedesktop.org/wiki/Software/PulseAudio/Notes/7.0/](http://freedesktop.org/wiki/Software/PulseAudio/Notes/7.0/)

Very Nice so far
```
me@me-Aspire-M3300:~$ pulseaudio --version
pulseaudio 6.99.2-6-g3920
```

Waiting for Zika's input here.

---

### Post by zika on 2015-09-27
Boy, thank You, You've woke me from a summer sleep with PA. I did not upgrade ppa.list file for PA...
Now, I'm on the right track: ([https://launchpad.net/~ubuntu-audio-dev/+archive/ubuntu/pulse-testing?field.series_filter=wily](https://launchpad.net/~ubuntu-audio-dev/+archive/ubuntu/pulse-testing?field.series_filter=wily) )
```
:~$ pulseaudio --version
pulseaudio 7.0
```Thank You again... ;)

---

### Post by QDR06VV9 on 2015-09-27
My gosh they have been busy I had just compiled this a couple of days ago.
Then I saw your version so after a re-compile.
```
me@me-Aspire-M3300:~$ pulseaudio --version
pulseaudio 7.0-13-g772d
```
So much cleaner sounding.
Thanks zika.

---

### Post by Yellow Pasque on 2015-09-28
> So much cleaner sounding.
Did they change the resampler to use sox by default?

---

### Post by QDR06VV9 on 2015-09-29
> [COLOR=#000000]Did they change the resampler to use sox by default?[/COLOR]
That is sadly a question that I never get a plain answer to.
Instead they tell me.
> [COLOR=#555555][FONT=monospace]It depends on the ALSA configuration. Often, the default output device is PulseAudio; in that case, PA will do the resampling.
[/FONT][/COLOR] 
That is all I know. Sorry.
I am guessing here but I do not think so.
> [COLOR=#000000][FONT=verdana]The resampler is also available separately as the [/FONT][/COLOR][SoX Resampler library]("http://soxr.sourceforge.net/")[COLOR=#000000][FONT=verdana] (libsoxr).
[/FONT][/COLOR]
From here [http://sox.sourceforge.net/SoX/Resampling](http://sox.sourceforge.net/SoX/Resampling)
Maybe you will find this interesting.
[http://soundcheck-audio.blogspot.com/2011/04/tt-resampling.html](http://soundcheck-audio.blogspot.com/2011/04/tt-resampling.html)
Regards

---

### Post by Yellow Pasque on 2015-09-29
I looked at pulse-testing's PPA, and they did not change resamplers (in /etc/pulse/daemon.conf). So I'm trying to figure out why you think 7.0 sounds better/"cleaner"/different. The only thing I can think of is that you have a subwoofer and you didn't have it configured to be used previously. Is that the case?

> Instead they tell me.. 'It depends on the ALSA configuration. Often, the default output device is PulseAudio; in that case, PA will do the resampling."
Yes, this is how Ubuntu is setup (see /usr/share/alsa/pulse-alsa.conf).

---

### Post by QDR06VV9 on 2015-09-29
I am not using the PPA
I compile from Git there are some difference's small but noticeable.
and I am familiar with the [COLOR=#000000] /usr/share/alsa/pulse-alsa.conf.[/COLOR]
[COLOR=#000000]Yes this setup is using just a cheap set of Creative 2.1 speakers but I notice enough to deem noteworthy. The 5.1 speakers are to disruptive here at the Office.
[/COLOR]And some more support was added for the 
> [COLOR=#2B5E82][FONT=Times New Roman]The "srbchannel" IPC mechanism enabled by default[/FONT][/COLOR][COLOR=#000000][FONT=Times New Roman]The "srbchannel" IPC mechanism, which improves efficiency particularly on low latency streams, was introduced in the previous release, but it was too buggy to be enabled by default at that time. Bugs have been fixed since, and now the feature is enabled by default.[/FONT][/COLOR]

Plus they have added more support for SB Cards.
[COLOR=#000000]I always feel challenged by you or called out? Don't know if that is intentional or Innocence.
But I come in peace.
Kind Regards[/COLOR]

---

### Post by Yellow Pasque on 2015-09-29
By default, I am skeptical of differences in perceived audio quality without some sort of double blind test (because of the placebo effect). So, if you heard a difference, I was wondering what the technical explanation was. I should have read the detailed release notes because this is probably the explanation:
```
Previously PulseAudio supported (creating the LFE output) by simply feeding the average of all input channels to the LFE channel, but it's often better to filter out any high frequencies going to the subwoofer. That's now supported, and enabled by default.
```

> I always feel challenged by you or called out? Don't know if that is intentional or Innocence.
I can be terse, cold, cynical, sarcastic and over-analytical (and those are some of my better qualities). No malice is intended though.
Maybe I should use more smilies to seem more personable? :)

---

### Post by QDR06VV9 on 2015-09-29
> **Temüjin said:**
> 
I can be terse, cold, cynical, sarcastic and over-analytical (and those are some of my better qualities). No malice is intended though.
Maybe I should use more smilies to seem more personable? :)
Nah! Not on my account anyway:D
I too tend to be a little matter of fact or (Gruff Sounding):eek: but a teddy bear on the inside. Besides with age those qualities are Earned.;)
Thanks for the reply, I have a lot of respect for your Technical skills.
Regards

---

### Post by valereguerin on 2015-12-16
pulseaudio --version
pulseaudio 7.1

sometimes steam crash (the sound crash at the same moment...maybe...i don't know where i can find error crash report !) if anyone know how leave steam when it crash, thanks for help

i7 bloomfield :for my kernel???xeon arch ??? i know it's the same arch. without ECC ; radeon R9 280 ; 8g DDR3 1800 Xénial Xérus Ubuntu-Gnome-Desktop 4.3.0-2-generic x86_64 (64 bit) Desktop: Gnome 3.18.2
Card: Advanced Micro Devices [AMD/ATI] Tahiti PRO [Radeon HD 7950/8950 OEM / R9 280]
           Display Server: X.Org 1.17.3 drivers: ati,radeon (unloaded: fbdev,vesa) Resolution: 1920x1080@60.00hz
           GLX Renderer: Gallium 0.4 on AMD TAHITI (DRM 2.43.0, LLVM 3.6.2) GLX Version: 3.0 Mesa 11.0.7

without this bug and freetuxTV6.6 crash when open it, and a little problem with my passeport only with virtual keyboard ? in logithèque and Synaptic ???? everything works fine, i forget i use a development version ! Top Fun but not funny there are no big bugs !!!! it's not Ubuntu !................................ i'm jocking ......

---

