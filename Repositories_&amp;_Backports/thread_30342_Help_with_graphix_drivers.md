---
title: "Help with graphix drivers"
date: 2005-04-28
forum: Repositories &amp; Backports
---

### Post by necorium on 2005-04-28
Ok, i know what repositories are now.. well not really but sorta (maybe someone should explain). Will be posting in correct sections from now. this is what i want to know. I'm reading the unofficial ubuntu starter guide as suggested and i'm starting to understand some of it. the first thing i want to do with ubuntu will be to try get my graphics card working. I have a Inno3d Tornado G-Force FX 5200. The guide says ...

---------------------------------------------------
   1. Read General Notes
   2. Read How to add extra repositories?
   3.

sudo apt-get install nvidia-glx
sudo apt-get install nvidia-settings
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
sudo nvidia-glx-config enable
sudo gedit /usr/share/applications/NVIDIA-Settings.desktop

   4. Insert the following lines into the new file

[Desktop Entry]
Name=NVIDIA Settings
Comment=NVIDIA Settings
Exec=nvidia-settings
Icon=
Terminal=false
Type=Application
Categories=Application;System;

   5. Save the edited file (sample)
   6. Read How to restart GNOME without rebooting computer?
   7. Applications -> System Tools -> NVIDIA Settings

----------------------------------------------------

Now i understand that i must type the code bits into the termninal but will i type it exactly how its typed there or will i have to change something to get the right drivers for my card. Also i have no idea why i "add following lines into a new file".. can someone maybe explain this to me in simple easy peasy terms. I'm trying to read up so i don't ask too much but the more i read the more questions i have.. 

ps.. i finally found out what sudo means - yay - its been bugging me :)

thanks as always

---

### Post by TravisNewman on 2005-04-28
You don't have to change a thing in this case.

You don't need to follow anything after "sudo nvidia-glx-config enable" if you don't want, except for restarting GDM (number 6). If you don't do this part of 3: " sudo gedit /usr/share/applications/NVIDIA-Settings.desktop", or numbers 4,5, or 7, you'll just have to type "nvidia-settings" whenever you want to adjust the low level settings.

---

### Post by elasticwings on 2005-04-28
Yeah, I never edit anything when setting up the nvidia drivers.  The nvidia-glx-config enable command edits the xorg.conf file for you.

---

### Post by necorium on 2005-04-28
ok thanks

i don't understand section 4
what is inserting into a new file?
a text file?
i can't find any place that explains these parts to me

---

### Post by elasticwings on 2005-04-28
Yeah, just ignore that step.  I don't know why they put it in there.

---

