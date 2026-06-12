---
title: "apt-pinning not working? Where's the error? please someone help!"
date: 2008-12-01
forum: Repositories &amp; Backports
---

### Post by asbesto on 2008-12-01
Maybe i'm wrong?

I want to prevent the package 

> 
libgnutls26_2.4.1-1build1_i386.deb


to be upgraded by apt-get.

So, I created the /etc/apt/preferences, containing

> 
Package: libgnutls26
Pin: version 2.4.1*
Pin-Priority: 1001



but apt-get continues to update it. 

Where I am wrong?!?

:(

---

### Post by arcanus on 2008-12-02
> **asbesto said:**
> I want to prevent the package libgnutls26 to be upgraded by apt-get.

This will mark the package as "hold" and apt won't update it.
```
echo "libgnutls26 hold" | sudo dpkg --set-selections -
```

to "undo" the change set the package back to install:

```
echo "libgnutls26 install" | sudo dpkg --set-selections -
```

You can also use the --get-selections switch to see the current status on all packages (which you can pipe through grep to filter);
```
dpkg --get-selections
```

Hope this helps :)

---

