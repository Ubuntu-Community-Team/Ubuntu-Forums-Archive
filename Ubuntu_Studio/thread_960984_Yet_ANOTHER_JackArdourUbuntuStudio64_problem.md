---
title: "Yet ANOTHER Jack/Ardour/UbuntuStudio64 problem"
date: 2008-10-27
forum: Ubuntu Studio
---

### Post by El Lance-O on 2008-10-27
So I have scoured every single thread on the internet about Jack/Ardour problems within Ubuntu Studio, 32-bit AND 64-bit.

I have tried, EVERY SINGLE METHOD. Running as sudo, changing buffer options, realtime/no realtime, changing hardware, EVERYTHING.

This is my last cry for help, as I am a beginner in the music production world, and at this point I have way too much to get going to have unsolvable linux problems hold me back.

BUT, I absolutely love Ubuntu, and have been wanting to use Ubuntu Studio for a long time. I LOVE how it's set up, and all it comes with. But obviously it's useless if this is happening.

I am running on 64-bit on an eMachines motherboard, AMD CPU, SoundBlaster Live! 5.1 sound card, with Nvidia 6600, and 2 GB of RAM.

Now the problem is, Jack says it is connected just fine, but when I record in Ardour it lags, skips, crackles, or just doesn't work at all whatsoever.

I can record in other programs no problem with a little lag, but I would very much rather use Ardour.

System sounds are fine, and my soundcard has never had a problem before this. Is it just 64-bit? I tried posting there, but even the forums are buggy these days, wouldn't let me because I didn't have the privileges to? :confused:

Anyways, any help would be greatly appreciated as I shelled out over $1000 on a keyboard and Kaoss Pad just to get things going only to have JACK slap me in the face.

