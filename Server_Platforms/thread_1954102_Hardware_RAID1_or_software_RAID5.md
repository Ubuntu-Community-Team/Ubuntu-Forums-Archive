---
title: "Hardware RAID1 or software RAID5?"
date: 2012-04-07
forum: Server Platforms
---

### Post by cyncicle on 2012-04-07
We got a really good deal on an almost new Dell PowerEdge R410, and I'm working on setting it up for our small (~10 user) office.

The R410 has an SAS 6/iR Inegrated RAID controller which, from what I have read, only supports RAID0 or 1.  I was going to just set it up as RAID1, but I got to thinking about whether or not I'd be better off going with a software RAID5 setup since I have an extra drive.  

The server will be used almost exclusively for document storage/backup; no plans at present to use it to host our website or email.

So, I'm looking for guidance from the experts.  Whatcha think?

---

### Post by skabople on 2012-04-07
The SAS 6/iR is not a bad card and can support RAID0, RAID1, RAID5, RAID10. I work in an extremely large Legacy DC with thousands of Dell R710, Dell R200, and so on with SAS 6/iR cards in them.

Software RAID can be fun to some but it's more work than just having a SAS 6/iR.

Tip: install the Dell Open Manage software. It's really nice ;)

---

### Post by cyncicle on 2012-04-07
> **skabople said:**
> The SAS 6/iR is not a bad card and can support RAID0, RAID1, RAID5, RAID10.

I think the PERC 6 is the card that supports formats other than 0 or 1, isn't it?  I'm only given 0 or 1 as options in the BIOS.

> Software RAID can be fun to some but it's more work than just having a SAS 6/iR.

That's what I was thinking, but the thought of additional redundancy at no cost was tempting.

> Tip: install the Dell Open Manage software. It's really nice ;)

I'll definitely do that.

Thanks for the tips!  This is my first experience with setting up server from scratch, so I'll take all the advice I can get.

---

### Post by skabople on 2012-04-07
lol yep Perc 6 is the one I'm thinking of..

---

### Post by cyncicle on 2012-04-07
Why do companies chose such similar names? ;)

So, I guess the other option would be to pick up a PERC 6 card.  They're relatively inexpensive on eBay.  Decisions, decisions...

---

### Post by skabople on 2012-04-07
Lol right.

A PERC 6 would be a good investment. Then to top it off slam a Latronix Spider KVM on there lol!

---

### Post by cyncicle on 2012-04-07
> **skabople said:**
> Then to top it off slam a Latronix Spider KVM on there lol!

Okay, you've just made my learning curve that much steeper!

---

### Post by skabople on 2012-04-07
What!?!? Lol 

Check out [Latronix Spider KVM]("http://www.lantronix.com/it-management/kvm-over-ip/securelinx-spider.html")

---

### Post by cyncicle on 2012-04-07
Yeah, I checked it out.  The server is in the closet next to my desk, so I'll probably be okay without the Spider - for now at least.

---

### Post by skabople on 2012-04-07
Yeah I agree. The Spider KVM is a little much... I think the Dell R410 has a IPMI compatible NIC card. IPMI can come in handy too.

---

### Post by cyncicle on 2012-04-07
> **skabople said:**
> I think the Dell R410 has a IPMI compatible NIC card. IPMI can come in handy too.

Yes, I believe you are correct.

Thanks again for the help!

---

### Post by cyncicle on 2012-04-09
Okay, I was looking at a PERC 6i on eBay, and I'm a little confused about the card layout.  Here's the card that's currently installed:

[IMG]http://i1051.photobucket.com/albums/s435/derekdci/PowerEdge%20R410/SAS6iR.jpg[/IMG]

As you can see, there are no cable connections on the board.  All of the PERC 6i boards I have found are mounted on a sled, and have connections for cables and a backup battery.  Is there a Dell RAID card that looks/works like this one?

---

### Post by skabople on 2012-04-09
The PERC 6i is what you want for that dell. The picture you supplied looks like the default card. The PERC 6i plugs into the same PCI slot.

---

### Post by cyncicle on 2012-04-09
> **skabople said:**
> The PERC 6i is what you want for that dell. The picture you supplied looks like the default card. The PERC 6i plugs into the same PCI slot.

Yeah I get that part, but the PERC 6 comes with cables and I'm not sure where they connect.

Seeing as this isn't Linux related, I should probably take this part of the issue to a Dell server forum.

Thanks!

---

### Post by skabople on 2012-04-09
PERC 6i comes with cabls for the BBU, and cables for the drives to connect to the card. There should be two connecters on the card where one end of the cable goes to while the other end will either plug directly into the hard drives or into the backplane on the server. Very simple I wouldn't stress it.

---

### Post by cyncicle on 2012-04-09
> **skabople said:**
> Very simple I wouldn't stress it.

Cool.  I just want to make sure I get the right stuff.

---

### Post by skabople on 2012-04-09
Right on lol

---

### Post by a2j on 2012-04-10
I don't think you can just install Linux on a software raid5. You'd need some other drive for /boot and grub.

---

### Post by skabople on 2012-04-10
To be on the safe side but generally RAID5 is 3 drives.

---

### Post by cyncicle on 2012-04-10
> **a2j said:**
> I don't think you can just install Linux on a software raid5. You'd need some other drive for /boot and grub.

According to the documentation it's doable - [https://help.ubuntu.com/11.10/serverguide/C/advanced-installation.html](https://help.ubuntu.com/11.10/serverguide/C/advanced-installation.html)

The more I read about it, I'm pretty sure hardware is ultimately the most trouble-free way to go anyway.

---

### Post by skabople on 2012-04-10
Yes I would agree. Hardware raid is less hassle.

---

### Post by rubylaser on 2012-04-11
The two main downsides to hardware RAID are typically cost (used PERC cards aren't very expensive, so that's not an issue here) and, you're locked into that particular type of card.  A few years down the line, if your RAID card fails, you'll typically need to secure the same model of card to recognize your array.

For home servers, I always use software RAID of some sort (mdadm or ZFS) based on their cost (free), portability, and flexibility.  At work, I have a mix of hardware and software RAID arrays deployed.

---

