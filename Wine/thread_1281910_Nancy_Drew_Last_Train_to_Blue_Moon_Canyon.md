---
title: "Nancy Drew: Last Train to Blue Moon Canyon"
date: 2009-10-03
forum: Wine
---

### Post by Joseph Schwenker on 2009-10-03
First of all, yes, I know, I am such a dork for playing Nancy Drew games, as I am a boy.  :rolleyes:
Second, I have successfully installed Nancy Drew: Last Train to Blue Moon Canyon, (**in Ubuntu 9.04 with WINE 1.1.30**) and have disc one in the drive.  I tried to launch the game, but the window closed as soon as it opened.  I then ran the file from the terminal, and got this output: 

[EMAIL="joseph@joseph:%7E/.wine"]joseph@joseph:~/.wine[/EMAIL]/dosdevices/c:/Program Files/Nancy Drew/Last Train to Blue Moon Canyon$ wine Game.exe
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
fixme:win:RegisterDeviceNotificationA (hwnd=0x12d280, filter=0x84ea04,flags=0x00000001),
    returns a fake device notification handle!
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
fixme:advapi:RegisterEventSourceW ((null),L"Bonjour Service"): stub
fixme:winsock:WS_setsockopt Unknown IPPROTO_IP optname 0x00000013
fixme:winsock:WSAIoctl SIO_GET_EXTENSION_FUNCTION_POINTER {f689d7c8-6f1f-436b-8a53-e54fe351c322}: stub
fixme:winsock:WSAIoctl SIO_GET_EXTENSION_FUNCTION_POINTER {f689d7c8-6f1f-436b-8a53-e54fe351c322}: stub
fixme:winsock:WSAIoctl -> SIO_ADDRESS_LIST_CHANGE request: stub
fixme:iphlpapi:GetAdaptersAddresses no support for IPv6 addresses
fixme:iphlpapi:GetAdaptersAddresses no support for IPv6 addresses
fixme:winsock:WS_setsockopt Unknown IPPROTO_IP optname 0x00000013
fixme:winsock:WSAIoctl SIO_GET_EXTENSION_FUNCTION_POINTER {f689d7c8-6f1f-436b-8a53-e54fe351c322}: stub
fixme:winsock:WS_setsockopt Unknown IPPROTO_IP optname 0x00000013
fixme:iphlpapi:DeleteIpForwardEntry (pRoute 0x87e9f8): stub
fixme:iphlpapi:CreateIpForwardEntry (pRoute 0x87e988): stub
fixme:service:EnumServicesStatusW 0x12d2c0 type=30 state=3 (nil) 0 0x87e818 0x87e824 0x87e820
fixme:advapi:ReportEventA (0xcafe4242,0x0004,0x0000,0x20000001,(nil),0x0001,0x00000000,0x87e628,(nil)): stub
fixme:advapi:ReportEventW (0xcafe4242,0x0004,0x0000,0x20000001,(nil),0x0001,0x00000000,0x12cd20,(nil)): stub
fixme:mixer:ALSA_MixerInit No master control found on USB Device 0x46d:0x89d, disabling mixer
fixme:keyboard:X11DRV_LoadKeyboardLayout L"00000409", 0001: stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x324f14,0x00000000), stub!
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x13fe98,0x141440): stub

Can anyone make any sense of this, or tell me what I need to install or configure?  I cannot seem to find an entry for this game on the WineHQ Bugzilla.  Please help!  Thanks!

---

### Post by eyecreate on 2010-10-21
Bug still exists:
[http://bugs.winehq.org/show_bug.cgi?id=19292](http://bugs.winehq.org/show_bug.cgi?id=19292)

---