Thanks ahead of time for any help, although I don't expect much as I don't have much here but complaints. :(

---

### Post by XVampireX on 2008-10-28
Try the Jack/Ardour IRC channels they provide support pretty quick... if anyone's there

---

### Post by cek on 2008-10-28
What JACK settings are you using?
What sound card are you using?

---

### Post by scarrabri on 2008-10-28
Hi my dear friend i have in the past done a lot of recording with some very good software ,but for two years i have struggled with Ardour,and it is indeed the worst useless recording never to use again studio i have ever come across,i thought it must be me ,but i know better,and i have ,like yourself tried everything,all i can say is some one is having a laugh,good luck my friend Brian

---

### Post by DARKAD on 2008-10-28
Are you running a realtime kernel?

launch the terminal and paste: uname -a

let me know

---

### Post by scarrabri on 2008-10-28
Linux brian-desktop 2.6.27-7-generic #1 SMP Fri Oct 24 06:40:41 UTC 2008 x86_64 GNU/Linux
,is this what you are after,because this is what came up lol

---

### Post by drelyn86 on 2008-10-28
Have you tried increasing your latency?

---

### Post by yelserpdog on 2008-10-29
I'm no expert but I think you need the real time kernel. It explains how to get it here:

[https://help.ubuntu.com/community/UbuntuStudio/GettingStarted]("https://help.ubuntu.com/community/UbuntuStudio/GettingStarted")

I'm running 64bit Ubuntu Studio and have Ardour running fine after some teething problems. I get better latency than I did when I was on Windows.
Rock on
:guitar:

---

### Post by jejones3141 on 2008-10-29
> **El Lance-O said:**
> 
I am running on 64-bit on an eMachines motherboard, AMD CPU, SoundBlaster Live! 5.1 sound card, with Nvidia 6600, and 2 GB of RAM.


You might want to take a look at [the Ardour Linux system requirements web page]("http://ardour.org/linux_system_requirements"). For example, do you have a VIA chipset on your motherboard? The folks who develop Ardour strongly urge that you avoid VIA chipsets.

---

### Post by thorgal on 2008-10-29
don't want to scare you ... but if I were you, I would downgrade the kernel to 2.6.24.xxx

---

### Post by barisurum on 2008-10-29
Hi, configuring JACK for a system can be a hard task. 
First of all I suggest installing a realtime kernel for best latency results. Realtime kernels have an -rt in the end. 
As far as I know creative devices are well supported in ALSA, so that cant be the problem.
Use qjackctl's setup to configure your JACK system. Maintain a high priority ie: 70 - 80. Try with buffer sizes like 128 - 256 etc. And keep an eye on the xrun messages from the messages window. They must be at a lowest rate. A latency value of 10 ms or more starts to be audible. You may have a look at [here]("http://jackaudio.org/faq") for info about low latency. You can find more info about low latency in alsa's webpage too.
Post your JACK messages here, they give valuable info about what's going on in your system.

---

### Post by thorgal on 2008-10-29
I may be proven wrong by someone else but a low latency performance is not to be expected from kernels 2.6.25 and on (2.6.25 may be OK). 2.6.24 has been so far the best for the work. It sucks for those who need newer kernels with better support for h/w.

---

### Post by drelyn86 on 2008-10-29
I've done comparisons between the -generic kernel and the -rt kernel... there was absolutely no difference in audio performance or latency. The only thing the rt kernel ever did for me was create visual artifacts while running the fglrx driver.

---

### Post by kvk on 2008-10-29
Hi~

I'm having the same sort of issues getting JACK and all hardware/software to work correctly. I'm running UbuntuStudio on Ibex, and unfortunately I can't regress to older kernels that have rt already written, due to hardware issues.

When I open JACK, it synchs with my FP10 fine, and returns these specific error messages:

```

libiec61883 warning: Established connection on channel 0.
You may need to manually set the channel on the receiving node.
libiec61883 warning: Established connection on channel 1.
You may need to manually set the channel on the transmitting node.
15:48:24.924 JACK connection change.
15:48:24.925 ALSA connection change.
LibFreeBoB ERR: Dropped packets on connection 1
15:48:55.054 XRUN callback (1).
LibFreeBoB ERR: Dropped packets on connection 1
15:49:21.574 XRUN callback (2).
LibFreeBoB ERR: Dropped packets on connection 1
15:49:25.496 XRUN callback (3).
LibFreeBoB ERR: Dropped packets on connection 1
etc.

```

I am unable to get sound from my monitors either. I've experimented with turning the mobo sound card off/on, which makes no difference. When I spoke with Presonus before purchasing the FP10, they indicated the best course of action would be to disable the mobo soundcard and simply run everything through the FP10 as a standard procedure.

Which would be fine, but I can't seem to get there! :)

---

### Post by barisurum on 2008-10-31
> I'm having the same sort of issues getting JACK and all hardware/software to work correctly. I'm running UbuntuStudio on Ibex

   Are you using an rt kernel? If so the Ubuntu Studio team doesn't recommend using an rt kernel with ibex at this time. They say it supports only one processor (even if you have 2) and they report known issues about it. See the release note [[COLOR="Blue"][FONT="Georgia"]here[/FONT][/COLOR]]("http://ubuntustudio.org/8-10_release_note")

   So I stick to 8.04 for now and suggest you to do the same. Let's wait for them to polish. ;)

> LibFreeBoB ERR: Dropped packets on connection 1
15:48:55.054 XRUN callback (1).
LibFreeBoB ERR: Dropped packets on connection 1
15:49:21.574 XRUN callback (2).
LibFreeBoB ERR: Dropped packets on connection 1
15:49:25.496 XRUN callback (3).
LibFreeBoB ERR: Dropped packets on connection 1


   These look like alsa xrun reports, and if they are that much this means there's a problem in communication between your card and alsa driver. Try downloading and compiling the latest alsa driver from their website. Compiling the driver solves many known issues. Also you may have to create the kernel module for your card manually.

   But again I suggest downgrading to 8.04 first.

---

### Post by vivichrist on 2008-10-31
> They say it supports only one processor (even if you have 2) and they report known issues about it
this is good to know. I thought for a while that the generic kernel was rt in the same since jackd seemed to allow it. caused me no end of frustration and anger. but now I am at peace with the knowledge. cheers

---

### Post by kvk on 2008-11-01
No rt kernel for 2.6.27.4 yet, so I'm using the generic. I can't regress to 8.04 due to hardware issues either.

I've downloaded the ALSA drivers and such for 1.0.18- where do they live? Do I install them into the /usr/bin file?

---

### Post by barisurum on 2008-11-01
> I've downloaded the ALSA drivers and such for 1.0.18- where do they live? Do I install them into the /usr/bin file?

Sorry about the advice, I didnt see that your card was a firewire device. As far as I know alsa doesnt have firewire support. Freebob (ffado) has. So here is advice2:

   Go to: 
1. System/Preferences/Sound and see if there's an option for freebob or ffado. If there's then select that in every field instead of autodetect. If not try with every option. You should hear the sinus wave. Then try with JACK.

2. In Qjackctl/setup there's an option for driver, make sure freebob is selected.
Try to Jack.

In Ffado's (freebob) site you can find detailed info about compiling the driver yourself. [http://www.ffado.org/](http://www.ffado.org/). Sorry but I'm neither firewire nor freebob expert.

---

### Post by thorgal on 2008-11-01
> **thorgal said:**
> I may be proven wrong by someone else but a low latency performance is not to be expected from kernels 2.6.25 and on (2.6.25 may be OK). 2.6.24 has been so far the best for the work. It sucks for those who need newer kernels with better support for h/w.

hehe, I am proving myself wrong. I just compiled 2.6.27.4 on my linux DAW (debian sid) without any patch. Impressive, it seems to work even better (was running stuff at 0.7ms latency with ardour - 16 tracks + fx, rosegarden and dssi-vst via jack transport). It really is working at least as good as 2.6.24. The only thing I enabled is CONFIG_PREEMPT=y when configuring the kernel. 

Note: the intel gigabit ethernet adapter that used to require the kernel module e1000 needs now e1000e (change that occured after 2.6.24 I think).

---

