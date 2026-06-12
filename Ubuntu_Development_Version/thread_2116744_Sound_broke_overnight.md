---
title: "Sound broke overnight"
date: 2013-02-16
forum: Ubuntu Development Version
---

### Post by cole.mickens on 2013-02-16
So, my sound stopped working, seemingly overnight. I'm guessing it's PulseAudio. I have my xbox piped in through the line in and enabled via alsamixer and I can always hear that (as I expect), but my other applications: Nada. I heard the KDE login sound (ugh) and then nothing. No VLC, nothing from Chrome, Clementine doesn't play, and in fact doesn't even progress through the song (the same behavior it exhibited when I had PulseAudio directed to a bad output device). 


So, is there anything I can check on?

---

### Post by craig10x on 2013-02-16
I'm getting the same...no sound on videos, streaming radio in Google Chrome...no sound on VLC media player either when i play videos...
I believe there was a pulse audio update yesterday or today...and that seems to have knocked it out...

Update: i re-booted and got sound back for google chrome stuff (radio steams, Streaming video, etc)
However, when i opened VLC media player, no sound there and then when i went back to Chrome again, knocked the sound out for that again...
So, as long as i boot up and don't go to VLC to play videos, i am fine, but once i do, it borks the Chrome sound as well...

Seems to be from the pulse audio updates which we received yesterday, i believe...

So far, we are the only ones posting about it...it seems that whatever came in those updates make it so that if you should open vlc and play a video, the sound gets knocked out on vlc and also then knocks it out for any sound on your web browser as well...Only re-booting will restore the sound to the browser, but then you can't dare go to open a video in vlc again because it will knock out the sound COMPLETELY for everything....

---

### Post by cole.mickens on 2013-02-16
> **craig10x said:**
> I'm getting the same...no sound on videos, streaming radio in Google Chrome...no sound on VLC media player either when i play videos...
I believe there was a pulse audio update yesterday or today...and that seems to have knocked it out...

Update: i re-booted and got sound back for google chrome stuff (radio steams, Streaming video, etc)
However, when i opened VLC media player, no sound there and then when i went back to Chrome again, knocked the sound out for that again...
So, as long as i boot up and don't go to VLC to play videos, i am fine, but once i do, it borks the Chrome sound as well...

Seems to be from the pulse audio updates which we received yesterday, i believe...

So far, we are the only ones posting about it...it seems that whatever came in those updates make it so that if you should open vlc and play a video, the sound gets knocked out on vlc and also then knocks it out for any sound on your web browser as well...Only re-booting will restore the sound to the browser, but then you can't dare go to open a video in vlc again because it will knock out the sound COMPLETELY for everything....

I thought that I had had something similar as well, but I tried rebooting and couldn't get Clementine or Chrome to work, even whilst avoiding VLC. :(

I'll just wait a few days and hope PulseAudio gets an update or start bug hunting on Launchpad I guess.

---

