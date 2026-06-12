---
title: "Cannot Boot 12.04.1 LTS with RAID Errors"
date: 2013-01-11
forum: Server Platforms
---

### Post by zimdba on 2013-01-11
I'm running the original kernel that shipped with 12.04.1LTS Server.

I have a 3x500GB array created with mdadm.  This is only redundant data, not containing boot or OS.  I should note that one or two of the disks in this array are failing or have bad connections.

My server will not boot as it is giving me issues with a degraded RAID.  It offers me the option to boot, but answering both y or N both drop me down to a busybox command prompt, which is effectively useless to me for managing the server.

Is there a way to stop mdadm from starting at boot so that I can actually start the server?  I can use gparted or a live linux CD to access my OS drive.

Thanks.

---

### Post by zimdba on 2013-01-12
OK, my bad.  I didn't realize that you could just type "exit" at the busybox prompt and it would boot to the shell. ](*,)](*,)

Now on to figuring out how to recover my array.

---

