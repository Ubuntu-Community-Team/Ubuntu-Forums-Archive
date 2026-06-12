---
title: "AOSS, Wine, Warcraft, and Ventrilo Help?"
date: 2009-07-09
forum: Wine
---

### Post by jeremyj on 2009-07-09
I'm having some problems with sound in WoW from Wine.  I can get to the login screen fine and access my audio settings, but I get no sound during the cinematics or login animation.

For reference, I haven't run WoW and Vent at the same time, so I'm not getting any sound at the very least from WoW.  Haven't tried Vent, but I also haven't run the following command for it yet.  Amarok plays sound fine.

Currently running:
-  Ubuntu 9.04 Desktop Version
-  ATI RadeonHD 3650 graphics card (not sure if that would matter with the sound issue)
-  Not sure how to figure out my sound card.  ```
cat /proc/asound/cards

``` prints this:  ```
0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xfdff4000 irq 22
 1 [HDMI           ]: HDA-Intel - HDA ATI HDMI
                      HDA ATI HDMI at 0xfddfc000 irq 17
```

Wine is setup as:
Version 1.1.20
[LIST]
[*]Vista
[*]No library overrides
[*]No registry edits
[*]Graphics---  Allow DirectX apps... NOT ticked;  Allow Window Manager to decorate... ticked;  Allow the Window Manager to control the windows ticked;  Emulate virtual desktop ticked;  Desktop size 1024x800;  Vertex Shader support--- Hardware and Allow pixel shader ticked;  Screen res 96 dpi
[*]Audio--- I've tried both ALSA and OSS at different times (not ticked together)[/LIST]



Here's what I get after running ```
aoss /home/jeremy/.wine/drive_c/Program\ Files/World\ of\ Warcraft/Wow.exe
```
```
fixme:mixer:ALSA_MixerInit No master control found on HDA ATI HDMI, disabling mixer
fixme:advapi:SetSecurityInfo stub
archive Data\enUS\patch-enUS.MPQ opened
archive Data\patch.MPQ opened
archive Data\enUS\patch-enUS-2.MPQ opened
archive Data\patch-2.MPQ opened
archive Data\expansion.MPQ opened
archive Data\lichking.MPQ opened
archive Data\common.MPQ opened
archive Data\common-2.MPQ opened
archive Data\enUS\locale-enUS.MPQ opened
archive Data\enUS\speech-enUS.MPQ opened
archive Data\enUS\expansion-locale-enUS.MPQ opened
archive Data\enUS\lichking-locale-enUS.MPQ opened
archive Data\enUS\expansion-speech-enUS.MPQ opened
archive Data\enUS\lichking-speech-enUS.MPQ opened
fixme:win:EnumDisplayDevicesW ((null),0,0x39edac,0x00000000), stub!
fixme:d3d:IWineD3DImpl_FillGLCaps OpenGL implementation supports 16 vertex samplers and 16 total samplers
fixme:d3d:IWineD3DImpl_FillGLCaps Expected vertex samplers + MAX_TEXTURES(=8) > combined_samplers
fixme:win:EnumDisplayDevicesW ((null),0,0x39ebd0,0x00000000), stub!
fixme:d3d:IWineD3DImpl_FillGLCaps OpenGL implementation supports 16 vertex samplers and 16 total samplers
fixme:d3d:IWineD3DImpl_FillGLCaps Expected vertex samplers + MAX_TEXTURES(=8) > combined_samplers
fixme:win:EnumDisplayDevicesW ((null),0,0x39f0a8,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39f3f0,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39f588,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39f584,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39f578,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39f140,0x00000000), stub!
err:ole:CoGetClassObject class {bcde0395-e52f-467c-8e3d-c4579291692e} not registered
err:ole:CoGetClassObject class {bcde0395-e52f-467c-8e3d-c4579291692e} not registered
err:ole:create_server class {bcde0395-e52f-467c-8e3d-c4579291692e} not registered
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x7
err:ole:CoGetClassObject class {bcde0395-e52f-467c-8e3d-c4579291692e} not registered
err:ole:CoGetClassObject class {bcde0395-e52f-467c-8e3d-c4579291692e} not registered
err:ole:create_server class {bcde0395-e52f-467c-8e3d-c4579291692e} not registered
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x7
err:ole:CoGetClassObject class {bcde0395-e52f-467c-8e3d-c4579291692e} not registered
err:ole:CoGetClassObject class {bcde0395-e52f-467c-8e3d-c4579291692e} not registered
err:ole:create_server class {bcde0395-e52f-467c-8e3d-c4579291692e} not registered
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x7
err:ole:CoGetClassObject class {bcde0395-e52f-467c-8e3d-c4579291692e} not registered
err:ole:CoGetClassObject class {bcde0395-e52f-467c-8e3d-c4579291692e} not registered
err:ole:create_server class {bcde0395-e52f-467c-8e3d-c4579291692e} not registered
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x7
err:ole:CoGetClassObject class {bcde0395-e52f-467c-8e3d-c4579291692e} not registered
err:ole:CoGetClassObject class {bcde0395-e52f-467c-8e3d-c4579291692e} not registered
err:ole:create_server class {bcde0395-e52f-467c-8e3d-c4579291692e} not registered
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x7
failed to open C:/Program Files/World of Warcraft/Interface/AddOns
fixme:win:EnumDisplayDevicesW ((null),0,0x39deec,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39df24,0x00000000), stub!
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 5000
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 5000
fixme:reg:GetNativeSystemInfo (0x374040a4) using GetSystemInfo()
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB

