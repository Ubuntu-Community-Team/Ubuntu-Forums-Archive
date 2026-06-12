---
title: "how to link the /var/www folder to another hard drive"
date: 2007-04-09
forum: Server Platforms
---

### Post by lime4x4 on 2007-04-09
i want to run a small webserver off my main computer.I have apache and that installed and running.I want to have the actual www folder located on another hard drive How would i link to the other hard drive? Another words currently /var/www is located on drive A in the main filesystem drive but i actually want the folder stored on drive B

---

### Post by kooseefoo on 2007-04-09
The simplest way to do that, that I know of, is using mount --bind.

```
mount --bind /path/to/var/www /var/www
```

That will make /path/to/var/www show up in two places: it's own location and /var/www
/var/www must be empty first.


You can also do this with an fstab entry that would look something like this:

```
/path/to/var/www    /var/www    none    bind    0 0
```

Good luck,
Chris

---

