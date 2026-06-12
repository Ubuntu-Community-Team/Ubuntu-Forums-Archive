---
title: "Windows 7 Ubuntu One cannot start"
date: 2013-12-26
forum: Ubuntu One (CLOSED)
---

### Post by Losergamer04 on 2013-12-26
I am having issues opening Ubuntu One on Windows 7 after installing it.  I get an error when I try to start Ubuntu one, something about its side-by side configuration is incorrect.  I tried to find this else ware but my Google-fu is failing me.  Below is a copy of my event log that shows up.
```
Activation context generation failed for "C:\Program Files (x86)\ubuntuone\dist\ubuntuone-control-panel-qt.exe".Error in manifest or policy file "C:\Program Files (x86)\ubuntuone\dist\Microsoft.VC90.CRT\Microsoft.VC90.CRT.MANIFEST" on line 4. Component identity found in manifest does not match the identity of the component requested. Reference is Microsoft.VC90.CRT,processorArchitecture="x86",publicKeyToken="1fc8b3b9a1e18e3b",type="win32",version="9.0.21022.8". Definition is Microsoft.VC90.CRT,processorArchitecture="x86",publicKeyToken="1fc8b3b9a1e18e3b",type="win32",version="9.0.30729.6161". Please use sxstrace.exe for detailed diagnosis.
```

---

### Post by Losergamer04 on 2013-12-27
I figured out the problem.  The manifest file had the wrong version.  9.0.21022.8 is what it was supposed to be and it was [LEFT][COLOR=#000000][FONT=Ubuntu Mono]9.0.30729.6161.[/FONT][/COLOR][/LEFT]

---

### Post by JohnSimonDoe on 2014-01-31
So where did you get the right manifest version from?

---

