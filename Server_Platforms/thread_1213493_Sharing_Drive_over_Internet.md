---
title: "Sharing Drive over Internet"
date: 2009-07-14
forum: Server Platforms
---

### Post by illyume on 2009-07-14
I have, on one of the windows computers in my array of computers at home, a folder full of all my music and stuff. 

I also have a computer running ubuntu linux server, that is set up to be seen over a public IP address. It has, mounted on it, a share link to the music folder on the windows computer, mounted as '/music'

I can get an http:// link to it and view the files, piece by piece, and everything... but I'd love to somehow, if possible, have the capability of mapping that as a network drive on another windows computer--basically, so that I have access to this music from anywhere that's hooked up to the internet, as if it was a drive my computer was currently connected to. (With some slowdown since the music files need to transfer over the internet, instead of just from a hard disk to RAM, of course.)

Anyway, I've tried doing the 'map network drive' from My Computer, and have set the IP address: 66.x.x.x (masked, since I'd rather not give out my server's IP address to everyone--security reasons)

When I do this, it comes up with a dialogue requesting my username and password. Nothing I've tried entering there seems to work.

Am I doing things right, or is there a better way to get this done?

---

### Post by HermanAB on 2009-07-15
Here you go:
[http://edna.sourceforge.net/](http://edna.sourceforge.net/)

---

