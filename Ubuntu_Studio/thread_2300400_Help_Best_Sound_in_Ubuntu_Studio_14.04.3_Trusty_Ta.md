---
title: "Help: Best Sound in Ubuntu Studio 14.04.3 Trusty Tahr LTS"
date: 2015-10-25
forum: Ubuntu Studio
---

### Post by sethanath2 on 2015-10-25
Hi,

I am new to Ubuntu Studio 14.04.3 Trusty Tahr. However, I have been using Linux Mint for the past three to four years.

What is your technique in obtaining the best sound when it comes to using VLC and Youtube? I usually adjust Audio Effects (Graphic Equalizer and Compressor from VLC), but I notice this OS has so many software such as QjackCtl, Patchage, gladish, LADI Player, and much more.

I wonder if you can give me suggestion. For example, is there any external software that VLC can link to improve its internal sound system?

How about Youtube? Is there any way?

---

### Post by CrocoDuck on 2015-10-28
Hi there. I am a fan of linearity, so the best audio processing for me is no processing at all, unless you need to correct room acoustics artefacts with some kind of pre-emphasis, make a HRTF - Speaker response based cross feed model for your headphones (you will need a convolution engine, like [this one]("http://manpages.ubuntu.com/manpages/lucid/man1/fconvolver.1.html")) or just coarsely adjust for room response through equalization. I think you should have the [VLC jack module]("https://wiki.videolan.org/Documentation:Modules/jack/") installed by default (if not, see if you can install [this]("https://apps.ubuntu.com/cat/applications/vlc-plugin-jack/")), so you can just follow the bottom paragraph [here]("https://wiki.archlinux.org/index.php/JACK_Audio_Connection_Kit#VLC_-_no_audio_after_starting_JACK") to use VLC with jack. Once VLC works with jack you can use all the processing tools running on jack as well, like Calf plugins, Invada, etc... VLC can stream videos from youtube as well (Media > Open Network Stream > paste Youtube page address) and I suggest to do it. You might like [this tutorial]("http://www.ap-linux.com/documentation/playing-music-without-monitor-and-mice-with-vlc/") as well.

---

### Post by yoshii on 2015-10-31
Is ALSA not working for you?

---

### Post by sethanath2 on 2015-10-31
> **CrocoDuck said:**
> Hi there. I am a fan of linearity, so the best audio processing for me is no processing at all, unless you need to correct room acoustics artefacts with some kind of pre-emphasis, make a HRTF - Speaker response based cross feed model for your headphones (you will need a convolution engine, like [this one]("http://manpages.ubuntu.com/manpages/lucid/man1/fconvolver.1.html")) or just coarsely adjust for room response through equalization. I think you should have the [VLC jack module]("https://wiki.videolan.org/Documentation:Modules/jack/") installed by default (if not, see if you can install [this]("https://apps.ubuntu.com/cat/applications/vlc-plugin-jack/")), so you can just follow the bottom paragraph [here]("https://wiki.archlinux.org/index.php/JACK_Audio_Connection_Kit#VLC_-_no_audio_after_starting_JACK") to use VLC with jack. Once VLC works with jack you can use all the processing tools running on jack as well, like Calf plugins, Invada, etc... VLC can stream videos from youtube as well (Media > Open Network Stream > paste Youtube page address) and I suggest to do it. You might like [this tutorial]("http://www.ap-linux.com/documentation/playing-music-without-monitor-and-mice-with-vlc/") as well.

Thank you so much. I will check it out. I was looking for ways to improve VLC sound for decade. This is very good.

---

### Post by sethanath2 on 2015-10-31
> **yoshi2 said:**
> Is ALSA not working for you?

Everything works, but since this is Ubuntu Studio with latency kernel, I want to see what else this linux can do, which others cannot.
Thank you so much. If anyone have something else to suggest too, please let me know.

---

