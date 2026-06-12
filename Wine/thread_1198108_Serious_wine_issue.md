---
title: "Serious wine issue"
date: 2009-06-27
forum: Wine
---

### Post by Ollock on 2009-06-27
I recently downgraded to 8.04 looking for better performance in Wow.  It had been working decently (but with framerate issues) in 8.10, but upgrading to 9.04 made it unplayable.

So far the game runs very smoothly in opengl mode and d3d mode makes it impossible to enter the game (there is no crash -- that registers -- it just freezes at the load-in screen and I have to kill the process).  However, when running in opengl it will be fine for a few minutes and then I will suddenly get corrupted text (no other ui corruption, just the text).

Here is the text of my config.wtf file:

SET readTOS "1"
SET readEULA "1"
SET readTerminationWithoutNotice "-1"
SET readScanning "-1"
SET readContest "-1"
SET locale "enUS"
SET movie "0"
SET showToolsUI "1"
SET realmList "us.logon.worldofwarcraft.com"
SET coresDetected "1"
SET hwDetect "0"
SET gxRefresh "60"
SET gxMultisampleQuality "0.000000"
SET gxFixLag "0"
SET videoOptionsVersion "2"
SET Sound_OutputDriverName "System Default"
SET farclip "177"
SET particleDensity "0.10000000149012"
SET spellEffectLevel "0"
SET installType "Retail"
SET patchlist "us.version.worldofwarcraft.com"
SET Gamma "1.000000"
SET Sound_MusicVolume "0.40000000596046"
SET Sound_AmbienceVolume "0.60000002384186"
SET mouseSpeed "1"
SET Sound_VoiceChatInputDriverName "System Default"
SET Sound_VoiceChatOutputDriverName "System Default"
SET ChatMusicVolume "0.29999998211861"
SET ChatSoundVolume "0.39999997615814"
SET ChatAmbienceVolume "0.29999998211861"
SET weatherDensity "0"
SET realmName "Drenden"
SET gameTip "92"
SET VoiceActivationSensitivity "0.39999997615814"
SET Sound_EnableMusic "0"
SET Sound_MasterVolume "0.80000001192093"
SET Sound_SFXVolume "0.40000000596046"
SET Sound_EnableHardware "1"
SET Sound_EnableDSPEffects "1"
SET ffxGlow "0"
SET ffxDeath "0"
SET M2Useshaders "0"
SET accountName "ollock"
SET accounttype "LK"
SET gxWindow "1"
SET textureFilteringMode "0"
SET UIFaster "0"
SET baseMip "1"
SET environmentDetail "0.5"
SET gxApi "opengl"

And my xorg.conf:

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
	Option		"XkbVariant"	"alt-intl"
	Option		"XkbOptions"	"lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"fglrx"
	Option "Capabilities" "0x00000800"
	Option "UseFastTLS" "off"
	Option "KernelModuleParm" "locked-userpages=0"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Defaultdepth	24
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
	Inputdevice	"Synaptics Touchpad"
EndSection
Section "Module"
	Load		"glx"
EndSection

My video card is ATI Technologies Inc RS485 [Radeon Xpress 1100 IGP] and I have 2 GB of RAM.  I don't remember what my processor is nor how to check, but it seems to be single-core.

I have tried ideas from every guide and forum post I can find and cannot get things to work properly.

---

