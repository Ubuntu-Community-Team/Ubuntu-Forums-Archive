---
title: "planning a server build"
date: 2013-05-05
forum: Server Platforms
---

### Post by Scrumps on 2013-05-05
I have been trying to plan out a server, but unfortunately everything I have come up with somehow has a hurdle one way or the other.

I was wondering if someone could suggest the best way to do this.

I would prefer a ubuntu server base, only because it doesn't have a bunch of extra crap installed on it. I know I am also going to hear some cringes when I say that it needs a GUI on it as well.

The server will be running:r
Apache2, BIND9, ISC-DHCP, Samba, postgresql & sqlite3, webmin, subsonic & musiccabinet, RealVNC 5.0.5, rtorrent/rutorrent or deluge, ssh server, a IRC Client, DLNA server, OpenVPN-AS, postfix, logwatch

I would prefer running it with ubuntu server because like I mentioned, I can keep all the extra stuff to a minimum, since this is going on a somewhat old box. It is a dual core, but has plenty of memory.

Anyways, I was trying to get a feel for this earlier today, I installed ubuntu server, got a desktop environment installed, and then went to make sure everything was usable. While this could be an issue of the VM, it takes a huge amount of load to finally boot the thing, during this stall process, I lookup up the load:
load average: 33.63 22.62 12.37

Not to mention, I seem to have some issues with certain programs, for instance, the Network Manager applet sees that I have a wired connection, but it won't let me configure it at all. Every time I click "Options...", I get the following error: "Error editing connection | Did not find a connection with UUID '(null)'. 

The only commands I have done were:
sudo aptitude install gnome xorg

I was wondering if I could just get some help planning, and eventually later on configuring if I run into any troubles.

I was going to attempt the same thing with arch, seeing which one I liked better. Unfortunately, arch currently has a bug with their latest live cd iso where networking is completely broken, and I had issues with the last one. So, some planning would definitely be helpful.

---

### Post by boogerama on 2013-05-05
If you're really set on using a GUI give CentOS a try.  Or if you prefer to stick with Ubuntu you can run Webmin.  It's not a traditional GUI but you get a lot of GUI like functionality via your browser.

---

### Post by Scrumps on 2013-05-05
I am familiar with CentOS, and well, at the time of using it I really didn't like it. I would prefer to stick with Ubuntu only because all of my config files are already setup for Ubuntu, and for the things that matter (samba, DHCP, DNS, and possibly apache) I would like to stick with it.

I am familiar with webmin as well, but I have found that some of the features don't work well all the time, and would prefer a GUI when it comes to something like that. Right now, I am testing it out on a spare laptop I have, so the problem I was experiencing earlier does seem to be with the VM specifically. 

While I know RealVNC 5.x isn't open source, I have been trying to figure out their config file with a trial key to see if it work before I drop money on it to use with all my systems (Windows and Linux). Unfortunately, I have been having some issues with getting the config file to run in their virtual mode, which is basically a gateway that then creates sessions after you provide authentication details. For reference the man pages I am using are located here:
[http://www.realvnc.com/products/vnc/documentation/5.0/misc/reference/](http://www.realvnc.com/products/vnc/documentation/5.0/misc/reference/)
[http://www.realvnc.com/products/vnc/documentation/5.0/misc/reference/Xvnc.html](http://www.realvnc.com/products/vnc/documentation/5.0/misc/reference/Xvnc.html)
[http://www.realvnc.com/products/vnc/documentation/5.0/misc/reference/vncserver-virtuald.html](http://www.realvnc.com/products/vnc/documentation/5.0/misc/reference/vncserver-virtuald.html)


If I understand correctly. I should be able to place a config file here:
/etc/vnc/config.d/Xvnc
/etc/vnc/config.d/common.custom
/etc/vnc/config.d/vncserver-virtuald

But maybe I just don't have the config file setup correctly. I will post it when I am near that machine again.

Here was the config I was using:
-geometry 1920x1080 -RandR=1920x1080 -DisableTrayIcon=0 -AllowHTTP=0 -EnableRemotePrinting=0 -EnableChat=0 -IdleTimeout=0

---

### Post by boogerama on 2013-05-05
I hear you about Webmin, t's fine but there are some minor annonyances.  As for CentOS I really liked it.  It did require more work than Ubuntu but once it was up and running it was solid.  The thing I liked best about Ubuntu Server 12.04 was that it just worked right off the bat.  I loaded LAMP, BackupPC, Webmin and after a few minutes configuring a small handful of files everything just worked!

I've never spent much time trying to get a GUI going on server 12.04.  If you're succesful in getting it operational please post a tutorial, it would be a nice weekend project.

---

### Post by Zukaro on 2013-05-06
You might need to install the network manager for gnome if it's not working, although I'm not sure.  Just installing gnome should install everything that gnome includes (at least, that's my experience with KDE on ArchLinux).  If you can't manage to get the network manager working however, you could just configure your network via the command line.

```
sudo nano /etc/network/interfaces
```
(or whatever editor you prefer)

That will bring you to a config file that looks like this:

```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp
```

Change dhcp to static and add the following:

```

address 192.168.3.6
netmask 255.255.255.0
broadcast 192.168.3.255
gateway 192.168.3.1
network 192.168.3.0
dns-nameservers 208.67.222.222 208.67.220.220 208.67.220.222
```

Swap out those IP's with the ones you need (this is the config file from my server).  If you're using a wireless connection I'm not sure how to do it however.  You don't need to add the dns-nameservers part however unless you're using domain names to access things (so if you apt-get things you'll have to specify the mirror by IP rather than URL in the file which contains all the mirrors).  I'm using OpenDNS's IP's for the name servers but you could point this at your router if your router is setup to use a DNS server (my routers are set up like that however, but I didn't think about that until now :P).  And if you have multiple DNS servers you're pointing at you separate them with spaces.

---

