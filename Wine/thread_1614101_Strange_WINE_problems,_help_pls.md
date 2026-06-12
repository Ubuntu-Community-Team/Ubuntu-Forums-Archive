---
title: "Strange WINE problems, help pls"
date: 2010-11-05
forum: Wine
---

### Post by realac0 on 2010-11-05
Heya all.
first all all:

spec
E8400@3,6
4gb ram corsair 1066
ATI HD5850 with 10.10 linux proprietary drivers
Ubuntu 64bit 10.04
differents wine versions with PlayOnLinux and prefix

well, second of all i have a lot of games running perfectly, i usually use POL for use and manage differents versions of wine a manage the prefix.

here a ss of my actual POL games list:

[http://www.webalice.it/aconet/PlayOnLinux.jpg](http://www.webalice.it/aconet/PlayOnLinux.jpg)

all work (and i think they are some of the best pc game ever done ^_^) THAN FIFA11, PES11 and M&B.

i ask here because the problems are really strange

FIRST PROBLEM 1) and more annoying

as u can see here:

[http://www.webalice.it/aconet/fifa11_1.jpg](http://www.webalice.it/aconet/fifa11_1.jpg)
wine version 1.3.5
[http://www.webalice.it/aconet/pes11_1.jpg](http://www.webalice.it/aconet/pes11_1.jpg)
[http://www.webalice.it/aconet/pes11_2.jpg](http://www.webalice.it/aconet/pes11_2.jpg)
wine version 1.3.5
[http://www.webalice.it/aconet/M&B_1.jpg](http://www.webalice.it/aconet/M&B_1.jpg)
wine version 1.2

the game start, seem to work well and then for some strange motivation don't show the characters. Take fifa11 or pes11 as exemple, u can see ball, stadium, name of players, all, but NOT THE CHARACTERS.
Another exemple is M&B, where game work 100% (audio, on line, all), the complete world is loaded, but i can't see any CHAR, any HORSE, nothing.

on my opinion the problem are ATI drivers. 
After new kernel update (2.6.32-25), i had to recompile 10.09 drivers (that was working well) but was impossible. Have read somewhere on line that there was incompatibility so i have just w8 for 10.10. When 10.10 out, installed and all seem to work well than these games.

i think is a problem of drivers because M&B, with old kernel and old ATI drivers, was working well, i played a lot if on line.

Have tryied to re-install 10.09 on differents kernel (the ones i choose when i start ubuntu) but is impossible to re-install. Seem i can use only 10.10 atm.

any idea?

SECOND PROBLEM 2) FIFA11

i had this problem with fifa11 demo too.
i can install the game and all seem to work.
before the problem 1), so with old kernel and 10.09 drivers, on FIFA11 demo, i was able to see the character, i can move it, and all was ok (on area) till i select the new game . I select the teams and start to load.
at this point, while loading, FIFA11 crash.
I continue to have this problem now. So i can't see the chars for problem 1) but loading a game (repeat, on arena all work) FIFA 11 crash

this is a ss of the log:

[http://www.webalice.it/aconet/fifa_error.jpg](http://www.webalice.it/aconet/fifa_error.jpg)

and this is a txt version of wine log:

```

------------------------------------------------------------
Total user memory:      2048.00 MB - 2147483647 bytes
Total available memory: 2048.00 MB - 2147483647 bytes
------------------------------------------------------------
arg0: fifa.exe
loading: C:\Programmi\EA Sports\FIFA 11\Game\memoryfw.ini
Using Use embeded copy of file C:\Programmi\EA Sports\FIFA 11\Game\memoryfw.ini
MemoryTracking heap disabled!
Memory Initialization over
-----------------------------------------------------------------------
Memory before heap allocation:            2048.00 megs - 2147483647 bytes
Memory available after heap allocation    2048.00 megs - 2147483647 bytes
Total memory used by heaps:               0.00 megs - 0 bytes

Creating EA::Messaging::Server
Initializing EA Messaging system
fixme:thread:SetThreadIdealProcessor (0x11c): stub
fixme:thread:SetThreadIdealProcessor (0x320): stub
fixme:thread:SetThreadIdealProcessor (0x324): stub
fixme:thread:SetThreadIdealProcessor (0x328): stub
fixme:thread:SetThreadIdealProcessor (0x32c): stub
Preloading 1st big file
fixme:thread:SetThreadIdealProcessor (0x330): stub
fixme:thread:SetThreadIdealProcessor (0x334): stub
fixme:thread:SetThreadIdealProcessor (0x338): stub
~~~~~~~~~~~done preload
loading locale big file
~~~~~~~~~~~done loading locale big file
fixme:thread:SetThreadIdealProcessor (0x344): stub
fixme:system:SystemParametersInfoW Unimplemented action: 59 (SPI_SETSTICKYKEYS)
fixme:psapi:GetProcessImageFileNameA (0x34c, 0x247540, 260) stub
fixme:psapi:GetProcessImageFileNameA (0x34c, 0x247540, 260) stub
fixme:psapi:GetProcessImageFileNameA (0x34c, 0x247540, 260) stub
fixme:thread:SetThreadIdealProcessor (0x354): stub
Changelist # for this build: 736063fixme:win:EnumDisplayDevicesW ((null),0,0x1a2eadc,0x00000000), stub!
fixme:d3d:debug_d3dformat Unrecognized 1515474505 (as fourcc: INTZ) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(1515474505) in the format lookup table
fixme:thread:SetThreadIdealProcessor (0x358): stub
Before LoadDataArchives(1)
After LoadDataArchives(1)
fixme:wbemprox:wbem_locator_ConnectServer 0x7465cf28, L"\\\\.\\root\\cimv2", (null), (null), (null), 0x00000000, (null), (nil), 0x1a2f45c)
fixme:wbemprox:wbem_locator_ConnectServer 0x7465d490, L"\\\\.\\root\\cimv2", (null), (null), (null), 0x00000000, (null), (nil), 0x1a2f45c)
fixme:wbemprox:wbem_locator_ConnectServer 0x704b1648, L"\\\\.\\root\\cimv2", (null), (null), (null), 0x00000000, (null), (nil), 0x1a2f45c)
fixme:dinput:JoystickAImpl_SetProperty DIPROP_AUTOCENTER(0)
fixme:wbemprox:wbem_locator_ConnectServer 0x6b3b7b38, L"\\\\.\\root\\cimv2", (null), (null), (null), 0x00000000, (null), (nil), 0x1a2f45c)
Pads 3 out of 3
Device 0: 6->6: PAD
Device 1: 7->7: PAD
Device 2: 5->5: KEYBOARDPAD
Device 3: 4->4: MOUSE
Device 4: 5->5: KEYBOARD
H:\\FIFA 11\buttonDataSetup.ini : size 100474, pointer 03526B10
fixme:mixer:ALSA_MixerInit No master control found on HD-Audio Generic, disabling mixer
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x6b50a5a0,0x6b50a9e0): stub
fixme:thread:SetThreadIdealProcessor (0x39c): stub
fixme:thread:SetThreadIdealProcessor (0x3a0): stub
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x6b521040,0x6b520fc8): stub
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x6b5209c8,0x6b520fc8): stub
fixme:thread:SetThreadIdealProcessor (0x3e0): stub
fixme:thread:SetThreadIdealProcessor (0x3e4): stub
RenderThread started
fixme:thread:SetThreadIdealProcessor (0x3e8): stub
FEThread started
InputThread started
fixme:thread:SetThreadIdealProcessor (0x3f8): stub
Mounting data/sceneassets/genheadtex.big
fixme:thread:SetThreadIdealProcessor (0x3fc): stub
DLC Event received: INITIALIZATION_COMPLETE
fixme:winsock:WSAIoctl unsupported WS_IOCTL cmd (c8000014)
fixme:winsock:WSAIoctl unsupported WS_IOCTL cmd (c8000014)
fixme:winsock:WSAIoctl unsupported WS_IOCTL cmd (c8000014)
fixme:thread:SetThreadIdealProcessor (0x420): stub
fixme:dinput:joy_polldev joystick cannot handle type 4 event (code 4)
fixme:dinput:joy_polldev joystick cannot handle type 4 event (code 4)
Before LoadAnimation
maxCacheSize: 0
After LoadAnimation
After LoadEbosFromDisc
Start Audio Logic Init
AudioLogic::Init()
[AUDIO] Load file 'audiodata/dynamicmixer/soccer_dynmixGAME_MODE_SOCCER_MATCH.mxb' size 4k
[AUDIO] Load file 'audiodata/rwaudiocontroller/registerpatches.xml' size 5k
[AUDIO] Load file 'audiodata/rwaudiocontroller/Global_Patch.ptc' size 132k
[AUDIO] Load file 'audiodata/rwaudiocontroller/AEMS_AmbienceLoops.ptc' size 1k
[AUDIO] Load file 'audiodata/rwaudiocontroller/AEMS_Anticipation.ptc' size 2k
[AUDIO] Load file 'audiodata/rwaudiocontroller/AEMS_BallBounce.ptc' size 1k
[AUDIO] Load file 'audiodata/rwaudiocontroller/AEMS_BallHit_Net.ptc' size 1k
[AUDIO] Load file 'audiodata/rwaudiocontroller/AEMS_BallHit_Post.ptc' size 1k
[AUDIO] Load file 'audiodata/rwaudiocontroller/AEMS_BallHit_Stadium.ptc' size 3k
[AUDIO] Load file 'audiodata/rwaudiocontroller/AEMS_BallTouch.ptc' size 3k
[AUDIO] Load file 'audiodata/rwaudiocontroller/AEMS_BallTouch_Pass.ptc' size 1k
[AUDIO] Load file 'audiodata/rwaudiocontroller/AEMS_BallTouch_Shoot.ptc' size 1k
[AUDIO] Load file 'audiodata/rwaudiocontroller/AEMS_BallTouch_Taps.ptc' size 1k
[AUDIO] Load file 'audiodata/rwaudiocontroller/AEMS_Beds_High.ptc' size 1k
[AUDIO] Load file 'audiodata/rwaudiocontroller/AEMS_Beds_Low.ptc' size 1k
[AUDIO] Load file 'audiodata/rwaudiocontroller/AEMS_Beds_Med.ptc' size 1k
[AUDIO] Load file 'audiodata/rwaudiocontroller/AEMS_Breath.ptc' size 1k
[AUDIO] Load file 'audiodata/rwaudiocontroller/AEMS_Cloth.ptc' size 1k
[AUDIO] Load file 'audiodata/rwaudiocontroller/AEMS_Collision.ptc' size 2k
[AUDIO] Load file 'audiodata/rwaudiocontroller/AEMS_Feet.ptc' size 1k
[AUDIO] Load file 'audiodata/rwaudiocontroller/AEMS_fe_sfx.ptc' size 1k
[AUDIO] Load file 'audiodata/rwaudiocontroller/AEMS_Grains_Whistle_High.ptc' size 2k
[AUDIO] Load file 'audiodata/rwaudiocontroller/AEMS_Grains_Whistle_High_UK.ptc' size 2k
[AUDIO] Load file 'audiodata/rwaudiocontroller/AEMS_Grains_Whistle_Med.ptc' size 2k
[AUDIO] Load file 'audiodata/rwaudiocontroller/AEMS_Grains_Whistle_Med_UK.ptc' size 2k
[AUDIO] Load file 'audiodata/rwaudiocontroller/AEMS_Jostle.ptc' size 1k
[AUDIO] Load file 'audiodata/rwaudiocontroller/AEMS_LoadLoop.ptc' size 2k
[AUDIO] Load file 'audiodata/rwaudiocontroller/AEMS_Loop_Whistle_BRAZIL.ptc' size 0k
[AUDIO] Load file 'audiodata/rwaudiocontroller/AEMS_Loop_Whistle_EURO.ptc' size 0k
[AUDIO] Load file 'audiodata/rwaudiocontroller/AEMS_Loop_Whistle_FRENCH.ptc' size 0k
[AUDIO] Load file 'audiodata/rwaudiocontroller/AEMS_Loop_Whistle_GERMAN.ptc' size 0k
[AUDIO] Load file 'audiodata/rwaudiocontroller/AEMS_Loop_Whistle_LATIN.ptc' size 0k
[AUDIO] Load file 'audiodata/rwaudiocontroller/AEMS_Loop_Whistle_SMALL.ptc' size 0k
[AUDIO] Load file 'audiodata/rwaudiocontroller/AEMS_Loop_Whistle_UK.ptc' size 0k
[AUDIO] Load file 'audiodata/rwaudiocontroller/AEMS_PaMusic.ptc' size 4k
[AUDIO] Load file 'audiodata/rwaudiocontroller/AEMS_Pepper_Drums.ptc' size 2k
[AUDIO] Load file 'audiodata/rwaudiocontroller/AEMS_Pepper_Heckles.ptc' size 2k
[AUDIO] Load file 'audiodata/rwaudiocontroller/AEMS_Pepper_SFX.ptc' size 2k
[AUDIO] Load file 'audiodata/rwaudiocontroller/AEMS_Rct_Angry.ptc' size 1k
[AUDIO] Load file 'audiodata/rwaudiocontroller/AEMS_Rct_Applause.ptc' size 1k
[AUDIO] Load file 'audiodata/rwaudiocontroller/AEMS_Rct_Boo.ptc' size 1k
[AUDIO] Load file 'audiodata/rwaudiocontroller/AEMS_Rct_Cheer.ptc' size 1k
[AUDIO] Load file 'audiodata/rwaudiocontroller/AEMS_Rct_GoalAway.ptc' size 1k
[AUDIO] Load file 'audiodata/rwaudiocontroller/AEMS_Rct_GoalHome.ptc' size 1k
[AUDIO] Load file 'audiodata/rwaudiocontroller/AEMS_Rct_Jeer.ptc' size 1k
[AUDIO] Load file 'audiodata/rwaudiocontroller/AEMS_Rct_Oh.ptc' size 1k
[AUDIO] Load file 'audiodata/rwaudiocontroller/AEMS_Rct_OhAngry.ptc' size 1k
[AUDIO] Load file 'audiodata/rwaudiocontroller/AEMS_Rct_PaCheers.ptc' size 1k
[AUDIO] Load file 'audiodata/rwaudiocontroller/AEMS_Rct_PaCheers_Ole.ptc' size 1k
[AUDIO] Load file 'audiodata/rwaudiocontroller/AEMS_Rct_Shot.ptc' size 1k
[AUDIO] Load file 'audiodata/rwaudiocontroller/AEMS_Rct_Taunt_ooo.ptc' size 1k
[AUDIO] Load file 'audiodata/rwaudiocontroller/AEMS_Rct_Whistle.ptc' size 1k
[AUDIO] Load file 'audiodata/rwaudiocontroller/AEMS_Ref_Whistle.ptc' size 2k
[AUDIO] Load file 'audiodata/rwaudiocontroller/AEMS_Tag_Action.ptc' size 1k
[AUDIO] Load file 'audiodata/rwaudiocontroller/AEMS_Tag_BodyFall.ptc' size 3k
[AUDIO] Load file 'audiodata/rwaudiocontroller/AEMS_Tag_BodyFalls_Grass.ptc' size 2k
[AUDIO] Load file 'audiodata/rwaudiocontroller/AEMS_Tag_Cloth.ptc' size 4k
[AUDIO] Load file 'audiodata/rwaudiocontroller/AEMS_Tag_Effort.ptc' size 3k
[AUDIO] Load file 'audiodata/rwaudiocontroller/AEMS_Tag_Slide.ptc' size 3k
[AUDIO] Load file 'audiodata/rwaudiocontroller/AEMS_Tag_Vox.ptc' size 3k
[AUDIO] Load file 'audiodata/rwaudiocontroller/Chants_Away_Sub.ptc' size 1k
[AUDIO] Load file 'audiodata/rwaudiocontroller/Chants_Home_Sub.ptc' size 2k
[AUDIO] Load file 'audiodata/rwaudiocontroller/AEMS_AmbienceIncidentals.ptc' size 1k
[AUDIO] Load file 'audiodata/rwaudiocontroller/Pan3d.ptc' size 2k
[AUDIO] Load file 'audiodata/rwaudiocontroller/src_Announcer.ptc' size 2k
[AUDIO] Load file 'audiodata/rwaudiocontroller/src_ChantsAway.ptc' size 0k
[AUDIO] Load file 'audiodata/rwaudiocontroller/src_ChantsHome.ptc' size 0k
[AUDIO] Load file 'audiodata/rwaudiocontroller/src_Commentary.ptc' size 0k
[AUDIO] Load file 'audiodata/rwaudiocontroller/src_EA_Trax.ptc' size 1k
[AUDIO] Load file 'audiodata/rwaudiocontroller/src_Mp3.ptc' size 0k
[AUDIO] Load file 'audiodata/rwaudiocontroller/src_Player_Speech.ptc' size 1k
[AUDIO] Load file 'audiodata/rwaudiocontroller/src_Replay_Playback.ptc' size 0k
[AUDIO] Load file 'audiodata/rwaudiocontroller/SubmixGroups.ptc' size 60k
[AUDIO] Load file 'audiodata/rwaudiocontroller/createpatches.xml' size 0k
[AUDIO] Load file 'audiodata/moduledefs/sound3dmoduledef.xml' size 0k
[AUDIO] Load file 'audiodata/aemsdata/aems.bin' size 0k
[AUDIO] Load file 'audiodata/aemsdata/aems_events.csi' size 7k
[AUDIO] Load file 'audiodata/aemsdata/Initialization.abk' size 16k
[AUDIO] Load file 'audiodata/aemsdata/ui_ionaudioevents.abk' size 259k
[AUDIO] Load file 'audiodata/aemsdata/Ambience.abk' size 1k
[AUDIO] Load file 'audiodata/aemsdata/Pitch_SFX_01.abk' size 302k
[AUDIO] Load file 'audiodata/aemsdata/Player_SFX_01.abk' size 1707k
[AUDIO] Load file 'audiodata/aemsdata/Pepper_Shaker_GEN.abk' size 10k
[AUDIO] Load file 'audiodata/aemsdata/PA_Music.abk' size 35k
[AUDIO] Load file 'audiodata/aemsdata/PressStart_Screen.abk' size 3513k
[AUDIO] Load file 'audiodata/moduledefs/commentaryspeechmoduledef.xml' size 1k
[AUDIO] Load file 'audiodata/speechdata/commentary_triggers.csi' size 2k
[AUDIO] Load file 'audiodata/speechdata/commentary_events.csi' size 31k
[AUDIO] Load file 'audiodata/speechdata/commentary_eventsystem.xml' size 103k
[AUDIO] Load file 'audiodata/speechdata/ita_it/commentary_graffitiruntime.xml' size 2658k
[AUDIO] Load file 'audiodata/speechdata/ita_it/commentary_repetitionpools.xml' size 0k
[AUDIO] Load file 'audiodata/speechdata/ita_it/commentary_sentences.xml' size 335k
[AUDIO] Load file 'audiodata/speechdata/commentary_triggers_eventsystem.xml' size 72k
[AUDIO] Load file 'audiodata/speechdata/commentary_contextdata.xml' size 1215k
[AUDIO] Load file 'audiodata/speechdata/speechgas.css' size 330k
[AUDIO] Load file 'audiodata/speechdata/ita_it/ita_it.sbr' size 628k
[AUDIO] Load file 'audiodata/crowdlogic/crowdlogicevents.csi' size 2k
[AUDIO] Load file 'audiodata/crowdlogic/crowd_eventsystem.xml' size 37k
[AUDIO] Load file 'audiodata/crowdlogic/script.css' size 140k
[AUDIO] Load file 'audiodata/crowdlogic/crowd_contextdata.xml' size 489k
[AUDIO] Load file 'audiodata/moduledefs/announcerspeechmoduledef.xml' size 0k
[AUDIO] Load file 'audiodata/announcerdata/announcer_eng.sbr' size 257k
[AUDIO] Load file 'audiodata/announcerdata/announcer_events.csi' size 0k
[AUDIO] Load file 'audiodata/announcerdata/announcer_eventsystem.xml' size 9k
[AUDIO] Load file 'audiodata/announcerdata/announcer_graffitiruntime_eng.xml' size 1543k
[AUDIO] Load file 'audiodata/announcerdata/announcer_repetitionpools_eng.xml' size 0k
[AUDIO] Load file 'audiodata/announcerdata/announcer_sentences_eng.xml' size 22k
[AUDIO] Load file 'audiodata/moduledefs/playercallsspeechmoduledef.xml' size 0k
[AUDIO] Load file 'audiodata/playercalls/playercalls.sbr' size 95k
[AUDIO] Load file 'audiodata/playercalls/playercalls_events.csi' size 0k
[AUDIO] Load file 'audiodata/playercalls/playercalls_eventsystem.xml' size 2k
[AUDIO] Load file 'audiodata/playercalls/playercalls_graffitiruntime.xml' size 324k
[AUDIO] Load file 'audiodata/playercalls/playercalls_repetitionpools.xml' size 0k
[AUDIO] Load file 'audiodata/playercalls/playercalls_sentences.xml' size 3k
[AUDIO] Load file 'audiodata/moduledefs/chantsmoduledef.xml' size 0k
[AUDIO] Load file 'audiodata/chantdata/samples.sbr' size 46k
[AUDIO] Load file 'audiodata/chantdata/chantevents.csi' size 0k
[AUDIO] Load file 'audiodata/chantdata/graffitievents.xml' size 10k
[AUDIO] Load file 'audiodata/chantdata/graffitiruntime.xml' size 119k
[AUDIO] Load file 'audiodata/chantdata/chant_eventsystem.xml' size 3k
[AUDIO] Load file 'audiodata/chantdata/repetitionpools.xml' size 0k
fixme:thread:SetThreadIdealProcessor (0x428): stub
~~AudioLogic::Init() Done...
Audio Logic Init Complete: 95 ms
[AUDIO] Load file 'audiodata/musicdata/music_snr.big' size 1k
fixme:thread:SetThreadIdealProcessor (0x458): stub
AudioCommentary::Remove
LiveSeason::Remove
VProBoosts::Remove
AudioCommentary::Add
LiveSeason::Add
VProBoosts::Add boost
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x4ed610a8) : pBox=0x1480a0d8 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x4ed610a8) : pBox=0x1480a0d8 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x4edcce08) : pBox=0x1480a0d8 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x4edcce08) : pBox=0x1480a0d8 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x4ee1ecb0) : pBox=0x1480a0d8 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x4ee1ecb0) : pBox=0x1480a0d8 stub
fixme:dinput:joy_polldev joystick cannot handle type 4 event (code 4)
fixme:dinput:joy_polldev joystick cannot handle type 4 event (code 4)
fixme:dinput:joy_polldev joystick cannot handle type 4 event (code 4)
fixme:dinput:joy_polldev joystick cannot handle type 4 event (code 4)
[DLC] AUDIO mLangString now set to ita_it
[AUDIO] Load file 'audiodata/moduledefs/commentaryspeechmoduledef.xml' size 1k
[AUDIO] Load file 'audiodata/speechdata/commentary_triggers_eventsystem.xml' size 72k
[AUDIO] Load file 'audiodata/speechdata/commentary_contextdata.xml' size 1215k
[AUDIO] Load file 'audiodata/speechdata/speechgas.css' size 330k
[AUDIO] Load file 'audiodata/speechdata/ita_it/ita_it.sbr' size 628k
[AUDIO] Load file 'audiodata/speechdata/commentary_eventsystem.xml' size 103k
[AUDIO] Load file 'audiodata/speechdata/ita_it/commentary_graffitiruntime.xml' size 2658k
[AUDIO] Load file 'audiodata/speechdata/ita_it/commentary_repetitionpools.xml' size 0k
[AUDIO] Load file 'audiodata/speechdata/ita_it/commentary_sentences.xml' size 335k
[AUDIO] callback time 48.631307ms
[AUDIO] callback time 28.381253ms
fixme:dinput:joy_polldev joystick cannot handle type 4 event (code 4)
fixme:dinput:joy_polldev joystick cannot handle type 4 event (code 4)
fixme:dinput:joy_polldev joystick cannot handle type 4 event (code 4)
fixme:thread:SetThreadIdealProcessor (0x45c): stub
fixme:dinput:joy_polldev joystick cannot handle type 4 event (code 4)
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1b17ae20) : pBox=(nil) stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1b17b3d0) : pBox=(nil) stub
ParticlesXmlParser::VerifyAttributes: Attribute 'version' not recognised in XML ''.
ParticlesXmlParser::VerifyAttributes: Attribute 'version' not recognised in XML ''.
ParticlesXmlParser::VerifyAttributes: Attribute 'version' not recognised in XML ''.
ParticlesXmlParser::VerifyAttributes: Attribute 'version' not recognised in XML ''.
ParticlesXmlParser::VerifyAttributes: Attribute 'version' not recognised in XML ''.
ParticlesXmlParser::VerifyAttributes: Attribute 'version' not recognised in XML ''.
ParticlesXmlParser::VerifyAttributes: Attribute 'version' not recognised in XML ''.
ParticlesXmlParser::VerifyAttributes: Attribute 'version' not recognised in XML ''.
ParticlesXmlParser::VerifyAttributes: Attribute 'version' not recognised in XML ''.
ParticlesXmlParser::VerifyAttributes: Attribute 'version' not recognised in XML ''.
ParticlesXmlParser::VerifyAttributes: Attribute 'version' not recognised in XML ''.
ParticlesXmlParser::VerifyAttributes: Attribute 'version' not recognised in XML ''.
ParticlesXmlParser::VerifyAttributes: Attribute 'version' not recognised in XML ''.
ParticlesXmlParser::VerifyAttributes: Attribute 'version' not recognised in XML ''.
ParticlesXmlParser::VerifyAttributes: Attribute 'version' not recognised in XML ''.
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6b7b52a0) : pBox=(nil) stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x4eff9840) : pBox=(nil) stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x4eff9a00) : pBox=(nil) stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x4eff9bf8) : pBox=(nil) stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x4eff9e08) : pBox=(nil) stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x4effa018) : pBox=(nil) stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x4effa228) : pBox=(nil) stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x4effa438) : pBox=(nil) stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x4effa648) : pBox=(nil) stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x4eff73b8) : pBox=(nil) stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1b17ad58) : pBox=(nil) stub
[AUDIO] Load file 'audiodata/aemsdata/Arena_NA.abk' size 2k
[AUDIO] callback time 0.141638ms
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1b17b1c0) : pBox=(nil) stub
[ECG] Environment Collision Geo Sent.
[ECG] Sending Environment Collision Geo due to Gameplay::StartHalf message.
[ECG] Environment Collision Geo Sent.
NISAI:: HaltAllSequence
NISAI::DestroyScene 1fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1a07bf28) : pBox=(nil) stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1b17afb0) : pBox=(nil) stub
[ECG] Environment Collision Geo Sent.
TeamID = 243
TeamID = 243
fixme:dinput:joy_polldev joystick cannot handle type 4 event (code 4)
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1a07be40) : pBox=(nil) stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1b17aee8) : pBox=(nil) stub
fixme:dinput:joy_polldev joystick cannot handle type 4 event (code 4)
fixme:dinput:joy_polldev joystick cannot handle type 4 event (code 4)
fixme:dinput:joy_polldev joystick cannot handle type 4 event (code 4)
fixme:dinput:joy_polldev joystick cannot handle type 4 event (code 4)
fixme:dinput:joy_polldev joystick cannot handle type 4 event (code 4)
fixme:dinput:joy_polldev joystick cannot handle type 4 event (code 4)
fixme:dinput:joy_polldev joystick cannot handle type 4 event (code 4)
fixme:dinput:joy_polldev joystick cannot handle type 4 event (code 4)
fixme:dinput:joy_polldev joystick cannot handle type 4 event (code 4)
fixme:dinput:joy_polldev joystick cannot handle type 4 event (code 4)
fixme:dinput:joy_polldev joystick cannot handle type 4 event (code 4)
fixme:dinput:joy_polldev joystick cannot handle type 4 event (code 4)
fixme:dinput:joy_polldev joystick cannot handle type 4 event (code 4)
fixme:dinput:joy_polldev joystick cannot handle type 4 event (code 4)
fixme:dinput:joy_polldev joystick cannot handle type 4 event (code 4)
fixme:dinput:joy_polldev joystick cannot handle type 4 event (code 4)
fixme:dinput:joy_polldev joystick cannot handle type 4 event (code 4)
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1b17ae20) : pBox=(nil) stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1b17b3d0) : pBox=(nil) stub
NISAI:: HaltAllSequence
NISAI::DestroyScene 1NISAI:: HaltAllSequence
NISAI::DestroyScene 1fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1b17ad58) : pBox=(nil) stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1b17b1c0) : pBox=(nil) stub
[ECG] Environment Collision Geo Sent.
[ECG] Sending Environment Collision Geo due to Gameplay::StartHalf message.
[ECG] Environment Collision Geo Sent.
!!!!!!!!! set setstadiumselect to matchsetup 197
!!!!!!!!! set setstadiumselect to matchsetup 197
[AUDIO] callback time 6.503618ms
TeamID = 45
TeamID = 44
NISAI:: HaltAllSequence
NISAI::DestroyScene 1setting weather to 0
[AUDIO] Load file 'audiodata/moduledefs/announcerspeechmoduledef.xml' size 0k
[AUDIO] Load file 'audiodata/announcerdata/announcer_ita.sbr' size 257k
[AUDIO] Load file 'audiodata/announcerdata/announcer_eventsystem.xml' size 9k
[AUDIO] Load file 'audiodata/announcerdata/announcer_graffitiruntime_ita.xml' size 2054k
[AUDIO] Load file 'audiodata/announcerdata/announcer_repetitionpools_ita.xml' size 0k
[AUDIO] Load file 'audiodata/announcerdata/announcer_sentences_ita.xml' size 17k
[AUDIO] callback time 47.744602ms
ParticlesXmlParser::VerifyAttributes: Attribute 'version' not recognised in XML ''.
ParticlesXmlParser::VerifyAttributes: Attribute 'version' not recognised in XML ''.
ParticlesXmlParser::VerifyAttributes: Attribute 'version' not recognised in XML ''.
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1a07bf28) : pBox=(nil) stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1b17afb0) : pBox=(nil) stub
[ECG] Environment Collision Geo Sent.
wine: Unhandled page fault on read access to 0x00000010 at address 0x7b0fd4ae (thread 002c), starting debugger...
XIO:  fatal IO error 11 (Risorsa temporaneamente non disponibile) on X server ":0.0"
      after 57 requests (57 known processed) with 0 events remaining.
realac0@realac0-desktop:~/.PlayOnLinux/wineprefix/FIFA11/drive_c/Programmi/EA Sports/FIFA 11/Game$ 


```any idea?

i really can't understand what is the problem.
have already tryied differents wine versions and change windows compatibility on wine settings.

any help will be appreciated

cya and sorry for my english, i ' am italian.

Realac0

---

### Post by cwwilson721 on 2010-11-05
It seems to be an ATi driver/Linux kernel issue.

About all I can say is wait to see what happens with newer kernels and ATi driver updates.

Have you tried to install the latest ATi drivers from ATi (not the official Ubuntu package from Additional Drivers)?

Look on other parts of the Ubuntu Forums on how to do this.

And wait and see about kernel updates.

---

### Post by lkjoel on 2010-11-05
I did not see any problems with FIFA.
Your WINE version is outdated, which might create a few problems
```
sudo apt-get update
sudo apt-get dist-upgrade
```

---

### Post by realac0 on 2010-11-06
what mean my wine version is outdated?
i don't want update to 10.10 (want stay on LTS version).
But i change differents version on wine with PlayOnLinux.
U think this can be a problem?
pls help i really dunno how to solve problems explained
realac0

---

### Post by realac0 on 2010-11-06
this is the error on WINE running FIFA 11 that i'd like to know if someone can solve for me:

```
!!!!!!!!! set setstadiumselect to matchsetup 197
!!!!!!!!! set setstadiumselect to matchsetup 197
[AUDIO] callback time 6.746666ms
TeamID = 45
TeamID = 44
NISAI:: HaltAllSequence
NISAI::DestroyScene 1setting weather to 0
[AUDIO] Load file 'audiodata/moduledefs/announcerspeechmoduledef.xml' size 0k
[AUDIO] Load file 'audiodata/announcerdata/announcer_ita.sbr' size 257k
[AUDIO] Load file 'audiodata/announcerdata/announcer_eventsystem.xml' size 9k
[AUDIO] Load file 'audiodata/announcerdata/announcer_graffitiruntime_ita.xml' size 2054k
[AUDIO] Load file 'audiodata/announcerdata/announcer_repetitionpools_ita.xml' size 0k
[AUDIO] Load file 'audiodata/announcerdata/announcer_sentences_ita.xml' size 17k
[AUDIO] callback time 20.469635ms
ParticlesXmlParser::VerifyAttributes: Attribute 'version' not recognised in XML ''.
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x55cbd720) : pBox=0x1480a0d8 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x55cbd720) : pBox=0x1480a0d8 stub
ParticlesXmlParser::VerifyAttributes: Attribute 'version' not recognised in XML ''.
ParticlesXmlParser::VerifyAttributes: Attribute 'version' not recognised in XML ''.
[ECG] Environment Collision Geo Sent.
wine: Unhandled page fault on read access to 0x00000000 at address 0x7afeb0ae (thread 003a), starting debugger...
^Crealac0@realac0-desktop:~/.PlayOnLinux/wineprefix/FIFA11/drive_c/Programmi/EA orts/FIFA 11/Game$ 
```

again, any idea?

---

### Post by realac0 on 2010-11-18
so, no one ever see something similar?
is very annoying i can t play pes2011 and/or fifa11 for this stupid thing all seem to work than i just can't see players ;(

about M&B Warband yesterday, after a lot of test and change, i managed to make it work. Needed to set on config directx7 instead of directx9 and have done some change on edit wine configuration too.

what is strange, is that before, with 10.09 ATI drivers, all was working on directx9 ...

last thing:

why i can't install anymore 10.09 drivers on 2.6.32.26 kernel?
i can install 10.10, now 10.11 (downloaded today, but nothing changed on my problems) but can't go back to 10.09 - 10.08 etc etc

this is my uname -a
Linux realac0-desktop 2.6.32-26-generic #46-Ubuntu SMP Tue Oct 26 16:47:18 UTC 2010 x86_64 GNU/Linux

so, no one can help me?

(sorry for my english)

---

### Post by tora201 on 2011-01-08
Same problem here man! Ah, so it was not just me. I put this on the PlayonLinux Forums as well. Pity! I hope somebody manages to get Fifa 2011 going...

Cheers

---

