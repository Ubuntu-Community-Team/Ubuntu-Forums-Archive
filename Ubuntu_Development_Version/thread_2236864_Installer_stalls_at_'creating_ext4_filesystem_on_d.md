---
title: "Installer stalls at 'creating ext4 filesystem on /dev/sda2...'"
date: 2014-07-29
forum: Ubuntu Development Version
---

### Post by sgage on 2014-07-29
I'm trying to install using today's daily build, and I'm running into the same problem I have been having over the past couple of weeks.

Everything proceeds normally with the installation. I get to the partitioner, select 'something else' as I always have, made my configuration, and continued. The installation screens sequence as normal - time zone, keyboard, user info, but the progress bar just sticks at the msg given in the title of this post.

Any idea what I might try to workaround this issue?

TIA...

---

### Post by cariboo on 2014-07-29
Have you tried just formatting an existing partition?

---

### Post by Elfy on 2014-07-29
or using gparted to deal with the partition prior to using the installer

---

### Post by sgage on 2014-07-29
It was an existing partion - the partitioner in the installer wouldn't format it. Unless you meant what Elfy said below...

---

### Post by sgage on 2014-07-29
> **Elfy said:**
> or using gparted to deal with the partition prior to using the installer

That's what I ended up doing - the installation went fine subsequently...

Thanks for the reply...

---

### Post by Elfy on 2014-07-29
have you reported it?

ubuntu-bug ubiquity

---

