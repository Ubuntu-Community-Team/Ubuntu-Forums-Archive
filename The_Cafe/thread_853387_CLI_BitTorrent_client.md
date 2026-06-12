---
title: "CLI BitTorrent client"
date: 2008-07-08
forum: The Cafe
---

### Post by happysmileman on 2008-07-08
Anyone want to recommend a good CLI bittorrent client.

I'd much prefer if it had a web interface, but can't really seem to find any CLI based clients with one, rTorrent can be controlled by SCGI, but I'm not entirely sure what that means, would that be the same?

I'm looking for a client I can have running pretty much constantly, and control (add/remove/pause torrents) remotely, so I'm looking for one as lightweight as possible, which isn't prone to crashing or leaking memory.

I've heard good things about rTorrent but not sure if it can be controlled remotely easily.

---

### Post by LookTJ on 2008-07-08
rtorrent can be controlled via screen+ssh. If you are on a remote windows machine, you can have putty on your flash drive and use

```
screen -r torrent
``` the above code will work if you have the screen session titled as "torrent"
```
screen -dmS torrent
```to detach a screen without quitting
```
ctrl+a, release, then hit d
```so it's pretty much simple. I'm not too sure about a web client for rtorrent. but you can always use torrentflux on a web server if you want :). Torrentflux isn't CLI by the way

---

### Post by happysmileman on 2008-07-08
> **Taylor said:**
> rtorrent can be controlled via screen+ssh. If you are on a remote windows machine, you can have putty on your flash drive and use

```
screen -r torrent
``` the above code will work if you have the screen session titled as "torrent"
```
screen -dmS torrent
```to detach a screen without quitting
```
ctrl+a, release, then hit d
```so it's pretty much simple. I'm not too sure about a web client for rtorrent. but you can always use torrentflux on a web server if you want :). Torrentflux isn't CLI by the way

Sounds pretty good, didn't really think of SSH, I probably will end up going with rTorrent

---

### Post by chalewa on 2008-07-08
rtorrent is phenomenal.. by far my favorite client out there (gui or cli). 

it is pretty easy to control it remotely, i mean after you get your config file set up, you can have a folder to autostart/stop torrents with. i have that folder shared, and can drop torrents into that folder whenever i want...or take them out if i want to stop them. 

there are a few pretty good tutorials out there to set up the config file

also

```
screen rtorrent 
```

and then 

```
screen -r
```to resume it.

---

### Post by Mateo on 2008-07-08
rtorrent isn't CLI though ;).  It's TUI.

---

### Post by happysmileman on 2008-07-08
> **chalewa said:**
> 
it is pretty easy to control it remotely, i mean after you get your config file set up, you can have a folder to autostart/stop torrents with. i have that folder shared, and can drop torrents into that folder whenever i want...or take them out if i want to stop them. 

... That's probably even better than web interface for me, I could just have a folderview widget on my desktop and drag and drop the torrent files to the desktop :P

---

### Post by chalewa on 2008-07-08
> **Mateo said:**
> rtorrent isn't CLI though ;).  It's TUI.

lol this is true

---

### Post by LookTJ on 2008-07-08
> **Mateo said:**
> rtorrent isn't CLI though ;).  It's TUI.

Ah I never realized that, considering that ncurses is indeed TUI(text user interface). Haha:)

---

### Post by happysmileman on 2008-07-08
> **Mateo said:**
> rtorrent isn't CLI though ;).  It's TUI.

Hmmm I'd never heard of a TUI, but after looking looking it up, it turns out you're right :P

---

### Post by chalewa on 2008-07-08
yea it is in fact tui, but i think that a lot of people (myself included) would consider apps like rtorrent and naim to be cli even tho they use ncurses and are in fact tui

---

### Post by forger on 2008-07-08
> **happysmileman said:**
> I'm looking for a client I can have running pretty much constantly, and control (add/remove/pause torrents) remotely, so I'm looking for one as lightweight as possible, which isn't prone to crashing or leaking memory.


```
apt-cache search torrent.*cli
```

1) [deluge-torrent]("http://www.deluge-torrent.org"), has a plugin for web administration (webui)
2) [azureus / vuze]("http://azureus.sf.net") - same, [http://azureus.sourceforge.net/plugin_details.php?plugin=azhtmlwebui](http://azureus.sourceforge.net/plugin_details.php?plugin=azhtmlwebui)
3) transmission-cli - free, lightweight BitTorrent client (command line interface)
transmission-gtk - free, lightweight BitTorrent client (graphical interface)
clutch - Web-based BitTorrent client using Transmission engine
4) torrentflux - web based, feature-rich BitTorrent download manager

---

### Post by Mateo on 2008-07-08
i didn't realize that tranmission had a cli and daemon... i actually have them installed but had never used them or realized of their existence.  how nice.

---

### Post by forger on 2008-07-08
..you're welcome :twisted:

---

