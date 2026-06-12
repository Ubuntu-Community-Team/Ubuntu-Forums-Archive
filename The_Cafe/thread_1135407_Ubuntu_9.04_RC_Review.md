---
title: "Ubuntu 9.04 RC Review"
date: 2009-04-24
forum: The Cafe
---

### Post by NightwishFan on 2009-04-24
Ubuntu 9.04 RC Review

Anyone who read my review of Kubuntu 9.04 will know this review is mainly about the changes (good and bad) and the user experience. It is intended for those who have not tried Ubuntu 9.04 and may want to. Enjoy!


I used the AMD64 Live CD to install the system. Booting was very fast, even from the live CD.

The Ubuntu Usplash has a new theme. It is a thin strip, with light to dark gradient Ubuntu colors. It feels more animated, but it is also a good deal smaller than the previous ones. Overall, a good change, I suppose it works better with more screens.

Ubuntu also has a new theme for it's GDM. Which is a dark theme with a 3D Ubuntu logo. Very slick.

When the system fully logged on to the desktop, I was greeted with the human colors of previous releases. Very warm and visible theme, and I happen to like it, despite it's sometimes poor reception.

The two new wallpapers for this release are very different from each other. The default one is clean and professional, a very great choice. The other is more flashy, and similar to the KDE "Air" wallpaper, only using human colors.

Included in the example content is a nice picture of the Canadian sky, which I adopted for my Compiz-Fusion Skydome.

Default themes aside, I checked the Appearance dialog for new additions, and found that some of the old themes are not included by default, such as Glossy. The brown DarkRoom theme is available, as well as Dust, Dust Sand, and NewWave. All of which are dark themes.

A few applications are missing from this release. Tracker is not included by default, which I miss (it indexes my immense folder of HTML documentation in about 4 minutes), but the GNOME search tool is sufficient. Nautilus CD Burner is replaced by Brasero, which has had a major overhaul. It is both functional and very easy on the eyes, and can preview sound files before burning an Audio CD.

A new "Cruft Removing" Computer Janitor application is available. I am fairly sure it would be useful to remove problematic packages after an upgrade, and to reduce the leftovers.

OpenOffice.org 3 makes an appearence, which was missed last release. No problems here. It may be useful to know that the Nvidia drivers seem to work well with OpenOffice now. Previously I had problems with the window border winking out or distorting. It was worse on KDE plasma, which entirely winked out. :D

One thing to notice is the new notification system. I am sorry to say I do not really know it's full capabilities, and I would be glad to have someone explain that to me as well. From what I know, it standardizes notification output among various GNOME apps. It also keeps track of all communication applications (Pidgin, Evolution) that are open.

When enabling Nvidia drivers, the build of 180 failed, so I used the 173 one. It works flawlessly and performance, especially in Compiz, is greatly improved. The window management feels more fluid and animations are less jerky (my card is horrible so compiz used to lag a bit).

The system log program is now far more comprehensive by default. You have more logging than you can stomach, which is good, since I like to know what is going on.

The Vinagre remote desktop tool seems to have improved a great deal. The configuration dialog is more comprehensive, and the connection dialog has more features, and an improved interface.

The Ubuntu Ubiquity installer has had a few parts that recieved a visible overhaul, such as the timezone selector. None more than the partitioner, which is displayed in a more human readable way. Informing you that you can install alongside other OSs and which ones that will be overwritten. Fantastic. Partitioning is the only difficult part of the installation.

As for booting, I chose ext4 as my root partition, with a separate SWAP and ext3 /boot partition. This allows me to take advantage of ext4 and not have to worry about any boot problems. From GRUB to typing your user name on GDM takes about 10 seconds on my machine. 2 seconds of that is GDM loading. Try it, you won't believe it.

The overall feel of the system can be described as smooth and speedy. Loggin in to a usable desktop is much faster. Programs open quicker, and so far nothing seems to have crashed. An overall improvment over 8.10. As my opinion goes, this is the best release yet.

I know I said I would mention the bad stuff. Frankly, there is honestly not much to tell. Note that these bugs might just be on my hardware, do not think they work for everyone. As of the RC the only bugs I have experienced are:

Nvidia 180 fails to compile module
Jockey-GTK/KDE sometimes does not detect drivers
Computer Janitor complains dash is not installed and exits, the package "dash" is installed, though.

That is all I can remember! Hope my review was useful for those of you who are doubtful about upgrading.

---

### Post by bookmunkie on 2009-04-24
Vinagre has an improved interface?  Hardly.  They gimped the program to the point where I can hardly use it.  All of the keyboard shortcuts have been removed, and you can't even get to the menu with Alt+Letter keys anymore.  This probably seems like a minor irritation to most people, but if I can't get to the Bookmarks menu with Alt+B anymroe I'm going to find a new VNC program

---

### Post by NightwishFan on 2009-04-25
I suppose so. Though I found that all the features you might use are simply there in one window, when they were not before. As for keyboard shortcuts, I do not think they would change too much, especially on a GNOME program, they hate doing that stuff.

---

