---
title: "How do you get the maximum resolution of Ubuntu running in Virtual PC 2007?"
date: 2010-05-10
forum: Virtualisation
---

### Post by Maximegalon on 2010-05-10
First of all let me say.

1.  Yes, Microsoft is evil, blah, blah, blah.
2.  I need to use Virtual PC 2007 for my situation.  Can't use VMWare, VirtualBox, etc. etc.
3.  I've looked on these forums and used non-MSFT search engines.
4.  I have the latest version, 10.04 , of Ubuntu.


I can't get the resolution above 800x600, using the xorg.conf file below.  Everything I've tried to modify it never works.   Yet, online people claim they have gotten it to work.


Section "Device"
        Identifier      "Configured Video Device"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
        SubSection "Display"
            Depth           32
            Modes   "1280x1024_60.00" "1024x768_60.00" "640x480_60.00"
        EndSubSection
EndSection

---

