---
title: "BitTorrent Clients"
date: 2006-11-29
forum: The Cafe
---

### Post by XVampireX on 2006-11-29
Hey, lets start a little topic (This topic) where each can review bittorrent clients they tried, how it works for them and perhaps even wishlists for each and basically, everything about bittorrent clients.

Here's a few I tried:

Azureus (3/5):
--------
It takes alot of ram and system resources, the download speeds are more stable than in other clients and sometimes can get very good speeds, some features are not obvious, while for some, default features/settings are just enough, at least for me it was enough, until I started looking for better clients.

BitTorrent (3/5):
----------
Uses python, a little overhead, more with a GUI (Sadly, a GTK1.2 GUI) but seems like curses is enough for some people and is quite lightweight when it comes to resources. Not the easiest to customize it, doesn't have multi torrent management design/GUI. The speeds are as much as you'd expect it to be, not much slower than azureus, maybe at times even faster.

BitTornado (3.5/5):
----------
Mostly the same as BitTorrent but is easier to customize via GUI and the GUI is now using GTK 2 instead of 1.2.

KTorrent (4/5):
--------
When I first started using it, I thought it was rather buggy and downloaded rather slow, but in a recent version (2.1beta1) it was rather buggy (read: CPU/MEM leaks), and they just fixed a bug that caused corruption of data during download, but they add new features that some people really wanted like feed downloader. The integration of KTorrent with KDE seems good, but that doesn't mean you can't use it with Gnome or any other environment, but you still need kdelibs. KTorrent download speeds are not the best but they are getting to a good point. Something that I would still like for KTorrent is a search parser, something that exists in qBitTorrent (Upcoming section).

qBitTorrent (4.5/5):
-----------
I first heard about qBitTorrent through digg, but when I tried it, I thought (at the time) it was better than KTorrent download wise, so I gave it good regards on digg, turns out that even now, qBitTorrent seems to have a weird system, most of the time it downloads fairly slow, but when it goes up, it goes UP! The Client is based on libtorrent from Rasterbar (Not the one with rtorrent), and the GUI is based on Qt4.2 so the GUI looks good. It seems that qBitTorrent as of right now tries to get the bloat away, and in that also hides alot of information you'd rather expect from a bittorrent client, such as statistics of peers. But it's all good, you don't need that. The Search Engine parser allows it to list torrents and give you direct links to it instead of opening it up via KHTML KPART, a very nice feature! I would recommend this client to people who don't mind waiting the few seconds/minutes/hours to get great speeds. Also, libtorrent SVN just added a few features such as Peer Exchange and better Quota Management feature, that would mean for greater and more stable/predictive download speeds.

Deluge (1/5):
------
(Sorry if I offended the developers, it's just my personal view, that's the point of this topic)
I tried the RC, but didn't use it for too long, it seems that it's still feature incomplete and the fact that it's based on Python gave it an unnecessary overhead. It's also based on libtorrent, the same one qBitTorrent uses. Some tabs take a bit to respond (I.E: refresh the information in them) and it unnecessarily tells the user that they have to forward ports. The plugin system is the only thing that I thought was very nice. Also, keep in mind that when I first tried Deluge it failed to connect to dattebayo tracker, so that gave me this little "I don't like this" feeling towards Deluge, though maybe at some point in time I should give deluge another try to see if it improved and if it's as I expected of it to become more bloated (resources wise) or if it would keep about the same as it is now. Again, sorry if I offended the developer.

For those people who want to try a libtorrent client based on gtk should give BTG a try, it's using C++ due to the gtkmm interface. Actually, BTG is just a daemon, it has 3 interfaces, GTKmm, curses, web. Here's the link: [http://btg.berlios.de/](http://btg.berlios.de/)
I haven't given it a try, personally, but if you want something that's libtorrent and doesn't have python overhead and has several interfaces for it as well as gtkmm interface for it (If you use Gnome or XFCE or QtCurve style KDE). The installation requires compilation but compilation doesn't hurt, I already compiled quite a few pieces of software ;)

