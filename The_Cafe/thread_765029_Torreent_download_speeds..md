---
title: "Torreent download speeds."
date: 2008-04-24
forum: The Cafe
---

### Post by happysmileman on 2008-04-24
I've just started downloading the KDE4 version of Kubuntu using BitTorrent, and to be honest I haven't been getting good speeds, I have an average download speed of under 2KB/s and reached a maximum of about 15.

What are your experiences with torrents today? In all versions, would be interesting to see how jmuch faster regular Ubuntu is to something like Edubuntu.

(While I typed this my speeds went up a bit, now it seems to be averaging about 5KB/s and reached a max of about 25)

EDIT: Yes I do realise that I might just be unlucky, so I'm not claiming that the torrent is very slow or anything, and I also understand that for a long while there will be much more leechers than seeders, I'm not complaining

---

### Post by Lostincyberspace on 2008-04-24
Also who is your isp they might be throttling.

I know mine does but I am getting quite a bit better speeds than you. 50 Kb/s

---

### Post by Amstell on 2008-04-24
I just finished downloading via torrent and was in the speed of 800.  Only took about 10 minutes to download.  Cheers

---

### Post by Kingsley on 2008-04-24
Which torrent client do you use? Deluge works perfectly out of the box for me on my university's firewalled network. I think it has something to do with inbound and outbound encryption.

---

### Post by Nano Geek on 2008-04-24
Limiting your upload speed makes the download go a lot faster.

---

### Post by Officer Dibble on 2008-04-24
Could you post some of these torrent links here, please? :)

---

### Post by happysmileman on 2008-04-24
> **Lostincyberspace said:**
> Also who is your isp they might be throttling.

Some regional Irish one, I know they don't throttle since I can regularly (including now), get my full D/L limit on a torrent (though that's only 512kbps).

Speed seems to have shot up after I did a manual announce.

> Could you post some of these torrent links here, please? 

The torrent files should be listed in same directories as the actual ISO downloads on the main servers.

---

### Post by Kvark on 2008-04-24
> **Officer Dibble said:**
> Could you post some of these torrent links here, please? :)
[http://torrent.ubuntu.com:6969/](http://torrent.ubuntu.com:6969/)

Just downloaded 64bit Kubuntu 8.04 in 4 minutes and 14 seconds with the torrent, the average speed was 2.7MB/s and the top speed 5.6MB/s, fastest torrent I've ever seen.:)

---

### Post by insane_alien on 2008-04-24
torrent speeds are likely suck because there are so many people downloading and not enough seeding. this will improve with time, be patient and seed so others don't have the same problem.

---

### Post by Teber on 2008-04-24
took me a little over 30 mins to get ubuntu 32 bit version. still uploading now

---

### Post by hyper_ch on 2008-04-25
I've seeded at 8.5 MByte/s - at least that's the max. I've seen on my server...

I have seeded now over 560 cd-images ;)

---

### Post by vishzilla on 2008-04-25
The ubuntu tracker isn't responding now. What about you guys?

---

### Post by hyper_ch on 2008-04-25
use DHT

---

### Post by vishzilla on 2008-04-25
> **hyper_ch said:**
> use DHT
Ah, using Transmission. No wonder. Thanks!

---

### Post by hyper_ch on 2008-04-25
no, using rtorrent ;)

[IMG]http://www.sjau.ch/rtorrent_hardy.png[/IMG]

--> that was about 2h ago

---

### Post by vishzilla on 2008-04-25
> **hyper_ch said:**
> no, using rtorrent ;)

--> that was about 2h ago

I meant i was using Transmission!

---

### Post by hyper_ch on 2008-04-25
you should start using rTorrent then ;)

Transmission does not support DHT?

---

### Post by anaconda on 2008-04-25
hmm.. interesting.. 

I am getting about 90-100kB/s with my 1MB 3G connection
Which is really really good, because I am behind an ISP firewall, from which I cant even open any ports that ktorrent needs..

And getting almost the max speed anyway!! The best I can get are 125kB/s..

---

### Post by vishzilla on 2008-04-25
Nope it doesn't. I am actually on a Fresh Hardy install. Downloading Xubuntu ISO for a friend. I will try out rtorrent

---

### Post by hyper_ch on 2008-04-25
if you wanna try out rtorrent you also should use it in conjunction with screen ;)

And also recommended to get the latest svn version of rtorrent ;) I can give you a howto for that ;)

---

### Post by vishzilla on 2008-04-25
> **hyper_ch said:**
> if you wanna try out rtorrent you also should use it in conjunction with screen ;)

And also recommended to get the latest svn version of rtorrent ;) I can give you a howto for that ;)

Sure

---

### Post by regomodo on 2008-04-25
got my torrent link from canonical. Speed seemed to vary a lot, sometimes over 1MB/s to 200kB/s. Could be because i ignore unencrypted connections

---

### Post by hyper_ch on 2008-04-25
> **vishzilla said:**
> Sure

need to adjust it to hardy:  [http://www.howtoforge.com/compiling_rtorrent_from_svn_on_ubuntu_gutsy_gibbon](http://www.howtoforge.com/compiling_rtorrent_from_svn_on_ubuntu_gutsy_gibbon)

But it's all the same...

A example .rtorrent.rc can be found in /usr/share/doc/rtorrent/examples/rtorrent.rc

Just copy it to /home/user/.rtorrent.rc

In there uncomment the DHT and also set other options. Set max. Upload to about 85-90% of your max upload speed...

Also set a  session folder and I'd recommend to set a watchfolder also (and uncomment the auto-add for the watchfolder in .rtorrent.rc)

Here's a little starter guide that made me use rtorrent: [http://kmandla.wordpress.com/2007/05/02/howto-use-rtorrent-like-a-pro/](http://kmandla.wordpress.com/2007/05/02/howto-use-rtorrent-like-a-pro/)

The official rtorrent homepage is [http://libtorrent.rakshasa.no](http://libtorrent.rakshasa.no)


And I recommend running rtorrent in a screen. A small introduction to screen is here:  [http://jmcpherson.org/screen.html](http://jmcpherson.org/screen.html)

---

### Post by vishzilla on 2008-04-25
**@hyper_ch**: thanks a million. i will try it out!!

---

