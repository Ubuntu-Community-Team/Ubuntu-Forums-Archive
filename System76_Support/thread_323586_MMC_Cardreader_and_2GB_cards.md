---
title: "MMC Cardreader and 2GB cards"
date: 2006-12-22
forum: System76 Support
---

### Post by sbalneav on 2006-12-22
Some of you may be having problems (as I was) with reading newer 2GB MMC cards in the integrated cardreader on your spiffy new laptop.

Turns out to be a kernel bug, that the card reports a blocksize that the mmc_block.c driver can't handle.  All is not lost, however, as all MMC cards must support a blocksize of 512 bytes.

[http://lkml.org/lkml/2006/6/8/234]("http://lkml.org/lkml/2006/6/8/234")
has a patch which worked for me (with some tweaking), and now my 2GB media cards work fine.

Thought some of you might like the tip.

Scott
[email]sbalneav@ltsp.org[/email]

---

### Post by GameManK on 2006-12-22
I think you are referring to this bug, already fixed in Edgy and Feisty.
[https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.17/+bug/61758](https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.17/+bug/61758)

---

