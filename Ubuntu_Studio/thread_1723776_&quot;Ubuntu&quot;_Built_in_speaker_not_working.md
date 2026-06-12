---
title: "&quot;Ubuntu&quot; Built in speaker not working"
date: 2011-04-07
forum: Ubuntu Studio
---

### Post by Manickaraj on 2011-04-07
I installed Ubuntu 10.04.2 LTS version in to Asus eeeTopET1610 PT PC. It has the following sound card configuration:

Sound Driver:3.8.1a-980706 (ALSA v1.0.23 emulation code)

Installed drivers: 
Type 10: ALSA emulation

Card config: 
HDA Intel at 0xfbbf8000 irq 29

Audio devices:
0: ALC887 Analog (DUPLEX)

Synth devices: NOT ENABLED IN CONFIG

Midi devices: NOT ENABLED IN CONFIG

Timers:
7: system timer

Mixers:
0: Realtek ALC887.

No audio output coming from the inbuilt speakers. when headphone is connected, audio is available with headphone. But not with internal speaker when headphone is not connected :(.

Please help me in fixing this issue.

---

### Post by DouglasAdams on 2011-04-07
this reply is simply to receive notifications of updates to this thread ...

---

### Post by AutoStatic on 2011-04-07
Try using ALSA instead of OSS.

Best,

Jeremy

---

### Post by Manickaraj on 2011-04-08
Im using AlSA but not OSS.

I checked Alsamixer and non of them are muted.
Also I verifed the following files
Through terminal, 
$cat /proc/asound/cards 
No such file or directory

But cards file is presnet under /proc/asound/ path. When i open through gedit the below driver is shown in the file.

 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xfbbf8000 irq 29
                      

and 
$cat /proc/asound/modules
 0 snd_hda_intel

Im sure the speakers are in working condition because the same speakers are working if i boot the system with windows OS.

---

### Post by Pablo_F on 2011-04-08
Hi, 

You might need to specify the model in a conf file. Check:

[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

If you are not sure, run the alsa-info scritp and give the URL.

Like this:

wget [http://www.alsa-project.org/alsa-info.sh](http://www.alsa-project.org/alsa-info.sh) -O alsa-info.sh && bash alsa-info.sh

Cheers, Pablo

---

### Post by Manickaraj on 2011-04-08
I checked the above mentioned link and i could not find the soundcard  ALC887 in 
either of /usr/share/doc/alsa-base/driver/HD-Audio-Models.txt.gz
or
/usr/share/doc/alsa-base/driver/ALSA-Configuration.txt.gz[FONT=Verdana]

[/FONT]

---

### Post by AutoStatic on 2011-04-08
Could you provide the output of **lspci | grep -i audio** ?
And it might help to install the **linux-backports-modules-alsa-lucid-generic** package.

Best,

Jeremy

---

### Post by Manickaraj on 2011-04-08
Here is the output of [B]lspci | grep -i audio:
[/B] 00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)

---

### Post by Pablo_F on 2011-04-08
Hi,

If you give the link we might help better.

---

### Post by Manickaraj on 2011-04-08
Here is the link for it.... 
[http://www.alsa-project.org/db/?f=5facd542e371cb2ca465852f9dad08cccfab97cc](http://www.alsa-project.org/db/?f=5facd542e371cb2ca465852f9dad08cccfab97cc)

---

### Post by Pablo_F on 2011-04-08
Hi, 

Sorry I was not clear enough. The alsa-info script gives info about your audio harware and software configuration, more complete than what you have provided so far. 

The command below gets the script and runs it, so the only thing you have to do is paste it to a terminal and give here the URL with the result which will appear in the terminal, if you wish. Needless to say, you have to choose "yes, upload" when you are asked for it.

```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh
```

Cheers, Pablo

---

### Post by Manickaraj on 2011-04-11
Thanks for your response... No Problem , i too did not execute the previous steps at that point of time. Now i executed and here is the link
[http://www.alsa-project.org/db/?f=5facd542e371cb2ca465852f9dad08cccfab97cc](http://www.alsa-project.org/db/?f=5facd542e371cb2ca465852f9dad08cccfab97cc)

---

### Post by Pablo_F on 2011-04-11
Hi, 

I found this:

[https://bugzilla.redhat.com/show_bug.cgi?id=677619](https://bugzilla.redhat.com/show_bug.cgi?id=677619)
(comment 1)
[https://bugtrack.alsa-project.org/alsa-bug/view.php?id=5047](https://bugtrack.alsa-project.org/alsa-bug/view.php?id=5047)
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/595094](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/595094)

Cheers, Pablo

---

### Post by Manickaraj on 2011-04-11
Im sorry, Headphone was connected during the previous log taken ... Now the new link without headphone connection. Still inbuilt speaker output is not there....
[http://www.alsa-project.org/db/?f=f0ace339fdc11868fc09289cdad718703841c2bc](http://www.alsa-project.org/db/?f=f0ace339fdc11868fc09289cdad718703841c2bc)

---

### Post by Manickaraj on 2011-04-11
Thanks for the links.... I too have the similler problem mentioned in the link "[https://bugzilla.redhat.com/show_bug.cgi?id=677619](https://bugzilla.redhat.com/show_bug.cgi?id=677619)". CPU Fan is always running and no audio output.

But i could not open the next two links :(

---

### Post by Manickaraj on 2011-04-11
I could not access [https://bugtrack.alsa-project.org/alsa-bug/view.php?id=5047](https://bugtrack.alsa-project.org/alsa-bug/view.php?id=5047) link to get the workaround provided for audio issue in the first link provided by you. Could you please copy paste the solution in this block... 

I registered for getting the login into "ALSA bugtracking system" but account activation is not yet done sofar.

Thanks,
Manickaraj

---

### Post by Manickaraj on 2011-04-11
Hi,
Thanks for your support.... By doing the workaround mentioned in the link [https://bugtrack.alsa-project.org/alsa-bug/view.php?id=5047](https://bugtrack.alsa-project.org/alsa-bug/view.php?id=5047) the actual issue is solved.

---

### Post by prat0318 on 2012-03-14
I am having the same situation, suddenly internal speakers have stopped running but headphones do work. I ran Dell diagnostics and found that speakers are fine.

This is alsa info script from my machine :
[http://www.alsa-project.org/db/?f=7a975db44ef7fb49c7a4d2bcf5d14e596cbc3355](http://www.alsa-project.org/db/?f=7a975db44ef7fb49c7a4d2bcf5d14e596cbc3355)

I have tried many options like re-installing alsa drivers, but that didnt work.
Please help me on this. Also let me know if a different thread was to be made for this.

Thanks.

---

