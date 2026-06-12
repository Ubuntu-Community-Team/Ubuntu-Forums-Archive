---
title: "updates on ubuntu server"
date: 2009-09-05
forum: Server Platforms
---

### Post by oospill on 2009-09-05
when I login to my ubuntu server, it tells me that I have some updates available.  how do I update from the shell prompt?

thanks,
oospill

---

### Post by Rhubarb on 2009-09-05
To check for updates:
```
sudo aptitude update
```

To install the latest updates:
```
sudo aptitude full-upgrade
```

This is what I do for my ubuntu server anyway.
There may well be a more "correct" way of doing this.

---

### Post by cariboo on 2009-09-05
Personally I use:

```
sudo aptitude update && sudo aptitude safe-upgrade
```

I'd rather not have any surprises. :)

---

### Post by Rhubarb on 2009-09-05
Thankyou cariboo907,

I should probably start using the safe-upgrade option with aptitude from now on, as it is for my server. (It's a personal server, so it doesn't matter too much if I have downtime).

---

### Post by oospill on 2009-09-05
that's what I needed.  thanks to both of you. ubuntuforums.com rocks!

---