---

### Post by jpkotta on 2006-11-29
I used to use BitTornado, because it was easy to use and small and fast.  But It got to be a PITA when I was down/uploading many torrents.  I have come to the conclusion that any good client will handle many torrents at once.  I think there's a way for BitTornado to do this, but I like Azureus better. 3/5

Opera's torrent client sucks.  1/5

The official client is too minimal in features for me. 1/5

I love Azureus.  I have plenty of memory for it to chew up, and it works great. 5/5

---

### Post by drphilngood on 2006-11-29
The only two I really like are KTorrent and Azureus and give both of them 4/5.  I can´t really put my finger on any area that either are lacking in but I suppose there is always room for improvement.

---

### Post by mzilhao on 2006-11-29
you should check [Transmission]("http://transmission.m0k.org/") out.
it's working great for me...

---

### Post by Polygon on 2006-11-29
its not really fair to judge deluge yet becuase its like nowhere near completion for a final version...

---

### Post by guX on 2006-11-29
I use Azureus, but I don't run a JVM, I use the gcj compiled package. You can install this by doing [FONT="Courier New"]sudo apt-get install azureus-gcj[/FONT]. It works fine for me, I've never had any major problems with it. There's definitely room for improvement, it's not the fastest and most responsive app, but it's certainly usable.

---

### Post by hotbrainz on 2006-11-29
Azureus gets a 4/5 from me too. I do not do any complex configuratios. There is ample memory and it works like a charm with simple basic settings.

---

### Post by Josh1 on 2006-11-29
I use Azureus, allows me to download my fully legal applications that have no copyright and is opensource... :rolleyes:

---

### Post by Super King on 2006-11-29
Transmission for me, very lean and basic but that's all I want/need in a Bit Torrent client.

---

### Post by XVampireX on 2006-11-29
I know deluge is not ready for final release, but lets not forget that qBitTorrent is not at the highest point release ;)

Actually, me thinks that with the latest libtorrent SVN it would work really really good, then we just have to choose some interface that we like and just use it, no need to argue which libtorrent client is the best as everyone would use their own preferred interface with the same core.

---

### Post by phatzmb on 2006-12-02
it seems to me azureus has (for many years now) had a big lead on all other clients in terms of configuration options).

my main issue is port forwarding, and without azureus's options for specifying the ip you send to trackers, and binding to a local ip address, i can't properly solve my NAT issues.

most other clients let you do a few basic things, which for me at least don't fully solve the NAT traversal.

---

### Post by xopher on 2006-12-02
4/5 for Azureus

^ It has great features, it works great, it's semi fast, the only downside is the huge chunk of RAM it consumes, often in one nasty bite ;)

---

### Post by RAV TUX on 2006-12-02
> **XVampireX said:**
> Hey, lets start a little topic (This topic) where each can review bittorrent clients they tried, how it works for them and perhaps even wishlists for each and basically, everything about bittorrent clients.

Here's a few I tried:

Azureus (3/5):
--------
It takes alot of ram and system resources, the download speeds are more stable than in other clients and sometimes can get very good speeds, some features are not obvious, while for some, default features/settings are just enough, at least for me it was enough, until I started looking for better clients.

BitTorrent (3/5):
----------
Uses python, a little overhead, more with a GUI (Sadly, a GTK1.2 GUI) but seems like curses is enough for some people and is quite lightweight when it comes to resources. Not the easiest to customize it, doesn't have multi torrent management design/GUI. The speeds are as much as you'd expect it to be, not much slower than azureus, maybe at times even faster.

BitTornado (3.5/5):
----------
Mostly the same as BitTorrent but is easier to customize via GUI and the GUI is now using GTK 2 instead of 1.2.