### Post by craig10x on 2013-02-16
Yeah..i guess i will have to do the same :(

Well, i don't know if it will help, but try avoiding going into any media player and see if re-booting at least brings back the sound for stuff on your browser anyway...

Hope some updates over the next few days will correct it...
let me know if you discover any fixes along the way...

Funny part was i was just thinking how smooth the updates were going so far since installing 13.04...

---

### Post by cole.mickens on 2013-02-17
> **craig10x said:**
> Yeah..i guess i will have to do the same :(

Well, i don't know if it will help, but try avoiding going into any media player and see if re-booting at least brings back the sound for stuff on your browser anyway...

Hope some updates over the next few days will correct it...
let me know if you discover any fixes along the way...

Funny part was i was just thinking how smooth the updates were going so far since installing 13.04...

Yeah, I don't mind some breakage this early on, comes with the territory.

This time when I restarted, I get sound from TF2. I'm afraid to open VLC though. :)

---

### Post by craig10x on 2013-02-17
I have an interesting update for you...

I get the impression that the updates broke the vlc media player in that if you try to play a video, you get no sound and then it also breaks the sound on everything else (like on the web browser when you try to listen to stream radio or watch a streaming video)...

However, i can play mp3s in VLC and the sound is fine and it doesn't break the sound on the entire system...

And...I can play VIDEOS on Totem Movie Player (the one ubuntu includes by default) and the Video Plays fine and the SOUND is fine ON THE VIDEO and it then DOES NOT BREAK the sound on everything else...

So....as long as i don't try to play a video on VLC...everything else is NORMAL....

Which means i can play mp3s on VLC or watch a video on Totem and no sound breakage...

I can ALSO PLAY MP3s on Rhythmbox and the sound is fine and it does NOT break the sound on everything else...

Weird bug we got...isn't it? ;)

See if your behavior matches what i got on my computer...On mine, the only thing that triggers it off is trying to play a video on VLC...

PS: I wonder if it would help to re-install VLC in the Package Manager..haven't tried that...wasn't sure if it would be a good move or not...

Other than that, i guess i'd have to see if any updates come down for pulse audio...otherwise, i will just have to stick to Totem for playing videos...i am planning on fresh installing 13.04 upon final release...I'm currently dual booting 13.04 with 12.10 (for a safety back up....lol)
and when final released, i am going to wipe everything, and just install 13.04 alone...

---

### Post by cariboo on 2013-02-17
To help in making a good bug report, you may want to look at the [Sound debugging]("https://wiki.ubuntu.com/DebuggingSoundProblems") wiki page.

---

### Post by sandeep.prasad30 on 2013-02-17
Yes.. Even i am facing this issue since update in morning. Not sure why this is occuring..

---

### Post by pressureman on 2013-02-17
I noticed this problem yesterday too. You don't need to do a full reboot. You can just kill pulseaudio and wait for it to respawn a few seconds later, and then your sound should work again.

```

kill `pidof pulseaudio`

```

---

### Post by zika on 2013-02-17
> **pressureman said:**
> I noticed this problem yesterday too. You don't need to do a full reboot. You can just kill pulseaudio and wait for it to respawn a few seconds later, and then your sound should work again.

```

kill `pidof pulseaudio`

```Or ask pulseaudio to do that ```
pulseaudio --kill
```...
Check also Your config files in ~/.pulse (if You have them) I think that some switches got changed...

---

### Post by fantab on 2013-02-17
I had the same issue.. for me though, System Settings - Sound Settings, just change something, anything and back.. the sound works system wide...

---

### Post by craig10x on 2013-02-17
Oh...so this is more widespread then i thought...i wonder if it would help to re-install VLC? haven't tried that yet...

Hope some updates will come down that will fix this...meanwhile i would have to avoid using VLC for playing videos (it's good that we have alternate players to use like Totem)...

---

### Post by zika on 2013-02-17
Check if Audio preference in VLC did not change to ALSA...
That might cause just the symptoms You describe...
If it did, simply change it to PA...
Also check gstreamer-properties...

---

### Post by Chelidze on 2013-02-17
Same problem here sound works and suddenly it stops can not here any sound from any software 
 and until I restart the system or restart puls audio ```
pulseaudio -k
```
it does not starts 
 ```
~$ lspci | grep Audio
00:1b.0 Audio device: Intel Corporation NM10/ICH7 Family High Definition Audio Controller (rev 01)
levan@Dreamcast:~$ aplay --list-devices
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC662 rev1 Analog [ALC662 rev1 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

 here look at this 

video 
[link 1]("http://ubuntuone.com/20l34bYAgzBgSDPhpJPSOb")
[link 2]("http://www.mediafire.com/?ce2if4nbgeetq2d")

---

### Post by craig10x on 2013-02-18
Just got my morning's updates for 13.04 and i see there are a bunch for Pulse Audio...hope it contains a fix for this...will have to check later after doing them..

---

### Post by sgage on 2013-02-18
> **craig10x said:**
> Just got my morning's updates for 13.04 and i see there are a bunch for Pulse Audio...hope it contains a fix for this...will have to check later after doing them..

I installed all the pulseaudio updates this morning, and it did not solve the problem I'm having with Rhythmbox. :(

---

### Post by dino99 on 2013-02-18
i have also had that issue, and seems not very new. Looks like the sound buffer is badly managed: not freed & badly refreshed. But i does not know the package to blame, maybe a kernel issue.

i get that problem each 4 hours or so when listening radiotray for example.

---

### Post by craig10x on 2013-02-18
Today's updates didn't help me either...trying to play a video in vlc triggers off borking sound on entire system is still there :(

As long as i play a video in totem instead, my sound will stay on system wide and sound works fine in totem...

---

### Post by craig10x on 2013-02-18
> **zika said:**
> Check if Audio preference in VLC did not change to ALSA...
That might cause just the symptoms You describe...
If it did, simply change it to PA...
Also check gstreamer-properties...

zika..you were "right on" with your suggestion...i went into the vlc media player, clicked "tools" then went to "preferences" and in the audio settings i noticed the sound module was set for "default"...the drop down list included alsa, pulse audio, etc... So, i just changed the setting to "pulse audio" hit "save" and exited vlc..

I then clicked on a video and had it play in vlc...as soon as it opened, video AND sound! :D

Then when i went back to Chrome browser and put my stream radio station back on...NO SYSTEM WIDE SOUND BREAKAGE...had sound!

Problem solved (for me anyway)...
Anyone with the VLC sound problem, try this fix...perhaps it got reset during those original "pulse audio" updates...

---

### Post by zika on 2013-02-18
> **craig10x said:**
> zika..you were "right on" with your suggestion...i went into the vlc media player, clicked "tools" then went to "preferences" and in the audio settings i noticed the sound module was set for "default"...the drop down list included alsa, pulse audio, etc... So, i just changed the setting to "pulse audio" hit "save" and exited vlc..

I then clicked on a video and had it play in vlc...as soon as it opened, video AND sound! :D

Then when i went back to Chrome browser and put my stream radio station back on...NO SYSTEM WIDE SOUND BREAKAGE...had sound!

Problem solved (for me anyway)...
Anyone with the VLC sound problem, try this fix...perhaps it got reset during those original "pulse audio" updates...I'm glad I could be of any help...
ALSA has a bad temper and hijacks device... ;)

---

### Post by celluloid on 2013-02-18
Oddly, I've got sound system-wide but cannot manage individual devices.
I usually plug in a USB head set - go to Sound Properties and turn down my laptop's speakers and turn up the head set - however, now I cannot manage the sound individually - turning up or down the volume on one device causes the other to respond as well. :(

Has anyone seen this?

---

### Post by rrnbtter on 2013-02-19
Greetings,
These Pulse Audio problems should go away when you load the 3.8 kernel. At least they did for me.

---

### Post by MacUntu on 2013-02-19
We are lucky, it could have been a broken init system. :D

---

### Post by craig10x on 2013-02-19
> **rrnbtter said:**
> Greetings,
These Pulse Audio problems should go away when you load the 3.8 kernel. At least they did for me.

That's great to hear...i am waiting for it to come through the software updater and will check after it's on...i will keep my "fingers crossed" ;)

I thought mine was fixed when i changed the audio module setting in VLC but it didn't work again the next time i booted up...I set VLC back to the default on that and will just wait to see what happens when i get the new kernel update...

---

