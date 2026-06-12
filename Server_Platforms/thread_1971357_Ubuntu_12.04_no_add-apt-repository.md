---
title: "Ubuntu 12.04 no add-apt-repository"
date: 2012-05-02
forum: Server Platforms
---

### Post by daneren2005 on 2012-05-02
As I continue to configure my server I keep coming across sites that say to use add-apt-repository and I had used it before on my 10.04 server.  I updated my server to 12.04 (fresh install) recently, and when add-apt-repository doesn't appear to be installed on my machine.  I tried googling for it and I couldn't find anyone else with the same problem so I imagine that it just didn't get installed correctly either because of a screwed up DVD or because something goofed on install.  My question is what repository/package is this supposed to be in?  I was wondering if I can manually install something to get it.  And if there isn't where can I find the official binary for add-apt-repository for 12.04?  I can just add it to the bin myself if I can download it.

This install is 12.04 Ubuntu Server x64 on a old Pentium D machine.

---

### Post by Dennis N on 2012-05-02
Install python-software-properties and you will have it.

---

### Post by daneren2005 on 2012-05-02
That seemed to have done the trick thank you

---

### Post by hp3171 on 2012-11-09
if sudo apt-get install python-software-properties does not work then try:

sudo apt-get install software-properties-common

---

### Post by zhongfu on 2012-11-21
> **hp3171 said:**
> if sudo apt-get install python-software-properties does not work then try:

sudo apt-get install software-properties-common

Thanks, that did the trick for me!

---

