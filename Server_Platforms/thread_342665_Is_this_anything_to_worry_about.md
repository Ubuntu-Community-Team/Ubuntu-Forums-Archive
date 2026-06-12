---
title: "Is this anything to worry about?"
date: 2007-01-20
forum: Server Platforms
---

### Post by Biggus on 2007-01-20
Hi there.

I've been running a little Apache server on my box, and I've noticed that for the previous 48 hours or so, one particular IP has been making repeated requests to me server.

> 82.9.95.39 - - [18/Jan/2007:21:00:19 +0000] "GET / HTTP/1.0" 200 3345 "-" "-"
82.9.95.39 - - [18/Jan/2007:21:23:43 +0000] "GET / HTTP/1.0" 200 3345 "-" "-"
82.9.95.39 - - [18/Jan/2007:22:23:06 +0000] "GET / HTTP/1.0" 200 3345 "-" "-"
82.9.95.39 - - [18/Jan/2007:22:56:43 +0000] "GET / HTTP/1.0" 200 3345 "-" "-"
82.9.95.39 - - [18/Jan/2007:23:01:38 +0000] "GET / HTTP/1.0" 200 3345 "-" "-"
82.9.95.39 - - [18/Jan/2007:23:26:30 +0000] "GET / HTTP/1.0" 200 3345 "-" "-"
82.9.95.39 - - [18/Jan/2007:23:50:33 +0000] "GET / HTTP/1.0" 200 3345 "-" "-"
82.9.95.39 - - [18/Jan/2007:23:58:14 +0000] "GET / HTTP/1.0" 200 3345 "-" "-"
82.9.95.39 - - [19/Jan/2007:01:46:26 +0000] "GET / HTTP/1.0" 200 3345 "-" "-"
82.9.95.39 - - [19/Jan/2007:01:52:14 +0000] "GET / HTTP/1.0" 200 3345 "-" "-"
82.9.95.39 - - [19/Jan/2007:01:58:04 +0000] "GET / HTTP/1.0" 200 3345 "-" "-"
82.9.95.39 - - [19/Jan/2007:02:03:14 +0000] "GET / HTTP/1.0" 200 3345 "-" "-"
82.9.95.39 - - [19/Jan/2007:02:31:05 +0000] "GET / HTTP/1.0" 200 3345 "-" "-"
82.9.95.39 - - [19/Jan/2007:02:37:10 +0000] "GET / HTTP/1.0" 200 3345 "-" "-"
82.9.95.39 - - [19/Jan/2007:03:41:38 +0000] "GET / HTTP/1.0" 200 3345 "-" "-"
82.9.95.39 - - [19/Jan/2007:03:46:14 +0000] "GET / HTTP/1.0" 200 3345 "-" "-"
82.9.95.39 - - [19/Jan/2007:04:04:54 +0000] "GET / HTTP/1.0" 200 3345 "-" "-"

(it goes on and on, I've edited it out)

82.9.95.39 - - [20/Jan/2007:13:17:20 +0000] "GET / HTTP/1.0" 200 3345 "-" "-"
82.9.95.39 - - [20/Jan/2007:14:21:01 +0000] "GET / HTTP/1.0" 200 3345 "-" "-"
82.9.95.39 - - [20/Jan/2007:14:32:31 +0000] "GET / HTTP/1.0" 200 3345 "-" "-"
82.9.95.39 - - [20/Jan/2007:14:35:26 +0000] "GET / HTTP/1.0" 200 3345 "-" "-"
82.9.95.39 - - [20/Jan/2007:14:37:29 +0000] "GET / HTTP/1.0" 200 3345 "-" "-"
82.9.95.39 - - [20/Jan/2007:14:58:56 +0000] "GET / HTTP/1.0" 200 3345 "-" "-"
82.9.95.39 - - [20/Jan/2007:16:01:52 +0000] "GET / HTTP/1.0" 200 3345 "-" "-"
82.9.95.39 - - [20/Jan/2007:16:48:27 +0000] "GET / HTTP/1.0" 200 3345 "-" "-"


Now, there doesn't appear, on the surface of things, to be anything particularly nefarious about this, but a quick nmap of the target show that it's running some pretty wacky services.

> Host cpc3-mfld3-0-0-cust806.nott.cable.ntl.com (82.9.95.39) appears to be up ... good.
Interesting ports on cpc3-mfld3-0-0-cust806.nott.cable.ntl.com (82.9.95.39):
Not shown: 1667 closed ports
PORT      STATE    SERVICE        VERSION
25/tcp    open     smtp           Microsoft ESMTP 6.0.2600.1
80/tcp    open     http           Microsoft IIS webserver 5.1
135/tcp   filtered msrpc
139/tcp   filtered netbios-ssn
443/tcp   open     https?
445/tcp   filtered microsoft-ds
593/tcp   filtered http-rpc-epmap
1025/tcp  open     msrpc          Microsoft Windows RPC
1032/tcp  open     msrpc          Microsoft Windows RPC
1433/tcp  filtered ms-sql-s
5000/tcp  open     upnp           Microsoft Windows UPnP
27374/tcp filtered subseven

It's highly unusual to see a windows box exposing *that* many services to the outside world, and I was just sort of wondering whether or not this

a) looks like a 'cracked' box (or maybe even a 'cracker')

