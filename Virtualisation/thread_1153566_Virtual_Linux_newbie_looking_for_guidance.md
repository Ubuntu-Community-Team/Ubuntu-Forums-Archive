---
title: "Virtual Linux newbie looking for guidance"
date: 2009-05-08
forum: Virtualisation
---

### Post by Pnuts on 2009-05-08
Hello,

I've been working my way around the command prompt as much as I can to learn Linux. Have been a Windows server administrator for several years in a windows only environment. I have no idea why I never looked at Linux before, but I started near the end of last year and have been loving it.

I want to take what I'm learning to the next step. I have an ok machine (dual 3.0ghz, 3x320hd, 8gb ram) and setup a dedicated KVM host. When everything is said and done, I would like to have multiple guests filling these roles:

--A Web server (replacing my current windows 2k3 server)
--A Email server (replacing same 2k3 server)
--A DNS and Network Time server (plus anything else i find that is fun\useful locally)
--A sand box Ubuntu server for me to mess around and test various things without breaking other stuff.
--A Remote server for a friend to use and convert to Linux servers
--Depending one mysql use, maybe a image hosting that instead of multiple installs on other guests.

So I have a few questions to get out of the way initially before I get knee deep in a learning adventure.

1. I'm unsettled on whether to use an Ubuntu 8.04 or 9.04 server. The PC I'm using is a Dell Optiplex 760 which I think will benefit more from the 9.04 version, but it losing support in 18 months verse the LTS is holding me back on the choice. Would anyone recommend one way or the other? Does 9.04 offer more power saving features?

2. I'm planning on using the 3x320 hd's in a software Raid 5. Giving about 40gb to the KVM Host (to much?) and the remaining 600gb for the guest images. I have been searching but do not see a suggested or recommended partition scheme. Would it be best to make multiple 50-100gb partitions each for their guest or one large volume for all guests? If the smaller route, is it better to use the partition as the hd, or to use an image file on the partition for the guests?

3. Is this going to be to much for the Host machine to handle? Should I limit myself to less guests? Website and mail would be low volume family use mainly.

4. Is there anything that I might find useful or helpful that I should also installing on the Host machine?

Thanks,
Pnuts

---

### Post by Pnuts on 2009-05-09
Well, to anxious to get started so I decided to go with Ubuntu 9.04 Server.

I have been unable to find any specific information regarding doing either dedicated partitions for the guest or and file. I decided to go the file route but if I find I think I made a wrong choice, I could probably dd it over to a partition. I'll see how it goes.

-Pnuts

---

### Post by merkourio on 2009-05-11
> **Pnuts said:**
> Hello,
1. I'm unsettled on whether to use an Ubuntu 8.04 or 9.04 server. The PC I'm using is a Dell Optiplex 760 which I think will benefit more from the 9.04 version, but it losing support in 18 months verse the LTS is holding me back on the choice. Would anyone recommend one way or the other? Does 9.04 offer more power saving features?

Pnuts

Look, if you want really long term stuff, I would certainly be with 8.04,
But if you just don't mind on updating to Karmic (9.10), then I would go with Jaunty!
Also I think that it would be more safe and wiser thought to always have the latest edition.

That's my point!

Cheers!

---

### Post by veloce on 2009-05-11
I upgraded my production vm server to 9.04 and it was hassle free.  Latest Ubuntu versions are not bleeding edge - there is the occasional issue but far less so in a server environment.

I have no direct experience on partition vs disk image.  disk image gives more flexibility - you can let the disk image grow as it needs to rather than allocating all the space immediately. A partition may be faster - not sure if it would be noticeable.

The conventional wisdom is that a sql server shouldn't be virtualised.  However, the tiny server we use is virtualised and it is fine.  I've heard anecdotes of latest vm technology being indistinguishable (in blind tests by sql experts) from "real" hardware.

Don't underestimate the resource pooling effect of virtualisation.  You'll be surprised how many machines you can load your server up with and still get excellent performance.  However, performance will drop dramatically across the board when your load starts reaching the limits of the resources.  Will all your vms work on that server?  It's probably a case of suck it and see.

---

### Post by Pnuts on 2009-05-12
thanks for the info guys, definately using 9.04 and .img files instead of partitions.

Ran into a time snag as I only have the OS isntalled, hopefully this coming weekend ill be able to get a few guest images up and running.

---

