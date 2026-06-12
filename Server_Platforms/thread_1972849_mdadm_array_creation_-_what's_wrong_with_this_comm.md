---
title: "mdadm array creation - what's wrong with this command?"
date: 2012-05-03
forum: Server Platforms
---

### Post by MakOwner on 2012-05-03
I have been working on this late at night too log...
What's wrong with this command?
```

# mdadm /dev/md3 --create --verbose /dev/md3 --level=5 --raid-devices=8 /dev/sdb1 /dev/sdc1 /dev/sdd1 /dev/sde1 /dev/sdf1 /dev/sdg1 /dev/sdh1 /devsdi1
mdadm: You have listed more devices (9) than are in the array(8)!

```


Near as I can tell, I only listed 8 devices...


Edit - I pasted the wrong command attempt, but as it turns out the position of the --verbose parameter is critical and results in nonsensical errors.

---

### Post by rubylaser on 2012-05-04
You can shorten that up by listing your drives in a group like this too, fyi. Glad you got it figured out.

```
mdadm --create --verbose /dev/md3 --level=5 --raid-devices=8 /dev/sd[bcdefghi]1
```

---

