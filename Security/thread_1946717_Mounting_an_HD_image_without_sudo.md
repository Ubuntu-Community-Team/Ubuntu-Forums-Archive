---
title: "Mounting an HD image without sudo"
date: 2012-03-25
forum: Security
---

### Post by Cadmus on 2012-03-25
I know a bit about forensics and recovery so I often help out friends and family. Now the first step I do is to make a forensically sound dump of the HD, after this I usually want to mount it, now I'd rather do this without sudo as there's no real need to as I own the image file and the proposed mountpoint.

Is there any way this can be done? I've seen guides for other devices using pmount but they seem to only work if your device is in /dev, rather than (say) /home/cadmus/forensics .

Or is there something fundamentally unsafe about allowing a regular user to perform image mounts I've not considered and I should stick with sudo?

---

### Post by SeijiSensei on 2012-03-25
I've not been able to mount an ISO image without root privileges.  However if you're worried about potentially altering the image, I suggest you mount it read-only like this:

```
sudo mount -o loop,ro /path/to/the.iso /path/to/mountpoint
```

---

### Post by Cadmus on 2012-03-25
Oh I only ever work on the original read-only, most of the time I also set the immutable bit too just to be certain. Space permitting I'll generally checksum the original, then make a copy and compare sums at the end just to satisfy myself that it's correct.

---

