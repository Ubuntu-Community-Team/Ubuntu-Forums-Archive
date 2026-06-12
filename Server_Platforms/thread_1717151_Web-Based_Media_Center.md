---
title: "Web-Based Media Center"
date: 2011-03-29
forum: Server Platforms
---

### Post by SlalomMan on 2011-03-29
Hey guys,

I want to set up a kind of "Media Library" on a server. The goal is to be able to share my music, movies, etc. with a few people on a local network. Ideally, this could support both streaming via mms (or something similar) and downloading (which I think would have to be via http). I looked into [TVEz](http://tvez.sourceforge.net/?content=home), and it looks like it mostly is what I need, but it hasn't been updated since 2004. I haven't done a whole lot of googling around yet, but I figured someone here must know of something to get the job done.

Thanks!

---

### Post by wyliecoyoteuk on 2011-03-29
There are lots!
Mythbuntu,(might be a little too much), LinuxMCE (definitely too much), Piren, Geexbox, Vortexbox is probably your best bet though.

---

### Post by nickleboyblue on 2011-03-29
Just fyi, LinuxMCE is not what you want.  Though it does have all of the features you mentioned, unless you're willing to tweak it for several months before it starts doing what you want it to, get something else.  Myth is a good and current distro that will probably do what you want it to, but LinuxMCE is still stuck on Ubuntu 8.10.  Just FYI.

---

### Post by SlalomMan on 2011-03-29
> **wyliecoyoteuk said:**
> There are lots!
Mythbuntu,(might be a little too much), LinuxMCE (definitely too much), Piren, Geexbox, **Vortexbox** is probably your best bet though.

Thanks. Vortexbox sounds closest to what I need, but it looks like it's designed to handle music only?

Just to clarify, the purpose of this server is to allow other network computers to download and/or stream the files from it. I may run XBMC on this box and play the files, but it's going to mainly be a file server. I know I could just set up a really simple Apache server to list all of the files, but I figured there'd be a bit more elegant solution available.

Thanks again.

---

### Post by R.Bucky on 2011-03-29
I have been using Ubuntu Server with MediaTomb for some time. It streams to your PS3/XBox over UPnP, both movies and music. Works great, is lightweight, and very reliable. A tutorial here: [http://nwlinux.com/use-ubuntu-server-to-stream-movies-to-your-ps3/]("http://nwlinux.com/use-ubuntu-server-to-stream-movies-to-your-ps3/")

---

### Post by SlalomMan on 2011-03-30
Coincidentally, I just came across MediaTomb in my searches. It looks like a good way to stream the media to computers, XBMC, or other devices on the network.

I was really looking for an application to create a web page with links to all video/music files on the machine, but this will work fine.

Thanks!

---

### Post by R.Bucky on 2011-03-31
Mediatomb does have a web based interface. I am sure that you could modify or create a page using the existing platform that will work for you.

---

### Post by K_Light2003 on 2011-04-01
Hi ya, 

I've just been doing the same sorta thing. I'm using mediatomb as well at the moment as it works well with my  Freecom [*MusicPal*]("http://www.musicpal.info/") and was very easy to set up.

I've just written up a little "howto" on my blog if it's any use to you. 

The link is [here]("http://linuxserver2011.wordpress.com/2011/04/01/mediatomb-a-upnp-media-server-ubuntu-10-10/") for the mediatomb bit.

---

