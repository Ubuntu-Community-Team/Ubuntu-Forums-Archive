---
title: "System update restored hangs"
date: 2007-06-10
forum: System76 Support
---

### Post by AusIV4 on 2007-06-10
Right after feisty came out, a lot of people were reporting that their system was freezing up for ~30 seconds at a time. Recently some update came through (possibly the kernel update) that reintroduced the problem. Running the system76-driver fixed the problem, but I thought I might mention that the problem was reintroduced in case anyone else runs into it.

---

### Post by tedrampart on 2007-06-10
is it the cdrom thats causing hangs on yours?  or is it xorg?  I have xorg lockups, but would be reassured if I wasn't the only one getting them..

---

### Post by AusIV4 on 2007-06-10
> **tedrampart said:**
> is it the cdrom thats causing hangs on yours?  or is it xorg?  I have xorg lockups, but would be reassured if I wasn't the only one getting them..
I'm not sure what exactly the original problem was, however when I first installed feisty, my hard disk was listed as /dev/sda. After running the system76-driver, it was listed as /dev/hda. After the update, it was back to /dev/sda and the hangs were back. I ran the system76-driver again, and now it is listed as /dev/hda, and the hangs are gone, so I don't think it's related to xorg.

---

