---
title: "ubuntu server seedbox?"
date: 2011-09-12
forum: Server Platforms
---

### Post by DanHorniblow on 2011-09-12
Hi, I have a ubuntu box running 11.04 server, and I would like to turn it in to a seedbox so I can moniter my torrents via the browser.

Any suggestions?

---

### Post by papibe on 2011-09-12
There are several alternatives, but I would recommend transmission-dameon. It runs on the server, but you control it from any computer using a web interface. I highly recommend it. Check it out, and tell us if you need more details.

Regards.

Edit: Although this guide is outdated (it is much easier in Ubuntu now) is describes the basics points. Take a look at the picture in the end: you are controlling your downloads using Firefox.

Edit2: Check out this [thread]("http://ubuntuforums.org/showthread.php?t=1841587&highlight=transmission+daemon"), it discuss more options.

---

### Post by DanHorniblow on 2011-09-12
Hi papibe, thanks for your reply.

I have just done a google on transmission-dameon and this is the perfect solution for me, however I want the web interface to run on port 443 as the server is already running apache.

Would it be difficult to make it run on that port?

---

### Post by papibe on 2011-09-12
You can easily change the port to whatever you want, however I don't think it's a good idea to conflict with apache's port.

Regards.

---

### Post by DanHorniblow on 2011-09-12
Conflict? Would apache not be serving it?

---

### Post by papibe on 2011-09-12
Not really, it is own implementation. For example, I don't have apache running in the server I running transmission-daemon. I can admin my torrents just fine.

Most torrent application's web ui are independent programs that work without the necessity of any web server.

Regards.

---

### Post by arrrghhh on 2011-09-12
There are options that do require apache to serve the page - ruTorrent (with rTorrent) requires apache (or some web server on the machine).

I love rTorrent - runs with very little footprint, and much more powerful than transmission.  I started out with transmission, but found it very limiting.  I had to add some plugins in ruTorrent to get it where I wanted it, but now I have a fully-functional seedbox.  Obviously everyone's requirements are different, as always use what works best for you ;).

---

### Post by DanHorniblow on 2011-09-12
Thanks for your reply arrrghh,

All i want to be able to do is to control my torrent downloads via firefox, so transmission is perfect.

However I have just installed it and it is working fine, apart from I want to download my torrents to /home/me/torrents/, how do I give both my account and debian-transmission read and write access?

---

### Post by arrrghhh on 2011-09-12
> **DanHorniblow said:**
> Thanks for your reply arrrghh,

All i want to be able to do is to control my torrent downloads via firefox, so transmission is perfect.

However I have just installed it and it is working fine, apart from I want to download my torrents to /home/me/torrents/, how do I give both my account and debian-transmission read and write access?

chmod the directory to something that allows guest write access, or chown it to another user (might cause more headache however).  chmodding this directory to 777 is probably pretty harmless.

---

### Post by papibe on 2011-09-12
> **DanHorniblow said:**
> I want to download my torrents to /home/me/torrents/
Stop transmission:
```
$ sudo service transmission-daemon stop
```
Edit the config file:
```
$ sudo nano /etc/transmission-daemon/settings.json
```
Change this like, so it looks like this:
```
   "download-dir": "/home/me/torrents",
```
Save the file, and restart transmission:
```
$ sudo service transmission-daemon start
```
All new torrents will download in the new location (you have to create the dir first).

Hope it helps,
Regards.

---

### Post by dudumomo on 2011-09-12
In my case I'm using Deluge torrent (I think this one is more powerful and nicer than transmission. However Deluge torrent is still a heavy torrent client.
What you can do will be to redirect the used port of your web client to 443 to better suit your needs (It's what i'm doing with deluge+apache as sometimes I'd like to use it under public wifi, etc...where ports are often blocked)

You may check the proxypassreverse option in apache.

---

