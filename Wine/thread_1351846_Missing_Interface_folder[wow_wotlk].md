---
title: "Missing Interface folder[wow wotlk]"
date: 2009-12-11
forum: Wine
---

### Post by domosplace on 2009-12-11
Hey everyone

Im a Ubuntu noob. For the past 7 weeks i been trying to get this game to Wow WOTLK
I really dont wanna have to go back to windows cause its a pain in the bum. So I downloaded Wine and configured it then downloaded firestarted and configured it. Then i downloaded Wow.  The patches installed without any problems for the first time. When i i opened it in terminal i got the following

```
 
lee@lee-desktop:~$ env WINEPREFIX="/home/lee/.wine" wine "C:\Program Files\World of Warcraft\Wow.exe" -opengl
fixme:advapi:SetSecurityInfo stub
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
fixme:win:EnumDisplayDevicesW ((null),0,0x39ed54,0x00000000), stub!
fixme:d3d_caps:wined3d_guess_vendor Received unrecognized GL_VENDOR "VA Linux Systems, Inc.". Returning VENDOR_WINE.
fixme:win:EnumDisplayDevicesW ((null),0,0x39ea68,0x00000000), stub!
fixme:d3d_caps:wined3d_guess_vendor Received unrecognized GL_VENDOR "VA Linux Systems, Inc.". Returning VENDOR_WINE.
fixme:win:EnumDisplayDevicesW ((null),0,0x39ef40,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39f264,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39f3c4,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39f534,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39f530,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39efa4,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39f0e4,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39f4c4,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39f4b4,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39efa4,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39f0e4,0x00000000), stub!
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x159828,0x159728): stub
fixme:avrt:AvSetMmThreadCharacteristicsW (L"Pro Audio",0x39f794): stub
fixme:avrt:AvSetMmThreadCharacteristicsW (L"Pro Audio",0x39f794): stub
err:dsound:DSOUND_MixOne Fatal error. Under/Overflow? primary_done=82908, mixpos=14452/90316 (15728/98304), primary_mixpos=20804, writepos=26096, mixlen=580
err:dsound:DSOUND_MixOne Fatal error. Under/Overflow? primary_done=82908, mixpos=84288/90316 (91740/98304), primary_mixpos=20804, writepos=26096, mixlen=580
err:dsound:DSOUND_MixOne Fatal error. Under/Overflow? primary_done=82908, mixpos=14452/90316 (15728/98304), primary_mixpos=20804, writepos=26096, mixlen=580
err:dsound:DSOUND_MixOne Fatal error. Under/Overflow? primary_done=82908, mixpos=84288/90316 (91740/98304), primary_mixpos=20804, writepos=26096, mixlen=580
err:dsound:DSOUND_MixOne Fatal error. Under/Overflow? primary_done=82908, mixpos=14452/90316 (15728/98304), primary_mixpos=20804, writepos=26096, mixlen=580
err:dsound:DSOUND_MixOne Fatal error. Under/Overflow? primary_done=82908, mixpos=84288/90316 (91740/98304), primary_mixpos=20804, writepos=26096, mixlen=580
err:dsound:DSOUND_MixOne Fatal error. Under/Overflow? primary_done=82908, mixpos=14452/90316 (15728/98304), primary_mixpos=20804, writepos=26096, mixlen=580
err:dsound:DSOUND_MixOne Fatal error. Under/Overflow? primary_done=82908, mixpos=84288/90316 (91740/98304), primary_mixpos=20804, writepos=26096, mixlen=580
err:dsound:DSOUND_MixOne Fatal error. Under/Overflow? primary_done=82908, mixpos=14452/90316 (15728/98304), primary_mixpos=20804, writepos=26096, mixlen=580
err:dsound:DSOUND_MixOne Fatal error. Under/Overflow? primary_done=82908, mixpos=84288/90316 (91740/98304), primary_mixpos=20804, writepos=26096, mixlen=580
err:dsound:DSOUND_MixOne Fatal error. Under/Overflow? primary_done=82908, mixpos=14452/90316 (15728/98304), primary_mixpos=20804, writepos=26096, mixlen=580
err:dsound:DSOUND_MixOne Fatal error. Under/Overflow? primary_done=82908, mixpos=84288/90316 (91740/98304), primary_mixpos=20804, writepos=26096, mixlen=580
err:dsound:DSOUND_MixOne Fatal error. Under/Overflow? primary_done=82908, mixpos=14452/90316 (15728/98304), primary_mixpos=20804, writepos=26096, mixlen=580
err:dsound:DSOUND_MixOne Fatal error. Under/Overflow? primary_done=82908, mixpos=84288/90316 (91740/98304), primary_mixpos=20804, writepos=26096, mixlen=580
err:dsound:DSOUND_MixOne Fatal error. Under/Overflow? primary_done=82908, mixpos=14452/90316 (15728/98304), primary_mixpos=20804, writepos=26096, mixlen=580
err:dsound:DSOUND_MixOne Fatal error. Under/Overflow? primary_done=82908, mixpos=84288/90316 (91740/98304), primary_mixpos=20804, writepos=26096, mixlen=580
err:dsound:DSOUND_MixOne Fatal error. Under/Overflow? primary_done=82908, mixpos=14452/90316 (15728/98304), primary_mixpos=20804, writepos=26096, mixlen=580
err:dsound:DSOUND_MixOne Fatal error. Under/Overflow? primary_done=82908, mixpos=84288/90316 (91740/98304), primary_mixpos=20804, writepos=26096, mixlen=580
err:dsound:DSOUND_MixOne Fatal error. Under/Overflow? primary_done=82908, mixpos=14452/90316 (15728/98304), primary_mixpos=20804, writepos=26096, mixlen=17532
err:dsound:DSOUND_MixOne Fatal error. Under/Overflow? primary_done=82908, mixpos=84288/90316 (91740/98304), primary_mixpos=20804, writepos=26096, mixlen=17532
err:dsound:DSOUND_MixOne Fatal error. Under/Overflow? primary_done=82908, mixpos=14452/90316 (15728/98304), primary_mixpos=20804, writepos=26096, mixlen=17532
err:dsound:DSOUND_MixOne Fatal error. Under/Overflow? primary_done=82908, mixpos=84288/90316 (91740/98304), primary_mixpos=20804, writepos=26096, mixlen=17532
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 5000
err:dsound:DSOUND_MixOne Fatal error. Under/Overflow? primary_done=82908, mixpos=14452/90316 (15728/98304), primary_mixpos=20804, writepos=26096, mixlen=17532
err:dsound:DSOUND_MixOne Fatal error. Under/Overflow? primary_done=82908, mixpos=84288/90316 (91740/98304), primary_mixpos=20804, writepos=26096, mixlen=17532
err:dsound:DSOUND_MixOne Fatal error. Under/Overflow? primary_done=82908, mixpos=14452/90316 (15728/98304), primary_mixpos=20804, writepos=26096, mixlen=17532
err:dsound:DSOUND_MixOne Fatal error. Under/Overflow? primary_done=82908, mixpos=84288/90316 (91740/98304), primary_mixpos=20804, writepos=26096, mixlen=17532
err:dsound:DSOUND_MixOne Fatal error. Under/Overflow? primary_done=82908, mixpos=14452/90316 (15728/98304), primary_mixpos=20804, writepos=26096, mixlen=20352
err:dsound:DSOUND_MixOne Fatal error. Under/Overflow? primary_done=82908, mixpos=84288/90316 (91740/98304), primary_mixpos=20804, writepos=26096, mixlen=20352
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB
fixme:keyboard:X11DRV_ActivateKeyboardLayout 0x4090409, 0000: semi-stub!
Error: Rage 128 timed out... exiting

```

No i dont know what to do. I thought i could fix this problem by adding libraries when i configured wine but i didnt get any change...Please help its been over 2 months since i played...

Thanks for reading

PS. Is there a way to add wow in pol (playonlinux)?

---

