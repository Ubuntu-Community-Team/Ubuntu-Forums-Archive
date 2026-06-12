---
title: "external root"
date: 2006-11-16
forum: Server Platforms
---

### Post by draeath on 2006-11-16
Well, here is the setup:
I am running a laptop. Most of the internal hard drive is set up for windows, but is also home to a 512mb (big, i know) /boot filesystem, and a 2gb swap partition (512mb ram, so also big)

My root filesystem lives on an external hard drive (/dev/sda) and takes up 100gb out of 320gb.


The issue is: most systems, the whole thing goes down on a power failure. In my case, only the device holding the root filesystem, network connection, and printer go.

How would I go about setting things up for robust handling of power loss? Ideally, I would like the system to pause reads/writes to the root filesystem. On device reconnection, I would like it to do at least a cursory file system check, and then resume drive read/write after any necessary corrections.

I could put the journal for the root system on the internal hard drive (take a chunk from that oversized swap), as I'm using ext3 and that's easy enough to do.


Would any of that extra stuff even be necessary? would putting the journal (and making it large, if needed. I can give it up to 1gb) on the internal drive (which stays up as long as the CPU has power) solve the problem? I can't see why though, as the journal would only save corruption due to writing to the disk.

---

