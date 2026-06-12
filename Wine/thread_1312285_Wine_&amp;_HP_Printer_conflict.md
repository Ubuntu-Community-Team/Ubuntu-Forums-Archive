---
title: "Wine &amp; HP Printer conflict"
date: 2009-11-03
forum: Wine
---

### Post by ygleung on 2009-11-03
Hi, 

OS: Karmic

First, I installed Wine, and run windows application well.
Next, I got hplip-cups and system-config-printer-gnome installed, until now, Wine still works fine.
Next, after I created a HP1320 laserjet printer, I found I can no longer launch Wine, these are the response msgs:

./lotus 
fixme:advapi:RegisterEventSourceW ((null),L"Print"): stub
fixme:winsock:convert_af_w2u unhandled Windows address family 26
fixme:winsock:convert_af_w2u unhandled Windows address family 26
fixme:winsock:convert_af_w2u unhandled Windows address family 26
fixme:ds:DsRoleGetPrimaryDomainInformation ((nil), 1, 0x32eef0) stub
fixme:advapi:LsaOpenPolicy ((null),0x32ee8c,0x00000001,0x32eea8) stub
fixme:advapi:LsaClose (0xcafe) stub
fixme:profile:CloseProfileUserMapping (), stub!
fixme:advapi:ObjectOpenAuditAlarmW stub (L"Spooler",0x1480148,L"Server",L"\\\\leo",0x134e88,0xd8,0x00000001,0x00000001,(nil),0,1,0x74c5c4f8)
fixme:advapi:ObjectCloseAuditAlarmW stub (L"Spooler",0x1480148,0)
err:winspool:add_printer_driver Failed adding driver "wineps.drv" ("Windows NT x86"): 1805
err:winspool:CUPS_LoadPrinters printer 'HP-LaserJet-1320' not added by AddPrinterA (error 1797)
err:ole:CoGetClassObject class {a9e69610-b80d-11d0-b9b9-00a0c922e750} not registered
err:ole:CoGetClassObject class {a9e69610-b80d-11d0-b9b9-00a0c922e750} not registered
err:ole:create_server class {a9e69610-b80d-11d0-b9b9-00a0c922e750} not registered
fixme:ole:CoGetClassObject CLSCTX_REMOTE_SERVER not supported
err:ole:CoGetClassObject no class object {a9e69610-b80d-11d0-b9b9-00a0c922e750} could be created for context 0x17


Anybody help? If more information is needed, pls let me now. Thks.






It's confirmed that is a bug, pls ref to this URL:
https://bugs.launchpad.net/ubuntu/+source/wine/+bug/476079

---

### Post by hikaricore on 2009-11-03
You didn't install the printer's software under wine or anything silly did you?
I can't imagine hooking up a printer would cause wine to stop working...

---

### Post by ygleung on 2009-11-03
> **hikaricore said:**
> You didn't install the printer's software under wine or anything silly did you?
I can't imagine hooking up a printer would cause wine to stop working...

No, I just installed wine and launch Lotus Notes which on the Windows D:, 
nothing else.

---

