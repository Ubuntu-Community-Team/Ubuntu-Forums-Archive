---
title: "Problems Recording With Audacity"
date: 2005-12-19
forum: The Cafe
---

### Post by Kregel on 2005-12-19
Alright so I've got a mic going into a mixer which is going into my computer. The recording program i'm using on my computer is Audacity. I push record it records one track fine. I push record again to try and record a second track on the same file, which it appears to record just fine. My problem arrises in the play back. In the playback the first track sounds just fine but the second track sounds ungodly low and/or distorted.

 Is there anyway to record two tracks on the same file? or to record a second track if the first track is a click track?

---

### Post by nalmeth on 2005-12-19
With Audacity you're supposed to be able to record as many tracks over one-another as you wish.

I actually had a similar problem, and it has only occured on Ubuntu. Ubuntu has some multimedia shortcomings that I've heard about, and this is what it probably has to do with.

Does it sound garbled only when you are listening to it as you are recording it? Because as soon as I stopped it and listened to it with both tracks, it actually sounded fine. It was only during recording that sound was garbled.

Try just going all the way through with recording and listening to it afterward. It may just be a minor annoyance if you can live with it. If this isn't the situation for you, just post some more info. What sound engine are you using? What kernel do you use?
Theres probably a way to resolve this. (sound engine, different editor, etc)

I like audacity so I can understand if you want to just fix it and stick with it.

---

### Post by Kregel on 2005-12-19
My problem actually sounds like the opposite of yours...It sounds just fine while recording the two tracks together, but listening to them afterwards is what's all garbled...


I actually don't know what sound engine or kernal i'm using...How would i find that out?

---

### Post by nalmeth on 2005-12-20
Are you using KDE or Gnome?
If you're using KDE, I've heard the KDE sound system can cause problems with other sound apps/engines. Try deactivating/activating it in KDE control center.

You can find out specifically what engine Audacity is using in Audacity
EDIT -> Preferences
There may be options here. 

I would guess that you are using ALSA, so you may want to install the OSS, if it isn't already. Google it with 'ubuntu' or 'ubuntuforums', along with anything else you think might be relevant. This forum is excelent, and there may be a how-to or thread that describes exactly this situation.

I only asked about the kernel in case anyone knew specifically if this could be a kernel related problem. Which architecture did you install? The basic i386 version, AMD64, or other? 

AMD64 and i386 gave me different sound behaviors, but if you have a 32-bit computer, AMD64 will do you no good.

Ardour is aparently a good music recorder/editor, but it runs on the Jack sound-system, which aparently is a little tricky to set-up. I haven't really pursued it yet, but I think I might tonight. It sounds worthwhile.

One last suggestion I can offer, is to install wine (if you haven't already), and install the windows version of Audacity. It has helped me out suprisingly, in funny situations.

EDIT:
A good place to post this type of question is in the HARDWARE - SOUND/VIDEO forum for UBUNTU or KUBUNTU

---

### Post by freedomjazzdance on 2005-12-30
yeah i think i had a problem just like that.   File>Prefs>  and then in the recording sectoin there is "Channels"  put it to more than one.

---

### Post by blueturtl on 2005-12-30
Gentlemen, I have your answer:

This has to do with the audio system support in Audacity!
It seems the version of Audacity in the repositories is compiled for OSS (most of us today use ALSA). I corrected the problem by compiling Audacity myself.

This is how I got it to work:

**./configure --with-portaudio=v19** (default =v18, which causes the buggy recording)
**make**
**sudo make install** or alternatively **sudo checkinstall**
(this tool will create a neat deb package of the compiled files for you to install)

There's a few dev-packages you need to install to be able to compile Audacity with most options enabled though.

---

### Post by Thumpy on 2006-04-29
I've been using AUDACITY on Windows 2000 Pro w/ SP4 going on around 6 months. I just upgraded to 1.2b. I've had pretty good luck thusfar figuring out how to use it. However, I have noticed some things that I wasn't sure if it was me doing something wrong outta ignorance, or if the application hick-up'd? I am currently trying to locate other users (I run only W2K version) that I can share information and exchange ideas with to better familiarize myself with digital recording on my computer.  And I can't even spell UBUNTU muchless know what it is or does.  Sounds like some O/S dirivitive from UNIX??


ANYBODY OUT THERE HEAR MY CALL??

email reply to: THUMPY
[email]vunovich@kc.rr.com[/email]

---

### Post by Rotarychainsaw on 2006-04-30
I say search this forum for a .deb of the audacity beta thats out. Works awesome!

---

### Post by hallbuzz on 2008-07-18
I was  able to record with Audacity in the following way:
1.  Right click on the volume control icon (little speaker picture bottom toolbar)
2.  Click on Open Volume control
3.  Click on Edit in the window which is then presented then Preferences
4.  Tick the Master, Microphone, Microphone Capture and Mic Select boxes
5.  Call up the volume Control menu again
^ Click on Switches and tick the Microphone capture box
7. Click on Options and in Mic Select select Mic 2

---

### Post by zmjjmz on 2008-07-18
Dude, this thread is **old**
Really old.

---

### Post by hanzomon4 on 2008-07-18
It may be old but with Pulse Audio I can't get audacity to record and it bugs the hell out of me

---

