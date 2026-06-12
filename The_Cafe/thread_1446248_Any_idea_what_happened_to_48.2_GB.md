---
title: "Any idea what happened to 48.2 GB?"
date: 2010-04-03
forum: The Cafe
---

### Post by Dark Aspect on 2010-04-03
The filesystem is ext4 and it shows up this way on Arch Linux and Ubuntu LiveCD.

[IMG]http://img545.imageshack.us/img545/9523/snapshot4.png[/IMG]

Ideas?

---

### Post by cgroza on 2010-04-03
that space is reerved by the filesystem in case you run out of space.

---

### Post by Dark Aspect on 2010-04-03
> **cgroza said:**
> that space is reerved by the filesystem in case you run out of space.

Is there a way to lower the reserved space on an ext4 filesystem? I know how to on an ext3 drive.

Also how safe is say 10 GB or 15 GB?

---

### Post by FuturePilot on 2010-04-03
> **Dark Aspect said:**
> Is there a way to lower the reserved space on an ext4 filesystem? I know how to on an ext3 drive.

Also how safe is say 10 GB or 15 GB?

If that isn't your / drive or partition you can probably safely lower it to 1%. Default is 5%.

```
sudo tune2fs -m 1 /dev/sdXY
```

Make sure it's not mounted when you do that.

---

### Post by Dark Aspect on 2010-04-03
> **FuturePilot said:**
> If that isn't your / drive or partition you can probably safely lower it to 1%. Default is 5%.

```
sudo tune2fs -m 1 /dev/sdXY
```

Make sure it's not mounted when you do that.

Thanks, it is a internal hard drive that I use as an external drive, so no its not my / partition.

[[IMG]http://img28.imageshack.us/img28/3553/20100313123728.th.jpg[/IMG]](http://img28.imageshack.us/img28/3553/20100313123728.jpg)

---

