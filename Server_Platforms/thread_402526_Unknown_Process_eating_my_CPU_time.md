---
title: "Unknown Process eating my CPU time"
date: 2007-04-05
forum: Server Platforms
---

### Post by apfritts on 2007-04-05
Hi,

I just upgraded to Feisty Fawn 7.04 yesterday, and now my computer is ALWAYS busy (CPU=100%).  The process has a high nice value, so I don't really notice a performance hit....but I would like to know what this process does.

Here is all that I know about it:
[FONT=Courier New] % CPU|CPU|nice|State|cpu time| args
74.7       | -           |  19     | S            | 00:01:58   | wcg_fcg1_ssearch_5.14_i686-pc-linux-gnu 10001201.faa 10001540.faa[/FONT]

And nothing comes up in gnome-system-monitor when run as my regular user or as root.

Any ideas? Thanks!
AP

---

### Post by Ench on 2007-04-05
Type *top* in the terminal, and see whats the first process... does it show there?

---

### Post by apfritts on 2007-04-05
YES IT DOES!!!  It belongs to boinc...which is the Linux client for the World Community Grid.

Thank you!!!
AP

---

