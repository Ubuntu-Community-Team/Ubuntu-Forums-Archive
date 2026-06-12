---
title: "Torrent server..."
date: 2011-05-09
forum: Server Platforms
---

### Post by Xeneth on 2011-05-09
I have a box running ubuntu server 11.04 at the moment.

What torrent clients are easy to use from CLI?

The server is my main storage/backup device, and have it setup to be mounted on my laptop through ssh from the net.  Looking for something that I can keep going, but be able to control through either terminal or a gui client on my laptop(Ubuntu 11.04)/desktop(Windows7)

Thanks.

---

### Post by rubylaser on 2011-05-09
I've used both Deluge and Transmission daemon.  Both of them have CLI versions with web frontends. They've both worked well for me in the past.

---

### Post by Cyked on 2011-05-09
I like deluge and use CLI exclusively for it.  To keep is simple I just set the config in gui to auto load torrents from a dir then just move torrent files into that dir from CL.

---

### Post by arrrghhh on 2011-05-09
rtorrent.  As far as I'm concerned, the **only** CLI-based torrent client...

With various front-end options like rutorrent, it really is the best solution IMHO.  Extremely flexible, and runs with an extremely small footprint - I've heard of people running 9,000+ torrents thru a single rtorrent instance.

---

### Post by Lars Noodén on 2011-05-10
btpd is a good text-only torrent app.

---

### Post by Xeneth on 2011-05-10
Thanks youall.  I use transmission on my laptop, so I set that upon the server.  Only down side is transmission deletes the torrent files.  Can I add to the config file to simply save them to another spot?

---

### Post by dfreer on 2011-05-10
I know you specified console based bittorrent clients, but have you ever seen torrentflux or torrentflux-b4rt? I've used them before and they work great.

---

### Post by BkkBonanza on 2011-05-10
I use Deluge as well and it's been very good. It has both a web front end and a gnome app, as well as some CLI control. I use the gnome app - it just connects to a given port and gives you full remote desktop functionality. It has quite a few options for managing the torrent files regarding moving files/deleting so you may find it better than Transmission. I know Transmission was std with Ubuntu but I've always found Deluge to be a better and more complete tool much akin to uTorrent on Windows.

---

### Post by kentish on 2011-05-18
I use rtorrent and rutorrent for a web interface, it's ok to set up and pretty light weight.

Rtorrent
[http://libtorrent.rakshasa.no/](http://libtorrent.rakshasa.no/)

Rutorrent
[http://code.google.com/p/rutorrent/](http://code.google.com/p/rutorrent/)

Although reading some of these posts I might try deluge.

---

### Post by Groodles on 2011-05-19
I'm also a deluge user.  The Web GUI is very good and it's easy to use.

I've also used rtorrent with rutorrent.  While powerful, it's not so simple to configure for an inexperienced user.

---

### Post by MarisO on 2011-05-19
I use rtorrent and gnu screen terminal session manager

---

### Post by arrrghhh on 2011-05-19
> **Groodles said:**
> I'm also a deluge user.  The Web GUI is very good and it's easy to use.

I've also used rtorrent with rutorrent.  While powerful, it's not so simple to configure for an inexperienced user.

rtorrent+rutorrent was a little more difficult to setup than deluge, but for me the effort was worth it.  IMHO it's worlds ahead of deluge - at least from the last time I used it.  rtorrent is **so** flexible.

---

### Post by Thegmandrive on 2011-05-19
> **Xeneth said:**
> Thanks youall.  I use transmission on my laptop, so I set that upon the server.  Only down side is transmission deletes the torrent files.  Can I add to the config file to simply save them to another spot?   I don't really see a need to save the actual torrent files I only care about what I'm actually downloading :)

I use transmission and have actually been asking a ton of questions about Transmission setup and some other port related issues at thread [HTML]http://ubuntuforums.org/showthread.php?t=1754441
[/HTML][[COLOR=#d40000]**BkkBonanza**[/COLOR]]("http://ubuntuforums.org/member.php?u=550406") Has been extremely helpful and patient in answering my questions, seeing as I am a complete noob. 

You may want to check out that thread.

---

### Post by Xeneth on 2011-05-22
Figure I would give an update.  First in case other people googleing for answers, and second incase some of you have some Idea's.

I started out with Transmission using the web UI, and for simply transfer, it was quite good.  Not very good for managing the torrents though.  Good for straightforward.  Also I cannot create my own torrents.

I then tried setting up deluge.  I got it working with webUI, but a couple things would not work right.  
First is it seems that it ignored my settings for ports.  I entered it into the webUI, but when I did netstat, the connections where everywhere but what I chose.  
Second the torrent speeds where not what I was seeing in transmission.  I think that was mainly due to the ports.  I have a 10Mb/s down and 1.5Mb/s up connection, and I never seemed to get out of the double digets Kb/s but once in a while.
Third, even after doing everything I could find online, the deluge-daemon would never listen to any ports for remote connections.  I know the webUI is limited, so  I wanted to connect using the gui client on my laptop to manage it and to create torrents.  Because it never listened, I could never connect.  Most things have a .config file I can use to set ports and other settings., but I could find nothing on the web about how to do this with deluge.  Only found that settings where in ~/.configure/, but no details.  

I am going to try out rutorrent next to see if that's what I want.  If not, I may be stuck with transmissioncli.

---

### Post by dfreer on 2011-05-22
> **Xeneth said:**
> 

I am going to try out rutorrent next to see if that's what I want.  If not, I may be stuck with transmissioncli.

What about [torrentflux-b4rt]("http://tf-b4rt.berlios.de/home.html")?

---

### Post by HighCommander540 on 2011-05-22
> **dfreer said:**
> What about [torrentflux-b4rt]("http://tf-b4rt.berlios.de/home.html")?

TorrentFlxu has been defunct for a long time. No DHT or Peer Exchange. I tried it a few years ago and it is still the same version since then.

I use the uTorrent CLI version for Linux servers. It starts up the uTorrent client and auto-runs the WebUI. Very nice has password and everything.

Then I have peerGuardianLinux running as my peer blocker (yeah I know everyone wants to tell me it does nothing).

---

### Post by arrrghhh on 2011-05-23
> **HighCommander540 said:**
> TorrentFlxu has been defunct for a long time. No DHT or Peer Exchange. I tried it a few years ago and it is still the same version since then.

I use the uTorrent CLI version for Linux servers. It starts up the uTorrent client and auto-runs the WebUI. Very nice has password and everything.

Then I have peerGuardianLinux running as my peer blocker (yeah I know everyone wants to tell me it does nothing).

Doesn't that run uTorrent under and instance of WINE?

rtorrent+rutorrent and done IMHO.  

TorrentFlux(-b4rt) was horrid even back in the day - it would spawn a separate process for **each** torrent.  So even if you had 10 torrents running, that means 10 separate processes.  I wasn't a big fan of this concept, plus it seemed that the webUI was very disconnected from the underlying applications... bleh.  Stay away!

---

