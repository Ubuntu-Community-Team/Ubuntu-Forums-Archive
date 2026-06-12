---
title: "WorldofWarcraft problem! Help&lt;"
date: 2010-04-18
forum: Wine
---

### Post by Demonlord1111 on 2010-04-18
[B]   :lolflag: Ok well I was able to install WoW perfect but once I went into the game Its all really bright. [COLOR=Red]I can see other player's characters all I see is a model also the ground beneath my feet and everyone else's feet is black.[/COLOR] I was asking people on my realm [Trade chat] in ORG if  anyone knew about it, some results show its my ([COLOR=Red]Config.wtf[/COLOR]). I tryed numerouse times to fix it with many tutorials online but I'm new with [COLOR=Red]Ubuntu linux 9.10[/COLOR] So if you can[COLOR=Blue] [COLOR=Blue]help please post! Config.wtf
[/COLOR][/COLOR][COLOR=Blue] will show under this.[/COLOR][/B]


SET accountName "Crazytrick27@aol.com"
SET alphaLevel "="
SET AmbienceVolume "="
SET anisotropic "="
SET automoveturnspeednarrow "="
SET automoveturnspeedwide "="
SET baseMip "="
SET bspcache "="
SET cameraBobbing "="
SET cameraBobbingFrequency "="
SET cameraBobbingLRAmplitude "="
SET cameraBobbingUDAmplitude "="
SET checkAddonVersion "="
SET CombatDeathLogRange "="
SET CombatLogRangeCreature "="
SET CombatLogRangeFriendlyPlayers "="
SET CombatLogRangeFriendlyPlayersPets "="
SET CombatLogRangeHostilePlayers "="
SET CombatLogRangeHostilePlayersPets "="
SET CombatLogRangeParty "="
SET CombatLogRangePartyPet "="
SET CombatModeMaxDistance "="
SET debugTaint "="
SET desktopGamma "="
SET DistCull "="
SET doodadAnim "="
SET EmoteSounds "="
SET EnableAmbience "="
SET EnableErrorSpeech "="
SET EnableGroupSpeech "="
SET EnableMusic "="
SET ErrorFilter "="
SET ErrorLevelMax "="
SET ErrorLevelMin "="
SET errors "="
SET farclip "177"
SET ffxDeath "="
SET ffxGlow "="
SET FootstepSounds "="
SET frillDensity "="
SET fullAlpha "="
SET gameTip "="
SET gamma "0.500000"
SET gxAspect "0"
SET gxCursor "0"
SET gxFixLag "0"
SET gxMultisampleQuality "0.000000"
SET gxOverride "="
SET gxRefresh "60"
SET gxVSync "0"
SET gxWindow "1"
SET hwDetect "="
SET Joystick "="
SET lastCharacterIndex "2"
SET lodDist "="
SET M2BatchDoodads "="
SET M2Faster "="
SET M2FasterDebug "="
SET M2UseClipPlanes "="
SET M2UsePixelShaders "="
SET M2UseShaders "="
SET M2UseThreads "="
SET M2UseZFill "="
SET mapObjLightLOD "="
SET mapObjOverbright "="
SET mapShadows "="
SET MapWaterSounds "="
SET MasterSoundEffects "="
SET MasterVolume "="
SET mousespeed "="
SET movie "="
SET movieSubtitle "="
SET MusicVolume " = "
SET nearclip "="
SET ObjectSelectionCircle "="
SET occlusion "="
SET particleDensity "0.4"
SET PetNamePlates "="
SET pixelShaders "="
SET PlayerAnim "="
SET PlayerFadeInRate "="
SET PlayerFadeOutAlpha "="
SET PlayerFadeOutRate "="
SET readContest "="
SET readEULA "1"
SET readScanning "="
SET readTOS "1"
SET realmList "us.logon.worldofwarcraft.com"
SET realmName "Garrosh"
SET scriptMemory "="
SET shadowBias "="
SET shadowLevel "0"
SET ShowErrors "="
SET showfootprintparticles "="
SET showfootprints "="
SET showGameTips "="
SET showsmartrects "="
SET SkyCloudLOD "="
SET smallCull "="
SET SoundBufferSize "="
SET SoundDriver "="
SET SoundInitFlags "="
SET SoundListenerAtCharacter "="
SET SoundMaxHardwareChannels "="
SET SoundMemoryCache "="
SET SoundMinHardwareChannels "="
SET SoundMixer "="
SET SoundMixRate "="
SET SoundOutputSystem "="
SET SoundReverb "="
SET SoundRolloffFactor "="
SET SoundSoftwareChannels "="
SET SoundVolume "="
SET SoundZoneMusicNoDelay "="
SET specular "="
SET spellEffectLevel "="
SET statusBarText "="
SET TargetAnim "="
SET targetNearestDistance "="
SET targetNearestDistanceRadius "="
SET texLodBias "="
SET textureLodDist "="
SET triangleStrips "="
SET trilinear "="
SET uiscale "="
SET UIFaster "“2”"
SET unitDrawDist "="
SET UnitNamePlayer "="
SET UnitNameRenderMode "="
SET useUiScale "="
SET useWeatherShaders "="
SET waterLOD "="
SET weatherDensity "="
SET widescreen "="
SET locale "enUS"
SET patchlist "us.version.worldofwarcraft.com"
SET videoOptionsVersion "3"
SET showToolsUI "1"
SET Sound_OutputDriverName "System Default"
SET Sound_MusicVolume "0.40000000596046"
SET Sound_AmbienceVolume "0.60000002384186"
SET accounttype "LK"
SET VoiceActivationSensitivity "0.39999997615814"
SET ChatMusicVolume "0.29999998211861"
SET ChatSoundVolume "0.39999997615814"
SET ChatAmbienceVolume "0.29999998211861"



[B]PS. I have an[COLOR=Blue] [Aspire 5735Z]("http://global-download.acer.com/GDHome.aspx?SC=PA_6&LC=en#") < [Aspire]("http://global-download.acer.com/GDHome.aspx?SC=PA_6&LC=en#") < [Notebook]("http://global-download.acer.com/GDHome.aspx?SC=PA_6&LC=en#")[/COLOR] How can I update my video drivers? I downloaded it off the Service & Support site becouse it wont show in [COLOR=Red]System > Administration > Hardware Drivers.[/COLOR]
[/B]

---

### Post by asdfoo on 2010-04-19
which video card does your laptop have?

---

### Post by 8Kuula on 2010-04-19
> **Demonlord1111 said:**
> 
SET accountName "..."

Maybe should not show that line in config.wtf file :roll:

---

### Post by Demonlord1111 on 2010-04-20
I have an Intel Duel core . an Crazytrick is not my account login its one of my alt emails not having anything to do with wow.

---

### Post by Alatar1 on 2010-04-20
try adding this to it 

```
SET gxApi "opengl"
```

---

### Post by Zintha on 2010-04-20
> **8Kuula said:**
> Maybe should not show that line in config.wtf file :roll:
Eh, whats the worst you could do with it?
Probably has an authenticator like a lot of people these days anyway.

---

### Post by Demonlord1111 on 2010-04-21
I tryed then It gives me on wow.exe a black screen with only the hand/mouse icon. Launch.exe wont even open

---

