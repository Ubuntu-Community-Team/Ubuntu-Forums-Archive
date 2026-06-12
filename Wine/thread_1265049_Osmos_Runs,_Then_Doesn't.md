---
title: "Osmos Runs, Then Doesn't"
date: 2009-09-12
forum: Wine
---

### Post by Joseph Schwenker on 2009-09-12
Hey everyone!  I just downloaded the Osmos demo from the Hemisphere, and it ran PERFECTLY in WINE.  I really enjoyed it, and then quit it, and played some Portal.  A few hours later, I was going to show Osmos to my Uncle Dave, but to my surprise, I double clicked on it, and it just crashed.  Nothing appeared after launching it.  I ran it from the terminal, and the terminal returned this.
> fixme:heap:HeapSetInformation (nil) 1 (nil) 0
fixme:win:RegisterDeviceNotificationA (hwnd=0x12c750, filter=0x84ea04,flags=0x00000001),
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
fixme:service:EnumServicesStatusW 0x12c730 type=30 state=3 (nil) 0 0x87e818 0x87e824 0x87e820
fixme:advapi:ReportEventA (0xcafe4242,0x0004,0x0000,0x20000001,(nil),0x0001,0x00000000,0x87e628,(nil)): stub
fixme:advapi:ReportEventW (0xcafe4242,0x0004,0x0000,0x20000001,(nil),0x0001,0x00000000,0x12c560,(nil)): stub
fixme:actctx:parse_assembly_elem wrong version for assembly manifest: 8.0.50608.0 / 8.0.50727.762
fixme:actctx:parse_manifest_buffer failed to parse manifest L"C:\\Program Files\\OsmosDemo\\Microsoft.VC80.CRT\\Microsoft.VC80.CRT.manifest"
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT" (8.0.50608.0)
err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\Program Files\\OsmosDemo\\OsmosDemo.exe") not found
err:module:import_dll Library MSVCR80.dll (which is needed by L"C:\\Program Files\\OsmosDemo\\OsmosDemo.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\Program Files\\OsmosDemo\\OsmosDemo.exe" failed, status c0000135> 
  have reinstalled Osmos several times, and even restarted my computer, but nothing works.  Please help!

---

### Post by castlefox on 2009-09-13
There will be a linux  port of this game.

Hardware?

version  of wine?

---

### Post by Joseph Schwenker on 2009-09-13
> **castlefox said:**
> There will be a linux  port of this game.

Hardware?

version  of wine?


The game worked just a few hours before I made my post.  I played through the entire game, then closed it, then showed it to my mom, then closed it again.  When I opened it the third time after playing Portal, it would not launch.  I am using Wine 1.1.29, and am using an Intel Pentium D 2.67 Ghz Processor, nVidia GeForce 8800 GT with 512 MB of graphical memory, and 2 GB of RAM.  I know that there will be a Linux port, but I got the Windows demo working PERFECTLY with Wine twice, then it just refused to open the third time.  Can you tell anything from what the terminal said?  Thanks for the reply!

---

### Post by castlefox on 2009-09-15
Have you installed Microsoft Visual Studio (C++) 2005 Redistributable Runtime  ??????

---

### Post by Joseph Schwenker on 2009-09-15
> **castlefox said:**
> Have you installed Microsoft Visual Studio (C++) 2005 Redistributable Runtime  ??????

Oh my god!  Thanks you SOOOOOOOOOOOOOOO much!!!  :D:D:D

---

### Post by castlefox on 2009-09-15
:P   No prob, Im just happy I can be helpful 


I learned that from games official web page, on the FAQ section.

---

