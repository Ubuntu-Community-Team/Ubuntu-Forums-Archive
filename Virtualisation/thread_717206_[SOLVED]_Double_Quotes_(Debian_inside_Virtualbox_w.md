---
title: "[SOLVED] Double Quotes (Debian inside Virtualbox without X)"
date: 2008-03-06
forum: Virtualisation
---

### Post by diegosouza on 2008-03-06
Hi people,

I'm running a Debian inside Virtualbox and without X, just text console.
Everything works fine, my keyboard is en_US, but the double quotes key (around the ENTER key) doesn't write.

Any suggestions?
Thanks.

---

### Post by diegosouza on 2008-03-07
No answers but I found my own way to solve the problem:

# gunzip /etc/console/boottime.kmap.gz
# vi  /etc/console/boottime.kmap

So I set the **keycode 125 = quotedbl**

# gzip /etc/console/boottime.kmap
# loadkeys /etc/console/boottime.kmap.gz

Now that useless key (windows key) writes double quotes for me  :)

---

