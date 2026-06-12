---
title: "A new WoW problem?"
date: 2009-01-31
forum: Wine
---

### Post by Nierfenhimer on 2009-01-31
Alright, so I suppose it makes more sense to simply make a whole new thread about this.

Through some various tweaking (and "untweaking") I managed to get WoW working without a hitch, except for one thing: the bloody frame rate.
The login screen, character screen, and certain small areas such as corridors in Undercity work great, around 20 fps and up. (Take note that 20 fps is actually very good for me - it's very smooth (and anything above that is a bit extraneous, honestly). My latency is also very good.) However, when I step into a more spacious area, the frame rate plummets to around 5-8 fps at best, rendering the game practically unplayable.

Honestly, I can't see why this should happen at all. The game ran more smoothly on my MacBook with a dead RAM slot running only 1 GB of RAM.
On this computer, I've got the following hardware:
nVidia nForce 650i Ultra Motherboard
Intel Pentium D 3.40 GHz Processor (Dual Core, obviously)
nVidia GeForce FX 5200 (256 MB) video card
1 GB RAM

Software is as follows:
Ubuntu 8.10 Intrepid Ibex
WINE 1.1.13
World of Warcraft: Wrath of the Lich King 3.0.8

To get the first few screens working well, I did (to the best of my knowledge - I had another helping me on this as well) the following:
Deleted the registry hack
Running under DirectX instead of OpenGL - OGL has a horrible interface lag, as well as very little to no improvement
Turned off all graphics options under WINE:
--All window settings unchecked
--Vertex Shader Support and Pixel Shader both disabled
WoW video options, while not mattering much in most instances, ae turned down to Low.
Config.wtf looks as follows (Realm info, etc, censored):
SET locale "enUS"
SET portal "us"
SET realmList "us.logon.worldofwarcraft.com"
SET patchlist "us.version.worldofwarcraft.com"
SET coresDetected "2"
SET hwDetect "0"
SET gxColorBits "24"
SET gxDepthBits "24"
SET gxResolution "1024x768"
SET gxRefresh "56"
SET gxTripleBuffer "1"
SET gxMultisampleQuality "0.000000"
SET videoOptionsVersion "1"
SET accountName "ACCOUNT NAME"
SET movie "0"
SET mouseSpeed "1"
SET Gamma "1.000000"
SET lastCharacterIndex "7"
SET readTOS "1"
SET readEULA "1"
SET showToolsUI "1"
SET Sound_VoiceChatInputDriverName "System Default"
SET Sound_VoiceChatOutputDriverName "System Default"
SET Sound_OutputDriverName "System Default"
SET ChatMusicVolume "0.29999998211861"
SET ChatSoundVolume "0.39999997615814"
SET ChatAmbienceVolume "0.29999998211861"
SET Sound_MusicVolume "0"
SET Sound_AmbienceVolume "1"
SET farclip "177"
SET particleDensity "1.000000"
SET baseMip "1"
SET spellEffectLevel "0"
SET environmentDetail "0.5"
SET weatherDensity "0"
SET realmName "REALM NAME"
SET gameTip "4"
SET VoiceActivationSensitivity "0.39999997615814"
SET groundEffectDist "70"
SET textureFilteringMode "0"
SET ffxGlow "0"
SET ffxDeath "0"
SET gxVSync "0"
SET uiScale "0.79999995231628"
SET useUiScale "1"

If any additional info is needed, I will gladly supply it, provided it is relevant and not personal, of course.:p

EDIT: A little something extra:
I checked the System Monitor and found that, as expected, WoW was running one of my processor cores to 100% and totally ignoring the other. Is there a possible way to work around this or at least relieve a bit of the strain on the core?

---

### Post by Martin Wolflux on 2009-01-31
Not running OpenGL? D3D (Direct 3D rendering) causes low framerates in Linux. Change to OpenGL to improve. Can't really advise you to do otherwise =/

From my experience, D3D is a mode more or less only used for Linux users having problems adjusting video settings in OpenGL mode (and personally, the interface lag isn't that bad) before changing back to OGL.

---

### Post by hikaricore on 2009-01-31
As with Burning Crusade, WotLC requires more powerful hardware than the required minimum.
1Gb of RAM is not really that much anymore, and your video card is a bit dated.

This may be all fine and good in Windows, but on Linux running with the WINE API compatability layer in OpenGL you may be pushing it.
Even in D3D mode you're using OpenGL, so as the Wolflux suggested try using OpenGL mode anyway and save your processor the conversion trouble.

You may find that turning off features such as shadows and full screen glow effects as well as reducing view distance goes a long way toward a smoother game.

---

### Post by Nierfenhimer on 2009-02-01
That was the one thing I hadn't tried. I tried OpenGL after having removed and tweaked like I had, and it worked!

Thanks so much.

---

