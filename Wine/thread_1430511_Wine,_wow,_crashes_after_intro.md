---
title: "Wine, wow, crashes after intro"
date: 2010-03-15
forum: Wine
---

### Post by Shadyboy on 2010-03-15
Well, here goes.
Have the newest wine, 1.1.40.
Have installed and updated Wow

[IMG]http://home.no/sh4dyb0y/wow%20crash.jpg[/IMG]
On the picture is what happens after the intro to Lich King is done.
I have googled and had no luck.
So I am now asking for help.

---

### Post by OMJD on 2010-03-15
Did you configure it to use OpenGL as opposed to Direct X? 

I highly suggest giving the following article a read if you haven't done so already. You won't need to do all of the steps, as you've done many of them already.

[https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft)

Also, you may want to install Wine Pulse as opposed to the standard version of Wine. If not, you may run into problems with sound. You just need to add the PPA to your software sources list, and then download it from Synaptic.

[https://launchpad.net/~neil-aldur/+archive/ppa](https://launchpad.net/~neil-aldur/+archive/ppa)

```
ppa:neil-aldur/ppa
```

---

### Post by Shadyboy on 2010-03-15
If you mean to edit the config.wtf file, then no, beacuse untill I get to log in once, I do not have the config.wtf file.

and for the audio, I could really care less. Never been the fan of the sounds in wow. And I have noticed, that as long as I have audio dissabled in the game, it runs a little more smoother does it..

---

### Post by OMJD on 2010-03-15
> **Shadyboy said:**
> If you mean to edit the config.wtf file, then no, beacuse untill I get to log in once, I do not have the config.wtf file.

and for the audio, I could really care less. Never been the fan of the sounds in wow. And I have noticed, that as long as I have audio dissabled in the game, it runs a little more smoother does it..

If you're using the European version of the game, try creating a Config.wtf file in the WTF dir with the following content:

```
SET readTOS "1"
SET readEULA "1"
SET readTerminationWithoutNotice "1"
SET readScanning "-1"
SET readContest "-1"
SET locale "enGB"
SET movie "0"
SET showToolsUI "1"
SET portal "eu"
SET realmList "eu.logon.worldofwarcraft.com"
SET coresDetected "4"
SET hwDetect "0"
SET gxResolution "1920x1080"
SET gxMultisampleQuality "0.000000"
SET videoOptionsVersion "3"
SET Sound_OutputDriverName "System Default"
SET farclip "727"
SET specular "1"
SET groundEffectDensity "64"
SET installType "Retail"
SET patchlist "eu.version.worldofwarcraft.com"
SET Gamma "1.000000"
SET Sound_MusicVolume "0.40000000596046"
SET Sound_AmbienceVolume "0.60000002384186"
SET mouseSpeed "1"
SET Sound_VoiceChatInputDriverName "System Default"
SET Sound_VoiceChatOutputDriverName "System Default"
SET ChatMusicVolume "0"
SET ChatSoundVolume "0.22999998927116"
SET ChatAmbienceVolume "0.25"
SET realmName "Twilight's Hammer"
SET gameTip "20"
SET VoiceActivationSensitivity "0.39999997615814"
SET textureFilteringMode "5"
SET groundEffectDist "120"
SET environmentDetail "1.5"
SET gxWindow "1"
SET Sound_EnableMusic "0"
SET accounttype "LK"
SET gxTripleBuffer "1"
SET componentTextureLevel "9"
SET projectedTextures "1"
SET gxApi "opengl"
SET gxRefresh "85"
SET Sound_NumChannels "64"
SET Sound_EnableSoftwareHRTF "1"
SET Sound_OutputQuality "2"
SET EnableVoiceChat "1"
SET Sound_MasterVolume "0.10000000149012"
SET OutboundChatVolume "2.5"
SET uiScale "0.95999997854233"
SET useUiScale "1"
SET particleDensity "1"
SET Sound_SoundOutputSystem "1"
SET Sound_SoundBufferSize "150"
SET shadowLevel "0"
SET weatherDensity "3"
SET Sound_EnableReverb "1"
SET lastCharacterIndex "4"
```

---

### Post by Shadyboy on 2010-03-15
I got 2 .wtf files in my WTF folder. RunOnce.wtf and RundOnce_WLK.wtf. Just delete theme or?


Just tried using the config.wtf file I made from you OMJD. Same thing. Same crash. Same error :(

---

### Post by OMJD on 2010-03-15
> **Shadyboy said:**
> I got 2 .wtf files in my WTF folder. RunOnce.wtf and RundOnce_WLK.wtf. Just delete theme or?

I don't have those in my wtf directory. I assume they're automatically deleted once you've logged in/loaded the game successfully. I suggest creating a directory called "backup" in the WTF directory, then move those 2 files into it. Once you've done that, create a new file called "Config.wtf" (exactly) and then copy and paste the contents in my post above.

EDIT: Go Applications > Wine > Configure Wine > Applications (Tab)
Make sure the Windows version is set to XP.

Also make sure you're using proper drivers for your graphics card and not the generic one. (System > Administration > Hardware drivers)

---

### Post by Shadyboy on 2010-03-15
Default on my wine is XP.
Have tried the Config.wtf file with and without my 2 other .wtf files.
When I tried without my 2 others, the game crashed right away. 

I am beginning to wonder if one of the error messages on the picture I showed have the awnsere. I looks like wine "can`t" write to my "C:" drive :S or something like that...

---

### Post by alphasoup on 2010-03-26
What graphics card, is that a Radeon.
I had same error consistently with a Radeon board, since this was not a laptop I tried
a different graphics board (nv) and the same game version, same config file
then got the same error, then switched the driver to nvidia 185 (binary) and
the problem went away. So persumably there is a bug in the common Xorg drivers
for both radeon and nv that is only fixed in proprietary drivers :(

---

