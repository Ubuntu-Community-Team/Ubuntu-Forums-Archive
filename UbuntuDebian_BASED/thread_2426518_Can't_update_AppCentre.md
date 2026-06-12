---
title: "Can't update AppCentre"
date: 2019-09-10
forum: Ubuntu/Debian BASED
---

### Post by lenixxthreeq on 2019-09-10
I started using Elementary OS since yesterday and first I mistakenly installed the non-proprietary display driver from PPA launchpad. I have an NVIDIA 1660ti and later I installed its proprietary driver. I did a lot of things by the night like- Installing python, testing my scripts, Installing VS CODE and messing around the OS since it's the first time I'm trying to move form WINDOWS.  Today morning I opened AppStore which comes preinstalled in Elementary OS and I keep encountering the following errors which prevent me from getting any updates. If you have an idea of some possible fix, it will be a great help.

---

### Post by cruzer001 on 2019-09-10
Looks like you need to remove a ppa for one, please post the output of:
```
sudo apt update
```

---

### Post by slickymaster on 2019-09-10
Thread moved to **Ubuntu/Debian BASED** for a better fit

---

### Post by lenixxthreeq on 2019-09-10
[https://imgur.com/a/lDqzZuJ](https://imgur.com/a/lDqzZuJ)
Thanks for the reply :D

---

### Post by lenixxthreeq on 2019-09-10
> **cruzer001 said:**
> Looks like you need to remove a ppa for one, please post the output of:
```
sudo apt update
```

[https://imgur.com/a/lDqzZuJ](https://imgur.com/a/lDqzZuJ)
Thanks for the reply!

---

### Post by cruzer001 on 2019-09-10
That ppa is no longer supported and needs to be removed.
[https://launchpad.net/~versable/+archive/ubuntu/elementary-update](https://launchpad.net/~versable/+archive/ubuntu/elementary-update)

Your software sources gui can do that.
```
software-properties-gtk
```
or
[https://itsfoss.com/how-to-remove-or-delete-ppas-quick-tip/](https://itsfoss.com/how-to-remove-or-delete-ppas-quick-tip/)

---

### Post by lenixxthreeq on 2019-09-11
> **cruzer001 said:**
> That ppa is no longer supported and needs to be removed.
[https://launchpad.net/~versable/+archive/ubuntu/elementary-update](https://launchpad.net/~versable/+archive/ubuntu/elementary-update)

Your software sources gui can do that.
```
software-properties-gtk
```
or
[https://itsfoss.com/how-to-remove-or-delete-ppas-quick-tip/](https://itsfoss.com/how-to-remove-or-delete-ppas-quick-tip/)

THanks for that! I uninstalled launchpad and removed all PPA stuff from the GTK 
The store works fine! I hope you Have a great day man!!!

---

### Post by cruzer001 on 2019-09-15
Sorry about the late reply, been away for a few days.  Glad it all worked out.

Don't forget to mark your thread as solved.  Located in the tool bar at the top of the thread.

Thanks

---

