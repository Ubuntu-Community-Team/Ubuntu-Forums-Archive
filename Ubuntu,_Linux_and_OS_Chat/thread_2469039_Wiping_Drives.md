---
title: "Wiping Drives"
date: 2021-11-17
forum: Ubuntu, Linux and OS Chat
---

### Post by Shibblet on 2021-11-17
Is there a Linux tool available for wiping drives?

I want to be able to run it from a LiveUSB environment, so that I can wipe 2 SSD's and 2 HDD's before I sell my old computer.

I also want the data to be irrecoverable.

Any suggestions?

---

### Post by MAFoElffen on 2021-11-18
I use 'hdparm' from a LiveCD... 
[https://grok.lsu.edu/article.aspx?articleid=16716](https://grok.lsu.edu/article.aspx?articleid=16716)

Also if you go to the drive manufacturer's website, they all usually have their own tools. SeaTools is a good vendor written tool, that has a good wipe utility.

---

### Post by TheFu on 2021-11-18
My data recovery friends say there really isn't any 100% safe way to wipe SSDs. Every write is there and one guy claims to have recovered over 80 layers of writes.  His policy is to always destroy old SSDs rather than reuse them if there was every any chance of sensitive data being stored on the media.

HDDs - there are lots of different ways to wipe it.  Fewer prior layers are recoverable, but MIL-Spec standards require multiple writes with different patterns.

If you are just wiping for yourself or to give to someone who will never give the storage away, you can just use dd or cp to fill the entire drive device with zeros.  A drive device looks like /dev/sdZ without any number.  The 'Z' would be replaced by a, b, c, d, e, f, g, h, i, .... you get the idea. The letter often changes from boot to boot, so always verify that you have the correct device name after any reconnection/reboot.  Getting the wrong device name can make for an extremely bad day. It is very possible to wipe the running OS.

There are tools like shred that will overwrite existing files as you delete them. That's another option.  **dban** was a popular tool. I think it was provided as an ISO which could be booted.  If you just want to wipe a partition or file system, there are specific tools for that ... or you can use dd or cp there too.  It comes down to understanding the different device names.

Good question.
I decided to wipe a scratch partition on an NTFS file system using **sudo ntfswipe -a /dev/sdc1**  This wipes all free space and puts 0x00 almost everywhere on that file system.  Previously deleted areas will get random hex values with that option. I typically use a little script to create 250x 1GB files on that scratch partition to make any undelete options with testdisk easier.  This scratch disk is used with some video hardware (no OS) and becomes corrupted from time to time. It never holds anything THAT important.

---

### Post by Tadaen_Sylvermane on 2021-11-19
> [COLOR=#000000]My data recovery friends say there really isn't any 100% safe way to wipe SSDs. Every write is there and one guy claims to have recovered over 80 layers of writes. His policy is to always destroy old SSDs rather than reuse them if there was every any chance of sensitive data being stored on the media.[/COLOR][COLOR=#000000]

To add to this. "If there is a will, there is a way." If someone is determined enough (and have the time + funds) they can do anything. The only real guarantee is melting the whole drive down to a molten state. Even a smashed drive, while not realistic could in theory be reassembled.

*EDIT* Was just gonna add if the data is that critical maybe in the future sell them driveless / just throw in an inexpensive ssd + hdd or something that are new.[/COLOR]

---

