---
title: "[SOLVED] Wipe drive before replacing ?"
date: 2008-10-21
forum: Security
---

### Post by Drakkor on 2008-10-21
I'm going to have to send back a seemingly bad hdd to the factory,is it enough to just format the drive before return,or should I use some sort of dedicated software to wipe it clean ? Thanks :)

---

### Post by Shunsuke_01 on 2008-10-21
> **Drakkor said:**
> I'm going to have to send back a seemingly bad hdd to the factory,is it enough to just format the drive before return,or should I use some sort of dedicated software to wipe it clean ? Thanks :)

Formatting it would be easier, but if you have/had personal or private information on it I would suggest you download a free program that is supposed to remove as much information as possible from it etc.

---

### Post by ratmandall on 2008-10-21
Durik's boot and nuke(dban)
[http://www.dban.org/](http://www.dban.org/)

---

### Post by cdenley on 2008-10-21
Deleted data is not the same as erased data, and many deleted files on your drive can probably be recovered easily. If you want to stop 99.9% of people from recovering the data, use this command from a livecd (assuming sda is your drive you want to erase)
```

sudo dd if=/dev/zero of=/dev/sda

```
An even better command (but much longer) would be
```

sudo hdparm --security-set-pass pass /dev/sda
sudo hdparm --security-erase-enhanced pass /dev/sda

```

---

### Post by Drakkor on 2008-10-21
Thanks guys, dban and the commands should do it ! :)

---

### Post by Dave_Connor on 2008-10-22
There is also shred and it works well when you just want to remove sensitive information.

---

### Post by cdenley on 2008-10-22
> **Dave_Connor said:**
> There is also shred and it works well when you just want to remove sensitive information.

Shred takes longer than the secure erase enhanced method, ignores sectors which may have been marked as bad but still contain data, and doesn't erase the track edges. Unless you're worried about the NSA or something, shred would work fine, though.

---

### Post by mobius357 on 2008-10-23
I just let old drives sit on top of my big unshielded subwoofer for a while. Accidentally set a box of diskettes on it once for a few weeks maybe, they were never usable again.

---

### Post by u-slayer on 2008-10-23
dd if=/dev/zero bs=4M | gpg --symmetric --passphrase `dd if=/dev/random bs=4 count=8 2>&1 | sha256sum | head -c 64` - > /dev/sd?

This is 6.5 times faster than urandom on my system.

---

