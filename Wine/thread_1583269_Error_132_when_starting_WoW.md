---
title: "Error 132 when starting WoW"
date: 2010-09-27
forum: Wine
---

### Post by jh77if on 2010-09-27
I installed wow according to ubuntu guide. I am opening Wow.exe in terminal with -opengl flag at the end. I would modify config.wtf accordingly to run in open GL mode but as i cannot even get to the log in screen, there is no config.wtf (the file is created after first log-in)

I did some searching and first step was to run a memory test. i downloaded and burned memtest 86 to a cd, ran it. and it said that i passed 100%. though error 132 is telling me that memory cannot be "read". 

when i open wow. i get the intro video for wrath of the lich king, if i hit escape the error #132 pops up and wow crashes. if i finish out the entire into video wow crashes and error 132 pops up. attached is a screen shot of the error message.

i have also tried messing with winecfg running in NT 4.0, 2000, 98, ME, XP, and 7. all windows OSes result with the same crash and error 132.

here is terminal code after running wow.exe -opengl:

:~$ '/home/andrew/.wine/dosdevices/c:/Program Files/World of Warcraft/Wow.exe' -opengl
archive Data\enUS\patch-enUS.MPQ opened
archive Data\patch.MPQ opened
archive Data\enUS\patch-enUS-2.MPQ opened
archive Data\enUS\patch-enUS-3.MPQ opened
archive Data\patch-2.MPQ opened
archive Data\patch-3.MPQ opened
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
fixme:win:EnumDisplayDevicesW ((null),0,0x192ee20,0x00000000), stub!
fixme:d3d_caps:wined3d_guess_card No card selector available for GL vendor 3 and card vendor 8086.
fixme:win:EnumDisplayDevicesW ((null),0,0x192eb0c,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x192f324,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x192f438,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x192f5fc,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x192f5f8,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x192f07c,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x192f1b4,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x192f574,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x192f564,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x192f07c,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x192f1b4,0x00000000), stub!
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x13dd68,0x13dc68): stub
fixme:avrt:AvSetMmThreadCharacteristicsW (L"Pro Audio",0x192f89c): stub
fixme:avrt:AvSetMmThreadCharacteristicsW (L"Pro Audio",0x192f89c): stub
failed to open C:/Program Files/World of Warcraft/Interface/AddOns
fixme:win:EnumDisplayDevicesW ((null),0,0x192df60,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x192df88,0x00000000), stub!
do_wait: drmWaitVBlank returned -1, IRQs don't seem to be working correctly.
Try adjusting the vblank_mode configuration parameter.
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 5000
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 5000
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB
fixme:reg:GetNativeSystemInfo (0x33fd9c) using GetSystemInfo()

any help much appreciated. also if you would like to try to take a crack at it email me at [email]andrewmtalalt@gmail.com[/email] and i will provide you with remote desktop information.

---

### Post by jh77if on 2010-09-27
it appears to be an IRQ problem. just one week ago i did a full 25 man  raid with 20-30 fps on medium settings. I cannot fathom how changing to  ubuntu could cause a problem with my hardware.

---

### Post by jh77if on 2010-09-27
bump, the opengl flag was causing the crash. it seems i cannot run wow in opengl. i logged in successfully and was running at 1 FPS in a very low population area (not normal at ALL) so the config.wtf file was created. however adding the opengl line to config.wtf caused the crash. also configuring my registry for opengl also resulted in crash and error 132.

---

### Post by cwwilson721 on 2010-09-28
> **jh77if said:**
> bump, the opengl flag was causing the crash. it seems i cannot run wow in opengl. i logged in successfully and was running at 1 FPS in a very low population area (not normal at ALL) so the config.wtf file was created. however adding the opengl line to config.wtf caused the crash. also configuring my registry for opengl also resulted in crash and error 132.
Let me guess...Intel Video?

---

