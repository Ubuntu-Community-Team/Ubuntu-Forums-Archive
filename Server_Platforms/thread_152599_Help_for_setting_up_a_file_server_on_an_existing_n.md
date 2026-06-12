---
title: "Help for setting up a file server on an existing network"
date: 2006-03-30
forum: Server Platforms
---

### Post by towerofsong on 2006-03-30
Hi there,

This is quite a big question and I really hope someone can help me. I am not new to Linux, I have been using it on and off for about 6 years, but I am no expert. I have spent the best part of two days trying to figure out how to do this but nothing I do will work exactly how I need it to. I’ve decided that Ubuntu seems to be the best option although I’ve not really used it in the past. I’ll outline everything now.
I work as IT Support for a Students Union and I am trying to set up a file server with Linux. The server is a PowerEdge 1400SC which I have had to take Windows NT Server off due to it being an illegal version. We access the network through the university, so I have no control over the main network.
I need the server to allow only certain people to log in, and they will have their own user name and password, ideally the same as their windows one. This will give them a mapped drive with access to their /home directory on the Linux server. 
Currently all users log onto a network to gain internet access, email..etc through Novell Netware and log onto a domain. This server is not controlled by me and I have nothing to do with it.
I’ve experimented with Samba and managed to access the /home directory on the Linux server, but how that happened I’m not sure.
So if a user’s username is davis14 then they would access the davis14 directory on the file server. Obviously their directory would have full read/write access but they will not be able to see anywhere else on the server. I think about 60 people will need access.
I will also need a firewall which will only allow connections from the network, no outside connections at all. I think this is the most secure way. But again I’m not sure. I’ve looked through the Ubuntu Server guide but this seems to be about setting up a proper server, not just a file server. No one will be accesing anything through this other than a /home directory. I need everything to be as secure as possible.
If you need anymore information please ask, I’ve been thinking about this for so long I’ve actually started to confuse myself.

Thanks if anyone can help :)

---

### Post by Iowan on 2006-03-30
All I can offer is an opinion.  Sounds like Samba can handle most of the file sharing you need done.  It might even handle authentication (I'm still struggling with my home network "domain").  My router/firewall is on a separate box, so I can't share how to set up Ubuntu as firewall (the name Firestarter seeems familiar, though).

---

### Post by olddog on 2006-03-30
Try this out:

[http://www.howtoforge.com/samba_setup_ubuntu_5.10](http://www.howtoforge.com/samba_setup_ubuntu_5.10)

I'm a newbie, and it worked great, although he doesn't explain how to actually set the use and group quotas once you get quotas running, but you can find that elsewhere, such as:

[http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch28_:_Managing_Disk_Usage_with_Quotas](http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch28_:_Managing_Disk_Usage_with_Quotas)

Also, when you first set up quotas, you'll get a couple warning messages, apparently that's normal.

---

### Post by xerophyte on 2006-04-19
you might wanna take look at the shorewall  too, it will help you configure the firewall for secure access

---

