---
title: "Sound problems with WINE"
date: 2008-12-16
forum: Wine
---

### Post by rmausser on 2008-12-16
I have recently installed Ubuntu Studio to my computer in hopes to use Ardour and some windows audio programs like LIVE. etc

LIVE runs great, however, when I go to WINE config to enable ALSA and JACK in the audio tab, I can't select them.

They are there, but when I try to click the checkmark in the box to enable them, nothing happens. 

This is really strange as I had Ubuntu Studio installed a year ago (but reformatted recently) and I could select them. Now I can't. 

I obviously really need and want JACK in Wine to work. What gives?

Oh also Wine-Doors won't open... maybe unrelated but could be a similar issue.

Please help thanks. 

Rob

---

### Post by rmausser on 2008-12-16
Here is the error I get for wine-doors

robmausser@studiocomputer:~$ wine-doors
Started logging session
Traceback (most recent call last):
  File "/usr/bin/wine-doors", line 22, in <module>
    from queue import queue
  File "/usr/share/wine-doors/src/queue.py", line 6, in <module>
    from application import ApplicationPack
  File "/usr/share/wine-doors/src/application.py", line 7, in <module>
    from packlist import packlist
  File "/usr/share/wine-doors/src/packlist.py", line 634, in <module>
    packlist = PackList()  
  File "/usr/share/wine-doors/src/packlist.py", line 167, in __init__
    self.GetInstalledPacks()
  File "/usr/share/wine-doors/src/packlist.py", line 183, in GetInstalledPacks
    for installed in wine.installedFromReg():
  File "/usr/share/wine-doors/src/wine.py", line 379, in installedFromReg
    if self.getRegistry( approot + app, "FriendlyName" ) != "":
  File "/usr/share/wine-doors/src/wine.py", line 300, in getRegistry
    [thiskey, thisval] = line.split( "=")
ValueError: too many values to unpack

---

### Post by YokoZar on 2008-12-16
Try not using Wine Doors

---

### Post by rmausser on 2008-12-16
alright... but that is not a very good answer imo. 

I really liked how easy it was to install Flash 8 and Dreamweaver 8, programs I use everyday. 

If there is another (and relatively easy way...I can code but I mean if there is a GUI way to do things I want to support it, GUI is whats going to make linux mainstream IMO, the average user doesn't want to code)

Also I have figured something else out about the audio settings, its not an audio problem, its an issue with selection. 

I can't seem to click on unclick the audio buttons. OSS is enabled, ALSA and JACK are not. I cannot click the checkmarks beside them on or off. I can't deselect OSS or select the others. 

Does anyone know what might be causing this problem?

Thanks

Rob

---

