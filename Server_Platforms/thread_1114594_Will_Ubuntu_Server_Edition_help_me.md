---
title: "Will Ubuntu Server Edition help me?"
date: 2009-04-02
forum: Server Platforms
---

### Post by Nixie Pixel on 2009-04-02
Hi, I am rebuilding the machine I have been using as a file server and LAMP server, and wanted to see if using the Server edition would be a good choice for me.

Here are the tasks I want to accomplish:  I have 2 500 GB, 1 160 GB, and 1 80 GB HDDs, and I want to create a RAID array for storing documents, music, videos, and other data for the people on the (home) network.  I also want to run Twonky or another streaming media server to serve the media to an Xbox and other media players.  Additionally I want to install and run LAMP for testing and development of web pages (not necessarily, though not ruling out, web services open to the internet).  Finally, I want the computer to be my main p2p file sharing box, downloading torrents (possibly adding several older machines as torrent slaves in the future).

Do I need Server edition to do these things?  I'll have 2 GB RAM and a 1.6 Ghz processor to play with.  I don't really need a GUI, though since I am much more familiar with GUI administration I would prefer it, at least for now.  But really I'm most concerned about how to set up 3 of my HDDs in a RAID array for fault tolerance (I don't care about performance), and handling the media/torrent/LAMP server duties.

Thanks!

---

### Post by hyper_ch on 2009-04-03
The sever edition contains a different kernel than the default one and no gui. It is aimed at providing best performance for "serving" other computers with data. For what you want you can use the server edition.

and besides, RAID is not a backup solution.

---

### Post by Nixie Pixel on 2009-04-03
Thanks...are there any other differences that I should be aware of?

I'm not sure what you mean about a backup solution.  I was looking at RAID for fault tolerance, not to create backups.

---

### Post by hyper_ch on 2009-04-03
a lot of people confuse fault tolerance with backups :)

