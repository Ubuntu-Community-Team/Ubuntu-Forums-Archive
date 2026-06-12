---
title: "Convert video for PSP, Ipod, PocketPC"
date: 2007-11-04
forum: Tutorials
---

### Post by netyire on 2007-11-04
_**What's This**_

It's a python frontend (license under GPL) for mencoder for converting video files for your PocketPC/PDA/PSP/iPhone/iPod.

It works on linux/windows and requires very few dependencies. (All of which are available in the repositories)

_**Features**_

1. Idiot-proof, no-knowledge required interface: choose your device, pick the input and output, queue up all desired files you want to watch, and hit 'start'.

2. Encodes all mplayer playable files. [AVI, MP4, WMV, MOV, RAM, etc]

3. Heavily tweaked and tested PocketPC/PDA presets. Works with TCPMP ([http://picard.exceed.hu/tcpmp/test/]("http://picard.exceed.hu/tcpmp/test/http://picard.exceed.hu/tcpmp/test/")).

4. Untested PSP and iPhone presets. (Based on internet posts, no real-world tests conducted.)

**_Running PPCV_**

1. Download PPCV.py.zip and unzip the file
2. Run "sudo apt-get install python python-tk mencoder mplayer" in a terminal
3. Right click on PPCV.py and select "Open With"->"Choose Application"
4. Type "python" in the box and click OK.

You only need to do this the first time you run the program, after which just double click PPCV.py to launch the application.

**_Using PPCV_**

1. Click "Modify Template"->"Preset"->[Your Device]
2. Select the input file
3. Select the output file
4. Hit queue
5. Repeat 2-4 for any other desired file, then click Start

**_Misc Notes_**

- An "Encode Report" window appears at the end of the encode run, the PSNR (video quality) is listed here, anything around 45 is very, very good. If it's below 35 you might want to get better source material. (Download another torrent)
- The post has been rewritten to refer to the newer PPCV.py, Movie2Mobile.py has been retired after a few months of testing PPCV and won't be updated anymore. Kept solely for reference purposes when reading posts 2 & 3.
- I'll post any significant changes here asap, but if you want to use PPCV as and when it changes, the latest code can always be downloaded here (correct to the latest second thanks to dropbox): [http://dl.getdropbox.com/u/264637/PPCV.py](http://dl.getdropbox.com/u/264637/PPCV.py)

---

### Post by pssturges on 2008-02-12
Great work!

It's a pitty your works seems to have gone unnoticed until now.

I have really been struggling to find a solution to convert videos that have LPCM audio. This is the first one that I have been able to find that does it, windows or linux!

I have managed to tweek the settings as you suggested for my Ipod classic, the only problem is, that the ipod only accepts .mp4 & .mov files. The only output i seem to be able to get from this program is avi. Is there anyway to alter that?

It would be nice to be able to use the h264 codec if possible?

The other thing is that my videos are wide screen, and are being squashed to fit standard screen ratios, is there a way to tweek the settings for this?

Anyway thanks again for your great work!

Phil

---

### Post by VMan on 2008-02-13
I had been using a Windows only program to easily convert the files.  I have the program set to change the resolution to 320x240 (the size of my device's screen) and the frame rate to 18fps.  I used this for TV captures.  Can you post some details on customizing this for similiar settings (resolution; I saw the fps setting).  I no longer have the PPC I was using (got stolen), but have a Motorola Q that I will be using with TCPMP.

Can't wait to try this when i get home and have Ubuntu available.

---

### Post by netyire on 2008-07-07
**[B]Improved Script On Post 1 (PPCV.py)**
[/B]Hey VMan sorry for the extremely long reply time (about 5 months). Since then the conversion routine has been improved upon to accommodate smoother and hopefully higher quality playback even on low powered devices. I've also written a new script which I think is better than the original due to the use of better parameters for mencoder. Some of the new features include previewing of the output as it is being converted, automatic preservation of video aspect)
 
**PSNR Logs**
PSNR Logs are now produced. PSNR wise ~45 is very good and <35 is approaching bad I think.
 
**Refining The Parameters For Your Device**
Read up on the Motorola Q. Here are the specs I've found (correct me if I'm wrong):
Display: 320x240, 65K Colors TFT
CPU: 312MHz
OS: Windows Mobile 5.0
Looks like the Motorola Q should be able to handle a higher bitrate and/or framerate. Try changing the framerate under ofps to about 14 or 15. Audio bitrates can be at 64 but I think it's good enough as it is. The vrc_maxrate can be set around 450 and the vbitrate to about 400. Play around with the settings, the existing command above produces good quality videos which require very little processing power - it'll play well at half of your CPU power.
 
**Troubleshooting**
Very eager to hear how it turns out, if you're using something besides the Motorola Q but still using TCPMP right now, find out what the specs are. More processing power means a higher framerate and bitrate (for both audio and video) and make sure to scale the video correctly for the device.

---

### Post by netyire on 2008-08-08
> **pssturges said:**
> Great work!
 
It's a pitty your works seems to have gone unnoticed until now.
 
I have really been struggling to find a solution to convert videos that have LPCM audio. This is the first one that I have been able to find that does it, windows or linux!
 
I have managed to tweek the settings as you suggested for my Ipod classic, the only problem is, that the ipod only accepts .mp4 & .mov files. The only output i seem to be able to get from this program is avi. Is there anyway to alter that?
 
It would be nice to be able to use the h264 codec if possible?
 
The other thing is that my videos are wide screen, and are being squashed to fit standard screen ratios, is there a way to tweek the settings for this?
 
Anyway thanks again for your great work!
 
Phil
Hi pssturges, apologies also for the late reply. The problem with widescreen videos has been corrected. There is a beta psp profile now, feel free to test it out. It's in the newer PPCV.py file in post1. Please post if it does/does not work, very interested to find out.
 
To activate the profile:

1. Run PPCV.py
2. Click "Modify Template"->"Preset"->"PSP"

---

### Post by fachex on 2008-12-07
> **pssturges said:**
> Great work!

It's a pitty your works seems to have gone unnoticed until now.

Phil

Great software!! I totally agree with Phil, I can't believe such useful and on-demand application is not as known as it should be. 
I just finished converting my first movie and it did a great job. Very tiny A/V sync problem, but it could be my PPC or my settings. For most people maybe unnoticeable. 
I just want to say thank you. You saved me again of going to windows for this kind of app. 
I did noticed ( at least in the attached version that you posted) that there is no option for 640x480 resolution that some PPC have (like mine, HTC Raphael). Is there any way you can add that option? 

Fabian

---

### Post by abdusamed on 2010-09-13
Can it embed subtitle like hard sub into the videp for ipod convert video?

---

### Post by samiscool30 on 2012-07-25
Can't get it to open with Python.  When i do Open with another application, and click show other application i couldn't find Python.  I am using 11.10 Ubuntu.

---

### Post by thatguruguy on 2012-07-25
Old thread is old.

In the meanwhile, use [handbrake]("http://handbrake.fr/").

---

