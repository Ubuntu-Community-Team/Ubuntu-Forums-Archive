---
title: "fedora btrfs?!"
date: 2010-07-22
forum: The Cafe
---

### Post by chris200x9 on 2010-07-22
How do I enable btrfs in fedora 13? I read the documentation and have been trying boot options -btrfs, btrfs and linux btrfs. Nothing makes it show up as a installer format option.

---

### Post by ajgreeny on 2010-07-22
I presume it will be available at the time of partitioning your hard drive for the installation, and at no other points.  You cartainly will not be able to do it with a boot option after installing, if that is what you are expecting.

Different file systems can only be changed at formatting time, other than minor changes to journaling of ext file systems afterwards, as far as I'm aware.

---

### Post by chris200x9 on 2010-07-22
> **ajgreeny said:**
> I presume it will be available at the time of partitioning your hard drive for the installation, and at no other points.  You cartainly will not be able to do it with a boot option after installing, if that is what you are expecting.

Different file systems can only be changed at formatting time, other than minor changes to journaling of ext file systems afterwards, as far as I'm aware.

I know that. I put those boot options on the livecd and still don't get a btrfs choice. I'm so confused, no wonder I don't use fedora. :)

---

### Post by alfplayer on 2010-07-23
[http://fedoraproject.org/wiki/Fedora_13_announcement?F13an]("http://fedoraproject.org/wiki/Fedora_13_announcement?F13an")

"only available for non-live images"

---

