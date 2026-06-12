---
title: "Can't record sound in anything... Ubuntu 9.04"
date: 2009-10-28
forum: Ubuntu Studio
---

### Post by judge jankum on 2009-10-28
I've tried Ardour,Audacity, Sound Recorder, Have Jack and it wont start either.....Ido have sound working in all audio and video i play...My sound card is listed "Ensoniq AudioPCI"....I have a guitar tuner that works great through the line-in or the mic...But i get error messeges trying to run Ardour and Jack...and Sound Recorder freezes as soon as i  click record... HELP!!!!!!!!!!!!!!!!!!!!!!!!! I love Ubuntu!!!!!! But i need to record!!!!
 I tried N-Track Studio also, installed through wine, but got the error "chunk contains no data"

---

### Post by judge jankum on 2009-10-28
In Ardour i get the error message "Ardour could not start Jack" Audacity freezes and I have to "force quit" the program...
N-Track gives the message "chunk contains no data"

---

### Post by judge jankum on 2009-10-28
List of PLAYBACK Hardware Devices ****
card 0: AudioPCI [Ensoniq AudioPCI], device 0: ES1371/1 [ES1371 DAC2/ADC]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: AudioPCI [Ensoniq AudioPCI], device 1: ES1371/2 [ES1371 DAC1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

Sound recorder also freezes when i click record

---

### Post by murderslastcrow on 2009-10-28
Odd. I'm going to look into this a bit more soon, but go into volume controls and make sure your mic and line-in aren't muted at all.

If you can tell us the model number of your computer, it may help us to narrow down to the most accurate version/model of this sound card. Unless, of course, you installed it manually.

---

### Post by judge jankum on 2009-10-28
This whole computer is built from scraps and spare parts. My other puter died with bad mother board and i scrapped this one together....Ubuntu worked great on the other one from the install. This one works great except i can't record audio.
 Jack gives the message "can not start jack"
I switched from XP so I don't know anything about fixing problems in Ubuntu, but i sure like it better when it's working.

---

### Post by kayosiii on 2009-10-28
Yeah Jacks configuration is broken by default in Jaunty...
Somebody asks about this problem on this forum pretty much every day.

You need to either untick the realtime option in Jack Control or
modify your computers security settings to allow audio applications to access realtime resources.

You should be able to pick out further instructions from the many many existing threads on this problem :)

---

