---
title: "source list for ubuntu 12.04"
date: 2012-10-13
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by rburkartjo on 2012-10-13
was in a middle of an upgrade to 12.10 and lost power made a mess of things. does anyone have a copy of the basic 12.04 (not a typo)source list they could share. my source list is now a mess have part 12.10 and 12.04. my machine says i still am running 12.04 just need to correct my source list to 12.04 and try again to upgrade after the storm. tks

---

### Post by PaulW2U on 2012-10-13
[http://repogen.simplylinux.ch/](http://repogen.simplylinux.ch/) will give you a source list for whichever country you require.

---

### Post by rburkartjo on 2012-10-13
paul tks pretty cool

---

### Post by grahammechanical on 2012-10-13
I recently had problems updating due to missing headers in a source list file. I found two command helpful. I suggest that you first make sure that the repositories are set to Precise and not Quantal. Then If you want you can run

```
sudo rm /var/lib/apt/lists/* -rf
```

```
sudo apt-get update
```

The first command deletes the sources lists. The second command repleces them.

Regards.

---

### Post by philinux on 2012-10-13
> **rburkartjo said:**
> paul tks pretty cool

You can mark your own threads as solved from the drop down menu "Thread Tools".

---

