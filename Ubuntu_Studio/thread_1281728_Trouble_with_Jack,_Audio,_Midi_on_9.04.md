---
title: "Trouble with Jack, Audio, Midi on 9.04"
date: 2009-10-03
forum: Ubuntu Studio
---

### Post by llwdtp on 2009-10-03
I have had a lot of trouble getting Ubuntu Studio to work right with audio and midi. The short version is:
1) My Nvidia card does not work with the Nvidia driver. That may not be an issue. But all of the windows on the desktop have 2 or 3 circles in the upper right corner instead of the normal symblos for minimize, maximize and close.
2) Jack does seem to run without xrun errors and I can trigger qsynth from a MIDI keyboard. But I get no sound out. And when I try to quit Jack, it will not quit. And when I try to shutdown after it will not quit, the computer freezes and I have to push and hold the power button for several seconds to shut it down.

Please help.

Now the longer version. I am using Ubuntu studio 9.04 with a Dell desktop machine about 7 years old. It has 500 mega bytes of memory and a sound blaster live card. I think it has a built in Intel sound system according to the various responses I have gotten. I cannot use that system as it does not appear to by wired to the outside world. 

The first problem is the windows with the funny symbols in the upper right hand corner. THere is either 2 or 3 circles in that corner. When there is 2 cilrcles, clicking on the right most circle does not shut the window down, but instead maximizes it. After doing a bit of searching, I presumed the problem may be the video drover. I tried to install the Nvidia driver for my Nvidia GeForce card. It told me it failed after attempting. When I reboot, the boot stalled when it tried to load the video driver and refused to go to X. My only recourse was to reinstall the OS. This happened several times before I decided to try and live with it.

I found I could navigate the windows OK, so I tried to get the audio working. THe two main references I used was [judgment day]("http://www.linuxjournal.com/content/judgement-day-studio-dave-tests-ubuntu-studio-904") which gives a detailed description of configuration changes to make including adding an "audio" group and suspending the HAL polling. In this article is another article the tells how to suspend [pulseaudio]("http://idyllictux.wordpress.com/2009/04/21/ubuntu-904-jaunty-keeping-the-beast-pulseaudio-at-bay/") which I also followed carefully. I made no other configuration changes than these. 

The net result is that I could get my external MIDI keybaord and Rosegarden to trigger Qsynth. But I got no sound out. And when I tried to close  Jack, it would not close and hung the system requiring a power off to get control again.

There are a lot more details but perhaps this is enough.

Thank you for the help.

Mark

---

### Post by hariks0 on 2009-10-03
Bump. I just installed all needed for Ubuntu Studio 9.04 but what I got was a theme and so many AV applications that don't work.

A detailed how to or tutorial would be higly appreciated.

---

### Post by solarbird on 2009-10-05
You might ask about the video hardware [over on the hardware forum]("http://ubuntuforums.org/forumdisplay.php?f=332"), maybe somebody there can help you with that.

I think first you need to concentrate on solving the problems with JACK. If Jack is hanging something is probably wrong there.

I also wonder about ALSA. Can you hear any other sounds on your system? Does ALSA know about the same soundcard for both sinks and sources?

---

### Post by llwdtp on 2009-10-05
Thank you Solarbird.

I had not considered the hardware forum for my video troubles. I will do as you suggest.

There was sound to my system until I disabled pulseaudio. That was recommended by this post [pulseaudio]("http://idyllictux.wordpress.com/2009/04/21/ubuntu-904-jaunty-keeping-the-beast-pulseaudio-at-bay/") because Jack and pulseaudio don't exist well together - I guess. 

I suspect my trouble is at least in part due to the fact that I have 2 sound cards; a built in one that I do not use and a PCI card that I am trying to use. Just a few minutes ago it occurred to me to try and disable the built in sound card in the bios and then maybe Linux can figure it out. I will try that.

[I]"Does ALSA know about the same soundcard for both sinks and sources?"

[/I]I am not sure how to answer that question. I look in jack and when it is behaving, I can see inputs from the various audio things like Qsynth. But I am not sure if that is what you mean by sinks and sources.

Lately when I try running the system, Jack will sometimes spew out a huge amount of xruns. Then other times it only burps an xrun every couple of seconds. I have read of people that had an xrun every couple seconds due to HAL polling of the CDROM. I think I have that turned off.

Thanks again for the reply. Sometimes it just helps to have someone to bounce ideas off of even if they do not have an explicit answer.

---

### Post by solarbird on 2009-10-05
> Jack and pulseaudio don't exist well together - I guess.
Jack and PulseAudio work together pretty well for most people on most versions of Ubuntu Studio afaik. They're working fine together for me.

One of the good things about PulseAudio is that it makes it easy to see what soundcards are active and what they're doing, and which is being used as the default for what audio functions. Since you have two soundcards, that's particularly important for you. Without PulseAudio you can still do this but it's more difficult.

Since you are not using the motherboard sound device I would definitely recommend disabling it in BIOS as you say. And then I would reinstall ALSA as described over [here, in this other forum thread]("http://ubuntuforums.org/showthread.php?t=1269806"). Then I would reinstall PulseAudio and see whether that all looks right.

> "Does ALSA know about the same soundcard for both sinks and sources?"
I am not sure how to answer that question.
I suspect but do not know that ALSA is directing your output to the other sound card or to the wrong output device on the correct sound card. But that's just a guess.

---

### Post by llwdtp on 2009-10-07
Thank you Solarbird. I did post my video question to the hardware and laptops forum. It did not take long for it to get way down the list. That is a busy place.

I did as you suggest and turned off the built-in sound card from the BIOS. I then tried to turn on Pulseaudio and reinstall ALSA. I did get pulseaudio to work but things were not the way I liked. So I reinstalled 9.04 to make sure I started from a clean slate. I added the audio group and put myself in that group and tested to see the pulse audio was working on videos from the browser. Then I started Jack and found I was still having xrun errors and jack was still hanging. I found a command the suspend pulseaudio (pasuspender cat). I think that is supposed to suspend pulseaudio so other programs can work. Jack was still not happy.

I will keep working on it.

---

### Post by solarbird on 2009-10-08
So you have Jack running now, that's good, even if there are overruns. Have you tried increasing the frames and all that to try to get rid of the xruns?

---

### Post by llwdtp on 2009-10-15
Thank you Solarbird for your several replies. 

I did get the system to work. I went back to version 8.04 after finding a few posts that say there are known issues with the real time kernel associated with 9.04. I put together notes of my experience and will post it on another thread. Perhaps it will save someone time.

---

