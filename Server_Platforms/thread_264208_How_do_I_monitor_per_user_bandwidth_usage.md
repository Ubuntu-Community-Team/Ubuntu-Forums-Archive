---
title: "How do I monitor per user bandwidth usage?"
date: 2006-09-24
forum: Server Platforms
---

### Post by peteyg on 2006-09-24
I have an Ubuntu server that many people are connecting to via SSH.  These people are tunneling their network traffic for certain applications through my server (they are World of Warcraft addicts behind a super restrictive firewall, and I'm helping them out).  I would like to make sure that they don't use my server to download TV shows and stuff (the bandwidth the server has available is limited).

I need an easy way to check, using just the command line, how much bandwidth each user has been using.  I seriously doubt I'm the first server owner who's had to deal with this, so I'm sure there is some default tool I don't know about, or some simple solution for finding this kind of information.  Unfortunately my initial research didn't quite turn up exactly what I was looking for.

I would ideally like to be able to narrow the usage down to specific users; there are enough of them that actually asking each one if they're being a lamer or not is difficult.

Any help or suggestions, relevant links, or nudges in the right direction would be most appreciated.  Thanks!

---

### Post by Miademora on 2006-09-24
I would restrict portforwarding to WoW Port 3724 TCP. Although im not sure if thats the correct one.

---

### Post by peteyg on 2006-09-24
That's a possibility, but I really don't care what everyone is doing...   so long as it doesn't suck up bandwidth.  I think people are playing Diablo 2 and other crazy stuff, and I don't really want to manage all of those weird ports. :P

---

### Post by Miademora on 2006-09-24
Then you might try one of the accountingpatches available for openssh like [here]("www.google.com/search?q=openssh+traffic+accounting+patch")

---

### Post by nix4me on 2006-09-24
You need to use traffic shaping.

lartc is a great resource to learn about it.

nix4me

---

### Post by peteyg on 2006-09-25
traffic shaping is really a lot more work than I need/have time for.  It also wouldn't, as I understand, help me find which users are using too much bandwidth.  I also really don't care about restricting bandwidth usage for various applications, I just want to find out how much bandwidth each user is using so I can deal with it myself.

The OpenSSH patch sounds great, but there's a 95% chance I would screw up ssh in trying to apply a patch, compile from source, install, and then configure.  If I mess up ssh, then there's no fixing it (I am connecting remotely, and nobody with linux experience has physical access to the machine).

Why wouldn't such functionality be incorporated into OpenSSH by default?  There have to be a lot of people who would find this feature incredibly useful.

---

### Post by airtonix on 2007-04-14
first when you do find out if they are going to need to be shaped....how are you going to do this without something like [wondershaper]("http://freshmeat.net/projects/wshaper/") ?

second, your talking about bandwidth usage reporting. so these are things to check out : 

for delayed log reports : munin, cacti, bandwidthd.
for real-time monitoring : jnettop(for nettraffic), htop(for monitoring each users ssha access cpu and mem usage)

hope that helps.....you will need to do shaping one way or another....even if you use the resitive nature of your tounge to bridge the copper wires to the router? lol

12:47 PM : just found this : [monowall]("http://m0n0.ch/wall/features.php") it has traffic shaping as one of its features. the iso is only 5 1/2 megs.

---

### Post by garcia01 on 2007-06-05
Hi there,

Bandwidthd doesn't really work to install. The .deb package seem to give problems. Has anyone a solution to install under Feisty Fawn?
Thx. for any help.

---

