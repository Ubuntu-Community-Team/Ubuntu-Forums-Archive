---
title: "Looking to make Ubuntu Internet Gateway"
date: 2007-07-06
forum: Server Platforms
---

### Post by kill4killin on 2007-07-06
Hello all,

I live on a college campus where every dorm room gets 1 ethernet port per person in the room. Until recently I have been using just a normal switch to multiply my ports to 5 ports so that I can connect all of my equipment to the network. However, I now have a laptop that I often bring to friends houses, work and just pretty much anywhere I go, that accumulates a lot of files from the places that I visit through the things I download or work that I do. Some of these files are rather large and at my school they have a port throttling system that gives priority to the more commonly used ports or ports that are used for academic purposes leaving other applications and computer operations with little to no bandwidth. The biggest problem for me that this brings about is through my use of windows file sharing that I use to transfer files from my laptop to my desktop and back again. I am running Ubuntu 7.04 on my laptop and Windows XP on my desktop so I use samba to accomplish this. However, because of this port throttling system that they have and the fact that I am still transfering my files through the schools network it is slowing down my transfer significantly (yesterday 5GB of data took 20 hours to transfer a distance of about 10 feet). To solve this problem I want to setup an internet gateway using my old PIII computer so that it can accept the school IP address and I can still get access to the internet as I always have been able to. But from now on when I transfer files between my machines I can keep it on a local level instead of bouncing all over the schools network and having my transfer speeds throttled.

So my real question is this. I have never done this before so I was wondering what software I would need to put on an installation of Ubuntu 7.04 server edition in order to achieve the above described goal? I also have no idea how to setup something like this once all of the software is installed so any setup tips or guides would be appreciated as well.

Thank you in advance, I know that was a lot to read;)

---

### Post by koenn on 2007-07-06
With iptables you can have that old PC get an ip address on your school network, and with a 2nd NIC and a hub you can have whatever PC, laptop in a local network, but connected to the school network / internet through the 'router' PC. 

This should get you started :
[http://users.telenet.be/mydotcom/howto/lanconnect/router/linux.htm](http://users.telenet.be/mydotcom/howto/lanconnect/router/linux.htm)

it's quite old & Debian-based, but will work with ubuntu (server) as well

---

### Post by kill4killin on 2007-07-07
Thank you koenn. I took a look at that but a friend recommended me to a distro called clarkconnect since I needed to get up and running as fast as possible this time around. When I have a little more time and a second box to set up ubuntu server on I will do so, again thanks for the link it was pretty much exactly what I needed.

---

### Post by koenn on 2007-07-07
y're welcome

---

### Post by bmathis on 2007-07-07
i understand what youre trying to do, but i think its gonna be more work than whats need. The easiest thing is go buy a cheap 5 port router. This will put you on your own network to be able to transfer your files.

Just a thought, no need to reinvent the wheel when you can buy one for $20

---

