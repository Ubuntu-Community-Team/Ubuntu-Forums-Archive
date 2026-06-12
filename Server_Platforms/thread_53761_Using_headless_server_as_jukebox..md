---
title: "Using headless server as jukebox."
date: 2005-08-02
forum: Server Platforms
---

### Post by billputer on 2005-08-02
I've got a headless hoary box that I'd like to plug some speakers into and play music off of.  I would like to find a way to be able to remotely control what is played on the headless box from another computer (we have windows, linux, and macintosh running on our home network).  Does anyone know of a graphical way to control what is played on the headless box?

---

### Post by dare2dreamer on 2005-08-02
I do this daily.

Check out [http://www.musicpd.org](http://www.musicpd.org)

They have a nice command line, web-based and gnome-ui client for your desktops, and the server runs on your headless server.

Everything you need should be in the repositories, iirc.

---

### Post by billputer on 2005-08-02
Thanks a ton, that's great.  Is there anyway I can set my output from either Linux or Windows so I output directly to the headless server?  I'd like to be able to use amarok on my desktop machine and just play music directly to the server as well.

---

### Post by dare2dreamer on 2005-08-03
MPD is really set up to be a server-side play sort of situation. It runs its own database, and all the clients do is manipulate the playlist and playing of the music.

There has been some talk on their wiki of integrating features like you describe though, so you might want to do a little digging.

As a suggestion for a quick and dirty solution, you could remotely mount (NFS, SMB, SHFS) your pc's local music share as MPD's music collection, and then let it index that. I'm planning on trying this when I set up my new media box.

---

