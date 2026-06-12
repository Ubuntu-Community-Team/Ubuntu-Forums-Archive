---
title: "dedicate server resources?"
date: 2007-09-23
forum: Server Platforms
---

### Post by joeashcraft on 2007-09-23
How do I dedicate certain resources such as bandwidth, memory and processor usage to specific applications?

I have a [LAMP/SSH/NFS/TorrentFlux server]("http://largo.mine.nu/") setup on a 700MHz P3 computer. How can I make sure that Apache still responds when I'm copying files over NFS? Or that NFS still responds when I'm downloading torrents? How can I make sure that Apache gets priority 1 over these other apps?

I've also thought that maybe I'm trying to do too much at once... but that idea quickly fades when I remember that I'm not using windows (not to bash windows, that's just a main reason I switched)

TIA!

---

### Post by kidders on 2007-09-24
Hi there,

What you're looking for is called "traffic shaping", I'd say. It's a little complicated to start off with, because Linux doesn't insulate you very much from the protocol-level underbelly of how network packets are prioritised and queued for transmission. If you can manage to wrap your head around it though, you can get pretty good control ... especially over outgoing data, such as responses to HTTP requests.

As far as your CPU is concerned, you need to be a little cautious. Most people approach your problem from the opposite direction ... ie how to *limit* the resources something like Apache can get hold of. Since you're trying to guarantee your web server the use of your CPU when it needs it, it's important not to compromise yourself in security terms, by inadvertently creating a situation where a bug or malicious attack could cripple your box.

One of the easiest ways to control resource usage on a box is with /etc/security/limits.conf.

---

### Post by HermanAB on 2007-09-24
Google for 'iptables rate limit'.

Cheers,

Herman

---

### Post by netlogic on 2007-09-24
For bandwidth: go to google and search for docs by typing, "iptables tc"
memory: do you mean how much cache you can reserve?
process: 
a) man renice and man nice 
b) launch top, hit h, and control renice that way. 
c) htop (samething as top, but better gui)

---

### Post by joeashcraft on 2007-10-07
Thanks. I used the limits.conf file to set up some basic user limits.
Now I'm trying to learn of traffic control via iptables :)

---

