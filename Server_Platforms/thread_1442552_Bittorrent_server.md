---
title: "Bittorrent server"
date: 2010-03-30
forum: Server Platforms
---

### Post by damo12 on 2010-03-30
[FONT="Comic Sans MS"]I support a company that has a headless Ubuntu Server which they use as a file server to access from Windows machines.  The sever is usually managed through Webmin.  As part of the work they do, they often download files using bittorrent.

They use utorrent to download the files over night.  Is there any way that they can search for the torrent file on the Windows machine and then set the server away carrying out the download?

Thanks in advance for your help.[/FONT]

---

### Post by Jakob Lundberg on 2010-03-30
You can use rtorrent to download torrents on a headless server.

If you start it inside a screen session you can detach the session and log out while rtorrent continues the download.

---

### Post by spynappels on 2010-03-30
Is there a HowTo on that? I've never run a screen session off an Ubuntu Server before, they've always been completely CLI except for Webmin for me.

---

### Post by steev182 on 2010-03-30
screen is just a session in cli that doesn't stop when you disconnect. It's really useful to use. I think in 9.10 upwards it's called byobu.

---

### Post by Jakob Lundberg on 2010-03-30
The basics are

Create a session named rtorrent
```
screen -dmS rtorrent
```

List sessions
```
screen -ls
```

Attach to a session namned rtorrent
```
screen -r rtorrent
```

Detach a session with
```
Ctr-a d
```

End the session with exit from within.
More indepth HowTos are available on the net or you can check
```
man screen 
```

---

### Post by tr333 on 2010-03-30
Transmission has a web interface called "Clutch" that can be accessed from any web browser on the network.  It runs as a daemon process, so you don't need to run any GUI software.  Once installed, it can be accessed on port 9091 ([http://servername:9091](http://servername:9091)).  It makes downloading torrents easy as the download will continue regardless of whether the webclient is loaded in the browser, since it's just a client for the backend transmission-daemon process.

[http://trac.transmissionbt.com/wiki/WebInterface](http://trac.transmissionbt.com/wiki/WebInterface)
[http://trac.transmissionbt.com/wiki/UnixServer/Debian](http://trac.transmissionbt.com/wiki/UnixServer/Debian)
[http://trac.transmissionbt.com/wiki/ConfigurationParameters](http://trac.transmissionbt.com/wiki/ConfigurationParameters)

---

### Post by 8Kuula on 2010-03-30
Deluge torrent client has daemon that can put to run in server, and workstations can connect to that daemon. 
Daemon can be connected with web ui too.

Console interface is not realy usefull, nothing like rTorrent level, but daemon can be connected that way too.

[http://deluge-torrent.org/](http://deluge-torrent.org/)

---

### Post by dudumomo on 2010-03-30
I really like Deluge torrent !
Very easy to set up and to use.

Check my "how to" here: [http://www.freelydifferent.com/self-hosting/deluge-torrent-daemon-webui/](http://www.freelydifferent.com/self-hosting/deluge-torrent-daemon-webui/)

I've just installed deluge on my ubuntu server a couple of days ago.

---

### Post by Aurelius on 2010-03-30
> **damo12 said:**
> [FONT="Comic Sans MS"]Is there any way that they can search for the torrent file on the Windows machine and then set the server away carrying out the download?

Thanks in advance for your help.[/FONT]

I use rtorrent in my headless Ubuntu server at home, set up to automatically start torrents in finds in ~/downloads/watch. I've got a drive mapped to that folder from my windows machine, and a Firefox extension that saves downloads to specific directories based on file extension.

When I download a .torrent from the windows machine, Firefox saves the .torrent file to rtorrent's watch folder on my Ubuntu server and rtorrent automatically starts downloading the torrent.

I don't remember the name of the extension off the top of my head, but it should be pretty easy to find.

---

### Post by damo12 on 2010-03-31
[FONT="Comic Sans MS"]Thanks, I'll get them to give that a try[/FONT]

---

### Post by jfmanamtr on 2010-03-31
Another one to check out is torrentflux (apt-get install torrentflux). You can either upload the torrents or search for them on your favorite bittorrent search engine. I run torrentflux & enjoy the heck out of it.

~John

---

