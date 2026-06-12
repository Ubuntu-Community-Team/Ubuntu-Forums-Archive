---
title: "Samba or WebServer for media share"
date: 2010-09-07
forum: Server Platforms
---

### Post by darms21 on 2010-09-07
I have recently set up a home server running ubuntu in which I would like to use mainly as a media sharing device. I would like to upload/download/stream and share music/movies/photos between this linux box and my windows computers. I have come across two solutions to this issue: 1)Samba 2)Stream the media on a Webserver.

Can this community help me decide which solution would be the best to use? Thanks in advance to all that lend a moment.

---

### Post by endotherm on 2010-09-07
> **darms21 said:**
> I have recently set up a home server running ubuntu in which I would like to use mainly as a media sharing device. I would like to upload/download/stream and share music/movies/photos between this linux box and my windows computers. I have come across two solutions to this issue: 1)Samba 2)Stream the media on a Webserver.

Can this community help me decide which solution would be the best to use? Thanks in advance to all that lend a moment.
if you are talking about PCs directly on your network, then samba has been my choice. the config is pretty easy, very flexible, and is navigated via the file browser (nautilus) the same as if it were a local folder. that way it can work for any file type, not just video. 

with a streaming server, you probably have to navigate to it within the browser. it would also be limited to video whose codec needs are well understood by the streaming server. additionally servers like that need indexing, so it is constantly checking the contents of your video collection (which can be a pain if you have video on hdds on 3 differant systems) etc.

---

### Post by darms21 on 2010-09-07
I would like to be able to view/stream files both on my local network and allow my family/friends to view them remotely. Am I correct in assuming that Samba is fit only for local access and and Web server combination would be best for remote access. Again, I would like to allow family/friends to be able to upload/download files to the server. Thanks again!

---

### Post by endotherm on 2010-09-07
well if you want externals to use it, then yes, you are stuck using a webserver for it. 
do you really really want that capability? public facing web resources are something only a professional should establish, just because the security considerations become so daunting.

---

### Post by theDaveTheRave on 2010-09-07
it seems to me that there should be no reason as to why the portion of the HDD that holds the data that will be shared can be on the 'www' directory (and served via apache or whatever is required for video etc) and also shared among the local pc's via a samba share.

Or is there another alternative...

could you set up the whole idea as a virtual private network?? then each member of your family has a dedicated username / password that connects them to the vpn, or maybe use vnc (or similar) and have your family learn about ssh etc.

I guess the security issues are the same as with a 'public facing web server' but are the solutions easier to implement?

I only ask as I am 'kind of thinking' of setting up a similar thing from here... once I have my domain name sorted, organised a fixed IP from my telephone provider and convinced the 'wife' that it is worth the extra expense on the electricity.

David

---

### Post by darms21 on 2010-09-07
How can I serve efficiently/effectively a piece of media from my home server to a laptop when I am on the road in a hotel for example. I understand that movie will be playable only if my web browser has the ability to play them. Is there a way to directly stream from the server to say VLC (or an equivalent unix video player) on my laptop?

Also, is it possible to share media through SSH?

---

### Post by theDaveTheRave on 2010-09-07
VLC can act as a media server and a player.

So it would seem to fit both your requirements.

You could even go one better...

Myth tv to get tv to your home pc, then stream it back out with vlc!

It's an idea I am thinking of but on a home network only.

David

---

