---
title: "Ubuntu as a home server with CLI only"
date: 2008-08-16
forum: Server Platforms
---

### Post by junming on 2008-08-16
I am wondering about a future issue as I plan to buy a secondhand box to use as a server on my local network (at home).

I would use this server to:
* put all the files that I want to access on the 2 laptops we have
* download other files from the Internet

I know that Ubuntu (or Debian) can do this pretty well thanks to samba, apache, proftp, etc. BUT the reason why I post here is that I would need:

1. a *mule client (amule?) with only the web server version running in the background (I wish NOT to install a desktop environment, or at least not run it by default) that I could access from the other pcs on the LAN, add files to download, etc.

2. a torrent client (deluge, transmission, whatever you advise me) that I can manage from a web page on the LAN (a webserver then) which will run without graphical frontend as well - as I do not wish to use gnome etc.

I wonder if these software can run by themselves at boot, how I can run them, to which runlevel (I guess running them as root is out of the question).

I post this here because I believe Ubuntu can do the job, but I am open minded enough, and can use any other distro you advise me (even if I prefer the Debian package management sistem ;)).

---

### Post by windependence on 2008-08-16
Well I don't use amule anymore but I think it has to have X running so that may be out.

Many people here use rtorrent and love it. Works from the command line.

Yes they can be run at boot but your right you don't want them running as root. You may be surprised (as I was) that in Ubuntu, runlevels don't make a difference unless you set them up that way (yeah really!).

Samba will work great for your other stuff.

-Tim

---

### Post by hrod beraht on 2008-08-16
> **windependence said:**
> Many people here use rtorrent and love it. Works from the command line.

I second that recommendation and have it running on an old PIII server right now.
Use rtorrent in combination with *screen* so you can easily detach the session and resume it later (even from a different computer).

Bob

---

### Post by Cheesehead on 2008-08-16
Once you figure out the apps you want,

1) Build a startup script to launch them
2) Place a link to the script in your favorite runlevel folder (/etc/rc*.d)
For more info, Google 'debian startup runlevels' or see the Debian info at [http://www.debian.org/doc/debian-policy/#contents](http://www.debian.org/doc/debian-policy/#contents)  "System run levels and init.d scripts"


Consider configuring two different runlevels:
One headless, administered by SSH and command line
The other with GDM and Vinagre for GUI admin.

---

### Post by SpaceTeddy on 2008-08-17
here is my two cent :)

i had a mldonkey server running for a long long time... they work rather well, and there is no console work needed, as you can have a client running on your computer that detects torrents and ed2k links and inserts them at the server. You can even configure it to send you email when a file is done :)
besdies that, it comes with a building web interface (if you do not want the client) that runs on port 4080. if i remember correctly, it is also found in the repositories and comes pretty much preconfigured.

BTW - mldonkey downloads torrent, ed2k, overnet, and three more i have never used...

---

### Post by cleam on 2008-08-17
I'm using Azureus with WebUI plugin. It works fine.

---

### Post by Vivaldi Gloria on 2008-08-18
> **windependence said:**
> Well I don't use amule anymore but I think it has to have X running so that may be out.


It looks like it has a cli version:

```
vivaldi@narval:~$ apt-cache search -n amule
amule - client for the eD2k and Kad networks, like eMule
amule-common - common files for the rest of aMule packages
[COLOR="DarkOrange"]amule-daemon - non-graphic version of aMule, a client for the eD2k and Kad networks
amule-utils - utilities for aMule (command-line version)[/COLOR]
amule-utils-gui - graphic utilities for aMule
```

junming, 

I suggest you start these from /etc/rc.local.

---

