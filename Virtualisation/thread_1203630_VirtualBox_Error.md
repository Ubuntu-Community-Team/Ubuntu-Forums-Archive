---
title: "VirtualBox Error"
date: 2009-07-03
forum: Virtualisation
---

### Post by Neon612 on 2009-07-03
I just had it open last night and everything worked fine. Then I try to open it this afternoon and bam, Error.


Could not load the settings file '/home/darin/.VirtualBox/Machines/Windows XP/Windows XP.xml'.
Element '{http://www.innotek.de/VirtualBox-settings}Machine': No match found for key-sequence ['{0f75a7b2-ddf1-498e-a1cb-e063efec2912}'] of keyref '{http://www.innotek.de/VirtualBox-settings}currentSnapshot'.


Result Code: 
VBOX_E_XML_ERROR (0x80BB000A)
Component: 
VirtualBox
Interface: 
IVirtualBox {339abca2-f47a-4302-87f5-7bc324e6bbde}


I've been able to pickup a bit about what the problem is, but I can't figure out how to fix it. The problem seems to be the Snapshot {0f75a7b2...} cannot be found, and after a look through the snapshot folder I can see that the file in question is NOT there. But there is a .vdi file and a .sav file. Correct me if I'm wrong, but isn't the .sav file the Snapshot? So will it work to replace the missing hex string with the .sav file?

Thank you.

---

