---
title: ".torrent... what can open this?"
date: 2005-02-05
forum: The Cafe
---

### Post by Lynx on 2005-02-05
Hey guys, I need a program that can open a .torrent file, any help would be much appreciated.

In fact I am having difficulty understanding the whole bittorrent thing... I have it installed but there doesn't seem to be a gui or anything.

---

### Post by carlc on 2005-02-05
Have you installed BitTorrent? You should be able to dl it with apt-get.

 [http://bittorrent.com/](http://bittorrent.com/)

---

### Post by Lynx on 2005-02-05
[QUOTE=carlc]Have you installed BitTorrent? You should be able to dl it with apt-get.

 [http://bittorrent.com/](http://bittorrent.com/)[/QUOTE]

I dled bittorrent via synaptic but when I go to the file there is nothing in it.

---

### Post by j-rock on 2005-02-05
I use Azureus for my bit-torrent transfers.  It's cool, but requires java, so YMMV.

---

### Post by Lynx on 2005-02-05
Is there a tutorial on how to use the bittorrent stuff?

---

### Post by carlc on 2005-02-05
I dont know of a tutorial but I am sure many exist. If you have bittorrent installed, then when you click on the bittorrent file that you want to download, it should give you two options, one to save to disk, and a second option to open with "btdownloadgui". If you open with btdownloadgui, it should take care of the download from there.

---

### Post by Quest-Master on 2005-02-05
[www.ubuntuguide.org](www.ubuntuguide.org) has a guide on installing Azureus. ;)

---

### Post by Wolven on 2005-02-05
If you want to use Firefox to download torrents just:
```
sudo apt-get install bittornado-gui
```
When you click a torrent link now FF should ask you if you want to "Open with /usr/bin/btdownloadgui (default)" Select OK and choose a dir to save the file(s).

---

### Post by adbak on 2005-02-05
I use BitTornado, which works great.  You just click as if you're going to download the  .torrent, but FireFox asks you if you want to use btdownloadgui (the GUI front-end for it) -- say yes.

I have also heard great things about Azureus, but it requires that you have Java installed.

---

### Post by Lynx on 2005-02-05
will epiphany ask me the same question?

---

### Post by ups on 2005-02-07
a simple and light bittorrent gui is gnome-btdownload - its present in synaptic and also supported in ubuntu. it doesnt require java or anything, so u can give it a try.

however, i'm running hoary - not sure if its present in warty.

---

### Post by Lynx on 2005-02-07
I got tornado up and running, only to find out that my school blocks p2p downloads, I now need to look into a proxy-server in order to bypass that and use tornado.

---

### Post by onlainari on 2005-02-20
Alrighty. I am going to look for a bt-client capable of handling many torrents in one window like azureus. 

Why not Azureus?  - I am struggling running wine at the same time. For some reason it totally freezes the wine. It will work real slow if I have azureus running in background.

---

### Post by YokoZar on 2005-02-20
[QUOTE=onlainari]Alrighty. I am going to look for a bt-client capable of handling many torrents in one window like azureus. 

Why not Azureus?  - I am struggling running wine at the same time. For some reason it totally freezes the wine. It will work real slow if I have azureus running in background.[/QUOTE]
Azureus is a Java program and can work natively without the use of Wine.  Check out [http://www.ubuntuguide.org/](http://www.ubuntuguide.org/) for intsructions.

---

### Post by poofyhairguy on 2005-02-20
[QUOTE=Lynx]will epiphany ask me the same question?[/QUOTE]


Maybe. If not, save the file to you home folder and open it.

---

### Post by poofyhairguy on 2005-02-20
[QUOTE=Wolven]If you want to use Firefox to download torrents just:
```
sudo apt-get install bittornado-gui
```
When you click a torrent link now FF should ask you if you want to "Open with /usr/bin/btdownloadgui (default)" Select OK and choose a dir to save the file(s).[/QUOTE]


Bit Tornado Gui is a lot better than the regular Bit Torrent client. With the regular client, it uses automatic settings for uploads and I can only the download to take up 10% or so of my bandwidth. With Bit Tornado I put my setting how I know they work (dsl slow, 13kps up) and I will download torrents faster than anything else.

---

### Post by Wardhog on 2005-02-22
[QUOTE=onlainari]Alrighty. I am going to look for a bt-client capable of handling many torrents in one window like azureus. 

Why not Azureus?  - I am struggling running wine at the same time. For some reason it totally freezes the wine. It will work real slow if I have azureus running in background.[/QUOTE]

I had a hard time figuring out how to run Azureus 24/7 on a headless box, and now use "nohup btlaunchmany . --max_upload_rate 9 &" and ssh in and use "tail -f nohup.out" to check progress. 

Azureus is the best-looking BT client IMO, but the tools provided with the bittorrent package only require a little time invested in learning how they work.

---

### Post by deviant03 on 2005-03-05
The regular Bittorrent client is a much easier install than Azureus, at least on Ubuntu that is. Havent tried Bit Tornado yet though.

---

