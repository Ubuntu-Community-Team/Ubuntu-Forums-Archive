---
title: "Android and mp3's"
date: 2011-06-12
forum: The Cafe
---

### Post by cariboo on 2011-06-12
Since I'm the only person in my department during my shift, and the corporate muzak is driving me nuts, I decided to use my HTC Desire as an mp3 player during working hours. When I transfer Music to the memory card, on uplugging the usb cable and checking to see if everything was transferred properly, I get a message saying that the music can't be played, yet if I wait 5 minutes, everything shows up as it should and all the tracks are playable, what is going on under the covers to make this happen?

---

### Post by manzdagratiano on 2011-06-12
I've been putting stuff on my Droid X for months now, and I never got any error! I just plug it in, and drag the songs to it in rhythmbox, which syncs everything perfectly. All I had to do was to make an empty file called '.is_audio_player' in the root of the SD card, so that rhythmbox recognizes it. Regarding what is happening under the covers, I haven't the darndest clue!

---

### Post by cariboo on 2011-06-12
My phone just shows up as an external drive, so I just copy the tracks from my server to the the external, this may have something to do with it.

---

### Post by manzdagratiano on 2011-06-13
Yes I think that is different from the syncing business that rhythmbox does - It places the files in their relevant Artist/Album folders inside the music folder on the SD card - and maybe there is an XML file somewhere corresponding to the database. Creating the empty '.is_audio_file' in the root of the card will allow it to show up as a music player in Ubuntu the next time it is plugged in. I used to do the same on my older Blackberry storm.

---

### Post by Spr0k3t on 2011-06-13
If you create the .is_audio_player file, you may as well make some use of it.  The file does not have to be empty and can contain some useful tools.

```
audio_folders=MUSIC/,RECORDINGS/
folder_depth=2
output_formats=application/ogg,audio/mpeg
```

Files that are not in those audio formats will be automatically transcoded when using the sync through Rhythmbox or even Banshee.  The latter supports more elements of the HAL config file.

---

### Post by TheSqueak on 2011-06-13
> **cariboo907 said:**
> Since I'm the only person in my department during my shift, and the corporate muzak is driving me nuts, I decided to use my HTC Desire as an mp3 player during working hours. When I transfer Music to the memory card, on uplugging the usb cable and checking to see if everything was transferred properly, I get a message saying that the music can't be played, yet if I wait 5 minutes, everything shows up as it should and all the tracks are playable, what is going on under the covers to make this happen?

There's a small time lapse between you unplugging the cable and the phone remounting the SD card itself, could it be that?

---

### Post by Tom Collier on 2011-06-13
My HTC Hero does exactly the same thing..and, like you, I just drag and drop the folder to the phone's SD card. HTC products are notorious for lag.

---

### Post by Lucradia on 2011-06-13
Had a DROID X for WiFi Only (used the bypass finger pattern) and never got that error either.

However, if I tried to use the MP3s as ringtones, it would randomly switch to the default every other day or so. Gosh, I miss my OldSpice alarm.

---

### Post by Spr0k3t on 2011-06-13
> **Lucradia said:**
> However, if I tried to use the MP3s as ringtones, it would randomly switch to the default every other day or so.

Use RingDroid (from the market) to modify your MP3 file as needed, then copy the resulting tone over to the phone.  Never had a problem after that.

---

### Post by 3rdalbum on 2011-06-13
I have the Desire and have not noticed this; the SD card tends to remount pretty quickly afterwards.

However, I don't think I've ever loaded up a reasonable amount of music and then immediately tried to play it. The explanation of "it has to rebuild the music library" sounds plausible because my standalone MP3 player does this process.

---

### Post by jeffathehutt on 2011-06-13
I think it is probably just scanning the card to rebuild the song index.  On my htc Incredible 2, once I unmount and remove the cable, the phone has to scan the card to find the new music.:)

---

### Post by ErikNJ on 2011-06-13
Yep, most players need to create an index on the contents and this takes a bit of time.  It'd be nice if the player supplied some feedback to let you know this (and when the update is complete).

---

### Post by whiskeylover on 2011-06-13
The OS scans the entire card for media once its mounted. This happens on boot up and re-mounting of SD cards after disconnecting from USB. My phone takes a good minute or so to scan the entire card. The amount of time required to scan would depend on the amount of stuff you have on your cards, I think.


> **ErikNJ said:**
> Yep, most players need to create an index on the contents and this takes a bit of time.  It'd be nice if the player supplied some feedback to let you know this (and when the update is complete).

Mine shows a notification saying "Media Scanning... x%" on mounting, and "Media Scanning Complete" on completion.

---

### Post by LowSky on 2011-06-13
My Droid Incredible seems to just have to rescan the card, and works fine. Heck all my mp3 players have to do it, including my iPod Classic and Sansa Clip+

---

### Post by cariboo on 2011-06-13
Thanks everyone, having to rescan the memory card is what i thought too. I don't use rhythmbox or banshee, as I don't have any music stored on the computers I use every day. At home I use a separate system running XBMC to play music, and in my shop I have an Apple G4 running Debian stable to play tunes.

The first time I noticed the problem was when I transferred 350+ tunes, and the second time I transferred 750 tracks to the phone, other than the delay to scan the memory card, playing music works just great.

---

