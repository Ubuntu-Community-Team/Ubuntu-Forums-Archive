---
title: "what would be involved in implementing video streams in a bit torrent client?"
date: 2010-07-13
forum: The Cafe
---

### Post by Dustin2128 on 2010-07-13
I was reading a softpedia news article a while back about utorrent 3 ([http://news.softpedia.com/news/Download-uTorrent-3-0-Alpha-145397.shtml](http://news.softpedia.com/news/Download-uTorrent-3-0-Alpha-145397.shtml)) and how it could stream video before it finished downloading, quite useful for large files like 720p Pioneer One. Unfortunately, utorrent is non-free software. From what the article said, it accomplishes the feat by making sure certain chunks download in order rather than the normal random pattern [QUOTE=softpedia]Normally, you wouldn&#8217;t be able  to do this with BitTorrent, since different chunks of a file are  downloaded in random order, part of the reason why the protocol is so  fast. uTorrent gets around this by building a buffer of sorts,  downloading some chunks in order, and then using a streaming server to  send the video to any player capable of receiving streaming video.  [/QUOTE] I was just wondering how difficult this would be for a linux torrent client.

---

### Post by Austin25 on 2010-07-13
Well, you could torrent video files, and set up rss feeds to supply a whole bunch, but having a built in player or using standard streams would be quite a bit of coding.

---

### Post by dmizer on 2010-07-13
In the settings for Deluge, you can set it to prioritize the first and last pieces of a torrent. Keep in mind though, that (depending on the number of free seeds) doing this could significantly reduce your download speed.

---

### Post by Dustin2128 on 2010-07-13
> **Austin25 said:**
> Well, you could torrent video files, and set up rss feeds to supply a whole bunch, but having a built in player or using standard streams would be quite a bit of coding.
I've been needing to test my coding skills on a project anyway :). As for the other post about download speed, it probably *would *reduce it significantly, but as long as it was downloading with at least real time speed, you could view it as you're torrenting it, so it doesn't matter quite as much. I'd use it.

---

### Post by YeOK on 2010-07-14
If you used Gstreamer and libtorrent you could probably have a client up and running soon enough. Prioritize download options are not new and Gstreamer can play videos in a few lines of code.

---

### Post by Redo on 2010-07-14
It could be a viable option for video sites, imagine youtube or hulu sources and whatnot using torrent technology while you watch their videos. They still provide the vast majority of the bandwidth, but they get some of that bandwidth back by having users provide uploads. 

They would have to detect your upload speed (which would cause a outburst for sure), and make certain the video is longer than 4 seconds or so, but they could easily end up gaining 10% of their bandwidth needs back, if not more.

It's probably a massive headache to implement, but there's plenty of brilliant minds that may be able to work out the details.

---

### Post by lovinglinux on 2010-07-14
> **Dustin2128 said:**
> I was reading a softpedia news article a while back about utorrent 3 ([http://news.softpedia.com/news/Download-uTorrent-3-0-Alpha-145397.shtml](http://news.softpedia.com/news/Download-uTorrent-3-0-Alpha-145397.shtml)) and how it could stream video before it finished downloading, quite useful for large files like 720p Pioneer One. Unfortunately, utorrent is non-free software. From what the article said, it accomplishes the feat by making sure certain chunks download in order rather than the normal random pattern  I was just wondering how difficult this would be for a linux torrent client.

[Tribler](http://en.wikipedia.org/wiki/Tribler) does that and is cross platform. Haven't tried tho.

> **Redo said:**
> It could be a viable option for video sites, imagine youtube or hulu sources and whatnot using torrent technology while you watch their videos. They still provide the vast majority of the bandwidth, but they get some of that bandwidth back by having users provide uploads. 

They would have to detect your upload speed (which would cause a outburst for sure), and make certain the video is longer than 4 seconds or so, but they could easily end up gaining 10% of their bandwidth needs back, if not more.

It's probably a massive headache to implement, but there's plenty of brilliant minds that may be able to work out the details.

Adobe is already doing that: [http://labs.adobe.com/technologies/stratus/](http://labs.adobe.com/technologies/stratus/)

---

