---
title: "is this type of drive span possible?"
date: 2007-06-07
forum: Server Platforms
---

### Post by Underpants on 2007-06-07
I've currently got a 1U rackmount server with Server 2003 and 4x250gb hard drives installed. It's on a via C3 motherboard, so no hardware raid. 

Currently, I have a single 8GB partition that is just for windows. The remaining part of the first disk, and the other 3 disks, are part of a software SPAN that makes out for a 921gb partition that is used as a backup location for several other systems. 

I'd like to move this to linux, as it backs up some apple servers which have long file names that NTFS can't handle properly. 

Is this type of span possible with linux? I don't want to use FreeNAS or anything like that. I'd like a full operating system on the machine.

---

### Post by craigp84 on 2007-06-07
> Is this type of span possible with linux?
Of course.

> I'd like a full operating system on the machine

Assuming you really are better off with a fuller flavour distro (takes longer to setup, harder to maintain, more time consuming, slower - am i putting you off yet ? :) ) then read up on LVM - there's no shortcuts, especially not around data, so make sure you're up to the studying before you jump in and inadvertently do something foolish. 

Linux aint windoze, it don't work the same. Plan accordingly.

Might do well to look here: [http://www.openfiler.com/](http://www.openfiler.com/) - trivial to setup in the same way as FreeNAS, but infinitely more expandable given that its a full-fat Redhat Linux core.

Hope this helps,

-c

---

