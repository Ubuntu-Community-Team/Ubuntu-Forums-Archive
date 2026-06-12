---
title: "Planswift install"
date: 2011-02-03
forum: Wine
---

### Post by pepsifx357 on 2011-02-03
I have a program called planswift 8.  It is an estimating software for construction.

It installed without a flaw but when I try to open the program I get this error.

```
----------------------------------------------------------------------------
Exception log with detailed tech info. Generated on 2/3/2011 10:21:32 PM.
You may send it to the application vendor, helping him to understand what had happened.
 Application title: PlanSwift
 Application file: C:\Program Files\PlanSwift9\PlanSwift.exe
----------------------------------------------------------------------------
Customer Number: 
PlanSwift Professional Viewer 9.0
C:\Program Files\PlanSwift9\PlanSwift.exe
9.0.13.10
Mouse Status: TmaNone   
----------------------------------------------------------------------------
Exception class: EAccessViolation
Exception message: Access violation at address 011BB9AF in module 'PlanSwift.exe'. Read of address 00000000.
Exception address: 011BB9AF
----------------------------------------------------------------------------
Exception stack
Stack list, generated 2/3/2011 10:21:32 PM
(00DBA9AF){PlanSwift.exe} [011BB9AF]
----------------------------------------------------------------------------
Call stack for main thread
Stack list, generated 2/3/2011 10:21:32 PM
[7BC7A686]{ntdll.dll   } ZwGetContextThread
----------------------------------------------------------------------------

```

It shows the splash screen and cursor.  It gets all the way to the end of loading and does this.  Not sure what this means.  Any ideas?

Here is the website: [http://www.planswift.com/](http://www.planswift.com/)

---

### Post by cogadh on 2011-02-04
Run the app from the terminal and get Wine's error output, it will likely be much more informative.

---

### Post by pepsifx357 on 2011-02-04
Here is the output:

```
ben@WS4:~/.wine/drive_c/Program Files/PlanSwift9$ wine PlanSwift.exe 
fixme:shell:FileIconInit (true)
fixme:keyboard:X11DRV_LoadKeyboardLayout L"00000409", 0080: stub!
fixme:ole:CoResumeClassObjects stub
fixme:reg:RegSetKeySecurity :(0xc0,4,0x32fdc4): stub
fixme:reg:RegSetKeySecurity :(0xc0,4,0x32fdc4): stub
fixme:reg:RegSetKeySecurity :(0xc0,4,0x32fdc4): stub
fixme:reg:RegSetKeySecurity :(0xc0,4,0x32fdc4): stub
fixme:reg:RegSetKeySecurity :(0xc0,4,0x32fdc4): stub
fixme:reg:RegSetKeySecurity :(0xc0,4,0x32fdc4): stub
fixme:advapi:RegisterTraceGuidsW (0x90d13b8, 0x9292830, {b2a40f1f-a05a-4dfd-886a-4c4f18c4334c}, 1, 0x32ecf0, (null), (null), 0x9292830,)
fixme:advapi:RegisterTraceGuidsW (0x90d13b8, 0x9292860, {ffdb9886-80f3-4540-aa8b-b85192217ddf}, 1, 0x32ecf0, (null), (null), 0x9292860,)
fixme:advapi:RegisterTraceGuidsW (0x90d13b8, 0x9292890, {5c8bb950-959e-4309-8908-67961a1205d5}, 1, 0x32ecf0, (null), (null), 0x9292890,)
fixme:advapi:RegisterTraceGuidsW (0x90d1481, 0x92912c8, {3e1fd72a-c323-4574-9917-5ce9c936f78c}, 1, 0x32ecd0, (null), (null), 0x92912d0,)
fixme:advapi:RegisterTraceGuidsW (0x90d1481, 0x92912e8, {afff9c82-5be3-4205-9b3e-49e014c09a63}, 1, 0x32ecd0, (null), (null), 0x92912f0,)
err:ole:CoGetClassObject class {00000514-0000-0010-8000-00aa006d2ea4} not registered
err:ole:create_server class {00000514-0000-0010-8000-00aa006d2ea4} not registered
err:ole:CoGetClassObject no class object {00000514-0000-0010-8000-00aa006d2ea4} could be created for context 0x5
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_END_BROWSER_SESSION: STUB
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_RESET_URLCACHE_SESSION: STUB

```

---

### Post by cogadh on 2011-02-04
Looks like you need a couple of DLLs, specifically the OLE ones. Use [winetricks]("http://wiki.winehq.org/winetricks") and install the dcom98 and ole2 packages, then run the app from the terminal again.

---

### Post by pepsifx357 on 2011-02-05
> **cogadh said:**
> Looks like you need a couple of DLLs, specifically the OLE ones. Use [winetricks]("http://wiki.winehq.org/winetricks") and install the dcom98 and ole2 packages, then run the app from the terminal again.

I can't seem to find the dcom98 package.  Is there another name for it?

---

