---
title: "First Ubuntu Media/ Code Server"
date: 2012-02-01
forum: Server Platforms
---

### Post by jr226 on 2012-02-01
Hi,

I am interested in setting up a server for media (music, movies, pictures) hosting, and holding the code files for my school work.  I would like to be able to run some version control software and store my repositories on the server, and access them from both my home network, and from my schools network, and have a second backup copy of all my files.

I was hoping to have the media playable through my PS3 to my TV, but I read somewhere that the data may have to be FAT formatted, so I understand this may not be an option.  Is there another way to connect to a TV, IE, having an HDMI output from the server? 

Also, is there any good beginner guide to server setup?  I've seen the official UBUNTU doc's, but I'm not sure if I would be setting up something which would be working for my needs.  Thanks for any advice, and sorry if this is too simple of a question, I'm very new to servers!

---

### Post by bubylou on 2012-02-03
I don't know much about code servers so i cant help you there but i do have a media server. Personally i use [UShare]("http://www.dd-wrt.com/wiki/index.php/Ushare_uPnP_media_server") to stream to my Xbox but i believe it supports ps3 as well. its very easy to setup and i have it share the movies of my samba share.

---

### Post by rubylaser on 2012-02-03
You could use [PS3 Media Server]("http://ps3mediaserver.blogspot.com/"). There's no need for the filesystem to be FAT32, so you could build a cheap mdadm software RAID array for your data.  For personal coding projects, I'd just use [GIT]("http://git-scm.com/"), rather than trying to setup a whole Subversion setup. You could back this up any way you'd like because it's still a directory structure.

Yes, you could hook it up to a TV with HDMI as long as your GPU has an HDMI out.

---

