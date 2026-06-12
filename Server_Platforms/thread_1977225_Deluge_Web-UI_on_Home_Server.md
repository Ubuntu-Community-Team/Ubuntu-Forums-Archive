---
title: "Deluge Web-UI on Home Server"
date: 2012-05-09
forum: Server Platforms
---

### Post by iSplicer on 2012-05-09
Hey everyone, hope you're all having an awesome day.

I have a quick question about setting up a torrent server on my home seedbox, which will be running Ubuntu server 12.04. I'd greatly appreciate

Normally if my machine was running the desktop version of ubuntu, I would simply install deluge, deluge-web and deluge web-ui using synaptic, and then fire up deluge, go to preferences, and check the box that enables web-ui. This would work fine, I could access the web-ui from any computer in my network.

However I'm struggling to get this working via the CLI whilst SSHing into my server, since there's no GUI available. I've tried executing the following code:

```
sudo apt-get install deluge
```
```
sudo apt-get install deluge-web
```
```
sudo apt-get install deluge-webui
```
```
sudo apt-get install deluged
```

However after this I've got no idea what to do in order to get the webui working from now. I'm having trouble understanding the official documentation =(. I'm sure it's a simple process, any help would be greatly appreciated =].

Thanks!

---

### Post by anuvnu387 on 2012-05-17
Check this post out: [http://linuxblog.avserver.info/install-deluge-with-webui-on-ubuntu-1204-precise-pangolin-server/](http://linuxblog.avserver.info/install-deluge-with-webui-on-ubuntu-1204-precise-pangolin-server/) 

It worked for me. good luck.

---

### Post by d4m1r on 2012-05-17
I'd recommend [transmission-daemon]("http://www.webupd8.org/2009/12/setting-up-transmission-remote-gui-in.html") instead. It is really simply to install (only 1 package) and use and has all the features 99% of bittorrent users needed.

---

