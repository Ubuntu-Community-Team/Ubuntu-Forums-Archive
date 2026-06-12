---
title: "rhythmbox usb mass storage"
date: 2008-06-19
forum: Ubuntu Brainstorm
---

### Post by soccerboy on 2008-06-19
I would love to see a usb mass storage device support added to rhythmbox.
What I was thinking, since the USB device interfaces are very diverse, a plugin can be created that has many events listed that you can specify what command to run when those happen.

Ex.
Copy Songs: run easypmp -u -d samsung_yh820 <insert mountpoint for the target>

Copy Playlists: run blah

What do you think, anyone else using USB Mass storage mp3 players that have internal databases?

---

### Post by ad_267 on 2008-06-19
Rhythmbox already has support for these. Is there a particular player that isn't working? Try adding an empty file called .is_audio_player in the root directory of the device and open Rhythmbox again.

---

### Post by soccerboy on 2008-06-19
that allows for music to be transferred but what about updating the players internal db
Also, the music transferred doesn't end up in the correct folder for the music player to play the music.

---

### Post by olskar on 2008-06-19
> **soccerboy said:**
> I would love to see a usb mass storage device support added to rhythmbox.
What I was thinking, since the USB device interfaces are very diverse, a plugin can be created that has many events listed that you can specify what command to run when those happen.

Ex.
Copy Songs: run easypmp -u -d samsung_yh820 <insert mountpoint for the target>

Copy Playlists: run blah

What do you think, anyone else using USB Mass storage mp3 players that have internal databases?

You should propably send an email to the rhythmbox develop mailinglist:
[email]rhythmbox-devel@gnome.org[/email]

---

