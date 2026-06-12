---
title: "failing"
date: 2005-06-12
forum: Repositories &amp; Backports
---

### Post by simple on 2005-06-12
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/libg/libgii/libgii0_0.8.5-2_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/libg/libgii/libgii0_0.8.5-2_i386.deb)  MD5Sum mismatch
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/libg/libggi/libggi2_2.0.5-1ubuntu1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/libg/libggi/libggi2_2.0.5-1ubuntu1_i386.deb)  MD5Sum mismatch

that's when i get when copy pasting code from the unofficial guide on how to install mplayer..

---

### Post by Xian on 2005-06-12
It's a problem with the us.archive mirrors.

Substitute [http://archive.ubuntu.com/~](http://archive.ubuntu.com/~) for each [http://us.archive.ubuntu.com/~](http://us.archive.ubuntu.com/~) instance in your /etc/apt/sources.list.

---

### Post by simple on 2005-06-12
[QUOTE=Xian]It's a problem with the us.archive mirrors.

Substitute [http://archive.ubuntu.com/~](http://archive.ubuntu.com/~) for each [http://us.archive.ubuntu.com/~](http://us.archive.ubuntu.com/~) instance in your /etc/apt/sources.list.[/QUOTE]
 well they're back now, i didn't sub, would it be best interest to still replace which you said?

---

