---
title: "nfs or samba for a file server"
date: 2012-01-15
forum: Server Platforms
---

### Post by Jennifer29 on 2012-01-15
OK I have had my file server set up for a while now it uses samba but there are no windows pc on my network and there won't ever be the transfer speed on my server is slow it takes about 15 minutes to transfer a 700mb avi file.I don't think it should be that slow i traced the problem down and samba isn't configured right so my question is I'M never going to have a windows pc on my network so would it be better for me to use samba or nfs and how do i configure it.I'M using Ubuntu desktop and ubuntu Server 11.10 with 512  mb of ram.
thanks

---

### Post by papibe on 2012-01-15
Hi Jennifer29.

In my experience, NFS is noticeable faster that Samba. [Here]("https://help.ubuntu.com/8.04/serverguide/C/network-file-system.html")'s a tutorial on how to set up NFS.

In any case, Samba isn't that slow (~0.8MB/s if 700MB takes 15min). That looks more like a weak wireless connection. Over a wired connection you should get at least around 8-9 MB/s.

Hope it helps, and let us know how it goes.
Regards.

---

### Post by Vegan on 2012-01-15
I have used SAMBA and its a very powerful when used in a mixed Windows and Linux shop

NFS is not as widely used

---

### Post by Jennifer29 on 2012-01-15
Thank you for the super quick reply papibe

I'M on a wired connection and it takes that long I read where if samba isn't configured right it would or could slow the transfer speed down.I was thinking nfs as well.nfs sounds better to me but I'M new to linux and ubuntu so i didn't know.

Thank you

---

### Post by Lucky. on 2012-01-15
A couple of years back I started down the NFS road.  Native security with NFS is practically nonexistent.  This led me down the path of Kerberos, which led me down the path of DNS.  Fun learning experience and it gave me a lot of respect for how graceful Active Directory is implemented.  But in the end it was too much personal time & overhead for a home server and my wife was ticked off every time something went down.  I returned to Samba and never looked back.

---

### Post by bubylou on 2012-01-16
.

---

### Post by bubylou on 2012-01-16
I have never used nfs before but samba has always worked perfect for me. You could give NFS a try to see if samba was the cause of your problems. Also ignore my above post.

---

### Post by varunendra on 2012-01-16
If file sharing/storage is all this server has to do, I'd recommend [FreeNAS]("http://www.freenas.org/category/version-comparison") (you name a file-system or protocol, and it has support for it). For a 512MB RAM, you'll need its older [version- 7.2 series]("http://sourceforge.net/projects/freenas/files/FreeNAS-7-Stable/") as the latest one (8x series) requires a lot of RAM and entire drive on which it gets installed.


But if the server is doing (or will be doing) anything more than serving/storing files, ignore the above suggestion.

---

### Post by a2j on 2012-01-16
I use NFS on my "home file server". Linux and Mac. windoze is only virtual and not needed to get files from server. I used to have samba. but with NFS, I see 200 MB/s speeds. I like NFS.

---

### Post by HermanAB on 2012-01-16
Well, setting up NFS is super simple compared to Samba.  You only need ONE line of configuration on the server and ONE line of configuration on the clients.  Most anyone with better than a room temperature IQ should be able to do a NFS setup.

