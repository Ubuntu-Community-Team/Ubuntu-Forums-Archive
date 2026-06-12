---
title: "ATI 5770 and Delta 44 issue"
date: 2010-11-27
forum: Ubuntu Studio
---

### Post by mlinder on 2010-11-27
So, went to install all the stuff for ubuntu studio this morning, and my sound stuff is defaulting to the HDMI stereo sound output on my Radeon 5770... with no outputs from the Delta 44 showing up, only input from the Delta.

I uninstalled the ATI drivers, but am still showing the juniper HDMI as my only output choices in the regular sound control panel.

Jack won't start as it stands....

Do I need to go back to an older nVidia card to get this working? Anyway to remove detection of the HDMI stereo out from my installation?

System:

Ubuntu 10.10
Installed RT and LL headers
Delta 44
ATI 5770

Thanks for any ideas.

---

### Post by mlinder on 2010-11-27
Ive blacklisted the audio driver for the ATI HDMI audio.

I still have no hardware listed for output. Reinstalled the m-audio drivers and everything.

---

### Post by Pablo_F on 2010-11-27
Having the relevant alsa info would help us help you:

wget [http://www.alsa-project.org/alsa-info.sh](http://www.alsa-project.org/alsa-info.sh) -O alsa-info.sh && bash alsa-info.sh

Anyway, the alsa driver works for that card so you don't have to install any aditional driver. Now, three things:

1. envy24control

You use envy24control to set DAC and ADC levels and internal mixer routing, if needed.

2. Pulseaudio.

It is the default audio system in ubuntu (a software layer higher than the driver). It does not work out of the box with the alsa driver (alsa module snd-ice1712) that supports your card. There are workarounds. See [https://bugs.launchpad.net/ubuntu/lucid/+source/pulseaudio/+bug/178442](https://bugs.launchpad.net/ubuntu/lucid/+source/pulseaudio/+bug/178442)

3. Jack

It is another audio system used for audio production. You normally launch it through qjackctl (Jack Control). It works out of the box with the alsa driver.

Cheers, Pablo

---

### Post by mlinder on 2010-11-28
Hello Pablo,

Issue is, the previous version of ubuntustudio worked just fine. Worked in system sounds without jack, as well as working with jack for studio apps. Doesn't do a damned thing now.

In any case, I removed the ATI card, installed a non-HDMI video card, and reinstalled.

Here is my ALSA info:
[http://www.alsa-project.org/db/?f=63ad874e3c124d73085aef2b87034c16a200ef06](http://www.alsa-project.org/db/?f=63ad874e3c124d73085aef2b87034c16a200ef06)

Jack is working now, envy24 control shows activity on the 'monitor pcms', but can't get anything back out, as my playback is still "dummy stereo".

I used jack to run a connection between system output and each system 'playback' device (1-10) and got nothing as output.

Help appreciated...

Mark

---

### Post by mlinder on 2010-11-28
After reading more on this, it seems a pretty big mess. I remember 64 Studio working just fine, I'll go back to that.

Thanks for your time, though.

---

### Post by Pablo_F on 2010-11-28
Hi, 

> Jack is working now, envy24 control shows activity on the 'monitor pcms', but can't get anything back out, as my playback is still "dummy stereo".

I used jack to run a connection between system output and each system 'playback' device (1-10) and got nothing as output.

According to amixer you have set levels for analog outputs 1 and 2 (DAC 0 and DAC 1) but the rest are zero. 

Check the levels in the analog volume tab of envy24control.

Cheers, Pablo

---

### Post by mlinder on 2010-11-28
> **Pablo_F said:**
> Hi, 



According to amixer you have set levels for analog outputs 1 and 2 (DAC 0 and DAC 1) but the rest are zero. 

Check the levels in the analog volume tab of envy24control.

Cheers, Pablo


Yeah, nothing. Again, the only 'out' listed is a dummy stereo in the system volume control.

---

### Post by Pablo_F on 2010-11-28
Hi, 

Let's see. You have jack up and running right? Then forget about system volume control which is a pulseaudio front-end. Jack is a different beast.

 But wait, we have to know better... 

Excuse me, what would you like exactly? What programs do you want to use, and do you want a system for general purpose in which you also can make some music, or do you want a computer dedicated to music production? This is important. 

Just not to desperate too soon, as a proof of concept, install aqualung which is a nice little player that finds out what audio server is up and running and play some music when jack is running. Check that aqualung outputs are connected to the system: playbacks.  

Again, when jack is up, envy24control is the tool for setting levels. However, you don't have to use it for that. You normally use the software levels in each application and leave the ACD and DCa levels alone, at 0 dB.

Cheers, Pablo

---

### Post by mlinder on 2010-11-28
> **Pablo_F said:**
> Hi, 

Let's see. You have jack up and running right? Then forget about system volume control which is a pulseaudio front-end. Jack is a different beast.

 But wait, we have to know better... 

Excuse me, what would you like exactly? What programs do you want to use, and do you want a system for general purpose in which you also can make some music, or do you want a computer dedicated to music production? This is important. 

Just not to desperate too soon, as a proof of concept, install aqualung which is a nice little player that finds out what audio server is up and running and play some music when jack is running. Check that aqualung outputs are connected to the system: playbacks.  

Again, when jack is up, envy24control is the tool for setting levels. However, you don't have to use it for that. You normally use the software levels in each application and leave the ACD and DCa levels alone, at 0 dB.

Cheers, Pablo

Audio production only. I will give aqualung a try after lunch.

List of apps: rodegarden, ardour, hydrogen, both the synth programs, etc.

Since 64 studio worked out of the box, and this is a dedicated audio machine, I will probably go to that.

---

### Post by mlinder on 2010-11-28
Yeah, nothing from aqualung.

From what I'm reading, there's issues with the output configuration of the Delta cards and pulse audio, etc.

Apparently no one is interested in fixing it.

Aqualung says "Output: PulseAudio @ 44100 Hz SRC Type: Linear Interpolator"

---

### Post by Pablo_F on 2010-11-28
> Audio production only

Then definitely, forget about pulseaudio and gnome sound preferences. 

Also, take a look at AVLinux. [http://www.bandshed.net/AVLinux.html](http://www.bandshed.net/AVLinux.html)

Cheers, Pablo

---

### Post by mlinder on 2010-11-28
> **Pablo_F said:**
> Then definitely, forget about pulseaudio and gnome sound preferences. 

Also, take a look at AVLinux. [http://www.bandshed.net/AVLinux.html](http://www.bandshed.net/AVLinux.html)

Cheers, Pablo


Interesting distro, have never heard of it before. Have you used it?

How does it compare to 64 studio or ubuntustudio?

---

### Post by cchhrriiss121212 on 2010-11-28
I have a Delta 44, and it is possible to get it working in Ubuntu, with or without pulse (though it is much easier without). What I would suggest is that you try turning up all the DACs/ADCs when testing (just in case), but beyond that I can't see why you are getting no jack output.

This is my opinion on what OS to use:
What I use now is a regular OS install, and add whatever programs I like on top. The pre-packaged distros like these are a great intro for new users, but if you know what you want (and it seems as though you do) then it is better to build it yourself. All the audio apps and kernels you can find in standard repos or PPAs. 

I could explain exactly what I have done in a few steps, but I don't know whether you will want the same set up as me. I would also say that 64studio is somewhat outdated now, the last stable release was 2 years ago.

---

### Post by Pablo_F on 2010-11-28
> Interesting distro, have never heard of it before. Have you used it?

I have tested it. It just worked, it has wonderful apps and plugins and it does not have pulseaudio. For your kind of work suites fine, I hope you are lucky with the kernel and graphic drivers. Support forum is here: [http://www.remastersys.com/forums/](http://www.remastersys.com/forums/)

 64studio is kind of obsolete. ubuntu / ubuntustudio is great for its huge number of packages in official and non-official repositories, because it has more users and it is very very flexible. But I think AVLinux suits better for musicians which don't like to deal with system configurations, especially sound related. All of them are debian based. 

Cheers, Pablo

---

### Post by mlinder on 2010-11-29
Pablo, have you noticed any issue with using a 32 bit PAE kernel vs a 64 bit kernel for audio production?

Looks like I'm FINALLY getting 10.10 64bit to work with the delta 44. It's not a RT kernel, though.

It looks like avlinux is an RT kernel, but 32 bit, with the ability to use all of my RAM, but at what cost?

---

### Post by Pablo_F on 2010-11-29
Hi, 

I (still) use ubuntu karmic, 32 bit version. I have 2 GB of RAM. I have no experience with PAE kernels. 

Read Chris's comments, I do the same, I build from the sources or install through PPA's.

This is just me but I would skip maverick for audio production. If I were you I would stick with ubuntu lucid + more recent packages of ardour, hydrogen... that you can find in some ppa's like philip5, autostatic, falktx... Use PPA's with caution though (install the needed packages, then disable). 

Cheers, Pablo

---

### Post by mlinder on 2010-11-29
Yeah, I was playing around a bit last night, and was not happy with the buffer size I had to implement in Jack to not get xruns while recording, with 10.10.

I could keep latency between 1.5 and 2.3ms with the older RT kernel...

I'll go back to that, then...

Shame, now that I got the delta card running in 10.10 :P

That AVLinux looked pretty cool, but I'm not convinced I'd be happy with a PAE kernel. There were too many areas in where a PAE kernel lags behind both the regular 32 bit kernel, and FAR behind the 64 bit. Didn't see any audio production benchmarks, but...

However, are you saying I should only go back to 10.04? I didn't see an RT kernel for it... I think it's important to have that.. And I think my xruns are largely due to the fact that I'm not running a RT kernel..

You don't think 9.04 and the RT kernel might be the way to go?

Thanks again for you time.

---

### Post by mlinder on 2010-11-29
Or see if the 'miracle patch' takes care of it...

[http://www.webupd8.org/2010/11/script-to-automatically-apply-200-lines.html](http://www.webupd8.org/2010/11/script-to-automatically-apply-200-lines.html)

---

### Post by Pablo_F on 2010-11-29
Hi, 

Afaik, there is a linux-rt in the lucid repos. It is a 2.6.31-rt. Nearly the same version as in karmic which is performing fine here. Also, Alessio Bogani's PPA has a 2.6.33-realtime for lucid.

xruns can be caused for different causes and you can make music with much higher latencies than 3 ms. Tweaking your system so you have a very low latency is not a trivial thing and it does not depend only on the kernel. I am not an expert though and months ago I gave up trying to understand everything. Lucid is a good base distro and AVLinux is a good out of the box distro.  I wouldn't go back to 9.04.

 That kernel patch... no idea, really. There has been some discussion in the LAU list but that goes beyond my knowledege.

Cheers, Pablo

---

### Post by mlinder on 2010-11-29
Yes, I'm not a fan of latency, though. Anymore than 10ms and things can get weird.

I'll check out the 10.04 RT, see how it works for me.

I'm adverse to the AVlinux because of it's 32 bit nature, and resource scheduling for > 4GB RAM.

I'll let you know how things go with the lucid RT setup.

---

