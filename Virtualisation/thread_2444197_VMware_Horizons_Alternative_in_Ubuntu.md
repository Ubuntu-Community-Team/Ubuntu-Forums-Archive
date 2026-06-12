---
title: "VMware Horizons Alternative in Ubuntu"
date: 2020-05-26
forum: Virtualisation
---

### Post by annihil2 on 2020-05-26
I have been trying to research VMware Horizons, open source, free client/server alternatives for a couple hours now and it seems - like most things technology related; there are multiple ways to skin a cat, some easier, some more difficult. So, I figured I would pose this question here in an attempt to get a definitive answer, perhaps to narrow down my search (perhaps I'm using the wrong seach terms even!).

The non-profit organization I work for is using VMware Horizons on Windows Server 2016 and serving Windows Server 2008 virtual desktop images to nearly 200 employees. Our servers seem to handle this quite well under normal conditions but, they seem to be stressed and things are slowing down as more and more employees are working from home.

After an early morning meeting and demonstrating a KDE desktop made to look like Windows, and using all our regular software I was given a green light to move forward with testing, and that's where I'm stuck! The problem - that was running on a standalone device, I have no idea if serving it will work, won't work, what software to use on the server end, client side, etc.

Ultimately since I made the Ubuntu suggestion and I've already put our organization on the open-source path, I'd love to use as much open-source client and server end as possible. 

I'm a fast learner - if anyone can just point me in the right direction that'd be fantastic! Again, so many options to chose from and not enough information to go off of.

Thanks for any and all guidance.

---

### Post by TheFu on 2020-05-26
We don't use VMware stuff since 2011-ish.

For remote desktops, **x2go** is pretty easy.  Users can connect to the same VM and share files if you set it up that way.  Probably better NOT to use KDE, but xfce, lxqt or Mate instead. They are probably 20% lighter than KDE. Try it with KDE - see how it goes.

Underneath, if you use virtual machines with LVM as the storage and take snapshots early every morning, then you can put things back almost immediately should something bad happen. By immediately i mean 5 sec or less plus reboot time for that VM.  You'll probably want to use LVM snapshots for stable backups anyways.

For VM management, there are lots of tools.   Depending on the server hardware, 200 concurrent users shouldn't be too hard on a 32-way server with enough RAM.  The CS will be shared on each VM for the same programs being run.  The DS is per process.  i'd try a 12-way system for a small group, say 5-10 users.  i've had 5 users on a 2 core server with remote x2go desktops.

Of course, if all the clients are Linux, then things can be pre-configured for the users pretty easily using ssh-keys for authentication.  For Windows, other tools need to be used to make the ssh-keys.  i've never bothered. My only Windows system can use x2go w/ ssh using password auth. Yuck.   Highly anti-security to use passwords.

x2go clients exist for Linux, Windows and OSX.  No iOS or android to my knowledge.

There are lots of connection tuning for x2go.  For internet, i usually set the connection to isdn and 4K-png for image compression.

---