KTorrent (4/5):
--------
When I first started using it, I thought it was rather buggy and downloaded rather slow, but in a recent version (2.1beta1) it was rather buggy (read: CPU/MEM leaks), and they just fixed a bug that caused corruption of data during download, but they add new features that some people really wanted like feed downloader. The integration of KTorrent with KDE seems good, but that doesn't mean you can't use it with Gnome or any other environment, but you still need kdelibs. KTorrent download speeds are not the best but they are getting to a good point. Something that I would still like for KTorrent is a search parser, something that exists in qBitTorrent (Upcoming section).

qBitTorrent (4.5/5):
-----------
I first heard about qBitTorrent through digg, but when I tried it, I thought (at the time) it was better than KTorrent download wise, so I gave it good regards on digg, turns out that even now, qBitTorrent seems to have a weird system, most of the time it downloads fairly slow, but when it goes up, it goes UP! The Client is based on libtorrent from Rasterbar (Not the one with rtorrent), and the GUI is based on Qt4.2 so the GUI looks good. It seems that qBitTorrent as of right now tries to get the bloat away, and in that also hides alot of information you'd rather expect from a bittorrent client, such as statistics of peers. But it's all good, you don't need that. The Search Engine parser allows it to list torrents and give you direct links to it instead of opening it up via KHTML KPART, a very nice feature! I would recommend this client to people who don't mind waiting the few seconds/minutes/hours to get great speeds. Also, libtorrent SVN just added a few features such as Peer Exchange and better Quota Management feature, that would mean for greater and more stable/predictive download speeds.

Deluge (1/5):
------
(Sorry if I offended the developers, it's just my personal view, that's the point of this topic)
I tried the RC, but didn't use it for too long, it seems that it's still feature incomplete and the fact that it's based on Python gave it an unnecessary overhead. It's also based on libtorrent, the same one qBitTorrent uses. Some tabs take a bit to respond (I.E: refresh the information in them) and it unnecessarily tells the user that they have to forward ports. The plugin system is the only thing that I thought was very nice. Also, keep in mind that when I first tried Deluge it failed to connect to dattebayo tracker, so that gave me this little "I don't like this" feeling towards Deluge, though maybe at some point in time I should give deluge another try to see if it improved and if it's as I expected of it to become more bloated (resources wise) or if it would keep about the same as it is now. Again, sorry if I offended the developer.

For those people who want to try a libtorrent client based on gtk should give BTG a try, it's using C++ due to the gtkmm interface. Actually, BTG is just a daemon, it has 3 interfaces, GTKmm, curses, web. Here's the link: [http://btg.berlios.de/](http://btg.berlios.de/)
I haven't given it a try, personally, but if you want something that's libtorrent and doesn't have python overhead and has several interfaces for it as well as gtkmm interface for it (If you use Gnome or XFCE or QtCurve style KDE). The installation requires compilation but compilation doesn't hurt, I already compiled quite a few pieces of software ;)

I prefer KTorrent (4.36789/5.0)

---

### Post by somuchfortheafter on 2006-12-02
I am a big fan of bit tornado combined with the torrenflux package, I can use my server to house all my torrents and schedule downloads remotely.

---

### Post by Christmas on 2006-12-02
I use KTorrent, version 2.0.3. I only tried two other clients, both GUI:

**Opera's integrated client** - It is useful indeed if you decide to use it as your single client, but it's getting harder to work with if you want only to download the .torrent file, not the whole content. For example, after a download began and you want to cancel it, it will delete the contents of what was downloaded until then plus the torrent file, so you'll have to download the .torrent file again using "Save Target As". It bothered me so I stopped using it. But again, for a person who uses Opera as the primary browser it could be a good choice.

