---
title: "Half Life 2 - &quot;Cannot write block to device&quot;"
date: 2010-04-17
forum: Wine
---

### Post by Yargh on 2010-04-17
Hello, I have recently installed Ubuntu 10.04 beta2 (because whenever I tried Debian, CentOS, Fedora, and OpenSuse, something didn't work correctly.), and soon after installing, I installed PlayOnLinux to be able to run steam. The PlayOnLinux install, the steam install, and the Windows Fonts install completed without any errors.

Now for the problem:

I also downloaded Half Life 2 through steam, and whenever I launch it (launch arguments are "-console -novid -w 1024 -h 768 -window", the console window pops up while it is loading and says in red text "Cannot write block to device." Soon after, about 4 seconds later, it closes without showing any other error messages. I have disabled steam community in-game. The game still does the same. 

Might PlayOnLinux be causing this problem? I have successfuly gotten it to work a year ago or so with Wine on Ubuntu 8.04, without any errors. 

[If needed] System specs:
2x Opteron 252, ~2.6ghz reported.
2GB ECC Ram
Asus K8N-DRE/SATA Motherboard
Some 40GB sata drive I had laying around.
Ubuntu 10.04 beta2 x64
ATI Radeon HD 4350 512mb

Will update with Wine version when I can check again.

---

### Post by asdfoo on 2010-04-18
> **Yargh said:**
> Hello, I have recently installed Ubuntu 10.04 beta2 (because whenever I tried Debian, CentOS, Fedora, and OpenSuse, something didn't work correctly.), and soon after installing, I installed PlayOnLinux to be able to run steam. The PlayOnLinux install, the steam install, and the Windows Fonts install completed without any errors.

Now for the problem:

I also downloaded Half Life 2 through steam, and whenever I launch it (launch arguments are "-console -novid -w 1024 -h 768 -window", the console window pops up while it is loading and says in red text "Cannot write block to device." Soon after, about 4 seconds later, it closes without showing any other error messages. I have disabled steam community in-game. The game still does the same. 

Might PlayOnLinux be causing this problem? I have successfuly gotten it to work a year ago or so with Wine on Ubuntu 8.04, without any errors. 

[If needed] System specs:
2x Opteron 252, ~2.6ghz reported.
2GB ECC Ram
Asus K8N-DRE/SATA Motherboard
Some 40GB sata drive I had laying around.
Ubuntu 10.04 beta2 x64
ATI Radeon HD 4350 512mb

Will update with Wine version when I can check again.


Upgrade to Wine 1.1.43 and retry.  Post the exact terminal output.

---

