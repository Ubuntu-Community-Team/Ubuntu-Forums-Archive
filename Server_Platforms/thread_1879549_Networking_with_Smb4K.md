---
title: "Networking with Smb4K"
date: 2011-11-11
forum: Server Platforms
---

### Post by Orcris on 2011-11-11
I have a Windows workgroup set up on my network named WORKGROUP, and I installed Smb4K to manage it. Smb4K detected both of my Windows computers right away, but when I try to scan them, it doesn't work. The message at the bottom stays on 'Querying host for shares'. Also, in Dolphin, I shared my home folder, but when I click 'Map Network Drive' in Windows, it detects my computer but says that it doesn't have anything shared. How do I connect to my Linux computer in Windows, and how do I connect to my Windows 7 and XP computers in Kubuntu?

---

### Post by cdoebbler on 2011-11-16
I am trying to set up a network for sharing files with two computers each running Ubuntu 11.10. One is an i8 HP 7200 desktop and the other a HP 110c Mini netbook.

I have installed smb4k and network neighbourhood on both, but neither one recognizes the other.

Here is messages I get when I run 'sudo smb4k' on desktop:

[HTML]

:~$ sudo smb4k
Error: "/var/tmp/kdecache-fb" is owned by uid 1000 instead of uid 0.
"sni-qt/31334" WARN  23:43:34.237 void StatusNotifierItemFactory::connectToSnw() Invalid interface to SNW_SERVICE 
fb@FB-HP:~$ Error: "/tmp/kde-fb" is owned by uid 1000 instead of uid 0.
Error: "/tmp/ksocket-fb" is owned by uid 1000 instead of uid 0.
Error: "/tmp/kde-fb" is owned by uid 1000 instead of uid 0.
kdeinit4: Shutting down running client.
Connecting to deprecated signal QDBusConnectionInterface::serviceOwnerChanged(QString,QString,QString)
Error: "/tmp/ksocket-fb" is owned by uid 1000 instead of uid 0.
Error: "/tmp/kde-fb" is owned by uid 1000 instead of uid 0.
Error: "/var/tmp/kdecache-fb" is owned by uid 1000 instead of uid 0.
kbuildsycoca4 running...
Error: "/var/tmp/kdecache-fb" is owned by uid 1000 instead of uid 0.
Error: "/var/tmp/kdecache-fb" is owned by uid 1000 instead of uid 0.
Error: "/var/tmp/kdecache-fb" is owned by uid 1000 instead of uid 0.
QDBusConnection: name 'org.kde.kwalletd' had owner '' but we thought it was ':1.6'
Error: "/var/tmp/kdecache-fb" is owned by uid 1000 instead of uid 0.
X Error: BadWindow (invalid Window parameter) 3
  Major opcode: 20 (X_GetProperty)
  Resource id:  0x6600143
X Error: BadWindow (invalid Window parameter) 3
  Major opcode: 20 (X_GetProperty)
  Resource id:  0x6600143
X Error: BadWindow (invalid Window parameter) 3
  Major opcode: 18 (X_ChangeProperty)
  Resource id:  0x6600143

[/HTML]

---

