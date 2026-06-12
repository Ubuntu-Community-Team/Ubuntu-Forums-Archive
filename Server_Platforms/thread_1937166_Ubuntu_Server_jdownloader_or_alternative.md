---
title: "Ubuntu Server jdownloader or alternative"
date: 2012-03-07
forum: Server Platforms
---

### Post by ptmuldoon on 2012-03-07
I have Ubuntu Server installed being used a NAS box for media and file storage.  Currently I use my Windows machine with jdownloader for any thing I need to download and than transfer that info to my NAS file shares.  

Can anyone recommend a similar program to run on Ubuntu Server?  This a headless unit with no GUI, but does have webmin installed on it.

EDIT:  I just found this post in german about using jdownloader on a headless install with xvfb.  But before installing it, anyone have any other recommendations?

Thanks
PT

---

### Post by papibe on 2012-03-07
Hi ptmuldoon.

I use 'wget' for direct links, and transmission-daemon (web interface) for torrents.

I've been waiting for the terminal version of jdownloader, but besides the old conceptual design found [here]("http://jdownloader.org/knowledge/wiki/terminal/index"), I haven't see the actual tool yet.

Just some thoughts.
Regards.

---

### Post by ptmuldoon on 2012-03-08
Thanks for the feedback papibe.  I do hope the terminal version of jdownloader does get developed.

I guess I forgot to post the link on also doing it with xvfb.  Its in german, but google can convert it for you.

[http://blog.is-a-geek.org/jdownloader-headless-mit-web-interface-auf-ubuntu-server-10-04](http://blog.is-a-geek.org/jdownloader-headless-mit-web-interface-auf-ubuntu-server-10-04)

My other thought once I have my new server build completed is to also run a virtual windows machine inside server.  I think that may work to access things that may work, but unsure, as the main OS will still be a headless OS with no GUI.

---

