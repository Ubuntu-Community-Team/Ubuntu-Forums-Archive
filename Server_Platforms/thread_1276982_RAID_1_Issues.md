---
title: "RAID 1 Issues"
date: 2009-09-27
forum: Server Platforms
---

### Post by coberg on 2009-09-27
Hello all,

I'm a moron.  Let's get that out of the way first!  I had an installation of Ubuntu 8.10 Desktop (with a 120 GB main install drive and two 250 GB data drives in Raid 1) fail on me, so  getting all pissed off I installed 9.04 Server right over top of the 8.04 and forgot to back up my Raid 1.  So I'm hoping I have all my data still on the two 250 GB drives, but I'm concerned about trying to mount the RAID without goofing everything up.  So my question is, how should I go about this?  Remember I'm a moron so use small words please!  :)

---

### Post by coberg on 2009-09-28
Bump.  Anyone?

---

### Post by nandemonai on 2009-09-28
```
sudo apt-get install mdadm
```

```
sudo mdadm --assemble --scan
```

Best of luck ;)

---

### Post by coberg on 2009-09-29
Thanks nandemonai, I'll give that a try and post back the results.

---

