---
title: "Back-Up to a USB Hard Drive ?"
date: 2011-05-26
forum: Server Platforms
---

### Post by leegold on 2011-05-26
Hi,

I'm learning with a local intranet server with Ubuntu Server 10.04. It works well:^) I have a back-up question:

I want to buy a hard drive of some kind to back-up to. I imagine a USB Portable Hard Drive would work OK. I'd plug it in to the box and mount it and then run a back-up routine. Is a workable way to do it?

 Thanks,

Lee G.

---

### Post by psusi on 2011-05-26
Yes, though eSATA is far better than USB.  You can even get an eSATA external dock that you can then just plug normal internal hard drives into.

---

### Post by CharlesA on 2011-05-26
> **psusi said:**
> Yes, though eSATA is far better than USB.  You can even get an eSATA external dock that you can then just plug normal internal hard drives into.
+1.

Altho, I haven't messed with eSATA as much as USB. I don't know if eSATA support hot swap in the same way that USB does.

---

### Post by Lars Noodén on 2011-05-26
Whichever type of drive you use, [rsync](https://help.ubuntu.com/community/rsync) is probably the simplest backup option.

---

### Post by psusi on 2011-05-26
> **CharlesA said:**
> +1.

Altho, I haven't messed with eSATA as much as USB. I don't know if eSATA support hot swap in the same way that USB does.

The one problem with eSATA is that currently the system doesn't know that it is external, and so won't automatically mount it.  It's easy enough to open it from the places menu yourself though.

---

### Post by sammiev on 2011-05-26
I myself use a USB HD and never had trouble with it. Takes about 20 to 30 mins to backup all OS of any kind. I prefer [Clonezilla]("http://clonezilla.org/") myself as it does all OS as well. GL :)

---

