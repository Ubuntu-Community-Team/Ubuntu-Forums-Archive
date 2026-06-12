---
title: "Mta sa"
date: 2009-09-04
forum: Wine
---

### Post by marshmallow1304 on 2009-09-04
Trying to install Multi Theft Auto San Andreas on Jaunty 64-bit.  According to [this]("http://mtavc.com/71.html"), it's possible to get it to work.

```
benn@system76-pc:~/Desktop$ wine --version
wine-1.1.29
```

The MTA installer downloads vcredist_x86.exe. but then it gives me
> Unable to install Visual Studio 2008 SP1 redistributable
and aborts.

Here's the terminal output:
```
benn@system76-pc:~/Desktop$ wine MTASA-1.0.exe 
fixme:advapi:CheckTokenMembership ((nil) 0x131468 0x32faf4) stub!
fixme:shell:SHAutoComplete SHAutoComplete stub
fixme:shell:SHAutoComplete SHAutoComplete stub
fixme:clusapi:GetNodeClusterState ((null),0x33ec4c,0) stub!
fixme:advapi:DecryptFileA "c:\\e6791cc3a8d21df10cb42813e29a2d\\" 00000000
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
fixme:advapi:LsaOpenPolicy ((null),0x33f358,0x00000001,0x33f380) stub
fixme:advapi:LsaClose (0xcafe) stub
err:seh:raise_exception Unhandled exception code c0000005 flags 0 addr 0x455383
```


I also tried getting vcrun2008sp1 through winetricks, which gives me
> Note: command 'wine

Terminal output:
```
benn@system76-pc:~/Desktop$ sh winetricks

(zenity:13451): Gtk-WARNING **: Error parsing gtk-icon-sizes string:
	'panel-menu=24,24
panel=20,20
gtk-button=18,18
gtk-large-toolbar=24,24'
drive_c already named harddiskvolume0
Executing wine /home/benn/.winetrickscache/vcrun2008sp1/vcredist_x86.exe
fixme:clusapi:GetNodeClusterState ((null),0x32ec4c,0) stub!
fixme:advapi:DecryptFileA "c:\\0efa11ef6d66bb912be42538b52e9f\\" 00000000
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
fixme:advapi:LsaOpenPolicy ((null),0x33f358,0x00000001,0x33f380) stub
fixme:advapi:LsaClose (0xcafe) stub
err:seh:raise_exception Unhandled exception code c0000005 flags 0 addr 0x455383
Note: command 'wine /home/benn/.winetrickscache/vcrun2008sp1/vcredist_x86.exe' returned status 1.  Aborting.

(zenity:13494): Gtk-WARNING **: Error parsing gtk-icon-sizes string:
	'panel-menu=24,24
panel=20,20
gtk-button=18,18
gtk-large-toolbar=24,24'
```

---

