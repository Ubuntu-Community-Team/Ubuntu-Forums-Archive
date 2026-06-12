---
title: "Dell PowerEdge 2970 - questions/concerns"
date: 2013-04-10
forum: Server Platforms
---

### Post by TnB on 2013-04-10
The office next to me was rolling over their equipment and i picked up this guy. It's overkill, but, as a learning experience I'm setting it up in my home as a NAS. I was pleasantly surprised to see this: [http://www.ubuntu.com/certification/hardware/200804-265/](http://www.ubuntu.com/certification/hardware/200804-265/). Does this mean a x64 installation isn't compatible or it's just not recommended? I also want to bond the two gigabit ports but I feel like that is just ridiculously fast and will just bottleneck elsewhere. I'm going to roll with Raid 5 with 6 hard drives. The ubuntu community/documentation is great and I'll figure it out as I go. I'm just reaching out if I'm going to hit any unforeseeable roadblocks.

edit: should this be in the servers forum?

---

### Post by mörgæs on 2013-04-11
> **TnB said:**
> 
edit: should this be in the servers forum?

Let's move it and see if you get more response.

---

### Post by tgalati4 on 2013-04-11
You'll be pleasantly surprised at the noise.  I made a rack enclosure for my 2 poweredge servers in the garage.  You're right, with gigabit cards, and twisted-copper DSL service, your bottleneck will not be the server.  RAID might be overkill, you might be better served with JBOD (just a bunch of disks) and mirror your disks once or twice a year as needed.  That way you can recover to a known, working configuration (except for changing disk UUID references as needed) in case of boot drive failure.  RAID should not be relied on as a form of backup.

You might want to put a hypervisor on it so you can run multiple guest operating systems.  I would suggest [http://xen.org](http://xen.org), but there are several to choose from.

---

### Post by TnB on 2013-04-12
I am using: [FONT=Ubuntu][SIZE=3][COLOR=#333333]Ubuntu 10.04.4 32-bit[/COLOR][/SIZE][/FONT]

Everything is running smoothly so far. Just wanted to make sure I could get it to work properly on a supported version before going newer and switching to x64.

Also, I'm doing a hardware raid5 for the "because i can factor." I know it's over kill, but at my level (helpdesk/jrIT), typical interview questions are: "whats your home set up look like?"

---

