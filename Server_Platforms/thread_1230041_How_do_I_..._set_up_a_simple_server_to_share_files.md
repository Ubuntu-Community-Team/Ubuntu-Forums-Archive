---
title: "How do I ... set up a simple server to share files?"
date: 2009-08-02
forum: Server Platforms
---

### Post by medicdave on 2009-08-02
Hi All-

I run a small Dell Poweredge with Ubuntu Server 8.04LTS. I'd like to set up some sort of service on it, for my family to use as a "drop box" for photos from the trips we take together.

Example: My fam just returned home from a trip this weekend. We all took photos, but now we're spread across 3 states. We could all mail each-other CD-Rs of our photos, but all told there were 7 cameras in use on our trip. I'd like us all to be able to drop our photos in one spot (that being my server) and then choose the ones we want to download.

I run Linux desktops, but the rest of my fam will be up/downloading via Mac OS-X and Windows XP. Initially, I thought about WebDAV, but I don't want to configure (and keep updated) an entire Apache server just to provide this service. FTP or SCP would be nice, but I can't find any method of restricting access to a specified area (ie chroot'ing) that is both straightforward and secure.

The users on this system will need to just drag and drop. If anyone can recommend a [preferably canned] way to realize such a system - even a well-done howto or blog post would be great - I'll be very much appreciative!

[LIST]
[*]Users can upload / download files reliably
[*]Requires authentication
[*]Perhaps offers a secure transport?
[*]Doesn't expose my server's whole filesystem
[*]Has a simple (read: drag-n-drop) client on OS-X and WinXP
[*]Keeps my WAN-side vulnerabilities minimized (this server is also my firewall/gateway)
[/LIST]

Thanks very much,
[medic]Dave

---

### Post by panayara on 2009-08-03
[http://shibuvarkala.blogspot.com/2009/07/how-to-share-files-quickly-in-ubuntu.html]("http://shibuvarkala.blogspot.com/2009/07/how-to-share-files-quickly-in-ubuntu.html") 

see the above link for setting up a simplest file sharing server
panayara

---

### Post by druhboruch on 2009-08-03
I believe that router and file server on the same box is not a great idea however...

Webdav would be the simplest thing to setup:
[http://www.howtoforge.com/how-to-set-up-webdav-with-apache2-on-ubuntu-8.10](http://www.howtoforge.com/how-to-set-up-webdav-with-apache2-on-ubuntu-8.10)

You may also have a look at mysecureshell:
[http://mysecureshell.sourceforge.net/](http://mysecureshell.sourceforge.net/)

I think it is also in the repo.

---