[http://www.aeronetworks.ca/howtos/nfs-howto.html](http://www.aeronetworks.ca/howtos/nfs-howto.html)

---

### Post by Morbius1 on 2012-01-16
> **HermanAB said:**
> Well, setting up NFS is super simple compared to Samba.  You only need ONE line of configuration on the server .... 
A one line configuration of a samba share:
> net usershare add documents /home/morbius/Documents "morbius documents" username:F guest_ok=y> ... and ONE line of configuration on the clients.And one line of configuration on the client:
> gvfs-mount smb://server/documentsOF course you don't have to do this in the terminal as all of this is incorporated into Nautilus.

If you want to compare NFS and Samba on say ... transfer speeds then that is legitimate. But don't compare them on ease of setup. In fact it's really a stretch to compare them at all since they are in different categories.

Samba is a browsable protocol and NFS is not. Almost all of the problems in this forum relate to browsing for samba shares instead of accessing them directly by ip address:
```
smb://192.168.0.100/documents
```

---

### Post by SeijiSensei on 2012-01-16
NFS preserves Unix file permissions which, to me, makes it the preferred choice for Unix-to-Unix file sharing.  I use both NFS and Samba on the same server so I can access my shared files from both Linux and Windows.  In an all-Unix environment, I'd only run NFS.

---

### Post by Jennifer29 on 2012-01-16
Thank you all for your answers I'M about to setup nfs.Samba is just taking a long time to transfer files.I looked at freenas before but with the ram that it needed and not knowing if I would add any more services on the server ubuntu server just fit what I was looking for.

Thank you all for your help.

---

### Post by snek on 2012-08-27
Personally I'd probably also go for NFS in a Linux only environment. However I am stuck with 3 windows pc's at home and thus use Samba. With 12.04 I have seen a dramatic improvement in speed compared to 8.04, speeds usually start at 120MB/s over a gigabit line dropping down to about 75MB/s (which is still basically HDD speed). On 8.04 it was only doing about 30MB/s, and I noticed this on a corp server as well which has 6x 500GB SATA in RAID5 on an Areca controller.

Right now I am running Manjaro Linux XFCE and speeds are even more stable than before due to less load and updated version of samba (3 not 4). I have yet to experiment with samba4, but I needed my server up quickly and had a backup of the smb.conf (which is just the default config with a few shares added).

Must say my homeserver is pretty ok though:

[LIST]
[*] Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
[*]AMD Athlon(tm) II X2 240e Processor
[*]2x 2TB Western Digital Green
[*]2x 1TB Western Digital Blue in mdadm RAID1
[*]1x 500GB Western Digital Blue
[/LIST]
 
```

             total       used       free     shared    buffers     cached
Mem:          ***7990       ***1189       6800          0         62        758
-/+ buffers/cache:        ***368       7621***
Swap:          517          0        517

```:guitar:

---

### Post by kgatan on 2012-08-29
If its server to server and both are *nix machines there is no reason to use samba instead of nfs.
For a user environment I'd use samba because its easier to set up. Sure its easy to get nfs working but if you want it secure then there is a lot more to do including configuration on all clients.

Towards windows machines I have no problems with samba36 and almost saturate a gigabit network. There is however some tweaking needed.

If you want to make managing shares and users easier you can always use webmin.

---

### Post by RoosterHam on 2012-11-22
So how has your NFS test gone?

I don't think that your speed issues are directly to related to your choice of either Samba or NFS. In my experience, given the same attention, there are difference between the two when you keep in mind performance-versus-features, but the numbers you describe here are beyond anything that seems normal.

 Both Samba and NFS do require some attention to configure correctly to your network and role, and for fine tuning and tightening security. If you don't require the features that Samba provides that NFS doesn't, it may be a very good fit for your situation.

The only time I have had an issue that showed for one but not the other may have other causes and I simply didn't want to investigate, and so shifted from samba to nfs. I had a samba share, a directory that contained all my digital videos, to play from my wifi mediacenter. 600+ files in an xfs partition.

Samba worked very well. 2 months later, my mediacenter told me I only had 200 files left and wouldn't play half of them. logging in and browsing the share showed corrupted filenames and I feared my hard drive may be failing. I logged in physically to the server, and an 'ls' listed all files, in perfect/original condition. With little time to investigate and 'other-half' and 'house-mate' both rather upset at losing the collection of movies (apparently they have forgotten what an optical disc is already) so instead of spending time investigating, it was in my best interest to simply configure an NFS daemon and export.

Before this happened, Samba worked well over wifi but importantly, with the right configuration of the entire network, but my complete disinterest in supporting anyone with a Microsoft OS on my network I had already considered avoiding Samba on my home network.

Whatever you use, set it up properly for you. The highest security precautions that YOU can deal with. The right settings at every part of YOUR network.

---

