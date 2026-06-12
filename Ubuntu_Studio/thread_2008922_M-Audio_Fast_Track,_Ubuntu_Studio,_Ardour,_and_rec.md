---
title: "M-Audio Fast Track, Ubuntu Studio, Ardour, and recording bass"
date: 2012-06-23
forum: Ubuntu Studio
---

### Post by MrBalloonHands on 2012-06-23
Before I begin I would like to say if I kinda sound condescending or mean, it's because I've posted a couple of threads, and done extensive research on this subject with absolutely no luck, and it's starting to get really aggravating. 

Ok, I'm new to all this, and all I want to do is record my bass in to Ardour THAT's IT. Below is a previous post I made, where someone was nice enough and try and help me, but it didn't do the trick. 

[http://ubuntuforums.org/showthread.php?p=12048825&posted=1#post12048825](http://ubuntuforums.org/showthread.php?p=12048825&posted=1#post12048825)

This is the type of device I have:

[http://www.americanmusical.com/Item-...FUJo4AodnV9Ezw]("http://www.americanmusical.com/Item--i-MII-FSTRKMK2-LIST?src=Y0802G00SRCHCAPN&utm_source=google&utm_medium=cpc&utm_campaign=PLA&gclid=CLzUrIzp4LACFUJo4AodnV9Ezw")

All I wast to do is be able to plug in my bass in to my M-Audio Fast Track Standard and record in Audour so I can share rough takes of tracks.

If anyone can help, maybe have a step by step guide that would be GREATLY appreciated. 

Thanks ahead of time.

---

### Post by jejeman on 2012-06-23
Opening multiple threads for the same question will not get you faster to solution. When asking on forums one must show patience.

---

### Post by sgx on 2012-06-23
The Connect button is lower right corner of the main qjackctl gui,
and on that panel that opens, there is another Connect button.
Make sure to press this one to 'make' the connections between
highlighted left/right items you select. (same for disconnections)

You have permission to be frustrated, and angry :popcorn:


Everybody experiences some bumps on the journey :wink:

from your command output screenshot, I see two phrases in brackets naming your maudio device as Fast Track, and Track.

Go to qjackctl Setup page, then at Input Device >

click the > widget, and type in Fast Track

It might currently say hw:0 or something else, at present.

Now in Output Device >  it should mention Intel xyz, and will
probably work, its your motherboard sound chipset. You can replace
whatever is there with

HDA Intel

Stop qjackctl, and restart it, for the changes to apply.

I think the Fast Track can also be the playback device.
In that case, replace HDA Intel with Fast Track. See which one
gives the best results.

The Mix knob on the FastTrack must be utilized for proper playback.

If in different sessions, various usb devices are swapped in/out,
these named references should still be found, whereas hw1,0
type of ID can be misplaced, leading to silence, and frustration.
Cheers

---

### Post by sgx on 2012-06-23
Also, timemachine is excellent for recording single takes,
default is a 24bit .w64 (Sound Foundry) file. .wav is an option
in its prefs, or as a command line option.

Import the file in audacity for fx, edits, and
export in common formats. 

vlc plays .w64 files, should one want to overdub a track or two
connecting vlc and timemachine in qjackctl.
Cheers.

---

### Post by MrBalloonHands on 2012-06-23
SGX,

Yeah, I'm not getting any signal at all when I press record. I however do now hear the click track, so that's progress. I have another screen shot of the JACK setting that I put in from what I understood what you typed. I have no idea what I'm doing wrong. I tried typing the names in the Input/Output, but the server would not start that way. I noticed that a lot of the other settings are set to default. Is this normal? 

[ATTACH]220125[/ATTACH]

---

### Post by MrBalloonHands on 2012-06-23
Here are my connection settings. If you see anything wrong please let me know! 

And thanks for all your help so far. It's greatly appreciated. 

[ATTACH]220126[/ATTACH]

---

### Post by sgx on 2012-06-24
Hi, a few things based on new screenshots, to make things easier,
for now.

[http://packages.debian.org/unstable/sound/](http://packages.debian.org/unstable/sound/) 

timemachine is in this list,
if you don't have it in your ubuntu package manager, click its link,
then scroll down below the dependencies to the Architecture area
and choose based on your cpu. This opens a list of ftp sites to
download from. the file will have a .deb 
to install timemachine, issue command:

sudo dpkg -i timemachine_0.3.3-1_i386.deb for i386

differen a bit, based on the architecture you download

To run it, type timemachine in a terminal, or choose it
from a menu. Next:reboot, then

issue command

killall pulseaudio

This pulse is looking for some surround sound,
and needs to die. :guitar:

Now start qjackctl, click the cursor in the Input Device field, to the right of hw:2, backspace to remove hw:2 and type in Fast Track. 

Restart qjackctl, and start timemachine. Go to the Connection page
of qjackctl, in the Audio tab, on the bottom left, System is your
Fast Track, and System on the right, is the Output Device chosen in qjackctl, either HDA Intel, which is your motherboard audio out, or
the Fast Track headphone out, depending on whats chosen.

timemachine should be on the right, below System. Select and highlite
System on both left and right, and press the Connect button on this
panel. Now select and highlite Timemachine, and press connect.

Timemachine green gui has a meter to show incoming audio level,
press the big button when ready to record.

Giving the fasttrack a constant sound source during testing, will alert you to success. mp3 player, Cd output etc

Cheers

---

### Post by MrBalloonHands on 2012-06-24
Ok, so I downloaded and installed Timemachine. I killed pulseaudio, but I couldn't do the next step about renaming input/output cause when I do, I get an error saying it can not start server, and in the messages saying it can not find the directory i.e. Fast Track and HDA Intel. 

Sorry about keeping using screen shots, but it;s the only way that I know of showing the issues. 

But when I put Input as HW:2 it worked and same result with putting Output as HW:0. I got time machine to work and when I played the bars went up showing it got a signal but now no sound. 

But NOW nothing works. I can't get jacks to work now and no signal or sound in timemachine. You can find a few screen shots below. 

I'm getting really confused. I just want to record a track. I liked the ardour more cause i need to record to a click track. Can we do this for audicy?

---

### Post by MrBalloonHands on 2012-06-24
I GOT IT!!!! It works. Thanks for all your help. It's greatly appreciated.

---

### Post by sgx on 2012-06-24
:guitar:

If you post what worked, it will help future google searchers.

Lots of youtubes out there for ardour session details.
Cheers

---

