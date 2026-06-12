---
title: "[SOLVED] Vbox inaccessible - hostpath problem"
date: 2008-08-18
forum: Virtualisation
---

### Post by kneewax on 2008-08-18
Hy Folks,

I started my Hardy machine today and went to open XP in Vbox to be faced my Vmachine being listed as inaccessible and with this error in the details section of the launcher.


```
 
Could not load the settings file '/home/ali/.VirtualBox/Machines/XP Pro/XP Pro.xml'.
Element '{http://www.innotek.de/VirtualBox-settings}SharedFolder', attribute 'hosstPath': The attribute 'hosstPath' is not allowed.
Element '{http://www.innotek.de/VirtualBox-settings}SharedFolder': The attribute 'hostPath' is required but missing.


Result Code: 
0x80004005
Component: 
VirtualBox
Interface: 
IVirtualBox {2d3b9ea7-25f5-4f07-a8e1-7dd7e0dcf667}

```


Can anyone help?  I've tried removind vbox and re-installing as suggested in one thread, but that didn't help.

Cheers

---

### Post by kneewax on 2008-08-18
Solved:

I did a bit more detective work and opened up the xml file for this machine.  A quick search found the error was 'hosstpath' specified rather than 'hostpath' in one of the path settings.

I have no idea how or why this changed since I no one has played with the XML files and the Vbox was woreking just fine last night!

Ho-hum.  Sorted now.  Phew!

---

