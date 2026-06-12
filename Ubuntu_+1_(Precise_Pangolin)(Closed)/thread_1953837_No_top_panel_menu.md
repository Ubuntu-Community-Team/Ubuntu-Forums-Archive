---
title: "No top panel menu"
date: 2012-04-07
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by djsroknrol on 2012-04-07
When I upgraded to Presice from Lucid, I lost the menu in the top panel...it worked on the LiveCD. 

Is there a package I can get to reinstall the top panel?

---

### Post by zombifier25 on 2012-04-07
Well, my guess is when upgrading from Lucid to Precise, you kept your home folder, is that correct? If so, then the Compiz profile is preserved as well, and the old Compiz profile has no Unity. This is a common problem when upgrading (me had it too)
Try reseting Compiz:
```
gconftool --recursive-unset /apps/compiz-1
```

---

### Post by djsroknrol on 2012-04-07
That borked all of Unity and the top panel...they both disappeared, so I went and re-installed it...much quicker that way and I had a problem with Grub 2 as well...that for your help anyway :p

---

### Post by JRV on 2012-04-08
The top panel menu is no longer included in Unity, but there is a PPA to add it back in.

```


sudo add-apt-repository -y ppa:diesch/testing
sudo apt-get update
sudo apt-get -y install classicmenu-indicator

```

Log out and back in.
It is the Ubuntu icon on the right hand side of the top panel.

---

