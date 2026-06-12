---
title: "ZFS list output"
date: 2017-10-18
forum: Server Platforms
---

### Post by tidder2 on 2017-10-18
is there any way of changing the output ZFS list to display free space in GB/MB/KB
or
getting the free space some other way

---

### Post by LHammonds on 2017-10-18
You mean something like:

```
df -h
```

or

```
du -sh /var
```

---

### Post by tidder2 on 2017-10-18
df -h gives me available space of 14T
but [COLOR=#000000]ZFS list say's 13.9T[/COLOR]
and
df --block-size=G gives 14276G

I find it confusing I just want the ZFS list to output in gigabytes
(update)
I think I have it 14276 / 1024 is 13.94140625 TB
so df --block-size=G is the way to go

---