### Post by AutoStatic on 2009-10-28
> **judge jankum said:**
> List of PLAYBACK Hardware Devices ****
card 0: AudioPCI [Ensoniq AudioPCI], device 0: ES1371/1 [ES1371 DAC2/ADC]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: AudioPCI [Ensoniq AudioPCI], device 1: ES1371/2 [ES1371 DAC1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

Sound recorder also freezes when i click recordES1371? That's a Creative Soundblaster that is like 10 years old? I would advise to swap the soundcard for another one, I reckon almost anything else would work better.

---

### Post by murderslastcrow on 2009-10-28
If there are any settings regarding the sound in your BIOS, it may also be a good idea to see if any of them could be tweaked. Many SoundBlaster cards work great after you disable certain settings for them in the BIOS.

---

### Post by trulan on 2009-10-28
> **AutoStatic said:**
> ES1371? That's a Creative Soundblaster that is like 10 years old? I would advise to swap the soundcard for another one, I reckon almost anything else would work better.
Correct, pretty much.  It was also a great card in its day, one of the best at full duplex (recording and playing back at the same time) and a great price to top it off - beat pretty much anything else for multitracking.  Still a good card IMO - though how it would or wouldn't perform in Ubuntu is another matter...

That comment isn't meant to be helpful, you just brought back some memories...

---

### Post by judge jankum on 2009-10-28
Just noticed 9.10 is almost ready to grab! I'm thinking of doing a clean install of that and see if it corrects my problem...
                      Your thoughts on the pro's and con's much appreciated

---

### Post by judge jankum on 2009-10-28
I get this when i try to start Jack

p, li { white-space: pre-wrap; }  [COLOR=#999999]22:55:12.153 Patchbay deactivated.[/COLOR]
 [COLOR=#999999]22:55:12.593 Statistics reset.[/COLOR]
 [COLOR=#66CC99]22:55:12.753 ALSA connection graph change.[/COLOR]
 [COLOR=#CCCC99]22:55:13.362 ALSA connection change.[/COLOR]

---

### Post by kayosiii on 2009-10-29
9.10 has a much better realtime kernel.... There is a backport of this in a PPA should you want to use it for 9.04 

Jack's configuration is still broken out of the box so you still have to do a bit of work to get jack up and running properly. (maybe not so much in the studio variant?)

---

### Post by AutoStatic on 2009-10-29
> **trulan said:**
> Correct, pretty much.  It was also a great card in its day, one of the best at full duplex (recording and playing back at the same time) and a great price to top it off - beat pretty much anything else for multitracking.  Still a good card IMO - though how it would or wouldn't perform in Ubuntu is another matter...

That comment isn't meant to be helpful, you just brought back some memories...I recall those cards were shipped with two different chipsets of which one didn't work (at least not on my Slackware 7 installation back in the days).

judge jankum, you could try the 9.10 LiveCD for starters. And the JACK output is too minimal, is that all you get? And what are your settings for Audacity (Edit - Preferences - Audio I/O & Quality)? Could you post screenshots of those settings?

---

### Post by judge jankum on 2009-10-30
Get this with Audacity........

Expression 'err' failed in 'src/hostapi/alsa/pa_linux_alsa.c', line: 2468
Expression 'ContinuePoll( self, StreamDirection_In, &pollTimeout, &pollCapture )' failed in 'src/hostapi/alsa/pa_linux_alsa.c', line: 2948
Expression 'PaAlsaStream_WaitForFrames( stream, &framesAvail, &xrun )' failed in 'src/hostapi/alsa/pa_linux_alsa.c', line: 3310
HCK OnTimer
Segmentation fault

---

### Post by AutoStatic on 2009-10-30
What are your settings in Audacity? Apparently Audacity segfaults because your current settings are not optimal.

---

### Post by judge jankum on 2009-10-30
I'm not sure how to dchange the settings in Audacity, 

Latency Correction setting has caused the recorded audio to be hidden before zero.
Audacity has brought it back to start at zero.
You may have to use the Time Shift Tool (<---> or F5) to drag the track to the right place.

---

### Post by AutoStatic on 2009-10-31
Hello judge jankum, what are your current settings in Audacity (Edit - Preferences - Audio I/O & Quality)? Could you post screenshots?

---

### Post by judge jankum on 2009-10-31
Maybe i attached these right...

---

### Post by trulan on 2009-10-31
The only thing I see majorly wrong is the 32 bit float sampling.  You have a 16 bit card.

---

### Post by judge jankum on 2009-10-31
ok, changed the settings to 16 bit...
 Still no audio signal showing in the meter, when i hit record it stops after 1 second and gives latency messege

---

### Post by judge jankum on 2009-11-01
ok, the mic is working and i have an audio signal, but Audacity stops in 1 second and still gives latency messege

---

### Post by AutoStatic on 2009-11-01
thanks for the screenshots! You should try disabling the Software Playthrough option (Audio I/O window).

---

### Post by judge jankum on 2009-11-02
I just did a clean install of 9.04 again, got Audacity, and i have no audio showing in the meters" It has to be something i'm doing wrong,,,,

---

### Post by judge jankum on 2009-11-02
Ok, now Audacity is picking up the mic, but the reading on the level meter is low..I checked and all mic volumes are wide open...And when i hit record it catches the first 2 words if i'm fast...then nothing...

---

### Post by judge jankum on 2009-11-02
I just loaded a pre-recorded wave file into Audacity, and it played fantastic..

---

### Post by AutoStatic on 2009-11-03
> **judge jankum said:**
> ok, changed the settings to 16 bit...
 Still no audio signal showing in the meter, when i hit record it stops after 1 second and gives latency messegeMaybe you should increase the latency (Edit - Preferences - Audio I/O - Latency - Audio to buffer).

---

### Post by judge jankum on 2009-11-03
Ok, it set at 100 on install...Is there any certain numbers i need to go by? or just increase and see what happens? I'm a newbie to all this.

---

### Post by AutoStatic on 2009-11-03
I don't have the faintest clue, I'm sorry. Apparently your machine is simply not up to par to run 9.04, maybe you could provide some more detailed specs of your machine?

---

### Post by judge jankum on 2009-11-03
This thing is built out of old spare parts, The sound and video cards were found in the floor lol" My ram came from and old tower found in a dumpster"
I may try changing the latency settings and see what happens

---

### Post by AutoStatic on 2009-11-04
> **judge jankum said:**
> This thing is built out of old spare parts, The sound and video cards were found in the floor lol" My ram came from and old tower found in a dumpster"Those are not very detailed specs. Could you post the outcome of **lspci** in a terminal?

---

### Post by judge jankum on 2009-11-04
How do i do that? i'll be glad to post it

---

### Post by AutoStatic on 2009-11-04
Applications - Accessories - Terminal
And then type **lspci** and press enter. It will give some output that you can copy and paste. Just select it with your mouse, right click and select copy.

---

### Post by judge jankum on 2009-11-04
00:00.0 Host bridge: Intel Corporation 82850 850 (Tehama) Chipset Host Bridge (MCH) (rev 02)
00:01.0 PCI bridge: Intel Corporation 82850 850 (Tehama) Chipset AGP Bridge (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 02)
00:1f.0 ISA bridge: Intel Corporation 82801BA ISA Bridge (LPC) (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801BA IDE U100 Controller (rev 02)
00:1f.2 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 02)
00:1f.3 SMBus: Intel Corporation 82801BA/BAM SMBus Controller (rev 02)
00:1f.4 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation NV11 [GeForce2 MX/MX 400] (rev b2)
02:0b.0 Ethernet controller: Davicom Semiconductor, Inc. 21x4x DEC-Tulip compatible 10/100 Ethernet (rev 31)
02:0c.0 Multimedia audio controller: Ensoniq ES1371 [AudioPCI-97] (rev 09)

---

### Post by AutoStatic on 2009-11-05
Thanks for the info! Intel Tehama? Googled that one, that chipset is like 10 years old! I fear that your system is simply not up to par for running a modern distribution and that it will never run flawlessly. Apparently recording just takes too many resources. That's just my opinion of course, maybe someone else has a clue, but I'm out of options.

---

### Post by judge jankum on 2009-11-05
I hadn't thought of that, but it could just be to out of date for Ubuntu and some of the software.
I used N-Track Studio in XP but can't figure out how to set it up in Wine...yet lol"
I was in shock this old relic even booted up" Other than the recording issue Ubuntu works much better than the other systems i've used..
 I'll do another check and make sure my cables are good..
 I appreciate everybodies help with this much.

---

### Post by Fishnuts on 2009-11-23
Confirmed on my system. I've been having the same issues with audacity or any other recording software when trying to record from this card:

01:06.0 Multimedia audio controller: Ensoniq ES1371 [AudioPCI-97] (rev 06)

It freezes after a second when recording in audacity. It used to work good in Intrepid but doesn't work in Jaunty and Karmic. I think it may be a pulseaudio issue because I can record on slackware13 with the same hardware with alsa and no pulseaudio.

---

### Post by AlexanderDGreat on 2011-04-13
I'm using Ubuntu LTS 10.04, Behringer UCA 200 usb soundcard, lsusb

Bus 004 Device 004: ID 08bb:2902 Texas Instruments Japan

I can confirm this also happens to me.

I wish there's a way to solve this.

---

### Post by drs305 on 2011-04-13
> **AlexanderDGreat said:**
> I'm using Ubuntu LTS 10.04, Behringer UCA 200 usb soundcard, lsusb

Bus 004 Device 004: ID 08bb:2902 Texas Instruments Japan

I can confirm this also happens to me.

I wish there's a way to solve this.

Since this thread is very old and you are using a different release than the thread title, please start a new thread of your own. You will most likely get better responses.

---

