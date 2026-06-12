---
title: "No UUID for Encrypted SWAP or TMP!? wtf?"
date: 2010-05-19
forum: Security
---

### Post by DizzyCoder on 2010-05-19
ARRRRGGGH  I'm going batty trying to figure out if it's possible to assign my tmp_crypt and swap_crypt in crypttab by UUID instead of /dev/path ..

I have to remember to not have a USB drive plugged in as to not mess up the sdX letter progression!! 

BAAHHH!! $#$&*@  It's just not possible ??

---

### Post by DizzyCoder on 2010-05-26
w00t!  I did it!  (sort of)

#1 there's no (at least that I could find) way to get the UUID of SWAP or TMP partition... aside from using gParted to create the swap partition and "save the details" to get UUID.

This however, still gives no joy for a SWAP partition created on top of LUKS.

So, I used palmiset (disk utility) to create a swap partition and checked the box to "encrypt underlying device"; this allowed me to check the underlying devices' UUID (for me it was /dev/sdf5) which I could not get before; and before rebooting I changed the line in crypttab as such:

```

swap_crypt UUID=20da2f18-fbbb-415c-b870-4a773976ffa8 /dev/urandom cipher=aes-cbc-essiv:sha256,size=256,swap

```

Now, for /tmp I could not find a solution but presumably that same trick would work, but in my research I found that using tmpfs was a better deal (security wise), here's my fstab

```

tmpfs	 /tmp	 tmpfs	nodev,nosuid,noexec,noatime,mode=1777	0	0
/dev/mapper/swap_crypt none            swap    sw              0       0

```

This was really bothersome telling me that /dev/mapper/swap_tmp was not available yet.. every other time I reboot my computer it rearranges the sdX drive order.  Now all my mandatory mounts are no longer dependant on drive letters.

huzzah!

---

