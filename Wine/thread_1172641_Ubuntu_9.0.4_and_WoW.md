---
title: "Ubuntu 9.0.4 and WoW?"
date: 2009-05-28
forum: Wine
---

### Post by Angelkorpse on 2009-05-28
I noticed other day before I installed 9.0.4 my WoW was crashing and not knowing why. My game's graphics were getting messed up to where u didnt know what u were looking at. And it seemed like the lag i would get the graphics would screwed up and crash the game. 

So i installed 9.0.4 and now it crashes still and When playing Amarok or maybe with any webpage that is open up with any kind of active media interferes with it and crashes WoW and also messes up. I also took notice in game that when I go to move the character with my arrow keys my character would take 2-3 steps and then freeze some way but still moves in a pose. but moves ok if i use my mouse keys.

Also my mouse is more faster than with Ubuntu v8 and in game where I kinda had trouble with the speed being it was kinda laggy slow now this time around its fast and I have both game and computer mouse settings on slow and still it zips around more than it use to do.

any thoughts??
thanks you for any suggestions

---

### Post by ATOMICplayer on 2009-05-29
I noticed that my WoW would run fine; however I experienced huge blobs of what looked like mirrors.  I turned the graphics all the way down on everything and unchecked all the features at the bottom.  My WoW now runs just fine.  Let me know if that helps.

Also: I believe that pose-looked walk is due to how the keys interact with WINE. I can press NUM LOCK and the pose-looked walk goes away.

---

### Post by themusicalduck on 2009-05-29
Could you post the contents of your config.wtf file here? it'll be in the WoW directory in the folder WTF.

Also if you don't already then you should disable compiz while playing. It usually causes problems for wine games.

---

### Post by Angelkorpse on 2009-05-30
> SET readTOS "1"
SET readEULA "1"
SET readScanning "-1"
SET readContest "-1"
SET locale "enUS"
SET hwDetect "0"
SET gxResolution "1280x1024"
SET gxRefresh "50"
SET gxMultisampleQuality "0.000000"
SET gxFixLag "0"
SET fullAlpha "1"
SET SmallCull "0.040000"
SET DistCull "500.000000"
SET trilinear "1"
SET frillDensity "24"
SET farclip "837"
SET specular "1"
SET pixelShaders "1"
SET unitDrawDist "300.000000"
SET movie "0"
SET realmList "us.logon.worldofwarcraft.com"
SET SoundOutputSystem "1"
SET SoundBufferSize "150"
SET gxApi "OpenGL"
SET readTerminationWithoutNotice "-1"
SET coresDetected "2"
SET videoOptionsVersion "2"
SET showToolsUI "0"
SET Sound_OutputDriverName "System Default"
SET patchlist "us.version.worldofwarcraft.com"
SET gameTip "125"
SET Sound_VoiceChatInputDriverName "System Default"
SET Sound_VoiceChatOutputDriverName "System Default"
SET gxWindow "1"
SET DesktopGamma "1"
SET Gamma "1.000000"
SET groundEffectDist "70"
SET uiScale "1"
SET autoLootCorpse "1"
SET ChatMusicVolume "0.29999998211861"
SET ChatSoundVolume "1"
SET ChatAmbienceVolume "0.29999998211861"
SET Sound_MasterVolume "0.69999998807907"
SET Sound_SFXVolume "1"
SET Sound_MusicVolume "0.69999998807907"
SET Sound_AmbienceVolume "1"
SET OutboundChatVolume "2.5"
SET InboundChatVolume "1"
SET VoiceActivationSensitivity "0.39999997615814"
SET PushToTalkButton "NUMPADDECIMAL"
SET Sound_EnableErrorSpeech "0"
SET Sound_ZoneMusicNoDelay "1"
SET Sound_EnableSoundWhenGameIsInBG "1"
SET weatherDensity "3"
SET installType "Retail"
SET Sound_OutputQuality "0"
SET Sound_EnableHardware "1"
SET Sound_EnableMusic "0"
SET CombatLogRangeParty "2000"
SET CombatLogRangePartyPet "2000"
SET CombatLogRangeFriendlyPlayers "2000"
SET CombatLogRangeFriendlyPlayersPets "2000"
SET CombatLogRangeHostilePlayers "2000"
SET CombatLogRangeHostilePlayersPets "2000"
SET CombatLogRangeCreature "2000"
SET accountName "account name here"
SET accounttype "LK"
SET projectedTextures "1"
SET lastCharacterIndex "4"
SET checkAddonVersion "0"
SET componentTextureLevel "9"
SET environmentDetail "1.5"
SET realmName "server name here"
SET particleDensity "0.80000001192093"
SET mouseSpeed "0.5"

heres my wtf config

---

### Post by divorce certificate on 2009-06-21
If you want to play WoW you're going to have to install the drivers for your graphics card. Just go to "System > Administration > Hardware Drivers" and select your graphics card. It should install. (You will need to be connected to the Internet of course). 
I think I tried that, and there were no options in Hardware Drivers. I don't remember what it said, but I'll check again this afternoon (I'm at work now :()
 
Did you install Wine from the Ubuntu repository or from the Wine site? There's a chance that the version of Wine in the repo's is an older version then the latest release on the Wine site, though unlikely since 9.04 was only just released.
I installed it from the website. Again, I think I checked the repo first since that what some guides I had checked recomended, but I didn't find it, either because I didn't know what I was doing or because it wasn't there.

---

