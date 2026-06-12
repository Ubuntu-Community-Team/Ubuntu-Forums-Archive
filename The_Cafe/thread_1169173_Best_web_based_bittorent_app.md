---
title: "Best web based bittorent app"
date: 2009-05-24
forum: The Cafe
---

### Post by Eviltechie on 2009-05-24
What is the web based bitorrent app? I tried transmission and ktorrent, as they both have web panels, but they didn't have enough features in them. I tried torrentflux, but it didn't look that good and wouldn't fit in with the theme I've got.

---

### Post by dmizer on 2009-05-24
> **Eviltechie said:**
> What is the web based bitorrent app? I tried transmission and ktorrent, as they both have web panels, but they didn't have enough features in them. I tried torrentflux, but it didn't look that good and wouldn't fit in with the theme I've got.

What features are you missing from transmission?

---

### Post by Sublime Porte on 2009-05-24
The latest deluge actually runs as a daemon, so you run a backend at startup, then can connect to it many different ways, either attaching a GTK interface (from any remote PC), or a console client, or a WebUI.

---

### Post by Eviltechie on 2009-05-24
The thing is I need the entire app as web based. I will be running this on a server, not a desktop, so I can't have anything with a gui.

EDIT: Ok, I tried deluge, and it is exactly what I needed.

---

### Post by stmiller on 2009-05-24
torrentflux

/end thread

:)

---

### Post by PurposeOfReason on 2009-05-25
> **stmiller said:**
> torrentflux **b4rt**

/end thread

:)
.

---

### Post by pwnst*r on 2009-05-25
> **stmiller said:**
> torrentflux

/end thread

:)

actually - beginning of thread.  try re-reading.

---

### Post by dmizer on 2009-05-25
> **Eviltechie said:**
> The thing is I need the entire app as web based. I will be running this on a server, not a desktop, so I can't have anything with a gui.

EDIT: Ok, I tried deluge, and it is exactly what I needed.

Just FYI, transmission can also be run as a daemon. Just install transmission-cli and start the daemon with:
```
transmission-daemon
```

---

### Post by ghindo on 2009-05-25
I've had good experiences with running Transmission on a headless, GUI-less server.  I just use the web UI and everything works out pretty well.

What advantages does Deluge have over Transmission?

---

### Post by Sublime Porte on 2009-05-25
With deluge you can also connect to it with the client-gui itself. So you're not limited to a cutdown web interface, nor a command line.

---

### Post by ghindo on 2009-05-25
> **Sublime Porte said:**
> With deluge you can also connect to it with the client-gui itself. So you're not limited to a cutdown web interface, nor a command line.Screenshot?

---

### Post by kpkeerthi on 2009-05-25
Deluge has sophisticated Queue management capabilities.

---

### Post by dmizer on 2009-05-25
> **kpkeerthi said:**
> Deluge has sophisticated Queue management capabilities.

Indeed, the more I investigate it the more I like it. I'm planning to give it a go this evening.

---

### Post by FuturePilot on 2009-05-25
> **ghindo said:**
> Screenshot?

daemon running on my server, connected to it from my laptop through the gtk interface. Nothing going at the moment but it behaves just as it would if it were running locally.

[http://dev.deluge-torrent.org/wiki/UserGuide/ThinClient]("http://dev.deluge-torrent.org/wiki/UserGuide/ThinClient")

---

### Post by ghindo on 2009-05-25
> **FuturePilot said:**
> daemon running on my server, connected to it from my laptop through the gtk interface. Nothing going at the moment but it behaves just as it would if it were running locally.

[http://dev.deluge-torrent.org/wiki/UserGuide/ThinClient]("http://dev.deluge-torrent.org/wiki/UserGuide/ThinClient")Looks interesting - I may have to try it out.  Thanks for the screenshot and info.  Out of curiosity, what's that theme?

---

### Post by FuturePilot on 2009-05-25
> **ghindo said:**
> Looks interesting - I may have to try it out.  Thanks for the screenshot and info.  Out of curiosity, what's that theme?

You're welcome. :) 
Theme is Shiki-Wise from [Shiki-Colors]("http://www.gnome-look.org/content/show.php/Shiki-Colors?content=86717")

---

### Post by Hortinstein on 2009-05-25
I am a big fan of rtorrent/screen combo over ssh so i can putty in using windows machines...and I set it up to categorize downloads based on what tracker for different watch folders and seperate the finished downloads.  Very effective...a little hard to setup, but so lightweight it's hard to beat

---

### Post by Sublime Porte on 2009-05-25
> Screenshot?

images.google.com

Search string: deluge connection manager

---

