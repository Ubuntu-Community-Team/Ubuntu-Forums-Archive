---
title: "WOW crashing/exiting after hitting play button"
date: 2009-04-18
forum: Wine
---

### Post by dslreports_snakeoil on 2009-04-18
Hello, this is my first post, so I beg forgiveness before hand.

Anyhow, I had WOW up and running for a week, on Ubuntu 8.10. Then the other day, I downloaded a patch for wine, which made wine 1.1.19 .

Add to that, I wanted to see the "kool" desktop effects that ubuntu has, so I was goofing with the settings for that as well. [I didn't try playing WOW until after the wine update and playing with the desktop settings.]

My hardware:

AMD dual core 3600+
Ram: 2 gig of DDR2.
Video card: Geoforce 7600GT 256MB ram.
Hard disk space: 98 gigs
Nvidia Xserver:  180.11

Game resolution 1920 X 1080 [I play it on my 1080p 42" TV

WTF.config file:

ET readTOS "1"
SET readEULA "1"
SET readScanning "-1"
SET readContest "-1"
SET readTerminationWithoutNotice "-1"
SET installType "Retail"
SET locale "enUS"
SET movie "0"
SET showToolsUI "1"
SET portal "us"
SET realmList "us.logon.worldofwarcraft.com"
SET patchlist "us.version.worldofwarcraft.com"
SET coresDetected "2"
SET hwDetect "0"
SET gxColorBits "24"
SET gxDepthBits "24"
SET gxResolution "1920x1080"
SET gxRefresh "69"
SET gxMultisample "1"
SET gxMultisampleQuality "0.000000"
SET videoOptionsVersion "1"
SET accountName ""
SET Gamma "1.000000"
SET Sound_OutputDriverName "System Default"
SET Sound_MusicVolume "0.40000000596046"
SET Sound_AmbienceVolume "0.60000002384186"
SET farclip "397"
SET specular "1"
SET particleDensity "1.000000"
SET groundEffectDensity "24"
SET mouseSpeed "1"
SET Sound_VoiceChatInputDriverName "System Default"
SET Sound_VoiceChatOutputDriverName "System Default"
SET ChatMusicVolume "0.29999998211861"
SET ChatSoundVolume "0.39999997615814"
SET ChatAmbienceVolume "0.29999998211861"
SET realmName "Llane"
SET gameTip "4"
SET VoiceActivationSensitivity "0.39999997615814"
SET gxApi "opengl"
SET M2UseShaders "0"
SET gxWindow "1"
SET lastCharacterIndex "1"
SET Sound_EnableSoundWhenGameIsInBG "1"

BTW:
Here is the system log veiwer message during the loading/unloading of WOW:

Apr 18 15:59:21 ******-desktop kernel: [ 2539.211123] Too big adjustment 32
Apr 18 15:59:21 ******-desktop kernel: [ 2539.252142] Too big adjustment 32
Apr 18 16:03:24 ******-desktop kernel: [ 2782.027291] Too big adjustment 32
Apr 18 16:03:24 ******-desktop kernel: [ 2782.068153] Too big adjustment 32

Note: I have gone to wineHQ and read their notes. I don't understand the notes/can't figure out how to apply them to my situation.

The game did work on Tuesday, then today didn't. The only things I did was accpet the updates for ubuntu, and play with the active desktop features.


Thank you for your help, and understanding.


*****EDIT*****

Just saw this:
[http://forums.worldofwarcraft.com/thread.html?topicId=16365947252&sid=1](http://forums.worldofwarcraft.com/thread.html?topicId=16365947252&sid=1)

quote:

Go into your install folder.

Right-click Wow.exe and select Properties.

Under the Compatibility tab go to Input Settings and select "Turn off advanced text services for this program."

(This is on XP)

Worked for me. Don't really know why. I reported it on the PTR but nobody really seemed to care. 

end quote.

Now how is this done in ubuntu?

---

