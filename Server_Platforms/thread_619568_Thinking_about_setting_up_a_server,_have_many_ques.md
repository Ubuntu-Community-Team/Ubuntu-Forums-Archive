---
title: "Thinking about setting up a server, have many questions"
date: 2007-11-21
forum: Server Platforms
---

### Post by Ould on 2007-11-21
Hi Everyone,

I am thinking about setting up server using Ubuntu with some old hardware that I have laying around. PC is in a large server sized tower so will have room for lots of drives and cards if needed. I believe the hardware is an AMD Socket A CPU, a 2000+ possibly if I remember correctly with most likely 512 megs of ram. This should be sufficient I think. Basically I want my server to act as a router/firewall, mythtv backend, VPN. webserver(for at least Mythweb and any other web based apps I install).

More or less I am not sure which apps to use for the different parts of my config or where to start really. Right now I have a combined MythTV frontend/backend setup running Ubuntu 6.10 and I also have my desktop which is currently running Arch linux which I also like. I will likely leave my desktop more or less as is and keep my Myth Front/Backend machine as hopfully a diskless frontend to keep it cool and quiet. I have a couple other network enabled devices in the network as well. A Roku media streamer and Toshiba HD DVD player and Soon a PS3. Just to give you an idea of my network. This is all behind a basic Linksys Router(which is not capable of having DD-WRT installed unfortunately).

With the server I am hoping to replace the router. Here is a list of things I am hoping to do:

1. Router - not sure which application to use here
2. Firewall - not sure here either
3. Myth Backend - Know what I am doing here, replicating my old setup and moving the tuners to this machine
4. Web server for web apps - apache with php, familiar with this from my MythTV box for Mythweb
5. VPN access to my complete LAN - OpenVPN?
6. Slimserver - got this now on my Myth box, use it with my Roku right now but may get a Squeezebox at some point
7. Torrent client - may use Torrentflux as it has a web app, any recommendations here?
8. newsgroup program - currently use sabnzbd and will probably continue that
9. File sharing for my lan as most of my storage will go in this box - Samba? Maybe some sort of UPNP app as well for media streaming, Myth has it but it doesn't seem to work well on some devices.
10. anything else anyone recommends or things I have forgotten.

Hopefully this message isn't too confusing, lol. But I would love some recommendations, places to start. I will likely base this server on the latest Ubuntu which is currently 7.10 I believe. 

Thanks,

Kevin

---

### Post by colo on 2007-11-21
1. Router - not sure which application to use here
 - Netfilter/Iptables. There's no choice to be made, as there are no alternatives. The provided solution is fantastic, though.


2. Firewall - not sure here either
 - Same as 1.)


3. Myth Backend - Know what I am doing here, replicating my old setup and moving the tuners to this machine
 - Sorry, don't know anything about MythTV.


4. Web server for web apps - apache with php, familiar with this from my MythTV box for Mythweb
 - There's Lighttpd, too - but Apache is much more flexible, and therefore my recommended solution.


5. VPN access to my complete LAN - OpenVPN?
 - OpenVPN is the best VPN solution out there imho. I got to deal with MS ISA (PPTP), Cisco VPN (proprietary IPSec magic), and OpenVPN a lot at work, OpenVPN is by far the most painless alternative.


6. Slimserver - got this now on my Myth box, use it with my Roku right now but may get a Squeezebox at some point
 - Don't even know what that is ;)


7. Torrent client - may use Torrentflux as it has a web app, any recommendations here?
 - ssh + screen + rtorrent. Alternatively, rtorrent plus one of its web interfaces (needs manual compilation of rtorrent, though).


8. newsgroup program - currently use sabnzbd and will probably continue that
 - Sorry, can't help.


9. File sharing for my lan as most of my storage will go in this box - Samba? Maybe some sort of UPNP app as well for media streaming, Myth has it but it doesn't seem to work well on some devices.
  - I use NFSv4, HTTP/HTTPS, SFTP and Samba in parallel.


10. anything else anyone recommends or things I have forgotten.
 -  You might want to do some fancy telephony and fax stuff by using Atserisk and Hylafax.

---

### Post by Ould on 2007-11-22
Thanks for the response Colo. Much appreciated. I would like to be able to manage/administer this through a web app. Is something like webmin a good way to go here or is there better alternatives. I came across something called ebox as well but not really sure what the best option is or if it is even recommended.

Thanks,

Kevin

---

### Post by Chayak on 2007-11-22
Just a suggestion for you but attatching a box loaded with all those services directly to the net when you don't have a lot of experience with security is generally a bad idea.  A specilized routing distro as a gateway is fine but a home router between a server and the internet is a sound suggestion

Most web servers are behind hardware firewalls or at least routers that direct the traffic to a machine.

Do what you will but if you think linux servers can't be cracked you're woefully mistaken.

---

### Post by mellowd on 2007-11-22
Unless you're pretty good with iptables I'd aggree with the above. If at all possible, get yourself a hardware firewall

---

