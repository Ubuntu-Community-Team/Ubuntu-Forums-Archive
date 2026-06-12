---
title: "Arista Transcode Gstreamer Element faac &amp; Gstreamer Element x264 encoder"
date: 2010-02-02
forum: Ubuntu Studio
---

### Post by NickJones on 2010-02-02
Hi there,
I installed Arista Transcode today to try and rip a DVD to PlayStation 3 format, I hit go and it said I had to install more codecs, which I did, I tried it again and it says the same thing, only this time it's asking for:

[LIST]
[*]GStreamer element faac
[*]GStreamer element x264enc
[/LIST]
And it says "No packages with the requested packages found"
I'm running a fully updated version of Ubuntu 9.10,
I have the following other media software installed as well as all the other media software that comes with Ubuntu:

[LIST]
[*]K9copy
[*]MPlayer Media Player
[*]PS3 Media Server
[*]DVD::RIP
[*]Xine
[/LIST]
Cheers,
Nick

---

### Post by ghostborg on 2010-03-03
hmmm, I wonder if it was asking for the codec to deal with the DVD protection? In that case go over to [https://help.ubuntu.com/community/Medibuntu]("https://help.ubuntu.com/community/Medibuntu")

and follow the instructions.

It probably wouldn't hurt to install ubuntu-restricted-extras if you did not already. 

Remember to re-do this after distribution upgrades.

---

### Post by michaelwheatland on 2010-05-01
In order to get Arista working correctly you need to add the official Arista repository to get the codecs.

Use the commands below:

[HTML]sudo sh -c "echo 'deb http://ppa.launchpad.net/danielgtaylor/ppa/ubuntu  jaunty main' >> /etc/apt/sources.list"[/HTML]Then add the PGP key:

[HTML]sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys A1B03D01[/HTML]You can then reinstall Arista from the new repository:

[HTML]sudo apt-get update && sudo apt-get install arista[/HTML]

**Then TRANSCODE!**

---

### Post by tsloper1 on 2010-09-03
I followed your instructions and re-installed Arista. It sees my DC10+ card, but when I run the program it say "The input file or device contains no audio or video streams" and closes the file

---

### Post by diablofatt on 2011-06-05
> **michaelwheatland said:**
> In order to get Arista working correctly you need to add the official Arista repository to get the codecs.

Use the commands below:

[HTML]sudo sh -c "echo 'deb http://ppa.launchpad.net/danielgtaylor/ppa/ubuntu  jaunty main' >> /etc/apt/sources.list"[/HTML]Then add the PGP key:

[HTML]sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys A1B03D01[/HTML]You can then reinstall Arista from the new repository:

[HTML]sudo apt-get update && sudo apt-get install arista[/HTML]

**Then TRANSCODE!**


This got the program working for me. Thanks!

---

### Post by hemna on 2011-10-04
W: Failed to fetch [http://ppa.launchpad.net/danielgtaylor/ppa/ubuntu/dists/jaunty/main/binary-amd64/Packages](http://ppa.launchpad.net/danielgtaylor/ppa/ubuntu/dists/jaunty/main/binary-amd64/Packages)  404  Not Found

---

### Post by cain071546 on 2012-04-17
> **hemna said:**
> W: Failed to fetch [http://ppa.launchpad.net/danielgtaylor/ppa/ubuntu/dists/jaunty/main/binary-amd64/Packages](http://ppa.launchpad.net/danielgtaylor/ppa/ubuntu/dists/jaunty/main/binary-amd64/Packages)  404  Not Found

BUMP,   the PPA is a dead end ie not working,  anyone know where i could find a copy of the [B]packages?
[/B]

---

