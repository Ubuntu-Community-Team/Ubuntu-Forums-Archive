---
title: "Samba High CPU usage?"
date: 2010-10-08
forum: Server Platforms
---

### Post by wall_e on 2010-10-08
Morning y'all :)

I am a little stuck with how to reduce my SMBD cpu usage.

When a user connects to their home directory over samba, each instance of smbd seems to be using a fair amount of CPU.

Is there anything I can do to improve/reduce this?

After doing some research I've tried reducing my logging level, but to no real effect. Clients are all Mac based.

I've attached an image of my top readout here.
[http://s1217.photobucket.com/albums/dd400/ag246/?action=view&current=Screenshot.png](http://s1217.photobucket.com/albums/dd400/ag246/?action=view&current=Screenshot.png)

Also I'm running 10.04 desktop as a server at the moment.

Some background on the hardware I have.

/home storage is all on hardware raid5 array (3ware 9550sx), CPU's are dual 3.06 xeon (p4 style) and2Gb memory. On the network I am currently 10/100 between the clients and switch and a gigabit to the switch.

The attached screenshot is with only 2 users connected pushing fairly big files. Both Mankit and Alex are using 17% and 20% respectively.

Also my SMB.conf looks like this:

```
#======================= Global Settings =======================

[global]
	unix extensions = no
	read raw = no
	write raw = no
	socket options = TCP_NODELAY IPTOS_LOWDELAY SO_RCVBUF=65536 SO_SNDBUF=65536
	os level = 20
	debug level = 1
	security = user
	share modes = no
        wide links = yes

#======================= Share Definitions =======================

[homes]
	browseable = no
	comment = Home Directories
	writeable = yes
	valid users = %S

``` 

Any pointers?

Thanks in advance!

---

### Post by HermanAB on 2010-10-08
You could try to 'nice' smbd, but it probably won't have a noticeable effect.

---

### Post by dtfinch on 2010-10-08
I see cpu spike whenever something is accessing a lot of files in a large folder (Samba has a fixed-size lookup/stat cache), and requesting those files by their short or wrong-case names rather than their exact names. When this happens, and the name isn't in Samba's cache, it has to do a full directory scan to find the file.

If you're looking at idle cpu usage, some programs will constantly rescan folders. I've seen Dreamweaver push a server's cpu to 100% whenever running, silently monitoring a site for changes. There was some option they had to uncheck to make it stop, though I've forgotten the name.

---

### Post by latz-twn on 2010-10-08
I had the same problem recently on my sheevaplug which is running ubuntu 9.04 and samba 3.3.2 and when a Windows 7 client came onto the network smbd load went up.

After changing some policies in windows 7 I got better results. You should go to this [link]("http://www.enterprisenetworkingplanet.com/_featured/article.php/3849061/Use-Samba-With-Windows-7-Clients.htm").

I don't know if it is really related to the same problem I had, but who knows maybe this helps you.

---

### Post by wall_e on 2010-10-09
Thanks for the replies :)

I ran "nice -10 smbd" which did make a fair difference on my system.

Also I'm fully running ubuntu server now, no gui etc.

I also bought a copy of Pro Ubuntu Server Administration which has helped me no end.

---

### Post by Vegan on 2010-10-09
I do not concern myself with server loading too much. If its chronically saturated then I simply go find a better machine.

My old machine has enough RAM to get the job done so I am not concerned. Most servers need more RAM than the stated minimum.

---

