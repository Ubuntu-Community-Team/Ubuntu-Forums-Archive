---
title: "What kind of server do run at home ?"
date: 2013-12-25
forum: The Cafe
---

### Post by linuxyogi on 2013-12-25
Hi,

Here I often read people saying they run servers at home. Personally I have used Linux only as a desktop OS.

I just want to know what possible types of servers people usually run at home.

TIA.

---

### Post by Iowan on 2013-12-25
I have one box as a DHCP/DNS server, another as LAMP server. I think both of them have Samba shares, and SSH access. The LAMP server is supposed to share music, too... but I don't have it properly configured, yet.

---

### Post by linuxyogi on 2013-12-25
> **Iowan said:**
> I have one box as a DHCP/DNS server, another as LAMP server. I think both of them have Samba shares, and SSH access. The LAMP server is supposed to share music, too... but I don't have it properly configured, yet.

Samba shares are for your Win machines.

Your home network must be quite large coz you maintain a DHCP server. If you don't mind how many PCs/laptops are connected to this network ?

Please tell me whats the use of the DNS server here ? I mean isnt the local resolver doing its work ?

I am asking all this coz I may implement these types of servers myself.

I did my MCSA (Win server 2003) 3 years back. I plan to learn configuring servers on the Linux platform soon.

---

### Post by Bucky Ball on 2013-12-25
I run a Raspberry Pi as a media server. That is running RaspBMC. It allows me to access all music/video (and anything else) from the three computers on the network on my TV in the living room. Nice. (as well as online content from Youtube, iView, etc.).

All devices have static IPs. Just easier that way, at least the way I see it. ;)

---

### Post by CharlesA on 2013-12-25
> **linuxyogi said:**
> Samba shares are for your Win machines.

Your home network must be quite large coz you maintain a DHCP server. If you don't mind how many PCs/laptops are connected to this network ?

Normally your router will do DHCP, but sometimes it's more efficient to have a dedicated DHCP/DNS server for your internal network so DNS is updated automatically when DHCP assigns ip address.

> Please tell me whats the use of the DNS server here ? I mean isnt the local resolver doing its work ?

I use it for local name resolution. You can also use it as a caching name server, so your machines don't have to query an internet DNS server for the addresses.

I use my server for VMs, File storage and (hopefully soon) media streaming.

The VMs are using for running Win7 and 12.04, but both of those are from when I run VBox, so they sit mostly unused except when I need to access the CrashPlan GUI.

A few of the other VMs I have running are OpenVZ and are duplicates of my production machines.

---

### Post by MartyBuntu on 2013-12-26
Xubuntu 12.04 LTS that's used primarily as a storage server. Been sitting on a shelf in my basement since 2007 with a gigabit ethernet connection.

[IMG]http://i.imgur.com/FgEYFs.jpg[/IMG]

I also do OTA captures on a Hauppauge 1800 PCI-E card, through Kaffeine. The card is hooked up to an 8 bay ATSC/OTA antenna on my roof.

Mostly, I access and administer this server by VNC with **xtightvncviewer** on my main workstation.
Otherwise, I just move files back and forth from my workstation and laptops to the server with **Filezilla's** sftp option.

---

### Post by lz1dsb on 2013-12-27
Well... I have a fairly old laptop which I use for the purpose. It's a Dell Studio 1555. It's always on and I often use it to get a remote desktop connection, and basically do anything. I run on it whatever I need to run, because Linux is so... flexible :)

---

### Post by SeijiSensei on 2013-12-27
> **CharlesA said:**
> I use it for local name resolution. You can also use it as a caching name server, so your machines don't have to query an internet DNS server for the addresses.

Like Charles, I have a local DNS server that resolves names on my local network.  It also uses DNS forwarding to query a client's private server so I can resolve names in its network as well.  The client's DNS server is visible via an OpenVPN tunnel.  My server routes all the traffic to the half-dozen or so VPNs I maintain.

The machine also handles mail for my domain and maintains an email listserver.

I store anything worth saving on the server which is backed up nightly.  Along with various documents, it also has all our photographs, music, and video files.  I use NFS to stream media from the server to client machines.

This machine is a fairly old Dell PowerEdge.  I've experimented a bit with a Raspberry Pi like BuckyBall uses and am considering using that to replace the Dell and cut down on my electric bill.

---

### Post by lykwydchykyn on 2013-12-28
Got a Pentium 4 running Debian, it does many things:

- Samba shares of our pictures &  files
- media server using mediatomb
- web filter for the kids with Dansguardian/squid
- ssh gateway from the outside
- backs up all the laptops/desktops using an rsync daily
- runs a variety of web applications:

  -- dokuwiki
  -- moodle
  -- iPython notebook
  -- bunch of custom ones I wrote

- APT proxy for all our debian/ubuntu boxen
- Print server

Probably some other stuff I'm forgetting too.

---

### Post by hoopia on 2013-12-28
Had an old Dell desktop running Mint OS, used it as a media server for my home network. After going through about 5 different distros, I decided on Mint as it blew the others out of the water in terms of video performance.

---

### Post by r3dd on 2013-12-29
I have my main computer set up with an nfs4 shared folder for my home network. Not much beyond that. Eventually I hope to configure it to be the compiler for my laptop to ease the load on it. That is still a ways down the road though.

---

