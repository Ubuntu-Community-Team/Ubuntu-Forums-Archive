---
title: "Gazelle Value Swap Partition"
date: 2007-02-14
forum: System76 Support
---

### Post by crichell on 2007-02-14
Today (February 14, 2007) it came to our attention that Gazelle Value laptops delivered within the last two weeks did not have swap active in our manufacturing image.  We apologize for the inconvenience and the manufacturing error has been resolved.

To check if swap is active on your machine first open a terminal (Applications > Accessories > Terminal):

```
$ swapon -s
```

You should see output that looks like this:

```
$ swapon -s
Filename                                Type            Size    Used    Priority
/dev/hda5                               partition       3907864 0       -1

```

If not then swap is not active.  Use the following command to activate swap:

```
sudo mkswap /dev/hda5
```

Reboot and your swap partition is now active.  You can use the "swapon -s" command to verify.

---

### Post by AusIV4 on 2007-02-14
I didn't have to reboot for the swap to become active, for whatever that's worth.

---

### Post by crichell on 2007-02-14
Thanks - and thanks for bringing this to our attention.  Feedback always helps.

---

