---
title: "Ithink my encrypted SD card is now being mounted read-only. Why would that be?"
date: 2010-08-09
forum: Security
---

### Post by stone1343 on 2010-08-09
Since recently, my encrypted SD card seems to be mounted read-only. In System Monitor (Ubuntu Lucid) shows the device as /dev/mapper/udisks-luks-uuid-then-a-whole-bunch-of-numbers, it's ext4. Even if it were full, which it's not, r/o doesn't make sense because how could I clear space?

Thanks in advance,
Jeff

---

### Post by OpSecShellshock on 2010-08-09
Have you checked the position of the write-lock slide?

---

### Post by stone1343 on 2010-08-15
that was it, wow, usually I don't get caught by such stupid things. Thanks & sorry for wasting your time...

---

### Post by OpSecShellshock on 2010-08-15
Hey, the only reason I know about it is because it's happened to me. It's pretty easy for it to be moved into the locked position just by putting the card into the reader.

---

