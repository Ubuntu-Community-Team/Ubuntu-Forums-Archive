---
title: "itunes"
date: 2010-08-08
forum: Wine
---

### Post by Landior on 2010-08-08
I tried installing itunes on linux through wine, it installed ok, but when i try to run it it says runtime error any ideas how to fix this, i really miss my podcasts

---

### Post by thenellt on 2010-08-08
Good luck with that. itunes doesn't look like it runs well under wine. (check [[COLOR="Blue"]this[/COLOR]]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=20885") report)
You can try this which might help your problems:
Install winetricks: (skip if you already have it)
sudo apt-get winetricks
then run:
sudo winetricks MDAC25

---

### Post by asdfoo on 2010-08-09
itunes doesn't work correctly for a number of reasons, you should ask apple to support it better.

---

### Post by ronnielsen1 on 2010-08-09
I don't have a Ipod right now. When I did, I installed rockbox on it - a lot more friendly. 
[http://www.rockbox.org/](http://www.rockbox.org/)
> **Adding music, syncing, and creating playlists**

 For this you can use [Banshee]("http://banshee-project.org/"), [Amarok]("http://amarok.kde.org/") or [gtkpod]("http://www.gtkpod.org/").  Banshee and Amarok are full music management applications that work  with the iPod (much like iTunes), whereas gtkpod is a simpler  application used only to sync with the iPod. 
All these apps can import music to your iPod, sync with your iPod, create playlists, and much more. [iTunes]("http://www.apple.com/itunes") is not currently available on Linux, although the Windows version can be used in Ubuntu using the proprietary [CrossOver Office]("http://www.codeweavers.com/products/crossover/") for a small fee. 
These applications work on every version of Ubuntu from 6.06, and can be downloaded directly from Add/Remove. [https://help.ubuntu.com/community/PortableDevices/iPod](https://help.ubuntu.com/community/PortableDevices/iPod)

---

