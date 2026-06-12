---
title: "Wine not starting Diablo II"
date: 2011-04-23
forum: Wine
---

### Post by khelben1979 on 2011-04-23
I'm using Wine version 1.3.18 over here and when trying to start the installer to Diablo II expansion I get this output from a text terminal:
> bear@81-224-174-40-o1123:~/.wine/drive_c$ wine SETUP.EXE
fixme:advapi:RegisterEventSourceA ((null),"sprtsvc_telia"): stub
fixme:advapi:RegisterEventSourceW (L"",L"sprtsvc_telia"): stub
fixme:advapi:ReportEventA (0xcafe4242,0x0004,0x0000,0x40020001,(nil),0x0001,0x00000000,0x74d7d8,(nil)): stub
fixme:advapi:ReportEventW (0xcafe4242,0x0004,0x0000,0x40020001,(nil),0x0001,0x00000000,0x163040,(nil)): stub
fixme:advapi:DeregisterEventSource (0xcafe4242) stub
fixme:ole:CoInitializeSecurity (0x463c38,-1,(nil),(nil),4,3,(nil),0,(nil)) - stub!
fixme:toolhelp:CreateToolhelp32Snapshot Unimplemented: heap list snapshot
fixme:toolhelp:Heap32ListFirst : stub
[email]bear@81-224-174-40-o1123:~/.wine[/email]/drive_c$ err:ole:CoUninitialize Mismatched CoUninitialize

The above isn't good english to me. :-k Does anyone know how this can get solved? I should add that I can start other Wine applications such as Google Earth and Picasa Web for instance, so the installation of Wine has been successful, just a note. It has been compiled from source just today.

---

### Post by khelben1979 on 2011-04-24
I decided to downgrade Wine to 1.1.42 stable version, so now it works again. 

I will leave this thread in peace until I upgrade my Linux distribution in the future where I expect a newer version of Wine will work better together with better graphic drivers as well.

---

### Post by disabledaccount on 2011-04-25
I have D2 LOD and D2 LOD + MedianXL running under wine 1.3.6 64bit. The problem is often caused by installer script, not by the games/programs. So I suggest to install programs in prefixes and keep backup copies of "installed" programs - that way you can get performance boost  from newest versions of wine without need to fight with installers :)

---

