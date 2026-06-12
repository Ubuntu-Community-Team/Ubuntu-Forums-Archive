---
title: "server for what ? usefull ?"
date: 2013-10-17
forum: Ubuntu, Linux and OS Chat
---

### Post by ClimateCrisis on 2013-10-17
hi
i am getting to be very interested in linux, ubuntu seem for now a good place to start.

i figure to learn, a server might be good to learn with that for all the command ,etc.

but is there any benefit for it ?
i mean let just say i succeed in learning how to play with a server with linux.
what advantage is there to have a server at your house if u have no company for example ?
more security ?
once u know how to run a linux server, some opportunity might happens?
waste of time ?

thx

ps: any link is appreciate as well if no one feel to make  a text :)

---

### Post by codybricesands on 2013-10-17
Hey there, If you are interesting in learning the Ubuntu command line you should check out this article: [https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal)
Also if you would like to run a home server it might be easier for you to learn off the desktop version of Ubuntu first before using server to get a understanding of what your doing when it comes to the terminal. It's how i learned atleast :) Ubuntu comes with a wide range of applications out there for you to use and it is very secure. And there are many tutorials for you out there for you to setup your server with! The advantage of using Ubuntu for a server is that it is fast reliable and easy to use once you get to know Ubuntu better. Make sure to check out [http://howtoubuntu.org/](http://howtoubuntu.org/) there you may find some useful tutorials there! Good luck!

---

### Post by papibe on 2013-10-17
Hi ClimateCrisis.

All of the services a server can provide are available in a desktop edition too. There's a matter of preference and how comfortable you feel with the command line.

As for learning purposes you wouldn't even need an actual machine. You could install it on a VM and the learning experience would be almost the same.

The benefits of an actual home server are many, however it would add value and sense to you only depending in your  tech needs.

Here are common services a home server could provide:
[LIST]
[*]File services (like a NAS):
[LIST]
[*][*]Backup service.
[*][*]Media repository.
[/LIST]
[*]Cache services:
[LIST]
[*][*]DNS relay or cache to speed up your Internet connection.
[*][*]Content transparent proxy to speed up browser page loading.
[/LIST]
[*]Download services (if you have a laptop or a dear desktop, it's always a good thing to turn them down at night and left the server do the job).
[LIST]
[*][*]Torrent download.
[*][*]Webcasts and RSS dowload.
[/LIST]
[*]Streaming services (combined with file services): Stream your music or movies to any device you want.
[*]Firewall: either replace your router security or add other layers of it.
[*]Etc.
[/LIST]

Hope that helps. Let us know how it goes.
Regards.

---

### Post by sandyd on 2013-10-17
> **papibe said:**
> Hi ClimateCrisis.

All of the services a server can provide are available in a desktop edition too. There's a matter of preference and how comfortable you feel with the command line.

As for learning purposes you wouldn't even need an actual machine. You could install it on a VM and the learning experience would be almost the same.

The benefits of an actual home server are many, however it would add value and sense to you only depending in your  tech needs.

Here are common services a home server could provide:
[LIST]
[*]File services (like a NAS):
[LIST]
[*][*]Backup service. - rdiff-backup, aerofs, OwnCloud, rsync
[*][*]Media repository. - samba, ftp (pure-ftpd), NFS
[/LIST]
[*]Cache services:
[LIST]
[*][*]DNS relay or cache to speed up your Internet connection. - dnsmasq
[*][*]Content transparent proxy to speed up browser page loading. - squid
[/LIST]
[*]Download services (if you have a laptop or a dear desktop, it's always a good thing to turn them down at night and left the server do the job).
[LIST]
[*][*]Torrent download. - Deluged, transmission-daemon/transmission, rutorrent
[*][*]Webcasts and RSS dowload.
[/LIST]
[*]Streaming services (combined with file services): Stream your music or movies to any device you want. - Plex, ps3mediaserver
[*]Firewall: either replace your router security or add other layers of it. - csf/iptables/dansguardian (internet filtering)
[*]Etc.
[/LIST]

Hope that helps. Let us know how it goes.
Regards.

Expanded the list with usable apps for each thing

---

### Post by papibe on 2013-10-17
> **sandyd said:**
> Expanded the list with usable apps for each thing
 :)

---

### Post by lingpanda on 2013-10-17
You could setup a Plex Media Server using Ubuntu.

---

### Post by tgalati4 on 2013-10-17
Go out and change the world.  Once you install the server and start playing with it, you will then want to install several frameworks and play with them:

[http://bitnami.org/stacks](http://bitnami.org/stacks)

---

### Post by ClimateCrisis on 2013-10-18
wow awesome ty!!

good idea in there imo :)

i just discover the possible "joy" of linux with elithecomputer guy on youtube and i want to expand it :)

ty for the links as well.

i guess i will need to buy a computer and put linux server on it .

would a old computer be fine for a small server at my house , and would it be better to have the max for ram in the computer i would use for a server ?
i mean the cache server suggestion to speed thing like internet connection and to load pages , and the streaming server as well ... does it matter if i a buy an old cheap computer and use it has a server ?

or like anything else, more recent the machine i buy to build me a server, the better for speed issue between computer communication .
what should i focus on, ram, cpu, or it would not matter much ?

guess i will have to learn some network info as well before i can make this work

ty 

ps: if i buy an old computer , can i use it for more then one server with it ? i guess so since i heard u can build virtual server on the same machine i think.
anyway, without virtualisation, i could put more then 1 kind of server on a cheap computer or not ?

like the file,cache and download server seem the most interesting for me :), just hope i could put all 3 server with ubuntu server on the same machine ?
lot of work ahead but seem fun work for now . Hope it will stay fun lol :)

---

### Post by Lars Noodén on 2013-10-18
> **ClimateCrisis said:**
> ps: if i buy an old computer , can i use it for more then one server with it ? i guess so since i heard u can build virtual server on the same machine i think.
anyway, without virtualisation, i could put more then 1 kind of server on a cheap computer or not ?

like the file,cache and download server seem the most interesting for me :), just hope i could put all 3 server with ubuntu server on the same machine ?
lot of work ahead but seem fun work for now . Hope it will stay fun lol :)

Usually the best way is to add the services all to the same machine.  You can fit Apache2 or Nginx, OpenSSH, Squid, Samba, and many others all on the same machine and they do play nice together.  That's the way UNIX and Linux are designed to work.  

If you want to you can set up a virtual machine in Qemu or Virtualbox for learning.  That way it's easy to take snapshots and undo a mess by reverting to a snapshot.  Running a VM wastes lots and lots of resources, both CPU and RAM, so you get a lot less machine for your money if you use a VM.  But running a non-virtual machine is better practice.

---

### Post by mörgæs on 2013-10-18
Yes, begin with some old hardware you have around. Don't buy expensive stuff until you are experienced (and maybe it won't even be necessary then).

I'm surprised noone has mentioned a web / LAMP server. It's very convenient to build web sites on a local server in stead of constantly uploading and testing.

---

### Post by Elfy on 2013-10-18
*Thread moved to **Ubuntu, Linux and OS Chat**.*

---

