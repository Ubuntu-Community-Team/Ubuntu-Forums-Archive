---
title: "Morrowind can't load save game"
date: 2010-08-08
forum: Wine
---

### Post by superbum on 2010-08-08
everything else seems to work just fine but when I try to load a save game it freezes up.

I have ubuntu 10.04 for 64 bit processor and wine 1.2 I don't know what else would be relevant.  I know other people play morrowind on linux but I can't figure out how to fix this.

---

### Post by Progressive on 2010-08-08
Execute it from the terminal. Just type:

wine "C:\Program Files\Bethesda Softworks\Morrowind\Morrowind.exe"

Then when the error occurs, see what the output is. If you can't find a similar error through Google, then it could be a new issue and it might be worth submitting a bug report.

---

### Post by colinambulance on 2010-10-15
Same problem here.

my output is as follows:

fixme:heap:HeapSetInformation (nil) 1 (nil) 0
fixme:advapi:RegisterEventSourceW ((null),L"Bonjour Service"): stub
fixme:winsock:WS_setsockopt Unknown IPPROTO_IP optname 0x00000013
fixme:winsock:WSAIoctl SIO_GET_EXTENSION_FUNCTION_POINTER: unimplemented WSARecvMsg
fixme:winsock:WS_setsockopt Unknown IPPROTO_IPV6 optname 0x00000013
fixme:winsock:WSAIoctl SIO_GET_EXTENSION_FUNCTION_POINTER: unimplemented WSARecvMsg
fixme:winsock:WSAIoctl -> SIO_ADDRESS_LIST_CHANGE request: stub
fixme:winsock:WS_setsockopt Unknown IPPROTO_IPV6 optname 0x00000013
fixme:winsock:WSAIoctl SIO_GET_EXTENSION_FUNCTION_POINTER: unimplemented WSARecvMsg
fixme:winsock:WS_setsockopt Unknown IPPROTO_IP optname 0x00000013
fixme:iphlpapi:DeleteIpForwardEntry (pRoute 0x76e9c8): stub
fixme:iphlpapi:CreateIpForwardEntry (pRoute 0x76e958): stub
fixme:service:EnumServicesStatusW 0x126378 type=30 state=3 (nil) 0 0x76e7e8 0x76e7f4 0x76e7f0
fixme:advapi:ReportEventA (0xcafe4242,0x0004,0x0000,0x20000001,(nil),0x0001,0x00000000,0x76e5f8,(nil)): stub
fixme:advapi:ReportEventW (0xcafe4242,0x0004,0x0000,0x20000001,(nil),0x0001,0x00000000,0x1261a8,(nil)): stub
fixme:win:EnumDisplayDevicesW ((null),0,0x32ee70,0x00000000), stub!

I'm practically illiterate when it comes to Linux, but I thought I'd try.

---

### Post by Half-Left on 2010-10-15
Try a different Windows versions in the Wine configuration. You could also try using Wine 1.3, you can get a repo from winehq's website [http://www.winehq.org/download/deb](http://www.winehq.org/download/deb)

---

### Post by PineappleMuffin on 2010-11-11
What worked for me is starting a new game and then loading the save state from there. Loading from the title screen still freezes the game, though.

---

