---
title: "Home media server recommendations"
date: 2011-05-10
forum: Server Platforms
---

### Post by stealth. on 2011-05-10
I will be putting Ubuntu on my home server (about to order within a week or so).
 
1. Good recommendation for a wifi card, or should I just go eth0?
 
2. Will I just be able to open the file on my "main" computer and watch a movie over the network?
 
3. Any personal recommendations for a CLI torrent program?, I'm going to download torrents from afar [-d(:D)b-]
 
4.Best way to install Ubuntu Server w/o a monitor, or should I just hook my monitor up to it until I get ssh working?

---

### Post by Lars Noodén on 2011-05-10
> **stealth. said:**
> 
3. Any personal recommendations for a {text-based} torrent program?, I'm going to download torrents from afar [-d(:D)b-]
 

[btpd](http://packages.ubuntu.com/natty/btpd) is nice.

---

### Post by arrrghhh on 2011-05-10
1. I'd recommend eth0/hardwire if at all possible.  You can get a server going on wifi, but for stability, sanity and speed - go with the wire ;).

2. What is your 'main' computer?  Also, do you want to stream the file like UPnP or simply just browse & play like samba/NFS?  I'd use NFS if the machine is Mac or Linux, samba if it's Windows.  For UPnP I really do love PS3MediaServer - it works on anything that supports UPnP/DNLA, not just the PS3.

3. rtorrent - great software.  Coupled with rutorrent, it is simply unbeatable for versatility and low footprint.

4. You'll need a monitor to do the initial install/setup - once you get the network working and ssh, everything else can be done remotely ;).

---

### Post by Jose Catre-Vandis on 2011-05-10
1. Good recommendation for a wifi card, or should I just go eth0?

[COLOR="Sienna"]A. More reliable to go wired/eth0 if you can. If you must go wifi, get one that matches with your wirless router for compatibility, or perhpas have a look at Powerline (run over electrical system)[/COLOR]

2. Will I just be able to open the file on my "main" computer and watch a movie over the network?
[COLOR="Sienna"]
A. Yes. I suggest you serve with nfs, with samba for windows machines[/COLOR]

3. Any personal recommendations for a CLI torrent program?, I'm going to download torrents from afar [-d()b-]

[COLOR="Sienna"]A. For simplicity, aria2c or use transmission-cli[/COLOR]

4.Best way to install Ubuntu Server w/o a monitor, or should I just hook my monitor up to it until I get ssh working?

[COLOR="Sienna"]A. You'll struggle to set it up without a monitor, unless you absolutely know the install sequence and the commands required, so hook up a monitor for the installation / setup, then ssh/vnc for operation and configuration. Use screen so that you can run things and disconnect while they are running.

I have a monitor on my server all the time, but only need to use it once a month (saves lugging it back and forth)

I use screen with four instances, more than enough for running torrents, encoding video, downloads with aria2c, and general admin[/COLOR]

---

### Post by stealth. on 2011-05-10
> **arrrghhh said:**
> 1. I'd recommend eth0/hardwire if at all possible.  You can get a server going on wifi, but for stability, sanity and speed - go with the wire ;).

2. What is your 'main' computer?  Also, do you want to stream the file like UPnP or simply just browse & play like samba/NFS?  I'd use NFS if the machine is Mac or Linux, samba if it's Windows.  For UPnP I really do love PS3MediaServer - it works on anything that supports UPnP/DNLA, not just the PS3.

3. rtorrent - great software.  Coupled with rutorrent, it is simply unbeatable for versatility and low footprint.

4. You'll need a monitor to do the initial install/setup - once you get the network working and ssh, everything else can be done remotely ;).

Its going to be a high-end Windows gaming rig. I'll probably put Mint on it too.

1. Ok I'm going eth0

2. Looks like I'm going to use samba/nfs

3. I'll checkout all the programs one by one, I'm thinking I might like transmission-cli as I use the GUI

4. And I will temporarily use my monitor to set the machine up.

Thanks everyone I appreciate it. I'll still be monitoring this thread if anyone else posts.  

:)

---

