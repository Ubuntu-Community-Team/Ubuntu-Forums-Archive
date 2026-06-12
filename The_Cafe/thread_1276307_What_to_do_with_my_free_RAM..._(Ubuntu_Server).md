---
title: "What to do with my free RAM... (Ubuntu Server)"
date: 2009-09-26
forum: The Cafe
---

### Post by sammcj on 2009-09-26
I have 4GB of DDR2/667 in my Ubuntu Server which is only acting as a Samba server for NAS.

I only actually use 256-512MB of that 4GB and am looking for some interesting ideas on what to do with the left-over 3.5+GB.

[IMG]http://www.nullamatix.com/images/I-dunno-lol.jpg[/IMG]

Ideas anyone?

---

### Post by sandyd on 2009-09-26
Seti@ home ?

---

### Post by Paqman on 2009-09-26
> **carlee said:**
> Seti@ home ?

Doesn't really use much RAM, it's all about CPU cycles. Actually these days it's more about GPU cycles, but you get my point.

You could always create some ramdisks. /tmp is an obvious candidate for this.

---

### Post by sammcj on 2009-09-26
> **carlee said:**
> Seti@ home ?

Doesn't really use lots of a RAM, also I don't really want my NAS to be running hot!

---

### Post by renkinjutsu on 2009-09-26
run a bunch of daemons that you can connect to with gui's? like quassel (i think), Deluge? anything.. Game servers for LAN parties xD

---

### Post by foremannz on 2009-09-27
VirtualBox an Ubuntu client, then remote access it from another computer - could be good for things like torrents when you don't want your desktop to be used

---

### Post by gletob on 2009-09-27
> **foremannz said:**
> VirtualBox an Ubuntu client, then remote access it from another computer - could be good for things like torrents when you don't want your desktop to be used

Then you would just run a torrent server like the deluge web ui.  Much more efficent than A VM, but a VirtualBox backend does seem like a cool idea.

---

### Post by sammcj on 2009-09-27
Right, well I'm running Deluge...
So now with Deluge, Apache, Mysql, PHP, firefly media server, ushare xbox upnp server, samba and some other services running I'm using a whopping 119MB of my 4GB of RAM... (Not counting the 256MB RAMDisk I setup too).

Tell me more about running a VM on it headless?

[IMG]http://i66.photobucket.com/albums/h255/sammcj2000/Screenshot2009-09-27at105720PM.png[/IMG]

---

### Post by hessiess on 2009-09-27
Bake massive fluid sims in Blender, honestly this is the only thing I am aware of which would eaven start to use that much RAM.

---

### Post by sammcj on 2009-09-27
> **hessiess said:**
> Bake massive fluid sims in Blender, honestly this is the only thing I am aware of which would eaven start to use that much RAM.

fantastic...

how do you take your rendered coffee?


can anyone feel a rendering farm coming along?

---

### Post by Paqman on 2009-09-27
Sell the extra RAM on eBay and buy something useful.

---

### Post by bodhi.zazen on 2009-09-27
Linux is not windows and the sad truth is most people do not use more then 1.5 Gb RAM . That is not to say that some users do not require more, just that most do not.

Server side I would advise you look at Virtualization.

---

### Post by HavocXphere on 2009-09-27
So you have the solution but not a matching problem. Right.

Use /dev/shm to dump files into the memory. Just remember that its gone when you restart or power gets cut. Unlike your RAMdisk, it will use as much RAM as is needed/available.

I use it mainly when working on images. Much faster than HDD. In your case a slow network might kill any gains though since its on the server.

---

### Post by sammcj on 2009-09-27
> **HavocXphere said:**
> So you have the solution but not a matching problem. Right.


I guess you could say that's correct; I hate to see RAM go to waste!


> **HavocXphere said:**
> 
Use /dev/shm to dump files into the memory. Just remember that its gone when you restart or power gets cut. Unlike your RAMdisk, it will use as much RAM as is needed/available.

I use it mainly when working on images. Much faster than HDD. In your case a slow network might kill any gains though since its on the server.


Hmm this sounds interesting, I have a full-duplex GbE network.
Thanks.

---

### Post by sammcj on 2009-09-27
> **Paqman said:**
> Sell the extra RAM on eBay and buy something useful.

Unfortunately DDR2 is near worthless, if you go to our local shop you can buy 2GB for NZ$30 (US$21).

I was more interesting in what projects people had in mind.

---

### Post by sammcj on 2009-09-27
> **bodhi.zazen said:**
> Linux is not windows and the sad truth is most people do not use more then 1.5 Gb RAM . That is not to say that some users do not require more, just that most do not.

Server side I would advise you look at Virtualization.

Yes I fully agree and understand, I find I can use 2GB+ with VM / Photoshop.

Having more RAM does allow the OS to preload higher amounts of data which is nice; but this applies more the the desktop scene.

---

### Post by Paqman on 2009-09-27
> **sammcj said:**
> Unfortunately DDR2 is near worthless, if you go to our local shop you can buy 2GB for NZ$30 (US$21).


Enough for several beers.

---

### Post by 3rdalbum on 2009-09-27
> **Paqman said:**
> Sell the extra RAM on eBay and buy something useful.

+1. I don't think there's anything worthwhile you can do on a headless server that will use up RAM and not push your CPU.

---

### Post by bear24rw on 2009-09-27
put /tmp in a ram disk and then cat /dev/urandom > /tmp/really_big_file.txt see how long it takes to eat your ram

---

### Post by Dimitriid on 2009-09-27
Get a more modest PC to run as server and use your current server for something like gaming ( you will need a videocard but with the recent launch of new ATI cards nvidia won't be trailing for long and we'll have incredible prices as the result of their all out war )

---

### Post by sammcj on 2009-09-27
> **Dimitriid said:**
> Get a more modest PC to run as server and use your current server for something like gaming ( you will need a videocard but with the recent launch of new ATI cards nvidia won't be trailing for long and we'll have incredible prices as the result of their all out war )

Thanks for the suggestion but no no no no no no; the idea of this thread is to come up with something that it could be used for on this server - brainstorm time!

---

### Post by Dimitriid on 2009-09-27
I'd say donate resources to a good cause but I think they are more interested in CPU and not ram again.

---