```

---

### Post by jeremyj on 2009-07-09
Changed Wine's Window's version to XP, and I now have sound in WoW.  However, Amarok doesn't have sound if I open WoW before Amarok.  Pidgin, Evolution, and Flash in Firefox play sound with WoW running just fine.

With WoW playing first, I open Amarok and get this message from the icon bar up top:

Phonon:  KDE's Multimedia Library
The audio playback device HDA Intel (ALC888 Analog) does not work.
Falling back to HDA ATI HDMI ATI HDMI (HDMI Audio Output)



I'm thinking this Terminal line (from above post) is the key to my problems:

```
ixme:mixer:ALSA_MixerInit No master control found on HDA ATI HDMI, disabling mixer
```

I have AOSS installed to use with WoW, but it doesn't seem to be working.  Do I need to set it up for Amarok as well?  Or is this something else?

Any help would be appreciated.

---

### Post by jeremyj on 2009-07-09
Restarted my computer and all seems well.  I can hear WoW, Amarok, and Ventrilo together.

Since I had trouble finding info on all of this, here's what I did.  Maybe it will help someone else.  ):P

If I'm correct, my sound card should be a Realtek ALC888, BUT I'm not 100% on that.

AOSS installed via ```
sudo apt-get install aoss
```
Set WoW and Ventrilo to use AOSS via these Terminal commands (change <user> to your username in Ubuntu):
```
aoss /home/<user>/.wine/drive_c/Program\ Files/World\ of\ Warcraft/Wow.exe
```
```
aoss /home/<user>/.wine/drive_c/Program\ Files/Ventrilo/Ventrilo.exe
```

Note:  Program Files may not be where you installed WoW if you previously had Vista set as Wine's Windows version.  At least, this was my case, because during install, WoW asked me if I wanted to move the game to the Public folder.  I believe this is because Vista needs Administrative privileges for games such as WoW.

Sound setup details in Wine:
[LIST]
[*]Ubuntu 9.04
[*]Wine ver. 1.1.20
[*]Set Windows version to XP
[*]ALSA audio driver, Full hardware acceleration, Driver Emulation ticked/checked, didn't change anything else in this window
[*]Didn't emulate virtual desktop (under Graphics tab).  This may just be for aesthetics sake in hindsight, because I don't know if a virtual desktop would have an effect on sound.[/LIST]

Ubuntu sound setup details:
[LIST]
[*]System>Preferences>Sound
[*]Sound events- Sound playback:  Autodetect
[*]Music and Movies- Sound Playback:  Autodetect
[*]Audio Conferencing-  Sound playback:  Autodetect; Sound Capture:  ALSA- Advanced Linux Sound Architecture
[*]Default Mixer Tracks-  Device:  HDA Intel (Alsa Mixer)
[*]Volume Control icon in upper-right iconbar is set to HDA Intel (Alsa Mixer)[/LIST]


Hope this helps anyone else, and I hope this is a permanent fix for me as well.

EDIT:  Just thought I'd add that, when I run winecfg in the Terminal, I still get: ```
fixme:mixer:ALSA_MixerInit No master control found on HDA ATI HDMI, disabling mixer
```

Maybe this is ok, maybe this will cause problems down the road.  Someone else may be able to shed some light on that.

---

