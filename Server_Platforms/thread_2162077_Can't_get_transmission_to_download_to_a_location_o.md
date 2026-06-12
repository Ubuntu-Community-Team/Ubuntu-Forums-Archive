---
title: "Can't get transmission to download to a location on the mounted drive...."
date: 2013-07-13
forum: Server Platforms
---

### Post by Kdar on 2013-07-13
On my Ubuntu headless server, I am trying to install and configure Transmission-daemon.
I created a "torrents" directory in my mounted drive: "/mnt/drive01/torrents

I set  all proper chown and chmod for that directory per several similar tutorials such as this one:
[http://learnedstuffs.wordpress.com/2012/12/29/installing-transmission-web-client-on-ubuntu-server-12-10/](http://learnedstuffs.wordpress.com/2012/12/29/installing-transmission-web-client-on-ubuntu-server-12-10/)
```
mkdir torrents
sudo chown debian-transmission:debian-transmission torrents
sudo usermod -a -G debian-transmission <user>
sudo chmod 770 torrents

```
...... etc (with modification to settings.json to include changed directories)

However, no matter what I do, I always get this error when I try to download a torrent (it stops at 4.49MB and displays the error):
```
Error: No data found! Ensure your drives are connected or use "Set Location". To re-download, remove the torrent and re-add it.
```

---
Nevermind.. I got it working with Deluged and Deluged web Ui.

---

