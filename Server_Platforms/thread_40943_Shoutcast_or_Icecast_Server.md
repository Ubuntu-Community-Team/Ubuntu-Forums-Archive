---
title: "Shoutcast or Icecast Server"
date: 2005-06-11
forum: Server Platforms
---

### Post by andlinux21 on 2005-06-11
Has anyone tried to setup a shoutcast or icecast server on Ubuntu I used to run one when I had SUSE 9.1 it was fairly easy to setup and run.  I was wondering if it would be any different to set up. :)

---

### Post by GrumpySmurf on 2005-06-11
I haven't set up a streaming server on Ubuntu, like you mine was on SuSE 9.1.  A quick search for shoutcast in apt reveals some packages:

```
$ apt-cache search shoutcast
darkice - Live audio streamer
icecast-server - MPEG Layer III Streaming Server
icecream - non-interactive stream download utility
kstreamripper - kde frontend for streamripper
libapache-mod-mp3 - turns Apache into a streaming audio server
somaplayer - Player audio for the soma suite
streamripper - download online streams into mp3 files
zinf - Extensible, cross-platform audio player
xmms-liveice - XMMS plugin that sends your audio to a shoutcast server
totem - A simple media player for the Gnome desktop (dummy package)
totem-gstreamer - A simple media player for the Gnome desktop based on gstreamertotem-xine - A simple media player for the Gnome desktop based on xine
streamtuner - A GUI audio stream directory browser
```
I would try the icecast-server package, or maybe darkice.  You could also try installing Shoutcast.com's own version manually.  I imagine that's what you did before on SuSE?  I did... 

Good luck

---

### Post by andlinux21 on 2005-06-26
yes I went to the shoutcast site and downloaded the files and installed it.  
Straight forward and pretty easy for me to get it up and running just wondered if I could do the same here I will try it and let you know how I come out.

---

### Post by keithacole on 2005-07-31
anything new?

---

### Post by andlinux21 on 2005-08-19
I am waiting to replace my old motherboard then I will put the shoutcast server back online

---

### Post by Velox Letum on 2005-08-20
I was able to download a Linux version of the Shoutcast server from their site and run it with minimal effort (I've set them up in the past), but no problems on my Ubuntu install.

---

### Post by Mr. Electric Wizard on 2005-08-20
So, what are your server's address?
I'm waiting to jam out... :)

---

### Post by Velox Letum on 2005-08-20
Besides being on my home box, it isn't up 24/7. At home I only have 512kbps uplink. I do run a production shoutcast server on a dedicated FC1 server however, though it hasn't seen much use as of late.

---

### Post by Velox Letum on 2005-08-20
My production server: [http://radio.nanoshock.net:7000/](http://radio.nanoshock.net:7000/) Up until I decide to go and try to fix my Kubuntu install.

---

### Post by andlinux21 on 2005-08-25
finally got my board so I should be testing it out this weekend yahoo!! :)

---

