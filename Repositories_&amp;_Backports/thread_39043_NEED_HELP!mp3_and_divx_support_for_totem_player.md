---
title: "NEED HELP!mp3 and divx support for totem player"
date: 2005-06-03
forum: Repositories &amp; Backports
---

### Post by bluecode77 on 2005-06-03
I am trying for the last 2 days to come over a problem over my system.
When I try to install necessary packages for mp3 and divx, synaptic says " there is an error on your system" and gives the error message  below:

E: /var/cache/apt/archives/libid3tag0_0.15.1b-3_i386.deb:  files list file for package `fglrx-control' is missing final newline

How would I resolve that issue... ?

Thanks already

PS: except that problem above, i am quite happy ubuntu user

---

### Post by az on 2005-06-03
I think you have a borked package database:

Drop to a command line and type

sudo dpkg --clear-avail

and see if that helps...


Then do sudp apt-get update

---

### Post by bluecode77 on 2005-06-03
thanks i will try that immediately

---

### Post by az on 2005-06-03
If that is the problem, would you check to see if synaptic has a way of clearing the package list lke that?  I am not in front of an ubuntu computer right now.

If there is no such option, would you please visit bugzilla.ubuntu.com

Open up a bug report to request this feature for the synaptic package.  Thanks!

---

