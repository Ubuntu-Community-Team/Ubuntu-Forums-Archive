---
title: "Put to next output erratic/broken after latest updates?"
date: 2012-02-13
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by prusswan on 2012-02-13
is this happening for anyone else? I'm using Button 2 (middle mouse button) if that matters

---

### Post by prusswan on 2012-02-14
should this issue be filed against compiz or ccsm?

---

### Post by mc4man on 2012-02-14
If there is an issue with a plugin then file against it (compiz-plugins-main

The only time i've seen ccsm be in issue in this area is if one tries to use the Ctrl key in a key binding which isn't the case here

---

### Post by prusswan on 2012-02-14
> **mc4man said:**
> If there is an issue with a plugin then file against it (compiz-plugins-main

The only time i've seen ccsm be in issue in this area is if one tries to use the Ctrl key in a key binding which isn't the case here

thanks, I will try to downgrade to an earlier version of this package to verify it was working before

---

### Post by mc4man on 2012-02-14
> **prusswan said:**
> thanks, I will try to downgrade to an earlier version of this package to verify it was working before

If you are up to date then downgrading won't be that simple, for example here is the list I'd need to dg to  to check against the previous compiz/unity, if you were headed towards trying the 2 -dev packages are not likely to be needed 
```
$ ls
compiz_0.9.6+bzr20110929-0ubuntu8_all.deb                   libcompizconfig0_0.9.5.94-0ubuntu2_i386.deb
compiz-core_0.9.6+bzr20110929-0ubuntu8_i386.deb             libcompizconfig0-dev_0.9.5.94-0ubuntu2_i386.deb
compiz-dev_0.9.6+bzr20110929-0ubuntu8_i386.deb              libdecoration0_0.9.6+bzr20110929-0ubuntu8_i386.deb
compiz-gnome_0.9.6+bzr20110929-0ubuntu8_i386.deb            libdecoration0-dev_0.9.6+bzr20110929-0ubuntu8_i386.deb
compiz-plugins_0.9.6+bzr20110929-0ubuntu8_i386.deb          libunity-core-5.0-5_5.2.0-0ubuntu3_i386.deb
compiz-plugins-default_0.9.6+bzr20110929-0ubuntu8_i386.deb  unity_5.2.0-0ubuntu3_i386.deb
compiz-plugins-main_0.9.6-0ubuntu4.2_i386.deb               unity-common_5.2.0-0ubuntu3_all.deb
compiz-plugins-main-default_0.9.6-0ubuntu4.2_i386.deb       unity-services_5.2.0-0ubuntu3_i386.deb
```

A number of things/plugins related to windows broke with the latest compiz

Additionally your 'put' plugin isn't one of the 'default' plugins so you may or may not get any directed bug fixing specific to it.

---

### Post by prusswan on 2012-02-15
> **mc4man said:**
> If you are up to date then downgrading won't be that simple, for example here is the list I'd need to dg to  to check against the previous compiz/unity, if you were headed towards trying the 2 -dev packages are not likely to be needed 
```
$ ls
compiz_0.9.6+bzr20110929-0ubuntu8_all.deb                   libcompizconfig0_0.9.5.94-0ubuntu2_i386.deb
compiz-core_0.9.6+bzr20110929-0ubuntu8_i386.deb             libcompizconfig0-dev_0.9.5.94-0ubuntu2_i386.deb
compiz-dev_0.9.6+bzr20110929-0ubuntu8_i386.deb              libdecoration0_0.9.6+bzr20110929-0ubuntu8_i386.deb
compiz-gnome_0.9.6+bzr20110929-0ubuntu8_i386.deb            libdecoration0-dev_0.9.6+bzr20110929-0ubuntu8_i386.deb
compiz-plugins_0.9.6+bzr20110929-0ubuntu8_i386.deb          libunity-core-5.0-5_5.2.0-0ubuntu3_i386.deb
compiz-plugins-default_0.9.6+bzr20110929-0ubuntu8_i386.deb  unity_5.2.0-0ubuntu3_i386.deb
compiz-plugins-main_0.9.6-0ubuntu4.2_i386.deb               unity-common_5.2.0-0ubuntu3_all.deb
compiz-plugins-main-default_0.9.6-0ubuntu4.2_i386.deb       unity-services_5.2.0-0ubuntu3_i386.deb
```

A number of things/plugins related to windows broke with the latest compiz

Additionally your 'put' plugin isn't one of the 'default' plugins so you may or may not get any directed bug fixing specific to it.

I am only able to find the older versions of a few of those packages (compiz is one of them) through update-manager, how can I get/see the rest?

---

### Post by cariboo on 2012-02-15
> **prusswan said:**
> I am only able to find the older versions of a few of those packages (compiz is one of them) through update-manager, how can I get/see the rest?

For a new user like you synaptic package manager would probably be the best program to use. If you want to search for packages via the command line aptitude is probably the best application. Check man aptitude.

---

### Post by prusswan on 2012-02-15
Filed as [Bug #932624]("https://bugs.launchpad.net/compiz-plugins-main/+bug/932624"). Downgrade to 0.9.6 is the only workaround now

---

