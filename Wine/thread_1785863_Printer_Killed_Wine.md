---
title: "Printer Killed Wine?"
date: 2011-06-18
forum: Wine
---

### Post by That Nerd 2049 on 2011-06-18
I cant run any program though Wine.

Starting notepad though the console gives me this error message.

```
fixme:advapi:RegisterEventSourceW ((null),L"Print"): stub
fixme:ds:DsRoleGetPrimaryDomainInformation ((nil), 1, 0x32effc) stub
fixme:advapi:LsaOpenPolicy ((null),0x32ef98,0x00000001,0x32efb4) stub
fixme:advapi:LsaClose (0xcafe) stub
fixme:profile:CloseProfileUserMapping (), stub!
fixme:advapi:ObjectOpenAuditAlarmW stub (L"Spooler",0x7b4180,L"Server",L"\\\\myname-System-Pr",0x150808,0xac,0x00000001,0x00000001,(nil),0,1,0x743604f8)
fixme:advapi:ObjectCloseAuditAlarmW stub (L"Spooler",0x7b4180,0)
err:winspool:add_printer_driver Failed adding driver "wineps.drv" ("Windows NT x86"): 1805
err:winspool:CUPS_LoadPrinters printer 'Deskjet-F4400-series' not added by AddPrinterA (error 1797)
err:ole:CoGetClassObject class {a9e69610-b80d-11d0-b9b9-00a0c922e750} not registered
err:ole:CoGetClassObject class {a9e69610-b80d-11d0-b9b9-00a0c922e750} not registered
err:ole:create_server class {a9e69610-b80d-11d0-b9b9-00a0c922e750} not registered
fixme:ole:CoGetClassObject CLSCTX_REMOTE_SERVER not supported
err:ole:CoGetClassObject no class object {a9e69610-b80d-11d0-b9b9-00a0c922e750} could be created for context 0x17
```[FONT=Verdana]

So after installing my printer on Ubuntu when I try to run Wine it try's to add a printer driver but fails.

Running Ubuntu 11.04 - Natty and Wine 1.2.2-0

Any Ideas?[/FONT][FONT=Verdana]:-k[/FONT]

---

### Post by Turtlicious on 2011-06-18
Un-install wine, and then re-install it.

---

### Post by That Nerd 2049 on 2011-06-19
> **Turtlicious said:**
> Un-install wine, and then re-install it.

Will I lose every thing that was installed under Wine?

---

