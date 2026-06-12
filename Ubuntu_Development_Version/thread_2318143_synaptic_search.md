---
title: "synaptic search"
date: 2016-03-23
forum: Ubuntu Development Version
---

### Post by mc4man on 2016-03-23
On this install the 'quick search' or whatever it is called is gone. From my perspective great, good riddance.
Am curious if it's gone in general or only from something I did locally. If the later I'll have to spend a few moments now  figuring out how so I can do on my upcoming fresh, for real  16.04 install

---

### Post by howefield on 2016-03-23
Same here, gone for some weeks.

---

### Post by dino99 on 2016-03-23
i've experienced this a few times in the past: looks like a logout/in is needed to get it displayed (possibly upstart related or some script activation)

---

### Post by cariboo on 2016-03-23
I've still got it here on one install.

---

### Post by pfeiffep on 2016-03-23
Using UM 16 ... I have the words "rebuilding search index" and then after relaunching synaptic quick filter is present

---

### Post by P-I H on 2016-03-23
Gone on this new install made some days back.

---

### Post by fthx on 2016-03-23
You have to install **apt-xapian-index** package.

---

### Post by PaulW2U on 2016-03-23
> **fthx said:**
> You have to install **apt-xapian-index** package.
Done that on one of my Xubuntu 16.04 installations, rebooted and the Quick Search box is **not** displayed.

There is obviously a bug here. Has anyone reported it? I can't see anything on Launchpad.

---

### Post by howefield on 2016-03-23
> **fthx said:**
> You have to install **apt-xapian-index** package.

Indeed, that did the trick.

Thank you.

---

### Post by mc4man on 2016-03-23
So apt-xapian-index is not on the current Ubuntu image.Apparently is was formerly pulled in by software-center (via packagesearch) , as far as synaptic it is just a Suggests

---

### Post by PaulW2U on 2016-03-23
> **fthx said:**
> You have to install **apt-xapian-index** package.
And that worked for me on my latest Xubuntu live images test, so thanks.
But it took **two** reboots for the search box to appear on my Xubuntu installation. :confused:

---

### Post by JMB74 on 2016-03-24
Won't appear until index has been updated.

Should happen automatically, but can be forced with

**sudo update-apt-xapian-index**

after which the quicksearch should show on a freshly started synaptic

---

