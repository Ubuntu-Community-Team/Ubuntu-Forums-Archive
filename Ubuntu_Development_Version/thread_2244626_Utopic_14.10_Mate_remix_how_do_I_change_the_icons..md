---
title: "Utopic 14.10 Mate remix how do I change the icons."
date: 2014-09-17
forum: Ubuntu Development Version
---

### Post by Cavsfan on 2014-09-17
I installed Ubuntu Utopic Mate Remix and for the life of me cannot seem to change the icons.

I have tried several different methods which did work on regular Ubuntu Utopic and every other earlier version of Ubuntu as well as Mint I have.

I'm stuck with this:

[[IMG]http://en.zimagez.com/miniature/screenshot-3154.png[/IMG]]("http://en.zimagez.com/zimage/screenshot-3154.php")

---

### Post by Cavsfan on 2014-09-18
OK now I am thoroughly convinced that there is no way to change the icon theme in Utopic Mate. 

I had installed the Buff3.10 icon theme in ~/.icons and with every other install that did the trick but not on Mate.

So I copied the folder ~/.icons/buuf3.10 to /usr/share/icons/buuf3.10. Rebooted and still nothing.

Mate is apparently a different animal compared to Ubuntu or Mint.

[ATTACH=CONFIG]256531[/ATTACH]

---

### Post by buzzingrobot on 2014-09-18
Make sure the permissions on the newly installed files match those of the other icons, the ones the system can see.

---

### Post by Cavsfan on 2014-09-18
> **buzzingrobot said:**
> Make sure the permissions on the newly installed files match those of the other icons, the ones the system can see.

I think you might be heading in the right direction. A lot of the icons are symlinked to another icons in the same folder. I'll have to look at this more tomorrow.
Thanks for the post!

---

### Post by buzzingrobot on 2014-09-18
I've had a number of occasions where manually installed icons didn't have the right permissions.  A "sudo chmod -R +rx" on the directory took care of that. 

That won't fix sym links, though. If, say, you copied files from another distro that had them symlinked (maybe links in ~/.icon to files in /usr/share/icons?), then you'd have a batch of broken symlinks and no icons.

---

### Post by Cavsfan on 2014-09-20
> **buzzingrobot said:**
> I've had a number of occasions where manually installed icons didn't have the right permissions.  A "sudo chmod -R +rx" on the directory took care of that. 

That won't fix sym links, though. If, say, you copied files from another distro that had them symlinked (maybe links in ~/.icon to files in /usr/share/icons?), then you'd have a batch of broken symlinks and no icons.

The icons pre-installed are symlinked and not the ones I'm trying to use. I changed all of the permissions to match the ones that do work. But the Buuf icons will not show up.

The only way I can change icons along with everything else is via System > Preferences >Appearances and then select a different theme and the icons follow.
Changing them in dconf-editor doesn't cut it. And I cannot seem to find a Buuf3.10 theme file to add there.

It took a lot of work as there were several directories so here is what I had to do (The Fog icons from the Fog theme worked):

```
cavsfan@cavsfan-MS-7529:/usr/share/icons/buuf3.10$ ls
128x128  36x36       brasero  dropbox             epiphany       file-roller   gdu                   gnome-games          gnome-power-manager-deprecated  midori         rhythmbox             totem       unity               yelp
16x16    48x48       ccsm     empathy             evince         f-spot        gnome                 gnome-media          gnome-settings-daemon           miscellaneous  rhythmbox-deprecated  tracker     vinagre
22x22    apt-daemon  cheese   empathy-deprecated  evolution      gajim         gnome-bluetooth       gnome-packagekit     gtranslator                     nm             synaptic              ubuntu      xfce
24x24    banshee     conduit  eog                 evolution-rss  gconf-editor  gnome-control-center  gnome-power-manager  index.theme                     notify-osd     tomboy                ubuntu-one  xfce-power-manager
cavsfan@cavsfan-MS-7529:/usr/share/icons/buuf3.10$ cd 128x128
cavsfan@cavsfan-MS-7529:/usr/share/icons/buuf3.10/128x128$ sudo chmod --reference=/usr/share/icons/Fog/256x256/places/folder-download.png *
cavsfan@cavsfan-MS-7529:/usr/share/icons/buuf3.10/128x128$ cd ..
cavsfan@cavsfan-MS-7529:/usr/share/icons/buuf3.10$ cd 36x36
cavsfan@cavsfan-MS-7529:/usr/share/icons/buuf3.10/36x36$ sudo chmod --reference=/usr/share/icons/Fog/256x256/places/folder-download.png *
cavsfan@cavsfan-MS-7529:/usr/share/icons/buuf3.10/36x36$ cd ..
cavsfan@cavsfan-MS-7529:/usr/share/icons/buuf3.10$ cd brasero
cavsfan@cavsfan-MS-7529:/usr/share/icons/buuf3.10/brasero$ sudo chmod --reference=/usr/share/icons/Fog/256x256/places/folder-download.png *
cavsfan@cavsfan-MS-7529:/usr/share/icons/buuf3.10/brasero$ cd ..
cavsfan@cavsfan-MS-7529:/usr/share/icons/buuf3.10$ cd dropbox
cavsfan@cavsfan-MS-7529:/usr/share/icons/buuf3.10/dropbox$ sudo chmod --reference=/usr/share/icons/Fog/256x256/places/folder-download.png *
cavsfan@cavsfan-MS-7529:/usr/share/icons/buuf3.10/dropbox$ cd ..
cavsfan@cavsfan-MS-7529:/usr/share/icons/buuf3.10$ cd epiphany
cavsfan@cavsfan-MS-7529:/usr/share/icons/buuf3.10/epiphany$ sudo chmod --reference=/usr/share/icons/Fog/256x256/places/folder-download.png *
cavsfan@cavsfan-MS-7529:/usr/share/icons/buuf3.10/epiphany$ cd ..
cavsfan@cavsfan-MS-7529:/usr/share/icons/buuf3.10$ cd file-roller
cavsfan@cavsfan-MS-7529:/usr/share/icons/buuf3.10/file-roller$ sudo chmod --reference=/usr/share/icons/Fog/256x256/places/folder-download.png *
cavsfan@cavsfan-MS-7529:/usr/share/icons/buuf3.10/file-roller$ cd ..
cavsfan@cavsfan-MS-7529:/usr/share/icons/buuf3.10$ cd gdu
cavsfan@cavsfan-MS-7529:/usr/share/icons/buuf3.10/gdu$ sudo chmod --reference=/usr/share/icons/Fog/256x256/places/folder-download.png *
cavsfan@cavsfan-MS-7529:/usr/share/icons/buuf3.10/gdu$ cd ..
cavsfan@cavsfan-MS-7529:/usr/share/icons/buuf3.10$ cd gnome-games
cavsfan@cavsfan-MS-7529:/usr/share/icons/buuf3.10/gnome-games$ sudo chmod --reference=/usr/share/icons/Fog/256x256/places/folder-download.png *
cavsfan@cavsfan-MS-7529:/usr/share/icons/buuf3.10/gnome-games$ cd ..
cavsfan@cavsfan-MS-7529:/usr/share/icons/buuf3.10$ cd gnome-power-manager-deprecated
cavsfan@cavsfan-MS-7529:/usr/share/icons/buuf3.10/gnome-power-manager-deprecated$ sudo chmod --reference=/usr/share/icons/Fog/256x256/places/folder-download.png *
cavsfan@cavsfan-MS-7529:/usr/share/icons/buuf3.10/gnome-power-manager-deprecated$ cd ..
cavsfan@cavsfan-MS-7529:/usr/share/icons/buuf3.10$ cd midori
cavsfan@cavsfan-MS-7529:/usr/share/icons/buuf3.10/midori$ sudo chmod --reference=/usr/share/icons/Fog/256x256/places/folder-download.png *
cavsfan@cavsfan-MS-7529:/usr/share/icons/buuf3.10/midori$ cd ..
cavsfan@cavsfan-MS-7529:/usr/share/icons/buuf3.10$ cd rhythmbox
cavsfan@cavsfan-MS-7529:/usr/share/icons/buuf3.10/rhythmbox$ sudo chmod --reference=/usr/share/icons/Fog/256x256/places/folder-download.png *
cavsfan@cavsfan-MS-7529:/usr/share/icons/buuf3.10/rhythmbox$ cd ..
cavsfan@cavsfan-MS-7529:/usr/share/icons/buuf3.10$ cd totem
cavsfan@cavsfan-MS-7529:/usr/share/icons/buuf3.10/totem$ sudo chmod --reference=/usr/share/icons/Fog/256x256/places/folder-download.png *
cavsfan@cavsfan-MS-7529:/usr/share/icons/buuf3.10/totem$ cd ..
cavsfan@cavsfan-MS-7529:/usr/share/icons/buuf3.10$ cd unity
cavsfan@cavsfan-MS-7529:/usr/share/icons/buuf3.10/unity$ sudo chmod --reference=/usr/share/icons/Fog/256x256/places/folder-download.png *
cavsfan@cavsfan-MS-7529:/usr/share/icons/buuf3.10/unity$ cd ..
cavsfan@cavsfan-MS-7529:/usr/share/icons/buuf3.10$ cd yelp
cavsfan@cavsfan-MS-7529:/usr/share/icons/buuf3.10/yelp$ sudo chmod --reference=/usr/share/icons/Fog/256x256/places/folder-download.png *
cavsfan@cavsfan-MS-7529:/usr/share/icons/buuf3.10/yelp$ cd ..
cavsfan@cavsfan-MS-7529:/usr/share/icons/buuf3.10$ cd 16x16
cavsfan@cavsfan-MS-7529:/usr/share/icons/buuf3.10/16x16$ sudo chmod --reference=/usr/share/icons/Fog/256x256/places/folder-download.png *
cavsfan@cavsfan-MS-7529:/usr/share/icons/buuf3.10/16x16$ cd ..
cavsfan@cavsfan-MS-7529:/usr/share/icons/buuf3.10$ cd 48x48
cavsfan@cavsfan-MS-7529:/usr/share/icons/buuf3.10/48x48$ sudo chmod --reference=/usr/share/icons/Fog/256x256/places/folder-download.png *
cavsfan@cavsfan-MS-7529:/usr/share/icons/buuf3.10/48x48$ cd ..
cavsfan@cavsfan-MS-7529:/usr/share/icons/buuf3.10$ cd ccsm
cavsfan@cavsfan-MS-7529:/usr/share/icons/buuf3.10/ccsm$ sudo chmod --reference=/usr/share/icons/Fog/256x256/places/folder-download.png *
cavsfan@cavsfan-MS-7529:/usr/share/icons/buuf3.10/ccsm$ cd ..
cavsfan@cavsfan-MS-7529:/usr/share/icons/buuf3.10$ cd empathy
cavsfan@cavsfan-MS-7529:/usr/share/icons/buuf3.10/empathy$ sudo chmod --reference=/usr/share/icons/Fog/256x256/places/folder-download.png *
cavsfan@cavsfan-MS-7529:/usr/share/icons/buuf3.10/empathy$ cd ..
cavsfan@cavsfan-MS-7529:/usr/share/icons/buuf3.10$ cd evince
cavsfan@cavsfan-MS-7529:/usr/share/icons/buuf3.10/evince$ sudo chmod --reference=/usr/share/icons/Fog/256x256/places/folder-download.png *
cavsfan@cavsfan-MS-7529:/usr/share/icons/buuf3.10/evince$ cd ..
cavsfan@cavsfan-MS-7529:/usr/share/icons/buuf3.10$ cd f-spot
cavsfan@cavsfan-MS-7529:/usr/share/icons/buuf3.10/f-spot$ sudo chmod --reference=/usr/share/icons/Fog/256x256/places/folder-download.png *
cavsfan@cavsfan-MS-7529:/usr/share/icons/buuf3.10/f-spot$ cd ..
cavsfan@cavsfan-MS-7529:/usr/share/icons/buuf3.10$ cd gnome
cavsfan@cavsfan-MS-7529:/usr/share/icons/buuf3.10/gnome$ sudo chmod --reference=/usr/share/icons/Fog/256x256/places/folder-download.png *
cavsfan@cavsfan-MS-7529:/usr/share/icons/buuf3.10/gnome$ cd ..
cavsfan@cavsfan-MS-7529:/usr/share/icons/buuf3.10$ gnome-media
gnome-media: command not found
cavsfan@cavsfan-MS-7529:/usr/share/icons/buuf3.10$ cd gnome-media
cavsfan@cavsfan-MS-7529:/usr/share/icons/buuf3.10/gnome-media$ sudo chmod --reference=/usr/share/icons/Fog/256x256/places/folder-download.png *
cavsfan@cavsfan-MS-7529:/usr/share/icons/buuf3.10/gnome-media$ cd ..
cavsfan@cavsfan-MS-7529:/usr/share/icons/buuf3.10$ cd gnome-settings-daemon
cavsfan@cavsfan-MS-7529:/usr/share/icons/buuf3.10/gnome-settings-daemon$ sudo chmod --reference=/usr/share/icons/Fog/256x256/places/folder-download.png *
cavsfan@cavsfan-MS-7529:/usr/share/icons/buuf3.10/gnome-settings-daemon$ cd ..
cavsfan@cavsfan-MS-7529:/usr/share/icons/buuf3.10$ cd miscellaneous
cavsfan@cavsfan-MS-7529:/usr/share/icons/buuf3.10/miscellaneous$ sudo chmod --reference=/usr/share/icons/Fog/256x256/places/folder-download.png *
cavsfan@cavsfan-MS-7529:/usr/share/icons/buuf3.10/miscellaneous$ cd ..
cavsfan@cavsfan-MS-7529:/usr/share/icons/buuf3.10$ cd rhythmbox-deprecated
cavsfan@cavsfan-MS-7529:/usr/share/icons/buuf3.10/rhythmbox-deprecated$ sudo chmod --reference=/usr/share/icons/Fog/256x256/places/folder-download.png *
cavsfan@cavsfan-MS-7529:/usr/share/icons/buuf3.10/rhythmbox-deprecated$ cd ..
cavsfan@cavsfan-MS-7529:/usr/share/icons/buuf3.10$ cd tracker
cavsfan@cavsfan-MS-7529:/usr/share/icons/buuf3.10/tracker$ sudo chmod --reference=/usr/share/icons/Fog/256x256/places/folder-download.png *
chmod: cannot access ‘*’: No such file or directory
cavsfan@cavsfan-MS-7529:/usr/share/icons/buuf3.10/tracker$ cd ..
cavsfan@cavsfan-MS-7529:/usr/share/icons/buuf3.10$ cd tracker
cavsfan@cavsfan-MS-7529:/usr/share/icons/buuf3.10/tracker$ ls
cavsfan@cavsfan-MS-7529:/usr/share/icons/buuf3.10/tracker$ cd ..
cavsfan@cavsfan-MS-7529:/usr/share/icons/buuf3.10$ cd vinagre
cavsfan@cavsfan-MS-7529:/usr/share/icons/buuf3.10/vinagre$ sudo chmod --reference=/usr/share/icons/Fog/256x256/places/folder-download.png *
cavsfan@cavsfan-MS-7529:/usr/share/icons/buuf3.10/vinagre$ cd ..
cavsfan@cavsfan-MS-7529:/usr/share/icons/buuf3.10$ cd 22x22
cavsfan@cavsfan-MS-7529:/usr/share/icons/buuf3.10/22x22$ sudo chmod --reference=/usr/share/icons/Fog/256x256/places/folder-download.png *
cavsfan@cavsfan-MS-7529:/usr/share/icons/buuf3.10/22x22$ cd ..
cavsfan@cavsfan-MS-7529:/usr/share/icons/buuf3.10$ cd apt-daemon
cavsfan@cavsfan-MS-7529:/usr/share/icons/buuf3.10/apt-daemon$ sudo chmod --reference=/usr/share/icons/Fog/256x256/places/folder-download.png *
cavsfan@cavsfan-MS-7529:/usr/share/icons/buuf3.10/apt-daemon$ cd ..
cavsfan@cavsfan-MS-7529:/usr/share/icons/buuf3.10$ cd cheese
cavsfan@cavsfan-MS-7529:/usr/share/icons/buuf3.10/cheese$ sudo chmod --reference=/usr/share/icons/Fog/256x256/places/folder-download.png *
cavsfan@cavsfan-MS-7529:/usr/share/icons/buuf3.10/cheese$ cd ..
cavsfan@cavsfan-MS-7529:/usr/share/icons/buuf3.10$ cd empathy-deprecated
cavsfan@cavsfan-MS-7529:/usr/share/icons/buuf3.10/empathy-deprecated$ sudo chmod --reference=/usr/share/icons/Fog/256x256/places/folder-download.png *
cavsfan@cavsfan-MS-7529:/usr/share/icons/buuf3.10/empathy-deprecated$ cd ..
cavsfan@cavsfan-MS-7529:/usr/share/icons/buuf3.10$ cd evolution
cavsfan@cavsfan-MS-7529:/usr/share/icons/buuf3.10/evolution$ sudo chmod --reference=/usr/share/icons/Fog/256x256/places/folder-download.png *
cavsfan@cavsfan-MS-7529:/usr/share/icons/buuf3.10/evolution$ cd ..
cavsfan@cavsfan-MS-7529:/usr/share/icons/buuf3.10$ cd gajim
cavsfan@cavsfan-MS-7529:/usr/share/icons/buuf3.10/gajim$ sudo chmod --reference=/usr/share/icons/Fog/256x256/places/folder-download.png *
cavsfan@cavsfan-MS-7529:/usr/share/icons/buuf3.10/gajim$ cd ..
cavsfan@cavsfan-MS-7529:/usr/share/icons/buuf3.10$ cd gnome-bluetooth
cavsfan@cavsfan-MS-7529:/usr/share/icons/buuf3.10/gnome-bluetooth$ sudo chmod --reference=/usr/share/icons/Fog/256x256/places/folder-download.png *
cavsfan@cavsfan-MS-7529:/usr/share/icons/buuf3.10/gnome-bluetooth$ cd ..
cavsfan@cavsfan-MS-7529:/usr/share/icons/buuf3.10$ cd gnome-packagekit
cavsfan@cavsfan-MS-7529:/usr/share/icons/buuf3.10/gnome-packagekit$ sudo chmod --reference=/usr/share/icons/Fog/256x256/places/folder-download.png *
cavsfan@cavsfan-MS-7529:/usr/share/icons/buuf3.10/gnome-packagekit$ cd gnome-packagekit
bash: cd: gnome-packagekit: No such file or directory
cavsfan@cavsfan-MS-7529:/usr/share/icons/buuf3.10/gnome-packagekit$ cd ..
cavsfan@cavsfan-MS-7529:/usr/share/icons/buuf3.10$ cd gtranslator
cavsfan@cavsfan-MS-7529:/usr/share/icons/buuf3.10/gtranslator$ sudo chmod --reference=/usr/share/icons/Fog/256x256/places/folder-download.png *
cavsfan@cavsfan-MS-7529:/usr/share/icons/buuf3.10/gtranslator$ cd ..
cavsfan@cavsfan-MS-7529:/usr/share/icons/buuf3.10$ cd nm
cavsfan@cavsfan-MS-7529:/usr/share/icons/buuf3.10/nm$ sudo chmod --reference=/usr/share/icons/Fog/256x256/places/folder-download.png *
cavsfan@cavsfan-MS-7529:/usr/share/icons/buuf3.10/nm$ cd ..
cavsfan@cavsfan-MS-7529:/usr/share/icons/buuf3.10$ cd synaptic
cavsfan@cavsfan-MS-7529:/usr/share/icons/buuf3.10/synaptic$ sudo chmod --reference=/usr/share/icons/Fog/256x256/places/folder-download.png *
cavsfan@cavsfan-MS-7529:/usr/share/icons/buuf3.10/synaptic$ cd ..
cavsfan@cavsfan-MS-7529:/usr/share/icons/buuf3.10$ cd ubuntu
cavsfan@cavsfan-MS-7529:/usr/share/icons/buuf3.10/ubuntu$ sudo chmod --reference=/usr/share/icons/Fog/256x256/places/folder-download.png *
cavsfan@cavsfan-MS-7529:/usr/share/icons/buuf3.10/ubuntu$ cd ..
cavsfan@cavsfan-MS-7529:/usr/share/icons/buuf3.10$ cd xfce
cavsfan@cavsfan-MS-7529:/usr/share/icons/buuf3.10/xfce$ sudo chmod --reference=/usr/share/icons/Fog/256x256/places/folder-download.png *
cavsfan@cavsfan-MS-7529:/usr/share/icons/buuf3.10/xfce$ cd ..
cavsfan@cavsfan-MS-7529:/usr/share/icons/buuf3.10$ cd 24x24
cavsfan@cavsfan-MS-7529:/usr/share/icons/buuf3.10/24x24$ sudo chmod --reference=/usr/share/icons/Fog/256x256/places/folder-download.png *
cavsfan@cavsfan-MS-7529:/usr/share/icons/buuf3.10/24x24$ cd ..
cavsfan@cavsfan-MS-7529:/usr/share/icons/buuf3.10$ cd banshee
cavsfan@cavsfan-MS-7529:/usr/share/icons/buuf3.10/banshee$ sudo chmod --reference=/usr/share/icons/Fog/256x256/places/folder-download.png *
cavsfan@cavsfan-MS-7529:/usr/share/icons/buuf3.10/banshee$ cd ..
cavsfan@cavsfan-MS-7529:/usr/share/icons/buuf3.10$ cd conduit
cavsfan@cavsfan-MS-7529:/usr/share/icons/buuf3.10/conduit$ sudo chmod --reference=/usr/share/icons/Fog/256x256/places/folder-download.png *
cavsfan@cavsfan-MS-7529:/usr/share/icons/buuf3.10/conduit$ cd ..
cavsfan@cavsfan-MS-7529:/usr/share/icons/buuf3.10$ cd eog
cavsfan@cavsfan-MS-7529:/usr/share/icons/buuf3.10/eog$ sudo chmod --reference=/usr/share/icons/Fog/256x256/places/folder-download.png *
cavsfan@cavsfan-MS-7529:/usr/share/icons/buuf3.10/eog$ cd ..
cavsfan@cavsfan-MS-7529:/usr/share/icons/buuf3.10$ cd evolution-rss
cavsfan@cavsfan-MS-7529:/usr/share/icons/buuf3.10/evolution-rss$ sudo chmod --reference=/usr/share/icons/Fog/256x256/places/folder-download.png *
cavsfan@cavsfan-MS-7529:/usr/share/icons/buuf3.10/evolution-rss$ cd ..
cavsfan@cavsfan-MS-7529:/usr/share/icons/buuf3.10$ cd gconf-editor
cavsfan@cavsfan-MS-7529:/usr/share/icons/buuf3.10/gconf-editor$ sudo chmod --reference=/usr/share/icons/Fog/256x256/places/folder-download.png *
cavsfan@cavsfan-MS-7529:/usr/share/icons/buuf3.10/gconf-editor$ cd ..
cavsfan@cavsfan-MS-7529:/usr/share/icons/buuf3.10$ cd gnome-control-center
cavsfan@cavsfan-MS-7529:/usr/share/icons/buuf3.10/gnome-control-center$ sudo chmod --reference=/usr/share/icons/Fog/256x256/places/folder-download.png *
cavsfan@cavsfan-MS-7529:/usr/share/icons/buuf3.10/gnome-control-center$ cd ..
cavsfan@cavsfan-MS-7529:/usr/share/icons/buuf3.10$ cd gnome-power-manager
cavsfan@cavsfan-MS-7529:/usr/share/icons/buuf3.10/gnome-power-manager$ sudo chmod --reference=/usr/share/icons/Fog/256x256/places/folder-download.png *
cavsfan@cavsfan-MS-7529:/usr/share/icons/buuf3.10/gnome-power-manager$ cd ..
cavsfan@cavsfan-MS-7529:/usr/share/icons/buuf3.10$ cd notify-osd
cavsfan@cavsfan-MS-7529:/usr/share/icons/buuf3.10/notify-osd$ sudo chmod --reference=/usr/share/icons/Fog/256x256/places/folder-download.png *
cavsfan@cavsfan-MS-7529:/usr/share/icons/buuf3.10/notify-osd$ cd ..
cavsfan@cavsfan-MS-7529:/usr/share/icons/buuf3.10$ cd tomboy
cavsfan@cavsfan-MS-7529:/usr/share/icons/buuf3.10/tomboy$ sudo chmod --reference=/usr/share/icons/Fog/256x256/places/folder-download.png *
cavsfan@cavsfan-MS-7529:/usr/share/icons/buuf3.10/tomboy$ cd ..
cavsfan@cavsfan-MS-7529:/usr/share/icons/buuf3.10$ cd ubuntu-one
cavsfan@cavsfan-MS-7529:/usr/share/icons/buuf3.10/ubuntu-one$ sudo chmod --reference=/usr/share/icons/Fog/256x256/places/folder-download.png *
cavsfan@cavsfan-MS-7529:/usr/share/icons/buuf3.10/ubuntu-one$ cd ..
cavsfan@cavsfan-MS-7529:/usr/share/icons/buuf3.10$ cd xfce-power-manager
cavsfan@cavsfan-MS-7529:/usr/share/icons/buuf3.10/xfce-power-manager$ sudo chmod --reference=/usr/share/icons/Fog/256x256/places/folder-download.png *

```

I fell asleep a few times while doing the above. :p
I didn't know I'd have to build a theme just to change the icons in Mate. In Ubuntu it was a piece of cake.

---

### Post by Cavsfan on 2014-09-20
I think I just figured it out. I opened System > Preferences > Appearances, selected the theme I'm on and clicked customize and changed the icon to the buuf3.10 ones.
I'll have to do some more checking to see if this fixed everything but it looks good so far.

---

