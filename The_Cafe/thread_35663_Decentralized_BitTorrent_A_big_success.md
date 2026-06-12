---
title: "Decentralized BitTorrent: A big success"
date: 2005-05-19
forum: The Cafe
---

### Post by jdong on 2005-05-19
This morning, I decided to have some fun: offer a 100MB OO.org2 backport via tracker-less Bittorrent (the Azureus in Ubuntu Backports). With a 20KB/s upload bandwidth and new, barely-tested P2P technology, I honestly expected it to be a failure.

8 hours later, we have 3 people who've completed the download, and 2 people still downloading. We're getting net speeds exceeding 70KB/s :)


All with one mouse click. No tracker, no complicated server to set up.


This is it -- the new era of downloading.

---

### Post by ow50 on 2005-05-19
I was impressed as well on how well it worked and how quickly I got connection with others. However, at some point after completing download, I lost connection to all peers, seeing one seed and one peer I don't have connection to.

And I don't even need OpenOffice much during summer, just wanted to test this. :)

---

### Post by deception on 2005-05-19
I am on 93% and am going to seed overnight  :) 

Good idea John!

---

### Post by Monchy on 2005-05-19
What exactly is different about Decentralized BitTorrent?

---

### Post by jdong on 2005-05-19
I think the Peers tab only shows peers you're connected to or trying to connect to, in decentralized mode.

---

### Post by Rule on 2005-05-19
well it's so you don't have to rely on a tracker to get your information.

---

### Post by NeoChaosX on 2005-05-19
Do you need Azureus to use this? i tried using the torrent with the default GNOME Bittorrent client, but it didn't work.

---

### Post by TravisNewman on 2005-05-19
yeah you need azureus

---

### Post by bored2k on 2005-05-19
[QUOTE=NeoChaosX]Do you need Azureus to use this? i tried using the torrent with the default GNOME Bittorrent client, but it didn't work.[/QUOTE]
 At the moment azureus is the only one with this feature after their 2.0.3 release 17 days ago. Maybe BitComet implemented this in their new version, but I doubt it.

At least azureus doesnt chew up your machina after you do the trick in
[http://www.ubuntuforums.org/showthread.php?t=35660&highlight=azureus+speed](http://www.ubuntuforums.org/showthread.php?t=35660&highlight=azureus+speed)

---

### Post by poofyhairguy on 2005-05-20
This is great. I hate when I find a torrent I want but the tracker is gone. I hope it doesn't become an excuse to call Bittorrent a "dark" technology, I think its the most important advance on the web since CSS.

---

### Post by bored2k on 2005-05-20
[QUOTE=poofyhairguy]This is great. I hate when I find a torrent I want but the tracker is gone. I hope it doesn't become an excuse to call Bittorrent a "dark" technology, I think its the most important advance on the web since CSS.[/QUOTE]
 Cops certaintly won't like this feature. They'll be having a hard time chasing the guys who leaked [this](http://www.cnn.com/2005/TECH/internet/05/19/star.wars.piracy.reut/index.html).

> The Motion Picture Association of America has been aggressive in going after Web sites that provide "tracker" links that enable BitTorrent downloads of copyrighted material, including six lawsuits this week against sites with links to TV shows.

---

### Post by bored2k on 2005-05-20
[QUOTE=panickedthumb]yeah you need azureus[/QUOTE]
 **NEWSFLASH**: Official BitTorrent Get's **[highlight]Trackerless**[/highlight] Treatment !
> Earlier this month, Azureus introduced a new beta client with DHT (Distributed Hash Table) layer support. Many touted this as a "trackerless" BitTorrent network. Two weeks later, the creator of BitTorrent, Bram Cohen, released the latest official version of his client, fresh with "trackerless" support.
[http://www.bittorrent.com/](http://www.bittorrent.com/)
[http://www.slyck.com/news.php?story=795](http://www.slyck.com/news.php?story=795)

---

### Post by fng on 2005-05-21
The only thing that keeps me from installing azureus is the java sdk dependency.

I installed java following the ubuntuguide and everything works fine (eclipse, home projects, ...)
Can't we just install azureus without installing java sdk from the backports?

---

### Post by jdong on 2005-05-21
The Ubuntu Guide method of installing Java is not correct -- it places binaries in system locations managed by dpkg/apt, yet it doesn't register the files with apt.

The correct way of installing Java is to use "make-jpkg" (part of the java-package package in Multiverse) to convert the .bin file into a .deb. This is exactly what I did, and it's undoubtedly the Debian way of getting Java.


APT is oblivious to the fact that you have Java, and so is /etc/alternatives, so the Debianized Azureus won't even FIND your Java environment.


I recommend you mark sun-j2re1.5 (not SDK) with Azureus at the same time, which won't force the SDK to be installed.

---

