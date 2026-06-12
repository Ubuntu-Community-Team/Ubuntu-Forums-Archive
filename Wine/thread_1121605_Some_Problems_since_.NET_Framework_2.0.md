---
title: "Some Problems since .NET Framework 2.0"
date: 2009-04-10
forum: Wine
---

### Post by Wild-Storm on 2009-04-10
Hi,
i just installed the .NET Framework 2.0 with winetricks but i have some huge problems with starting any application that needs this stuff (and some other too)

I always get these errors in the terminal:
err:module:attach_process_dlls "MSVCR80.dll" failed to initialize, aborting
err:module:LdrInitializeThunk Main exe initialization for L"C:\\windows\\Microsoft.NET\\Framework\\v2.0.50727\\mscorsvw.exe" failed, status c0000142

and then a window pops up with a message like: "microsoft c++ runtime library / could not load mscorsvw.exe"

any suggestions?

---

### Post by keplerspeed on 2009-04-10
Did you follow this exactly? [http://appdb.winehq.org/objectManager.php?sClass=version&iId=3754](http://appdb.winehq.org/objectManager.php?sClass=version&iId=3754)

Ensure you have a fresh c: drive, and ensure you have the latest version of wine, ie 'sudo aptitude update'

Cheers

---

### Post by Wild-Storm on 2009-04-10
oh, i didnt use a fresh install..

edit://
okay, the error does not appear any more but it doesnt work either :(

---

### Post by ajackson on 2009-04-10
Sadly while wine is now at a stage where it can install .NET it seems running .NET stuff is very hit-and-miss. I'd report a bug if I were you, the additional information might help a similar bug to solved or at least get the problem on the radar of the wine devs.

---

### Post by asdfoo on 2009-04-10
> **ajackson said:**
> Sadly while wine is now at a stage where it can install .NET it seems running .NET stuff is very hit-and-miss. I'd report a bug if I were you, the additional information might help a similar bug to solved or at least get the problem on the radar of the wine devs.

there is no point submitting more bug reports for .NET, they already exist and are being actively worked on

---

### Post by ajackson on 2009-04-11
> **asdfoo said:**
> there is no point submitting more bug reports for .NET, they already exist and are being actively worked on
Well common sense says that part of filling in a bug report starts with searching to see if the bug in question already exists (even if it is in another application). If it does and you can add something useful to that nug report you do so, if you can't you don't add anything. If by some chance there is not an existing bug report then you open a new one.

They can only fix bugs they know about, you should never just assume someone else has already reported, always check. That is my advice on the matter, yours is different. Lets agree to disagree on this.

---

### Post by asdfoo on 2009-04-11
> **ajackson said:**
> Well common sense says that part of filling in a bug report starts with searching to see if the bug in question already exists (even if it is in another application). If it does and you can add something useful to that nug report you do so, if you can't you don't add anything. If by some chance there is not an existing bug report then you open a new one.

They can only fix bugs they know about, you should never just assume someone else has already reported, always check. That is my advice on the matter, yours is different. Lets agree to disagree on this.

Yes, good point... always search for existing bug reports, and check the Wine AppDB for links to existing bugs.

---

### Post by SKLP on 2009-04-11
There's always Mono, you know ;-)

---

