---
title: "WINE Fails to load [URGENT]"
date: 2009-10-06
forum: Wine
---

### Post by Haykuroo on 2009-10-06
Wine was running perfectly the last time I booted up (yesterday). However, when attempting to run it just now - NOTHING. :confused:

Installed 5 updates, rebooted and still no response.

- Configure Wine doesn't respond.
- No .exe files will open, or links to installed programs.
- When attempting to open a program through terminal I get this:

```
wine "Sibelius.exe"
fixme:advapi:RegisterEventSourceW ((null),L"Print"): stub
fixme:winsock:convert_af_w2u unhandled Windows address family 26
fixme:winsock:convert_af_w2u unhandled Windows address family 26
fixme:winsock:convert_af_w2u unhandled Windows address family 26
fixme:ds:DsRoleGetPrimaryDomainInformation ((nil), 1, 0x32f080) stub
fixme:advapi:LsaOpenPolicy ((null),0x32f028,0x00000001,0x32f044) stub
fixme:advapi:LsaClose (0xcafe) stub
fixme:profile:CloseProfileUserMapping (), stub!
fixme:advapi:ObjectOpenAuditAlarmW stub (L"Spooler",0x1390158,L"Server",L"\\\\yates-desktop",0x140880,0xe0,0x00000001,0x00000001,(nil),0,1,0x75bfc4f8)
fixme:advapi:ObjectCloseAuditAlarmW stub (L"Spooler",0x1390158,0)
err:winspool:add_printer_driver Failed adding driver "wineps.drv" ("Windows NT x86"): 1805
fixme:winspool:AddPrinterW Can't create printer L"PDF"
err:winspool:CUPS_LoadPrinters printer 'PDF' not added by AddPrinterA (error 1801)
fixme:advapi:ObjectOpenAuditAlarmW stub (L"Spooler",0x1390158,L"Server",L"\\\\yates-desktop",0x140880,0xe0,0x00000001,0x00000001,(nil),0,1,0x75bfc4f8)
fixme:advapi:ObjectCloseAuditAlarmW stub (L"Spooler",0x1390158,0)
err:winspool:add_printer_driver Failed adding driver "wineps.drv" ("Windows NT x86"): 1805
fixme:winspool:AddPrinterW Can't create printer L"Photosmart_C4400_series"
err:winspool:CUPS_LoadPrinters printer 'Photosmart_C4400_series' not added by AddPrinterA (error 1801)
err:ole:CoGetClassObject class {a9e69610-b80d-11d0-b9b9-00a0c922e750} not registered
err:ole:CoGetClassObject class {a9e69610-b80d-11d0-b9b9-00a0c922e750} not registered
err:ole:create_server class {a9e69610-b80d-11d0-b9b9-00a0c922e750} not registered
fixme:ole:CoGetClassObject CLSCTX_REMOTE_SERVER not supported
err:ole:CoGetClassObject no class object {a9e69610-b80d-11d0-b9b9-00a0c922e750} could be created for context 0x17

```
[SIZE=2] I **urgently** need to use Sibelius tonight so any help would be greatly appreciated.[/SIZE]

---

### Post by Haykuroo on 2009-10-06
[EDIT]

Just tried opening a couple more programs and I successfully opened PhotoScore, this crashes when attempting to use any of its' functions though.

I'm assuming it's something to do with how much strain it's putting on my computer, then? This surely isn't the case though as I'm running a DualCore 3GHz, 2Gig RAM etc.

Help guys! :(

---

### Post by jpaugh64 on 2009-10-06
Did you change some of WINE's settings, or something like that? Is it possible that some other program that you installed or updated messed with it? *Something* must be different from the last time it worked. Unless someone who sees this thread has intimate knowledge of WINE specifically, you'll probably have to retrace your steps until you find out where things went wrong.

Also, a good question to answer is, which of the error messages the WINE gave you when you tried to load Sibelius are "normal" (in the sense that they always appear), and which are new; I know that sometimes WINE reports non-fatal errors and is able to continue.

Perhaps, even, some daemon that WINE relies on failed to load during the boot-up process. You might try rebooting, and paying close attention to the startup messages to see if anything fails.

---