and

b) should I be worried about it?

---

### Post by Error1312 on 2007-01-20
I don't really know a lot about security, but I'd say that looks like a denial of service attack (though, if true, I don't think there would be that much time between two attacks), or someone who is trying to run a port scan. Not sure though.

Also, the output of your nmap shows that the target is running subseven, which is known as a program often used by hackers.

Don't take my word for it, but personally, I wouldn't trust it, especially because it seems like it's been going on for a couple of days by now.

---

### Post by MJN on 2007-01-20
It's interesting granted, but if it is a DOS attack it's not a particularly effective one! ;)

I wouldn't worry about it - the only reason you ought to be worried is if you're running an insecure machine, in which case you should be worried anyway regardless of whether this particular IP is repeatedly connecting or not.

If it's bugging you block it with a firewall.

Mathew

---

### Post by Biggus on 2007-01-21
Thanks for that chaps.

I was (sort of) convinced in my own mind that it's nothing to worry about. I *am* running an Apache server, and someone *is* making http requests to that server, which *isn't*, in itself, particularly worrisome, after all, that's what I understand my Apache server is there for.

It just seemed unusual that someone would just be constantly checking up to make sure that I was still running it, that was all. I don't use php or mysql, and I haven't installed any Apache modules, so I am just in the dark as to what they actually want from me.

It *is* sort of bugging me, but I can't quite put my finger on why that should be, so I think I shall take your advice, and simply block it using Firestarter to save myself any more unnecessary stress.

Many thanks.

---

### Post by MrHorus on 2007-01-22
> **Biggus said:**
> Thanks for that chaps.

I was (sort of) convinced in my own mind that it's nothing to worry about.

Sorry to be the harbinger of doom here but please tell me I am not the first person to notice that the machine accessing you is running subseven, a notorious and well known trojan?

Repeated access attempts from ANY machine is ALWAYS something to worry about, more so if they are already compromised with one of the most well known trojans on the web.

You would be smart to block this IP and keep it as far away from your systems as possible.

---

### Post by Biggus on 2007-01-24
LOL

And it continues, this time with another 'botted' windows machine :

> 82.9.31.189 - - [24/Jan/2007:17:33:24 +0000] "GET / HTTP/1.0" 200 3345 "-" "-"
82.9.31.189 - - [24/Jan/2007:17:33:35 +0000] "GET / HTTP/1.0" 200 3345 "-" "-"
82.9.95.39 - - [24/Jan/2007:18:02:24 +0000] "GET / HTTP/1.0" 200 3345 "-" "-"
82.9.31.189 - - [24/Jan/2007:18:09:06 +0000] "GET / HTTP/1.0" 200 3345 "-" "-"
82.9.95.39 - - [24/Jan/2007:18:11:09 +0000] "GET / HTTP/1.0" 200 3345 "-" "-"
82.9.31.189 - - [24/Jan/2007:18:14:01 +0000] "GET / HTTP/1.0" 200 3345 "-" "-"
82.9.95.39 - - [24/Jan/2007:18:21:07 +0000] "GET / HTTP/1.0" 200 3345 "-" "-"
82.9.31.189 - - [24/Jan/2007:18:27:54 +0000] "GET / HTTP/1.0" 200 3345 "-" "-"
82.9.31.189 - - [24/Jan/2007:18:39:36 +0000] "GET / HTTP/1.0" 200 3345 "-" "-"

A quick nmap of the *other* IP reveals that it too is infected with the subseven trojan :

> Host client-82-9-31-189.manc.adsl.virgin.net (82.9.31.189) appears to be up ... good.
Interesting ports on client-82-9-31-189.manc.adsl.virgin.net (82.9.31.189):
Not shown: 1667 closed ports
PORT      STATE    SERVICE        VERSION
80/tcp    open     http?
113/tcp   open     auth?
135/tcp   filtered msrpc
139/tcp   filtered netbios-ssn
304/tcp   open     tcpwrapped
445/tcp   filtered microsoft-ds
593/tcp   filtered http-rpc-epmap
1025/tcp  open     msrpc          Microsoft Windows RPC
1433/tcp  filtered ms-sql-s
3689/tcp  open     rendezvous     Apple iTunes 5.0.1 (on Windows)
5000/tcp  open     upnp           Microsoft Windows UPnP
27374/tcp filtered subseven
Service Info: OS: Windows


I'm guessing that there must be some sort of resurgence of this trojan lately, which is simply leading to an increase in nefarious traffic.

---

### Post by psycho78 on 2007-01-24
> A quick nmap of the *other* IP reveals that it too is infected with the subseven trojan :

Here a small piece out of the nmap manpage:
[B] Filtered means that a firewall, filter, or other network obstacle is        blocking the port so that Nmap cannot tell whether it is open or        closed.

[/B]In all those posts I saw a filtered in front of the subseven port and also to several others... so you can't really tell whether there is a trojan behind it or not.....

---

