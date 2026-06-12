---
title: "Changing system defaults doesn't do anything"
date: 2012-04-18
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by ikt on 2012-04-18
Does this affect anyone else?

Example: (Install VLC)

System Settings > Details > Default Applications > Change music and video from Rythembox and Movie Player to VLC 

Then try and open a movie or mp3, does it still try and open in rhythmbox/totem?

---

### Post by ELD on 2012-04-18
Works fine for me using it from the right click menu on files themselves.
 
I only 1-2 days ago changed avi files to load from vlc, using the menu on right click to tell it to use vlc.
 
Haven't tried via system settings though.

---

### Post by philinux on 2012-04-18
> **ikt said:**
> Does this affect anyone else?

Example: (Install VLC)

System Settings > Details > Default Applications > Change music and video from Rythembox and Movie Player to VLC 

Then try and open a movie or mp3, does it still try and open in rhythmbox/totem?

Indeed. flac and mp3 open with RB. Ogg files opened with VLC though.

Movies with totem.

---

### Post by mc4man on 2012-04-18
system defaults changes 1 mimetype for audio & video so  they're not that useful options  

audio - audio/x-vorbis+ogg=
video - video/x-ogm+ogg=

---

### Post by philinux on 2012-04-18
> **mc4man said:**
> system defaults changes 1 mimetype for audio & video so  they're not that useful options  

audio - audio/x-vorbis+ogg=
video - video/x-ogm+ogg=

That explains it then, back to right click properties if needed.

Personally I'm ok with RB for music. Maybe there are better alternatives dunno.

---

### Post by mc4man on 2012-04-18
A little fill in concerning lens - 
the music lens/scopes opens in the scope or source player, unaffected by default per mimetype=

The file lens will use set default per mimetype=
The video lens will also use set default per mimetype=

On a user basis all is seen/set in ~/.local/share/applications/mimeapps.list

---