[http://www.ubuntu.com/products/whatisubuntu/serveredition/features](http://www.ubuntu.com/products/whatisubuntu/serveredition/features)

---

### Post by vpsville on 2009-04-03
I think the desktop edition will be fine for your needs.  Unless you have a lot of users connecting to the server at the same time resuling in a high load average, you really don't need the server edition and its optimizations.

---

### Post by tr33m4n on 2009-04-03
I however would suggest the server edition... and if you need a gui, you can install different desktops from ubuntu repos. I'd recommend xfce, it is easy to understand and familiar. To install simply issue the command:

```
sudo aptitude install xfce4
```

Hope this helps

Cheers
Dan

---

### Post by hyper_ch on 2009-04-03
well, do you want to use that computer also as normal computer? if so, then I'd install desktop edition and add server stuff... if not, then I't put in a pure server (hence no gui at all)

---

### Post by albinootje on 2009-04-03
> **Nixie Pixel said:**
> 
Here are the tasks I want to accomplish:  I have 2 500 GB, 1 160 GB, and 1 80 GB HDDs, and I want to create a RAID array for storing documents, music, videos, and other data for the people on the (home) network. 
The server edition has a kernel which supports 4 Gb of RAM and more, but for that reason you wouldn't need that kernel in your setup since your machine has 2 Gb of RAM.
Here's a howto for setting up RAID1 in Ubuntu :
[http://howtoforge.org/how-to-install-ubuntu8.04-with-software-raid1](http://howtoforge.org/how-to-install-ubuntu8.04-with-software-raid1)
And another one [http://www.howtoforge.com/software-raid1-grub-boot-debian-etch](http://www.howtoforge.com/software-raid1-grub-boot-debian-etch) 
for an already running system.

I've read (somewhere) that it is recommended to let RAID have the full disks, but I've run software RAID1 without problems on several partitions besides non-RAID partitions since years.
In your case I would use only the two 500 Gb disks with software RAID1.

---

### Post by Nixie Pixel on 2009-04-03
Thanks for all the advice.  I currently had it set up with Ubuntu Hardy, and when I needed to administer it I would connect via the Remote Desktop application.  I'm not sure I'm comfortable running purely from the command line just yet, especially for things like searching for & downloading torrents, unless there are ways to do that via GUI on one of my desktops and just have the server pull down the info (is that even possible?).

Thanks again!

---

### Post by BkkBonanza on 2009-04-03
Hey, if you actually want to LEARN how to setup and run a server then DO it from the console. What you learn will help you run any future server out on the internet. I can tell from your blog that you are the type that wants to know...

---

### Post by NaOH on 2009-04-04
Ditto.  My needs fell well within the realm of desktop edition, but going with server has been the best tour de force in linux I've had yet.  It has changed my perception on home networking and I couldn't imagine getting by without a centralized hub anymore.  Good luck!

---

### Post by MJWitter on 2009-04-04
There are a few programs for downloading torrents onto a headless server and a remote GUI.  I use deluge.  It can run as a daemon and you can connect the GUI to the daemon locally, over the LAN or over the internet. It also has a web gui for when you arent on a pc you can install deluge on.

---

### Post by Nixie Pixel on 2009-04-04
With server edition would I be able to set up the server on one of the smaller hard drives, do some data transfers to get info off the 500GB drives, and then later set up RAID 1 on the 500 GB drives?

> **MJWitter said:**
> There are a few programs for downloading torrents onto a headless server and a remote GUI.  I use deluge.  It can run as a daemon and you can connect the GUI to the daemon locally, over the LAN or over the internet. It also has a web gui for when you arent on a pc you can install deluge on.
Great - would this allow me to set up torrent slaves with an old PC or two I have lying around?

Thanks!

---

### Post by hyper_ch on 2009-04-04
I run rtorrent on my seedbox :) lightweight yet powerfull. Controllable through a ncurses interface over SSH - there are allso web UIs available but never tried them.

---

### Post by Nixie Pixel on 2009-04-04
One more RAID question - the 500GB drives are IDE, do I need to put them on the same IDE controller, or can they be on different controllers, for RAID 1?

Thanks!

---

### Post by netztier on 2009-04-04
> **Nixie Pixel said:**
> With server edition would I be able to set up the server on one of the smaller hard drives

My server runs off a [4GB flash IDE]("http://www.transcendusa.com/Products/ModDetail.asp?ModNo=26&LangNo=0&Func1No=&Func2No=") module, which leaves all SATA ports free for Hard drives and DVD-ROMs.

Just watch out that you don't have write-prone file systems (or branches thereof) on that module itself - the write speeds are not quite blazing-fast. swap, /tmp, /home, /var and (if used) /srv might better be placed onto other disks.

regards

Marc

---

### Post by MJWitter on 2009-04-04
> **Nixie Pixel said:**
> 

Great - would this allow me to set up torrent slaves with an old PC or two I have lying around?

Thanks!

To be honest I don't know if this is possible.  You can add more than one host in Deluge's Connection Manager so that you can connect to other deluge instances on other servers.

Out of curiosity, why add more machines as opposed to more drives to the main server?

---

### Post by BkkBonanza on 2009-04-04
"torrent slaves", kinky.

But ya, torrent servers aren't usually cpu bound but limited by your internet connection. So more connections = more fun, but more machines isn't going to help.

---

### Post by Nixie Pixel on 2009-04-04
> **MJWitter said:**
> Out of curiosity, why add more machines as opposed to more drives to the main server?
Because I have a couple old computers that I wanted to play with, and I was reading about what one could do with them, and the first suggestion was "torrent slaves!" 

And hey, I like slaves ;)

But really I wasn't quite sure what to do with them, and since I already loaded one up with a bunch of HDDs and turned it into a server, I wanted to find ways to make old computers useful.  I really had no idea how much it would help, it just seemed like a fun project.

---

### Post by volkswagner on 2009-04-04
You can also look into [torrentflux]("http://www.torrentflux.com/") if you are interested in a web based torrent client/server.

---

### Post by albinootje on 2009-04-04
> **Nixie Pixel said:**
> the 500GB drives are IDE, do I need to put them on the same IDE controller, or can they be on different controllers, for RAID 1?

If you put IDE disks on the same cable connected to one controller you will probably get less performance than putting them on different controllers.
But RAID1 will give you a slight performance loss already with each simultaneous writing to the disks.

---

### Post by Nixie Pixel on 2009-04-04
This is going to be a home network, so I am not too concerned about performance.  I just want the file server/streaming media server/LAMP server to stay up if one hard drive fails, and other than that it isn't going to get hammered so it will be just fine, I'm sure.

Well I went for it, I installed Ubuntu Server on the 160 GB IDE drive (it kept giving me an error message when trying to activate the 80 GB SATA drive, for some reason, so for now I can't use it).  Unfortunately the 160GB drive was not my boot drive, so after changing my boot configuration in BIOS grub is giving me an error 17.

My first server challenge, heh.

---

### Post by Nixie Pixel on 2009-04-05
Since this is a brand new installation, do you think it would be easier just to reinstall than to try to troubleshoot this Error 17 problem?  I am having no luck so far.

---

### Post by albinootje on 2009-04-05
> **Nixie Pixel said:**
> Unfortunately the 160GB drive was not my boot drive, so after changing my boot configuration in BIOS grub is giving me an error 17.

There are a few bootloader experts on this forum (And there's this script which you can run to check all kind of information needed to troubleshoot), if you want you can start a new thread for this Grub problem, as it doesn't sound to me that a new install will fix this.

That script is mentioned here :
[http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1103159](http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1103159)
(boot_info_script*.sh)

---

### Post by bigbearomaha on 2009-04-05
> Will Ubuntu Server Edition help me?

No.  

only a qualified shrink might be able to help you now.

;)

---

