---
title: "Server Torrent Programs"
date: 2010-05-30
forum: Server Platforms
---

### Post by Manix84 on 2010-05-30
Hi,

I'm having a little issue that I'm looking for a good torrent program for my Ubuntu Server 10.04 box.  Before I was running the Desktop edition, in order to user Vuze (Azureus).  The main advantages or which were that I could setup and RSS feed, and download shows based on filters.

Now that I've moved to the Server edition, I'm stuck with what program to use in Vuzes place.  I'm looking for something that doesn't require a GUI to run on the box, so I would hope it has a Web GUI to take it's place, and RSS feed filtering.

The program I had found, TorrentFlux (TorrentFlux-b4rs), just doesn't cut the mustard.  Can anyone suggest a good program to me?

Quick note; I'm looking at rTorrent now, but i can't see anything about RSS feed filtering yet, so it's probably a bust again.

Thanks in advance for any help you can give me with this program.

-Manix

---

### Post by Vegan on 2010-05-30
I use an old Windows license for a torrent server to distribute chess related files.

I have not seen any Torrent packages for CLI yet.

There is also a Torrent client for the standard GUI so that is another option.

---

### Post by cadriel on 2010-05-30
I've gone through this - and the solution for me was;

1) rtorrent. Exceptionally effecient.
2) ruTorrent. Web interface to rtorrent, provides broadcatching built in (download via RSS and filters).

Most of the other options were lacking in one department or another, or required more than 2 applications to get running.

With the rtorrent rutorrent combination, you get a fully featured torrent application that is usable on the command line - plus a fully featured web interface that supports plugins - plus has full broadcatching features built in.

The only things I'd note is;

1) You need to compile rtorrent yourself because
a) You need to build in xmlrpc-c support and
b) If you're concerned with privacy, you need to patch the source for blocklist support.

My system is now running sweet as with this combination. If you need any help with comppiling or what to do - feel free to holla.

--
Craig.

---

### Post by IanW on 2010-05-31
[Deluge](http://deluge-torrent.org/) works in exactly the manner you require. A daemon to run on your server, and a gui to run on your desktop/laptop.

---

### Post by cadriel on 2010-05-31
Deluge has a nice interface, however - its broadcatching capabilities require a seperate plugin, that interfaces with a seperate python script. So there's additional setup requirements there.

I hear it's good though - I just just disregarded it because it required more setup. Also - my tracker at the time blacklisted it.

Each to their own though! Both are good solutions.

---

### Post by Jive Turkey on 2010-05-31
I use rtorrent (built from SVN) and rtgui from the repositories to controll it.  I modified the rtgui apache config file to use https and added auth digest to keep it private.

You will need some other way to access the completed torrent files than rtgui though, it only manages rtorrent and doesn't serve the files to you.  I tried rutorrent but I found it wasn't stable enough for me.

You can set up the rtorrent config file to make it watch a certain directory for new torrent files to load, and set it to move the completed data files to a different directory.

I've heard good things about deluge too.

---

### Post by dudumomo on 2010-06-01
I'm using Deluge + with its web interface (WebUI)
[**TUTO**]("http://www.freelydifferent.com/self-hosting/deluge-torrent-daemon-webui/")

Easy to set up, nice interface and powerful.

But rtorrent is good too ! Very efficient, a lot of great features, etc...
But not so easy to set up and less "user friendly"

---

### Post by BobVila on 2010-06-01
I'm using rtorrent with a wtorrent frontend. It presents a web page from the server through which you can do you rss feeds, add torrents, etc. It's pretty nice, but I wish wtorrent were just a bit more flexible.

---

### Post by arrrghhh on 2010-06-01
rtorrent is definitely the most configurable system, but you need to find a webUI that you like.  So if you prefer to do things yourself, rtorrent is the way to go.  Very powerful, very light footprint.

However, if you want easy, deluge or transmission would probably be easier to setup.  I went with rtorrent, there are a lot of guides.

---

### Post by Manix84 on 2010-06-06
Really sorry it's taken me so long to reply, I've not been getting notifications on the thread.

So, about a week ago I found out that Vuze supports cli mode, if you add the options -UI=console when launching it.  This is great news, but then I found out that most of the plugins for it require the interface to be configured, including the RSS + Remote Application plugins (not so great).

Since I discovered these solutions and problems, I've not had a chance to sit down and do anything with it.

I'd be interested to hear what everyone thinks of the stage I've managed to get it upto.

PS's:

Additionally, I will be giving Deluge a go later today.  I managed to get rTorrent and rTorrentb4rs (or whatever it is) installed, but I've got a housemate that would be using it, and the interface would have been massively too much for him.  That and the RSS feed handling was god aweful, and I had no control over where files were being downloaded too.

Oh, one of the reasons I've stuck with the CLI version of ubuntu is that the server I'm using has reached the point where it refuses to launch any OS GUI.  LOL.

---

