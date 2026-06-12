---
title: "Ubuntu and hardware RAID 5"
date: 2005-05-11
forum: Server Platforms
---

### Post by valthonis on 2005-05-11
I've been searching the forums for RAID 5 solutions under Ubuntu for the last day or so, and haven't found anything definitive as far as a HOWTO or specific setup details.  ](*,)  Here's my situation: I have an old dual Pentium III server board (Tyan Tiger 100) that I want to bend into use as my family server.  I already have the CPUs, RAM, et cetera needed to run the system, and it presently has Ubuntu installed on a 20 GB volume.  What I'm looking to do is install four new drives  attached to a four-port PCI RAID controller and run a nice big RAID 5 array for speed and data protection.

So far, I've been unable to find an acceptable RAID controller on the market.  All the PCI cards I've found only support a kind of half-software RAID management that requires Windows-only driver support; under Linux, they become nothing more than very expensive IDE controllers that force you to use software RAID.  Seeing as how my machine only has a pair of 500 MHz Pentium IIIs, this isn't an acceptable solution.  [-X  In addition, all the cards I *have* found that manage their arrays transparently under Linux are PCI-X cards.  This being a rather old motherboard, there are no PCI-X slots onboard.  In fact, it has ISA slots!  Talk about OLD!

Does anyone out there have any wisdom or knowledge to share in this situation?  I've heard rumors that some of the PCI-X cards are backwards compatible with 32-bit PCI slots, but nothing definitive.  Google searches have come up negative as well.  I'd really appreciate any help you can give.

-V

---

### Post by LordHunter317 on 2005-05-11
I would suspect unless you need hot-swap or plan on using this thing more so than an average family file server, software RAID will be more than adequate.

---

### Post by alastair on 2005-05-11
A 4 port 3Ware card?

---

### Post by valthonis on 2005-05-12
[QUOTE=LordHunter317]I would suspect unless you need hot-swap or plan on using this thing more so than an average family file server, software RAID will be more than adequate.[/QUOTE]

Yeah, after a few hours thought, I figured that software RAID wasn't the end of the world... and while I DID confirm that PCI-X cards are backwards compatible with PCI slots, I wasn't prepared to invest $150-250 in a card that may or may not work seamlessly under Ubuntu.

I ran out to my local store and bought four 120 GB drives and a pair of PCI IDE controllers.  The computer is set up thusly:
[list]
[*]/dev/hda: 4.3 GB
[list]
[*]swap 1.2 GB
     [*]/boot 128 MB
     [*]/tmp 3.0 GB
[/list]
[*]/dev/hdc: ATAPI DVD-ROM
[*]/dev/hde: Software RAID 120 GB
[*]/dev/hdg: Software RAID 120 GB
[*]/dev/hdi: Software RAID 120 GB
[*]/dev/hdk: Software RAID 120 GB
[*]/dev/md0: 360.1 GB
[list]
[*]/ 360.1 GB[/list][/list]

Setup worked without a hitch, and I'm currently installing the smp kernel and my desired services.  If anyone is curious, I'll let you know how it goes.

---