The other client which I tried was **BitTornado**. In my personal opinion this is a very good client if you plan to download a torrent once in a while, say once a year. Otherwise (at least this was how it worked the version from the Debian 3.1 repositories, I haven't checked it lately) it forces you to open a separate window for each torrent file you download.

Now, the client which I find to be the most complete and easy to use, **KTorrent**.

The version which I'm talking about is 2.0.3. It's stable, fast, works very well, crashes extremely rare, and has lots and lots of features and options. To start, I'd highlight the possibility to download only certain files from the torrent, the built-in search tool which searches in various torrents sites (plus the possibility to add custom ones), the possibility to view all the peers and their IPs (that was useful  when I saw a download at about 200 KB/s when usually it works at ~ 30 KB - the IP was from my country according to ripe.net). So all in all, my impression on KTorrent is that it's a solid application which does what is supposed to do, maybe the best in its class and I'd recommend it to anyone :-)

---

### Post by kripkenstein on 2006-12-02
> **XVampireX said:**
> 
Deluge (1/5):
------
(Sorry if I offended the developers, it's just my personal view, that's the point of this topic)
I tried the RC, but didn't use it for too long, it seems that it's still feature incomplete and the fact that it's based on Python gave it an unnecessary overhead. It's also based on libtorrent, the same one qBitTorrent uses. Some tabs take a bit to respond (I.E: refresh the information in them) and it unnecessarily tells the user that they have to forward ports. The plugin system is the only thing that I thought was very nice. Also, keep in mind that when I first tried Deluge it failed to connect to dattebayo tracker, so that gave me this little "I don't like this" feeling towards Deluge, though maybe at some point in time I should give deluge another try to see if it improved and if it's as I expected of it to become more bloated (resources wise) or if it would keep about the same as it is now. Again, sorry if I offended the developer.


I'm one of the Deluge developers. I'm not offended by what you said; but basically Deluge is the youngest of all the clients you listed, which explains most of the issues you mentioned. I hope that in a few months Deluge will be suitable for comparison to mainstream clients. Currently, I freely admit that it is far from 'release-quality'.

However, regarding "the fact that it's based on Python gave it an unnecessary overhead" - last I checked, Deluge takes 20MB of RAM, and that's including all shared libraries. For comparison: under Ubuntu (i.e. GNOME), both KTorrent and utorrent under WINE take over 20MB - KTorrent because of the KDE libs, and utorrent because of WINE. Bittorrent (aka Mainline) takes 35MB on startup alone. Azureus - well, we all know the answer to that. So, 20MB for Deluge is fairly reasonable, I think.

Python, in general, is actually quite memory-efficient. It is also fast enough for things like a bittorrent GUI. The reason Deluge may seem slow is the tab updating that you mention. This is a coding issue, and hopefully will be fixed soon.

---

### Post by tosk on 2006-12-18
I like using uTorrent in Wine especially now since Wine has gotten a bit better. My copy of uTorrent doesn't use a lot of RAM either.

WINE - 1.0 MB
explorer.exe - 3.4 MB
uTorrent.exe - 4.4 MB

Total - 8.8 MB

The thing that I like most about it is the ability to route the P2P traffic through a proxy. This lets me setup an ssh tunnel to my server elsewhere in the world and download behind secured/firewalled connections.

---

### Post by kripkenstein on 2006-12-18
> **tosk said:**
> I like using uTorrent in Wine especially now since Wine has gotten a bit better. My copy of uTorrent doesn't use a lot of RAM either.

WINE - 1.0 MB
explorer.exe - 3.4 MB
uTorrent.exe - 4.4 MB

Total - 8.8 MB


utorrent takes more RAM after using it for a while (it starts buffering more and more data, etc). But still, it is the leanest client, memory-wise, no doubt. Let's hope it stays that way after being bought by bittorrent.com.

---

### Post by crypto178 on 2006-12-18
You forgot to include Rufus in the comparison, a little outdated, but still gets the job done.

---

### Post by Artemis3 on 2006-12-18
I use Azureus. Choosed it after learning about its unofficial DHT implementation: When trackers fail it works where the others don't, including mainline. OpenSource is great too. uTorrent now belongs to BitTorrent, and the ads and DRM will come and haunt you. Such is the destiny of proprietary software. Azureus might fork after the Zudeo thing, but will always live.

---

### Post by zachtib on 2006-12-18
> **kripkenstein said:**
> I'm one of the Deluge developers. I'm not offended by what you said; but basically Deluge is the youngest of all the clients you listed, which explains most of the issues you mentioned. I hope that in a few months Deluge will be suitable for comparison to mainstream clients. Currently, I freely admit that it is far from 'release-quality'.

I'm the other developer, and I agree with pretty much everything kripken said.

I notice that on the OP's profile, it mentioned they were using Kubuntu.  I don't know how well running GTK apps on KDE works, but on Gnome, Deluge (and PyGTK apps in general) have been perfectly responsive for me,

---

### Post by dakira on 2006-12-20
> **tosk said:**
> The thing that I like most about it is the ability to route the P2P traffic through a proxy. This lets me setup an ssh tunnel to my server elsewhere in the world and download behind secured/firewalled connections.

Can you elaborate on this?

dakira

---

### Post by gatewayasteroid on 2006-12-20
I like Transmission, only 80 kB:

[http://gir.deefa.com/debian/transmission/](http://gir.deefa.com/debian/transmission/)

---

### Post by dakira on 2006-12-20
> **gatewayasteroid said:**
> I like Transmission, only 80 kB:

[http://gir.deefa.com/debian/transmission/](http://gir.deefa.com/debian/transmission/)

It is nice, but it lacks two things:

#1 features: RSS feed capibility at least
#2 active development: the developer has gone awol for a while now. doesn't reply to emails, doesn't show up on IRC.. he is just gone. While I hope nothing serious happened to him, I'll rather stick with clients which are still being improved.

---

### Post by wilberfan on 2006-12-20
Interesting thread...   I like KTorrent (seems to run real good under Gnome) and am now giving qBitTorrent a try (is there no way to display who's connected to me?).  

* [Sidebar on KTorrent:  There is a torrent site (OK, it's a porn site!) that won't allow usage of KTorrent.  Someone in an IRC channel told me it could be used to "cheat"--but he wouldn't give me any details...]*

 I've been using bitTornado, too, and it works quite well--but I've always found it a bit dreary to look at (and never really liked one open window per torrent...)

Azureus has NEVER seemed to work for me (I've tried it on several different machines) and it's resource requirements have always given me pause...   Now that it's come up again, maybe I'll give it another try...:-k

---

### Post by dakira on 2006-12-21
> **wilberfan said:**
> Azureus has NEVER seemed to work for me (I've tried it on several different machines) and it's resource requirements have always given me pause...   Now that it's come up again, maybe I'll give it another try...:-k

Azureus 2.5 seems to have fixed alot of issues. I'm using uTorrent in Ubuntu (wine) for ages now and am very happy with it because of the low resource usage. But Azureus seems to be back in the game. Try to install the azureus-gcj package. That will improve the responsiveness of the GUI.

I just tried the new [Zudeo]("http://www.zudeo.com"). It is a little bit like a skin for Azureus. Maybe a little more. It is like youtube combined with bittorrent but (momentarily) without streaming. Instead most stuff on there is in HD or DVD quality.

In GNU/Linux you can only use Azureus 2.5 with the Website. In Windows and Mac you have it all included in the App which look REALLY nice and promising.

We'll see.

---

### Post by talbain on 2006-12-21
uTorrent+Wine=Heaven

---

### Post by dakira on 2006-12-21
> **talbain said:**
> uTorrent+Wine=Heaven

wowie.. I just tried uTorrents new WebUI.. looks REALLY great. I'm very impressed with it..

dakira

---

### Post by wilberfan on 2006-12-21
> **dakira said:**
> Azureus 2.5 seems to have fixed alot of issues. I'm using uTorrent in Ubuntu (wine) for ages now and am very happy with it because of the low resource usage. But Azureus seems to be back in the game. Try to install the azureus-gcj package. That will improve the responsiveness of the GUI.

I just tried the new [Zudeo]("http://www.zudeo.com"). It is a little bit like a skin for Azureus. Maybe a little more. It is like youtube combined with bittorrent but (momentarily) without streaming. Instead most stuff on there is in HD or DVD quality.

In GNU/Linux you can only use Azureus 2.5 with the Website. In Windows and Mac you have it all included in the App which look REALLY nice and promising.

We'll see.

I just tried the (non-) gcj Azureus overnight and all seems well...(that's NEVER happened before!).   I have the -gcj version loaded on my other box--but haven't tried that one yet.  It'll be interesting to compare the differences...  

I don't quite get yet how Zudeo works, but it sounds interesting...

---

### Post by Sammi on 2006-12-21
I used _Azureus_ for a long time. It's feature full and functional, but on the bottom line I just found it to be to resource demanding, which cost it it's perfect mark 4/5

Then I tried _KTorrent_ for a month on my Gnome desktop. I ran great and I was pretty happy with it, but in the end it just didn't seem
 ready and fully functional 3/5

I've since then been following the development of _Deluge_ with much delight. It's seems promising, but just is not there yet, and therefor I won't give it any marks ... yet */*

Currently I am using _uTorrent_. I's perfect. Only problem is that, I had to do two little "hacks" to get it to open torrents directly from Firefox and use Alltay to get a better looking tray icon. Oh and it's running trough Wine :roll: 4,5/5

---

### Post by wilberfan on 2006-12-21
Well, I just downloaded the Azureus-cgj package...   Am I supposed to have these ENORMOUS buttons on the toolbar??!  (See thumbnail!)

Does anyone know how the cgj package is different?  (And what does cgj stand for?)

---

### Post by shining on 2006-12-21
> **wilberfan said:**
> Well, I just downloaded the Azureus-cgj package...   Am I supposed to have these ENORMOUS buttons on the toolbar??!  (See thumbnail!)

Does anyone know how the cgj package is different?  (And what does cgj stand for?)

Don't you mean gcj instead of cgj?
If you are going to run azureus using gnu's java, instead of sun's one, you need to use native code for it to run at a decent speed.
That's what azureus-gcj is, azureus compiled natively with gcj.

There is a nice article there about sun java vs gcj:
[http://www.linuxjournal.com/article/4860](http://www.linuxjournal.com/article/4860)

---

### Post by XVampireX on 2006-12-21
> **wilberfan said:**
> Well, I just downloaded the Azureus-cgj package...   Am I supposed to have these ENORMOUS buttons on the toolbar??!  (See thumbnail!)

Does anyone know how the cgj package is different?  (And what does cgj stand for?)


1. No, you're not supposed to have these enormous buttons.

2. it's GCJ, not CGJ. It stands for Gnu Compiler for Java. Because it's a compiler, it compiles to native code, so it takes less time to load and doesn't use the overhead of the java virtual machine which compiles the code on the fly. [http://en.wikipedia.org/wiki/GCJ](http://en.wikipedia.org/wiki/GCJ)

---

### Post by wilberfan on 2006-12-21
> **XVampireX said:**
> 1. No, you're not supposed to have these enormous buttons.

2. it's GCJ, not CGJ. It stands for Gnu Compiler for Java. Because it's a compiler, it compiles to native code, so it takes less time to load and doesn't use the overhead of the java virtual machine which compiles the code on the fly. [http://en.wikipedia.org/wiki/GCJ](http://en.wikipedia.org/wiki/GCJ)

Hey, thanks for the clarification...more importantly, though, how the hell do I get rid of those mutant buttons?!  :-k

---

### Post by dbbolton on 2006-12-21
i prefer to stay as far away from torrent as possible

---

### Post by kiddo on 2006-12-21
gnome-btdownload ([gnome-bt]("http://gnome-bt.sf.net")), the default application, works well (it is in python, **don't** go telling me that's the reason it is slow).

The reason it does not seem to work so well compared to others is that [it does not have uPnP support]("http://sourceforge.net/tracker/index.php?func=detail&aid=1410157&group_id=93129&atid=603217"). Any decent python coder adding that would do a [SIZE="7"]huge service[/SIZE] to the gnome newcomers in general. That would actually make you download at maximum speed instead of 10kb/s.

(sorry about the big letters. Hope I did not scare you too much)

---

### Post by dakira on 2006-12-29
> **kiddo said:**
> The reason it does not seem to work so well compared to others is that [it does not have uPnP support]("http://sourceforge.net/tracker/index.php?func=detail&aid=1410157&group_id=93129&atid=603217"). Any decent python coder adding that would do a huge service to the gnome newcomers in general. That would actually make you download at maximum speed instead of 10kb/s.

Seriously, UPnP is a security desaster! It is convenient, yes. But **ANY** app can use it to open ports in your router. This is why you should have it disabled by default.

Programmers shouldn't endorse its usage by implementing UPnP support.

dakira

---

### Post by Mateo on 2006-12-29
been using utorrent under wine since Azureus is a memory hog. But now because of this thread I want to give transmission a try.

---

### Post by Paerez on 2007-01-12
I use rtorrent.It is small and fast and can be backgrounded with screen.

Learning curve is medium since you have to learn the keyboard shortcuts, but I love it.

I rate it 4/5, only marked down because you have to learn the commands.

---

### Post by Quillz on 2007-01-12
In Windows, I only ever use uTorrent. In Linux, I only ever use Azureus. I don't care what people say; Java does not slow down my system, and I paid good money for my RAM, and I fully intend to use it.

---

### Post by Kateikyoushi on 2007-01-12
Rtorrent, lightweight does everything I need and I always have a terminal open with screen for irssi and commander.
I tried transmission and although it looks nice lacks some functions and the development stopped.
Deluge looks pretty much like ut these days and if the new code is near as good as ut i expect a big shift from az to it.

---

### Post by Mateo on 2007-01-12
deluge looks nice.  i think i'll try it out.  hopefully i can stop using utorrent with wine, never liked that idea anyways.

---

### Post by Mateo on 2007-01-12
could someone possibly post a DEB of deluge, or point towards a repository which has it.  if i try to install it from source any longer, i'm likely to break my keyboard against the wall in frustration.

---

### Post by Mateo on 2007-01-12
cancel that, there is a deb on the deluge site that i missed.  and it worked.

---

### Post by Paerez on 2007-01-12
Deluge is actually really nice. I would rate it as my #1 GUI torrent application, with rtorrent as my #1 command line torrent application.

It has really nice gnome integration, and the torrent search thing is great.

Of course, I can't fully rate it until I have used it for a while.

---

### Post by nibi on 2007-01-12
Being used to uTorrent on windows, it was hard finding something similar when i made the switch to linux. Transmission however is working very well for me as its a lightweight and efficient client.

---

### Post by Stochastic on 2007-02-21
I use Freeloader in Gnome, I notice that nobody has mentioned that here yet but it seems to do just fine for me.  Does anyone else use this client?  I tried to look up some info for it a while back but found no website.  Any ideas info on what it is/does would be nice.

---

### Post by karellen on 2007-02-21
ktorrent all the way :)

---

### Post by dakira on 2007-02-22
[http://www.ruinedsoft.com/freeloader/](http://www.ruinedsoft.com/freeloader/)
Looks like FreeLoader is out of development.

People who want RSS feeds are still stuck with uTorrent or Azureus.

---

### Post by Mateo on 2007-02-22
I would like to use rtorrent but it doesn't have DHT.  Also it doesn't have a working directory (I think it just downloads from where the .torrent is located).  Also I don't think it moves completed downloads. 3 essential features for me.

---

### Post by Sukarn on 2008-01-04
My only problem with Deluge now is that it doesn't make use of multiple trackers if they are present in the torrent file. It only uses one (or so it seems).

---

### Post by Lostincyberspace on 2008-01-04
Thats because that is what all bittorrents are supposed to do according to the official bit torrents guideline

---

### Post by dakira on 2008-01-06
But that doesn't help. It is a flaw in the system that torrents rely on a single tracker and it greatly improved availability of torrents to have multiple trackers.

---

