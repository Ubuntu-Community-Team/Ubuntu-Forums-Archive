---
title: "How to create slideshow backgrounds of your own pictures?"
date: 2012-04-15
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by georgelappies on 2012-04-15
Is there a way to create a slideshow background of your own? If so how?

---

### Post by Perryg on 2012-04-15
I use Wallch to do this.  Have for some time.

---

### Post by cariboo on 2012-04-15
You can use /usr/share/backgrounds/contest/precise.xml as a template to create one.

---

### Post by grahammechanical on 2012-04-15
I tried this some months ago and I have modified the information to take into account the recent file name changes.

_To add new image as background image_

> 1) put new image in /usr/share/backgrounds/

2) Add markup to precise-wallpapers.xml before </wallpapers> tag according to following pattern

/usr/share/gnome-background-properties/precise-wallpapers.xml

  <wallpaper>
    <name>new name of image</name>
    <filename>/usr/share/backgrounds/new_image_file_name.jpg</filename>
    <options>zoom</options>
    <pcolor>#000000</pcolor>
    <scolor>#000000</scolor>
    <shade_type>solid</shade_type>
  </wallpaper>

_To create a new slide show_

> /usr/share/backgrounds/contest/precise.xml

1) Create a new folder in /usr/share/backgrounds
2) put new images in new folder
3) modify standard precise.xml file, replacing old image files names with new image file names changing path as necessary according to pattern

 <static>
    <duration>1795.0</duration>
    <file>/usr/share/backgrounds/Twilight_Frost_by_Phil_Jackson.jpg</file>
  </static>
  <transition>
    <duration>5.0</duration>
    <from>/usr/share/backgrounds/Twilight_Frost_by_Phil_Jackson.jpg</from>
    <to>/usr/share/backgrounds/Precise_Pangolin_by_Vlad_Gerasimov.jpg</to>
  </transition>

4) put modified precise.xml file in new folder

Be careful when editing these files as Nautilus will make backup copies by putting the tilde ( ~ ) character at the end of the file name. This makes them a hidden file but they still can be read by gnome control center and so you get duplicate images in the side panel of Appearance utility.

Let us know how you get on.

Regards.

---

### Post by Baldrick_NZ on 2012-04-15
> **Perryg said:**
> I use Wallch to do this.  Have for some time.

+1 for Wallch. Great app!

---

