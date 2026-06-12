---
title: "usermod"
date: 2014-03-22
forum: Ubuntu Development Version
---

### Post by pauljwells on 2014-03-22
Just wanted to post something I'm finding useful, in case it helps.
I keep the latest LTS and non-LTS Ubuntus on my home desktop. Each distro gets a partition for / on an SSD and shares a common HD for /home
I keep the same username for both distros, but maintain different /~ directories so I can keep one set of files and symlink from the secondary distro

The way I do this is to install with a dummy admin account, then immediately create a new account with my name etc, then use the command

```
usermod -d /home/distro/myname -m myname
```

Obviously I have trusty and saucy as 'distro' at the moment.

HTH

---

### Post by bapoumba on 2014-03-22
No issue with user configs files?
I'm not surprised it works, in particular for back to back releases, but I do not think I would advise doing so. It most probably sets grounds for trouble.

---

### Post by pauljwells on 2014-03-23
No, in fact the idea was to avoid config file problems.
I would agree that sharing a home directory between distros is a very bad idea, this was a way to avoid that whilst keeping the same username between distros and hence avoiding permissions problems.
Each distro gets its own home directory: trusty looks for /home/trusty/myname and saucy looks for /home/saucy/myname. I could have set up separate partitions with a dedicated /home for each, but this seemed like a neater way.

---

### Post by bapoumba on 2014-03-23
OK, I read your OP too quickly, sorry. Do the two users with the same username have the same userid or not ?

---

### Post by pauljwells on 2014-03-23
Yes. Same permissions, same ID everything.

---

### Post by bapoumba on 2014-03-23
Well, as the / and /home are different, I guess it can work. If it is a matter of sharing files, why not using an exchange partition ? This is what I routinely do here, I have 2 storage partitions that different users access. / and /home are kept at minimal viable sizes, everything else is on these 2 other partitions. I do not format them over when I run fresh installs.

---

### Post by zika on 2014-03-23
Because OPs I post is not about exchangeing the files but good and clever bookkeeping practice... Carefull reading of I OPs post reveals almost everything needed... ;)

---

### Post by bapoumba on 2014-03-23
> **zika said:**
> Because in OPs post is not about exchangeing the files but good and tidy bookkeeping practice... Carefull reading of I OPs post reveals almost everything needed... ;)
Yes, that is true (and I did read too quickly). Now, unless I am the only one to extrapolate and misread, I just wanted to point that out for other readers.

---

### Post by pauljwells on 2014-03-24
In fact bapoumba's setup is just as valid as mine, probably more so in most cases, and I did consider doing it that way first.
My intention is to keep 14.04 as production and to install each new non-LTS to play with, so I know my /home/trusty will be on the machine until 16.04 at least, so I can keep all media there and symlink from the other distro. I also keep all the older distro /home/distro diretories without needing separate partitions for each, which starts to get messy.

---

### Post by bapoumba on 2014-03-24
Thanks for the explanation pauljwells :)

---

