---
title: "install linblock on amd64"
date: 2006-02-16
forum: Server Platforms
---

### Post by Josef K. on 2006-02-16
[linblock]("http://www.dessent.net/linblock/"), like peerguardian, is a sw that automatically update iptables to block *malicious* ip

it need 3 perl module ( Net::IP, IPTables::IPv4, and LWP::Simple ) to setup properly
unfortunately I cannot find an amd64 version of IPTables::IPv4 
it's supposed to be libiptables-ipv4-ipqueue-perl but seems there's no amd64 package, and cpan failed the manual installation

it there anybody using linblock on amd64 that can help me? :-k

---

### Post by jamesford on 2006-02-20
i cant get it to work on 32 bit either :/

---

### Post by Josef K. on 2006-02-20
if your problem is just dependancies, on 32bit you can forget cpan and install via apt libraries you need 
just make a search in [http://packages.ubuntu.com]("http://packages.ubuntu.com") to find _in which packages_ are they

I wonder once installed how it works
on windows peerguardian doesn't take too much resources and don't slow down so much the connection, but under linux I've heard about lots of pg crashes, that's why I maked a try to linblock, but liblock uses iptables, so I guess things could be dramatically slow down :-k

---

### Post by Nutterpc on 2006-04-26
Linblock eh?

Interesting concept......given a few weeks to play about with it, I'll be able to tell you what this thing is capable of :)

---

