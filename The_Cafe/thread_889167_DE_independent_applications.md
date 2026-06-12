---
title: "DE independent applications?"
date: 2008-08-13
forum: The Cafe
---

### Post by TheOrangePeanut on 2008-08-13
I'm trying to go to a DE independent system, sort of.  I'm actually using LXDE, but I want to stay away from KDE and Gnome dependencies because of the bloat, and LXDE is way more light weight.  However, there are a couple of apps that I don't know how to replace.

The first was Kwrite/Gedit, but I found medit which works wonderfully.  Now for the more difficult ones.

Amarok.  I need 3 features that Amarok has, basically.  It needs to have library support that reads MP3 tags, a playlist function that works similarly to Amaroks (I double click the file or album in the library and it just adds it to the playlist), and lastfm integration (though this one is forgivable).  

Kaffeine.  I need a video player that can play DVDs, avis and wmvs (among whatever else I find) and has a playlist function similar to what I described above.

The toolkit doesn't matter, GTK or QT, I just want to stay away from large DE dependencies.  What programs should I look into?

---

### Post by LaRoza on 2008-08-13
> **TheOrangePeanut said:**
> I'm trying to go to a DE independent system, sort of.  I'm actually using LXDE, but I want to stay away from KDE and Gnome dependencies because of the bloat, and LXDE is way more light weight.  However, there are a couple of apps that I don't know how to replace.

The first was Kwrite/Gedit, but I found medit which works wonderfully.  Now for the more difficult ones.

Amarok.  I need 3 features that Amarok has, basically.  It needs to have library support that reads MP3 tags, a playlist function that works similarly to Amaroks (I double click the file or album in the library and it just adds it to the playlist), and lastfm integration (though this one is forgivable).  

Kaffeine.  I need a video player that can play DVDs, avis and wmvs (among whatever else I find) and has a playlist function similar to what I described above.

The toolkit doesn't matter, GTK or QT, I just want to stay away from large DE dependencies.  What programs should I look into?

I do the same thing now:

WM: wmii/xmonad
Filemanager: pcmanfm or mc
Media: VLC (for everything)

I don't know about your music though.

---

### Post by picpak on 2008-08-13
Music: Quod Libet?
Media: GNOME Mplayer (don't let the name fool you; it's DE independent)

SCiTE is another good text editor.

---

### Post by smartboyathome on 2008-08-13
I don't know if it will work for you, but there is always MPD + one of the many GUIs for it, or even Audacious!

---

### Post by original_jamingrit on 2008-08-13
for pdfs, if you don't like the barebones look of xpdf, try epdfview.  It uses gtk+, but doesn't depend on any gnome libraries.

Also, +1 for audacious

---

### Post by picpak on 2008-08-13
> **original_jamingrit said:**
> for pdfs, if you don't like the barebones look of xpdf, try epdfview.  It uses gtk+, but doesn't depend on any gnome libraries.

Neither does evince-gtk, which is a DE independent version of what GNOME uses. Both good choices.

---

### Post by ntowakbh on 2008-08-13
I think that Exaile might fit the bill for an audio player.  It's just like Amarok with the playlist part.  And it does have Last.fm.

As for videos, I just use MPlayer with no GUI.

---

### Post by voteforpedro36 on 2008-08-13
> **smartboyathome said:**
> I don't know if it will work for you, but there is always MPD + one of the many GUIs for it, or even Audacious!

MPD is great if you can make it work.

At the post above me, Exaile is far from lightweight and even DE independent.

---

### Post by smartboyathome on 2008-08-13
> **voteforpedro36 said:**
> MPD is great if you can make it work.

At the post above me, Exaile is far from lightweight and even DE independent.

Its not that hard, actually. Check out [this page]("http://wiki.archlinux.org/index.php/Mpd") for info on how to set it up. Its made for Arch, so some things will have to change, but once its set up, its easy to maintain.

---

### Post by voteforpedro36 on 2008-08-13
> **smartboyathome said:**
> Its not that hard, actually. Check out [this page]("http://wiki.archlinux.org/index.php/Mpd") for info on how to set it up. Its made for Arch, so some things will have to change, but once its set up, its easy to maintain.

I used that page a couple weeks ago to set it up myself. My only problem was, after getting it working, trying to get it to work on boot, that I had to change one file in there to a file in my home directory instead of /var, and then "touch" that file, but after that it worked perfectly... but that's for another time.

---

### Post by cardinals_fan on 2008-08-13
Music: AlsaPlayer-gtk
Video: Mplayer
File Manager: pcmanfm/clex
Image Organizer: GQview
Image Viewer: GPicView
Image Editor: GIMP
IDE: Geany
Game: Sudoku Savant
Calculator: Galculator
Archive Manager: Xarchiver
Browser: Opera/Kazehakase/Firefox (in my preferred order :))
FTP: Browser/gFTP
IRC: LostIRC
Spreadsheet: Gnumeric
Word Processor: Abiword
Organizer/Calendar: Osmo
PDF Viewer: ePDFview
Notes: NoteCase (an awesome app!) / Xpad (for sticky notes)
Editor: Vim/Leafpad

---

