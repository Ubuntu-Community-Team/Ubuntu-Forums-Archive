---
title: "A reply from ATI technologies to my frustrations"
date: 2004-11-11
forum: The Cafe
---

### Post by HiddenWolf on 2004-11-11
I recently e-mailed ATi, using the customer support e-mail form on their site, about how annoyed I was at their poor drivers, and informing them my next purchase would be an Nvidia solution.

Ofcourse I did not expect a reply, but to my amazement, I got this: Probably a fairly standard reply, but a reply nontheless.

```

Dear Hidde Brugmans,

Thank you for contacting ATI Customer Care.

ATI is constantly looking for ways to improve its products and services.  Feedback such as yours allows us to address the needs of our most valued assets – our customers.

We currently offer Linux drivers that have been fully tested by our Linux development team for the RADEON 8500 series and higher.  These drivers can be downloaded by going to http://www.ati.com/support/driver.html.  A HOW-TO that provides installation instructions for ATI's Linux driver can be found at http://www.ati.com/support/infobase/linuxhowto-ati.html.  For additional information, we've also published an FAQ located at http://www.ati.com/products/catalyst/linux.html with answers to the most commonly asked questions.  If you have any feedback regarding the driver, feel free to submit it at http://apps.ati.com/linuxDfeedback/index.asp.

Currently, ATI Customer Care supports Linux on the FireGL line of products and is investigating the potential of supporting Linux on the RADEON line of products.  We appreciate your patience while we evaluate the possibilities and look forward to serving you in the future.

Regards,

Rick Carman
Customer Care
ATI Technologies Inc.
http://www.ati.com

```

I guess it does pay off to email to **support@ati.com**, so why not go and send them a mail yourself

I have just sent off a more lengthy mail, informing them that I want to see X.org working drivers, and why.
I added a nice and juicy bit about XFree being dead, and their reputation among enthousiasts being very bad

```

Dear mr Carman,

At the moment, I have a working system with 3d acceleration on my Radeon  9200. However, I use one of the few remaining distributions which support the XFree 4.3 graphical subsystem. The next release of this distribution, due in April, will switch to the X.org X system, which is currently not supported by your driverset.
The same applies for the largest free linux distribution, the debian project. They are currently finishing their latest release, after that, XFree is abandoned by all but a handfull of distro's.

While since there are not many native-linux games, raw performance is not an issue for me personaly, a driver that does not support the most widely used X-system is a severe drawback.
In general, your drivers seem to be not only slower, but also much harder to work with then those of Nvidia corp.
It takes a lot of effort to get them going, which results in the fact that ATI has a very bad reputation among linux enthousiasts at the moment, with chat channels and message boards overflowing with questions about fglrx and ati cards.

While I understand linux customers are about 3% of your market, these are the people that are enthousiastic about computers, advice their family and friends, and in general like to be on the forefront of technology.
Many of these people would prefer an ATI solution, but due to inferior drivers, many decide to use the DRI modules of the Xfree/Xorg projects, which mostly work on older cards, or they put their new ATI cards up on ebay to find an NVidia card.

Regards,

Hidde Brugmans 

```

---

### Post by jdodson on 2004-11-11
right.  they need to keep with the times, the reason why i wont buy ATI is because they treat gnu/linux like second class citizens.  for what it is worth, its cool the auto-responded to you.  more people need to complain, its the only way stuff will change.  

after they get better drivers, then making them free software is the next step:)

---

### Post by HiddenWolf on 2004-11-11
Usually an auto-reply comes within ten minutes. This took two days.
That means this is a template, and somebody at least read it.
I wonder if i will get a serious responce to my reply. If I do, I'll post it here.

My main concern is they need X.org, and they need drivers that work. 
Speed will come, but 'work' is what really scares a lot of people away from ATI.

I am very hesitant to move to hoary right now. I've got a working 3d accel, and I don't want to spend a few hours messing with X,org to get it going on hoary.

---

### Post by jdodson on 2004-11-11
[QUOTE=HiddenWolf]Usually an auto-reply comes within ten minutes. This took two days.
That means this is a template, and somebody at least read it.
I wonder if i will get a serious responce to my reply. If I do, I'll post it here.

My main concern is they need X.org, and they need drivers that work. 
Speed will come, but 'work' is what really scares a lot of people away from ATI.

I am very hesitant to move to hoary right now. I've got a working 3d accel, and I don't want to spend a few hours messing with X,org to get it going on hoary.[/QUOTE]

i hear ya.

---

### Post by HiddenWolf on 2004-11-12
The chat with ati developers and PR people at Rage3d last night revealed some interesting snippets of information.

I am too tired to edit the logs, but here is what they more or less said:

They told us their main goal is to get x.org and amd64 support in the next release. Release is rumored for december.

Their main focus is on 2d, redhat, and suse. They want to get it right for the business and oem clients, aswell as optimise for the occasional 'wannahave' like doom.

A new installer script is underway, but if you run an enthousiast distro, and you have difficulties, bad luck, they support redhat, and are talking to suse.

Support for more games, composite, and stuff, well stuff it. It's coming 'as the market demands'

They are moving to using the same codebase for the linux and windows drivers, and tauted their bi-monthly release cycle.

Control panel, for gnome, no way.
User contributions, no way basicly
Assisting users developing for ATI, no way

So at the moment, there is little hope for full-featured drivers equal to nvidia's.

---

