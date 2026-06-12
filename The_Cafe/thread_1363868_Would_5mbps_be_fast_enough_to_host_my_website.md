---
title: "Would 5mbps be fast enough to host my website?"
date: 2009-12-25
forum: The Cafe
---

### Post by Jekshadow on 2009-12-25
I have a few Debian servers, and I was thinking about moving my website to my own servers so that I have full control over my website. I get an average 4-5mbps up on my home connection, would that be fast enough for the standard html/image transfer that goes on, I am not planning on putting anything other than the website, and tarballs of my projects (none are over 15MB).

---

### Post by kahumba on 2009-12-25
If your website has nothing to do with pr0n then 5mbps should be enough.

---

### Post by Warpnow on 2009-12-25
Make sure you're measuring upload speed. Its pretty important for a download server.

---

### Post by Jekshadow on 2009-12-25
> **Warpnow said:**
> Make sure you're measuring upload speed. Its pretty important for a download server.

I get 30mbps down and 4-5mbps up, yes I am measuring upload speed.

> **lieqie said:**
> depends on your site's bandwidth

All that will be transferred is text (html), images and a few videos. I tested my bandwidth with a friend by putting a 2GB flash drive image of Ubuntu on my webserver and he got a good 2mbps down constantly from my server, so I think I'm good.

---

### Post by The Real Dave on 2009-12-25
Unless you're gonna get alot of people downloading at once, you should be ok. Considering its just text and images

---

### Post by Warpnow on 2009-12-25
Well, you can think of it this way. 4mbs (your stated minimum) is 500 kb/s. If you have 10 people downloading the same file, each person will have roughly 50 kb/s download speed. 20 people, 25 kb/s. 

Downloads are more bandwidth intensive largely because they take longer. More people simultaneously accessing the server. I think its unlikely you'll have that many people simultaneously accessing the server. If the downloads are relatively spaced, to even a decent amount such as 10-20 an hour, you'll be fine, considering the files will download very quickly because they're small, and each user will finish the file before the next person starts, with little overlap.

---

### Post by -grubby on 2009-12-25
5 mbps up should be fast enough. However, you should double check your ISP allows you to host servers, specifically web servers using port 80.

Additionally, it's possible to get an unmanaged VPS for hosting; you'll get absolute root access, your choice of several OSes to install on the fly, and incredibly fast down and up speeds. I use [Linode](http://www.linode.com/?r=a31fce4c50571a0517d39099313b8138a047c534) for $20 a month and they've been awesome.

---

### Post by MaxIBoy on 2009-12-25
Consider seeding torrents of any files which aren't likely to change a lot with time (stable releases of programming projects, videos, etc.) Then set your server up as a torrent slave for those files.

You can also look into services like Vimeo for hosting versions of your videos in addition to torrents and HTTP downloads.

---

### Post by sandyd on 2009-12-25
you should create a seperate virtual host for the downloads
then use webmin or something to limit the amount of connections /bandwidth per user of the download system.
or simply consider torrenting the tarballs, or using sourceforge/some other file upload site. (mediafire?)

---

### Post by doorknob60 on 2009-12-25
Should be good, I run mine on 1mbps up and it's fine for what I use it for (wiki and wordpress and some small tarballs).

---

### Post by phillychease on 2009-12-25
> **kahumba said:**
> if your website has nothing to do with pr0n then 5mbps should be enough.

+1

---

### Post by SSTwinrova on 2009-12-26
> **-grubby said:**
> 5 mbps up should be fast enough. However, you should double check your ISP allows you to host servers, specifically web servers using port 80.

This.

If you're talking about a non-business class connection (and you live in the US), hosting a server is almost guaranteed to be forbidden in the TOS. Don't just assume port 80 being open means that you're in the clear.

---

