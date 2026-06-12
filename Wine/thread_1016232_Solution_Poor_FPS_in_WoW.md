---
title: "Solution: Poor FPS in WoW"
date: 2008-12-19
forum: Wine
---

### Post by OMJD on 2008-12-19
For a good few months, I had been experiencing low fps while playing Wow (15-20FPS) 6 months ago, I used to get 60+ FPS. 

Anyway, I've found the problem to be related to a registry tweak which is supposed to improve FPS, but it actually made it **much** worse. 

If you have made the following registry tweak (quoted below) and suffer from poor frame rates, then you may want to try deleting the entry from the registry. That's all I did and now my frame rates are a lot better. (40-60+ FPS depending on where I am in-game)
[B]
BAD TWEAK:[/B]
[quote=https://help.ubuntu.com/community/WorldofWarcraft#Registry%20configuration]

**Registry configuration**

This is a simple registry edit for Wine that may increase the framerate in game. It is gathered from this thread on Ubuntuforums.org: [http://www.ubuntuforums.org/showthread.php?t=303509](http://www.ubuntuforums.org/showthread.php?t=303509)

Open a terminal window, type regedit and press enter. This will start the Wine equivalent of the windows registry editor. If you are familiar with using the registry editor under windows then this is pretty much the same.

   1.

      Find this key HKEY_CURRENT_USER\Software\Wine\
   2. Highlight the wine folder in the left hand pane by clicking left on it. The icon should change to an open folder
   3.

      Right-click on the wine folder and select [NEW] then [KEY]
   4.

      Replace the text New Key #1 with OpenGL
   5.

      Right-click in the right hand pane and select [NEW] then [String Value]
   6.

      Replace New Value #1 with DisabledExtensions (Notice it's case sensitive!)
   7. Then double click anywhere on the line, a dialog box will open.
   8.

      In the value field type GL_ARB_vertex_buffer_object 

Note: If you are unable to rename the newly created key "New Key #1" to "OpenGL" then expand the left hand pane of the regedit window using the vertical divider bar. You should now be able to change it. A known bug in Wine is causing this unwanted behavior.

Note: If you have installed the patch Echos of Doom, 3.0.2, many users have discovered that they were getting very low frame rates and that by removing this registry tweak their framerates were returned to normal.[/quote]
Culprit source: [https://help.ubuntu.com/community/WorldofWarcraft#Registry%20configuration](https://help.ubuntu.com/community/WorldofWarcraft#Registry%20configuration)

I am aware that this issue is documented, but I just thought I'd make a thread for those who are unaware of this. 


Incase you're wondering, my system specs are:

Ubuntu 8.10 32-BIT
Intel Q6600 (177.80 drivers)
Nvidia 8800GT 512MB GPU
3GB DDR2 800MHz/PC2-6400 RAM
ASUS P5B Motherboard
Tagan 430W ATX 2.0 PSU
Seagate 250GB 16MB Cache 7200.10RPM SATA2 Hard Drive

---

### Post by OrbJinzo on 2008-12-19
I found updating the the 180 series beta drivers solved most of my problems. 

[http://www.nvidia.com/object/linux_display_ia32_180.06.html](http://www.nvidia.com/object/linux_display_ia32_180.06.html)

Removing pulse audio helps alot as well.

---

### Post by binbash on 2008-12-19
> **OrbJinzo said:**
> I found updating the the 180 series beta drivers solved most of my problems. 

[http://www.nvidia.com/object/linux_display_ia32_180.06.html](http://www.nvidia.com/object/linux_display_ia32_180.06.html)

Removing pulse audio helps alot as well.

YEs removing pulse audio for  wow helps a LOT

---

### Post by Elviswind on 2008-12-21
> **binbash said:**
> YEs removing pulse audio for  wow helps a LOT

Any suggestions on how to do this in a Xubuntu installations?  Not that I have any real performance problems with WoW, but I'm running 1900x1280 with all the video settings on high (apart from Northend, where I have to set  multisampling to 1x) and it's always interesting to try some performance tweaks.

---

### Post by OMJD on 2008-12-21
> **Elviswind said:**
> Any suggestions on how to do this in a Xubuntu installations?  Not that I have any real performance problems with WoW, but I'm running 1900x1280 with all the video settings on high (apart from Northend, where I have to set  multisampling to 1x) and it's always interesting to try some performance tweaks.


I haven't removed it myself, but I always kill it after each restart. 

Open up terminal and type: 

[PHP]killall pulseaudio[/PHP]

---

### Post by Elviswind on 2009-01-04
Well, that results in "pulseaudio: no process killed"  . . . .  guess that means it wasn't running to begin with, eh?

---

