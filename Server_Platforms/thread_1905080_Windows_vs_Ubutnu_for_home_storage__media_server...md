---
title: "Windows vs Ubutnu for home storage / media server..."
date: 2012-01-06
forum: Server Platforms
---

### Post by nderic77 on 2012-01-06
I am thinking about setting up an expensive file / media server for our home sometime in mid to late 2012. The primary purpose is just to serve as a software RAID server to host movies, songs and other files, and to stream those on-demand. The purpose of the RAID is redundant backup. What are the advantages and disadvantages of each option ? So far as I see, the following apply:

Windows Home Server 2011:
easier setup and file sharing
software RAID support out of the box

Ubuntu Server 12.04 LTS (when it comes out):
Price (free)
Software Center - lots of open-source programs available

---

### Post by 1clue on 2012-01-06
Why not get a small office/home office NAS appliance?  Already set up for everything you want to do and a bunch of things you hadn't thought of, and almost certainly has Linux under the hood.

---

### Post by nderic77 on 2012-01-06
> **1clue said:**
> Why not get a small office/home office NAS appliance?  Already set up for everything you want to do and a bunch of things you hadn't thought of, and almost certainly has Linux under the hood.

Where I live, it will be much cheaper to assemble my own server hardware; NAS appliances are not common here. The cheapest, most basic 2-bay NAS I can find is about 200 USD, and that is without any hdd. I want at least 4 drive bays, which nearly triples the price. 

FWIW, I am also considering FreeNAS as the software.

---

### Post by 2F4U on 2012-01-06
You get RAID support out of the box for Ubuntu Server and setting up file sharing with, for example, Samba is also not too difficult. However, much depends on you personal preferences and existing knowledge. If you are not used to Ubuntu or Linux in general, it may be easier for you to use Windows. But in general, you will be able to achieve your goals by both alternatives.

---

### Post by dazman19 on 2012-01-06
well i have a micro atx board, and a small box with hdmi out, 4gb ram and a single HDD which will stream data off my network at home. Just use windows networking or samba for the linux machines.

I am planning to put mythbuntu on it and use it to play all sorts of content, including the stuff i record with my camera.

If you are talking about the server then yeh you should probably raid up some disks in raid 5 or something and fill it with media content. try to stay away from proprietary raid like nvraid etc and use the ubuntu or generic software raid etc.. you wont get great performance increases out of it but you will get the redundancy. becuase if your motherboard cr@ps out and you have raided them up with the motherboard software, then you may not be able to connect those disks to the replacement board. but if you use the generic raid then you should be better set.

---

### Post by darkod on 2012-01-06
My vote goes towards ubuntu server but I might be biased and I haven't used WHS 2011. If you feel at least a little bit comfortable or willing to learn, I think linux is much better for a home server.

Plus, you will not be running some production server, only a simple home server which makes learning it far easier. You don't have to think too much about protection, hackers, etc, it will all be inside your LAN behind your internet router which has a firewall in place.

I have recently set up similar using a HP Proliant Microserver because it saved me money buying it as opposed to building it myself (my initial plan was to build it like you). I used 10.04.3 because it's LTS and will probably upgrade to 12.04 when it comes out.

I just selected OpenSSH and Samba server to be installed when installing, good enough for my role of sharing files on the LAN. My system is open, if you want particular users to have access only to particular folders/shares you will have to take care of that, but it's not difficult too.

---

### Post by TwiceOver on 2012-01-06
I use Ubuntu Server 11ish for my homeserver.  Works great.

Software Raid5 4x2tb drives, not one hiccup.

---

### Post by lykwydchykyn on 2012-01-06
If you want an easier interface than Ubuntu Server, while also being free and having access to a lot of free software, check out Zentyal (which is based on Ubuntu) or ClearOS (based on CentOS).  FreeNAS is also good.

Ubuntu server is good for a lot of things, but I would never direct someone to it as a first Linux server experience.

---

