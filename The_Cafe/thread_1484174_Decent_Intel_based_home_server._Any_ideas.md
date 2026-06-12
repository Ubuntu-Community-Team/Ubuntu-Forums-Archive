---
title: "Decent Intel based home server. Any ideas?"
date: 2010-05-15
forum: The Cafe
---

### Post by PryGuy on 2010-05-15
Good day to you all.
I'm thinking of building a decent Intel based home server in the future. I'm using Intel E5300 based server and I'm quite okay about it, but I'm going to upgrade it soon. I'm about to spend around $1000-1500 on all that. I have ICS/Firewall, Bind (with DDNS), DHCP, Samba, Squid, SSH, CUPS, LAMP stuff running on top of Ubuntu Server. RAID 1 (mirror) is also planned. Your ideas please? Thank you in advance!

---

### Post by Sporkman on 2010-05-15
You can get a good Intel Atom-based machine (which would handle everything just fine) plus a couple of HDs for about $500.

---

### Post by PryGuy on 2010-05-15
Well, I love Atom, I'm absolutely fond of it, but I'd love to have some more horsepower. I don't think Atom is more powerful than my current setup based on Intel E5300. Is it possible to go for low end Xeon with such a budget?

---

### Post by CharlesA on 2010-05-15
> **Sporkman said:**
> You can get a good Intel Atom-based machine (which would handle everything just fine) plus a couple of HDs for about $500.

+1 to Atoms.

I'm running a crappy dual core pentium with 4GB of RAM with no problems.

---

### Post by cariboo on 2010-05-15
I have to ask, what you intend on using the server for, if your current setup works the way you want it to, maybe just adding a raid card and more drives would suffice.

I have an E5400 based server with 2GB ram and 3TB of disk space, I use it as a file server, internal web server with php and mysql. Most of the time it sits there idling at less than 1% cpu usage, I have never yet seen more than 10% cpu usage even when serving media files to multiple computers.

---

### Post by cascade9 on 2010-05-15
> **PryGuy said:**
> Well, I love Atom, I'm absolutely fond of it, but I'd love to have some more horsepower. I don't think Atom is more powerful than my current setup based on Intel E5300. Is it possible to go for low end Xeon with such a budget?

The atom has way less horsepower than the E5300. 

[http://www.cpubenchmark.net/cpu_list.php](http://www.cpubenchmark.net/cpu_list.php)

You should be able to get a dual xeon for $1500, but it would probably be older CPUs, etc. An i7 (socket 1366) would probably faster for general use, and not that much slower at heavy CPU tasks. If you really want dual CPUs, AMD opterons are more affordable.

---

### Post by CharlesA on 2010-05-15
I've got an E6500 running a 4TB RAID 5 that serves a few machines. The CPU usage rarely goes above 10% unless I am running VMs on it.

---

### Post by PryGuy on 2010-05-15
Well, I'm fine with my current setup as I said, except for one thing: my disk subsystem chokes if I load it (perform a disk to disk operation and stream a video file to my media center simultaneously for instance). Maybe the best thing is to upgrade it only with a good RAID controller. The perfect is the enemy of the good. Linux server is almost perfect itself though... :)

The thing is I'm a system administrator and I have to feel all the bells and whistles of a powerful system at home before I start offering it to clients. And there's another philosophical question comes to that, do the clients really need a powerful system for common tasks if their servers are Linux powered? :)

---

### Post by Sporkman on 2010-05-15
When it comes to servers, bandwidth will be the limiting factor way before CPU power, unless you're doing number-crunching stuff.

A plus to getting an Atom is its low energy usage (my own atom-based home server running two HDs in RAID-1 runs off a 65W power supply).

---

### Post by The Real Dave on 2010-05-15
You could try for something like my Intel server, a 1.7Ghz Pentium IV (Socket 478, 256kB L2) with 384MB of RAM and a 500GB data drive, with an 8GB OS drive. 

This server runs [LIST]
[*]Squid Proxy
[*]Squint (Squid Monitor)
[*]NFS and Samba
[*]SSH
[*]rTorrent
[*]Firefly (mt-daapd)
[*]a LAMP stack
[*]Apt-Cacher-NG
[/LIST]

It only serves 4 computers, and the web pages on the LAMP stack are just for monitoring and links, completely internal. 

I'll admit that I'd like more RAM in there, at the moment it's using ~200Mb with 100MB of swap also. Squid is the heaviest, followed by Apt-Cacher-NG, which have caches of 6.1 and 2.9GB respectively. It's been up for 82 days running 9.10 Server x86 without a hitch, and I love it. 

It's quiet, and temps are generally ok, though one earlier error in an RSync script caused it to hit ~50C, both case and CPU with the disk approaching 45C. Understandable though, as this was after a few hours of compressing and sending RSync'ed data (in the region of 230GB). From then on I do my backups without compression >.<



My point that I've taken so long to get to is, that if you don't need the power for encoding or similar, why waste the electricity? It'll probably spend most of it's time idling, and you want it to idle efficiently. My server is in the region of 45Watts at idle I believe. It costs me about &#8364;50 a year. The hardware, bar the 500GB drive and the PCI RAID card were all salvaged, so the whole machine was under &#8364;60. 

If you don't need all that power, don't waste your money, or the world's electricity on it :D





If you do though, go mad, get yourself some dual quad cores and at least 12GB of RAM. If asked, you can always put it down to "Future Proofing" ;)

---

