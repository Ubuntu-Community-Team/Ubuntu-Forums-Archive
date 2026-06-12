---
title: "Annoying network hang on Media Server"
date: 2011-07-22
forum: Server Platforms
---

### Post by greenslade on 2011-07-22
First off - I'm a complete Linux newbie and this is my first Linux project.

I've set up an old Sempron machine we had lying around as a MediaTomb server. However, I've got a strange issue. When I'm playing back files, if there's no key or mouse input on the server the network connection randomly drops - ssh, vnc etc all become unresponsive. If I go and hit any key on the server keyboard it wakes itself back up and I can reconnect.

I'm sure this is something simple, but I can't figure out what it is. I thought at first it was Samba related, since it seemed to happen after I set up shared folders, but I've uninstalled Samba and have decided to just go with sshfs to move files over the network, and it still seems to be doing it.

Anyone have a clue what's going on? Could it be hardware related?

---

### Post by headvampyre@hotmail.co.uk on 2011-07-23
What specs are the machine? MediaTomb was a streaming server, and id say your gonna want something more powerful than an old Sempron for that :/ Also, if your using a standard desktop installation, look at the power management and screensaver settings.

---

### Post by greenslade on 2011-07-24
It's a 2500+. I know I'm not going to be doing any serious transcoding, but Mediatomb handles straight UPnP file transfers fine. Like I say, it all goes well until the system just stops, and then hitting "return" on the server's keyboard is enough to wake it up.

I'm using the server distro. I was using the Desktop distro but I changed it, because of this problem. The fact that it's continued, plus some googling, makes me think it's related to the driver for my NIC, so I'm going to put a new topic in a relevant forum.Thanks!

---

