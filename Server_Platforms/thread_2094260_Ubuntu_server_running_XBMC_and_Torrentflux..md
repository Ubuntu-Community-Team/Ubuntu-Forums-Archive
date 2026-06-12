---
title: "Ubuntu server running XBMC and Torrentflux."
date: 2012-12-13
forum: Server Platforms
---

### Post by Hobbes2k2 on 2012-12-13
Hey guys!  I used to have a setup with Ubuntu running the server edition, with XBMC as my media player.  It had no desktop, which I liked, just booted right into XBMC.  I also had torrentflux running so I could download free documentaries and music and such.  

I liked it because I could start the torrent from my laptop, it would download on my server, which was hooked up to my TV, then I could watch it right away.  

I'm going to attempt this setup again, I've gotten another desktop I'm not using.  I was just wondering if XBMC would be a good choice, because I don't really have the skills to remotely control the server, and move and rename files.  

Any help is greatly appreciated!  

Side note, I would also like opinions on a distro that would maybe run better, and take less power.  I plan on keeping this baby running for maybe 10 hours a day.

---

### Post by papibe on 2012-12-13
Hi Hobbes2k2. Welcome to the forums ):P

I'd recommend taking a look at transmission-daemon as your bittorrent client. It runs as a service, so no desktop environment is necessary, and can be used through your browser.

As for XBMC, this are my thoughts: as a simple media player is an overkill. However, if you keep a what you download and your media library gets medium/big, it is **fantastic**.

For full HD playback, you may need to consider getting hardware that supports video hardware acceleration. The easiest option would be to get a ~$40 Nvidia card.

Let us know how it goes.
Regards.

---

### Post by cariboo on 2012-12-14
You can use nautilus for file management, using sftp, just setup openssh server, on the server, and access it from any other desktop system on your local network.

Have a look at the openssh-server howto [here]("https://help.ubuntu.com/community/SSH/OpenSSH/Configuring").

Once you have ssh set up, just open nautilus, press Ctrl-t to open an other tab, then press Ctrl-l to open the location bar and type:

```
sftp://servername
```

**Note:** This presupposes that you have aliased the server ip address to the server name in /etc/hosts eg:

```
127.0.0.1	localhost
127.0.1.1	alexis
192.168.0.104	willy
192.168.0.240	likely
```

Likely and willy are my two file servers.

---

### Post by Hobbes2k2 on 2012-12-14
Thanks for the reply guys!  I'll definitely check these out!

---

