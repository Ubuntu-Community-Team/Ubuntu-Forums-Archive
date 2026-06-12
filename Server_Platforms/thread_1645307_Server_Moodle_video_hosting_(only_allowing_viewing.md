---
title: "Server Moodle video hosting (only allowing viewing access to moodle users)"
date: 2010-12-14
forum: Server Platforms
---

### Post by EndersJ on 2010-12-14
I've set up my first Ubuntu server system for my school and am using it to host Moodle. I was asked to post some instructional videos, however, they are copyrighted so Youtube posting and embedding in the Moodle site is not an option. If I simply drop the video file in the database folder (/var/www) on the server, it can be accessed and viewed by anyone with the appropriate url (e.g. [http://XXX.XX.XXX.XXX/video.avi](http://XXX.XX.XXX.XXX/video.avi), with XXX.XX.XXX.XXX being the server IP address). I also thought to drop the video in the Moodle database folder (/var/www/moodle) but that had the same effect (viewable by anyone with the url).

What I would like is to be able to host a video file that would only be accessible to users of the Moodle site I am hosting but I am unsure how to set these permissions if that is what the issue is. The video needs to be playable in the browser so that it is not downloaded and distributed. Any advice on hosting videos in this fashion would be greatly appreciated! Thanks!

The server was set up within the past 3 months, so no packages are any older than that. It is running 32-bit Ubuntu Server 10.04, Moodle 1.9.10+, LAMP server (w/ PHP5), can't think of anything else that may be relevant...

---

