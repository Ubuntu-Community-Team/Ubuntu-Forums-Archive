---
title: "Why use bittorrent to download 9.10? Curious"
date: 2009-11-05
forum: The Cafe
---

### Post by Tholley on 2009-11-05
Just want to know what the advantage of downloading the new version using bittirrent
as to just downloading from the Ubuntu website?

---

### Post by philinux on 2009-11-05
Spreads the bandwidth about and is resumable.

---

### Post by Darce on 2009-11-05
Eases the load on the Ubuntu servers, and probably gets you a faster DL   :)

---

### Post by gdlx on 2009-11-05
> **Darce said:**
> Eases the load on the Ubuntu servers, and probably gets you a faster DL   :)
I tried bit torrent only once and the download time was so much greater than a conventional download that I have not wanted to try it again. Maybe I'll give it another try. 
I have been using wget and have been very satisfied with the download times.

---

### Post by MelDJ on 2009-11-05
to  not make the server be too overloaded. and if more people share, the faster it becomes

---

### Post by fede82 on 2009-11-05
> **gdlx said:**
> I tried bit torrent only once and the download time was so much greater than a conventional download that I have not wanted to try it again. Maybe I'll give it another try. 
I have been using wget and have been very satisfied with the download times.

Speed on bittorrent depends on many factors. ie, if your router not properly configured or if you are downloading some not-so-new/popular file your download speed will be very poor. Also many ISP is filter bittorrent transfers and throttles them down.

However if your ISP is cool and you´re downloading something hot (like Ubuntu on release day) you´re pretty sure going to get very VERY high speeds.

---

### Post by marshmallow1304 on 2009-11-05
In addition to allowing for very high speeds (depending on configuration and number of seeds & leeches) and easing the load on the servers, bittorrent clients perform hash checks while downloading, which makes it much more difficult to end up with a corrupted iso image.

---

### Post by sadaruwan12 on 2009-11-05
Bittorrent speed depend on many things this is a shared thing and it doesn't relay on a one single server to deliver the package.

---

### Post by lovinglinux on 2009-11-05
> **gdlx said:**
> I tried bit torrent only once and the download time was so much greater than a conventional download that I have not wanted to try it again. Maybe I'll give it another try. 
I have been using wget and have been very satisfied with the download times.

See [BitTorrent optimization and troubleshooting guide](http://ubuntuforums.org/showthread.php?t=1259923)

---

### Post by ikisham on 2009-11-05
The only two reasons I can see for downloading from the Ubuntu servers instead of from a torrent in the release day and some days after are either if your Internet Provider blocks torrent (which I've just heard about) or ignorance (not knowing that the torrent exists).

---

### Post by kyuubi777 on 2009-11-05
torrents #$%^)&* rock!!! .. i'd torrent college education if it was possible! :D

---

### Post by t0p on 2009-11-05
I downloaded the 9.10 live cd and alternate install cd isos over bittorrent the other day, and the speed was blistering.  Much faster than when I got 9.04 through the regular route.  So there's a selfish motive as well as the selfless one.  Being a saint is so cool!!  :p

---

### Post by ST3ALTHPSYCH0 on 2009-11-05
> **ikisham said:**
> The only two reasons I can see for downloading from the Ubuntu servers instead of from a torrent in the release day and some days after are either if your Internet Provider blocks torrent (which I've just heard about) or ignorance (not knowing that the torrent exists).

Reason #3: upgrading (which is highly discouraged anyway)

---

### Post by Tholley on 2009-11-05
>  
The only two reasons I can see for downloading from the Ubuntu servers instead of from a torrent in the release day and some days after are either if your Internet Provider blocks torrent (which I've just heard about) or ignorance (not knowing that the torrent exists).

 
igorance... yep that would be me... :-s

---

### Post by Tholley on 2009-11-05
oops... I just realized I mispelled download on the title...:-\"

---

### Post by x C0MMAND0 x on 2009-11-05
1. It is much faster assuming there are enough seeders (which I have never had an issue with.

2. You can pause and resume it later

3. Torrents check the files so that it is matched bit for bit so whatever you download won't be corrupted. (It can become corrupted if you burn it to a disc at too high of a speed though)

---

### Post by bribera on 2009-11-05
You can get the best of both downloading worlds if you use a client that supports .metalink files. Metalink files allow a content provide to specify **many** different download sources - so you can simultaneously download from a BitTorrent swarm and from the Ubuntu server system.

There are a number of clients that support metalinks; I've used aria2 with success. When I grabbed the Karmic Xubuntu install CD, I did it like this:

```
sudo apt-get install aria2
aria2c http://cdimage.ubuntu.com/xubuntu/releases/karmic/release/xubuntu-9.10-desktop-amd64.metalink
```

Read more at: [https://wiki.ubuntu.com/metalink](https://wiki.ubuntu.com/metalink)

---

### Post by madhi19 on 2009-11-05
I use it because it faster and I love the fact that am downloading a legit torrent. Kind of turn all that crap we take from ISP's throttling and shove it down their a..!

---

### Post by wrgb2 on 2009-11-05
Because it helps take the load off the servers.  Bittorrent uses other pcs all over the place to upload part of what they're downloading, thus reducing the load on the server.

---

### Post by hoppipolla on 2009-11-05
yeah, it's easier on the Ubuntu servers that way, and it's faster :)

---

### Post by markbuntu on 2009-11-05
I downloaded a Karmic iso in less than 4 minutes using torrent.

---

### Post by geoken on 2009-11-05
The results from my unscientific test are as follows;

Initiated direct http download, after about 20 seconds never saw a speed above 320KB/s.

Fired up the torrent, it took a few seconds to get up to speed but within a minute was downloading around 800KB/s.

Shut down the http download, and within 30 seconds had the torrent shoot up even higher to 1100KB/s

---

### Post by drawkcab on 2009-11-05
> **marshmallow1304 said:**
> bittorrent clients perform hash checks while downloading, which makes it much more difficult to end up with a corrupted iso image.

This is the primary reason I use bittorrent to pull my .iso files.

---

### Post by Grifulkin on 2009-11-05
Torrents are awesome.

---

### Post by Tholley on 2009-11-18
ok... I just needed to understand bittorrent better. I have used peer to peer (Limewire) and thought it all the same. 
 
Now by using Deluge, I re-downloaded 9.10 over again (since I thought the first one was flawed) and it worked great.
 
Thanks for all the great replies! :D

---

