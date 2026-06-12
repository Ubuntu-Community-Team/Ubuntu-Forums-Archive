---
title: "compiz update may require a force overwrite"
date: 2014-06-06
forum: Ubuntu Development Version
---

### Post by mc4man on 2014-06-06
If you have compiz-plugins installed then the new compiz upgrade will cause a small issue (compiz 1:0.9.11+14.10.20140606-0ubuntu1

So if an error occurs (/var/cache/apt/archives/compiz-plugins ...blah, blah) no matter. After update in a terminal - 
```
sudo dpkg -i --force-overwrite /var/cache/apt/archives/compiz-plugins_1%3a0.9.11+14.10.20140606-0ubuntu1_amd64.deb

```
or for i386
```
sudo dpkg -i --force-overwrite /var/cache/apt/archives/compiz-plugins_1%3a0.9.11+14.10.20140606-0ubuntu1_i386.deb
```

If you haven't yet upgraded then you could  remove the compiz-plugins package, upgrade, then re-install compiz-plugins

---

### Post by ventrical on 2014-06-07
Got this:

```


Errors were encountered while processing:
 /var/cache/apt/archives/compiz-plugins_1%3a0.9.11+14.10.20140606-0ubuntu1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
ventrical@ventrical-MS-7798:~$ sudo dpkg -i --force-overwrite /var/cache/apt/archives/compiz-plugins_1%3a0.9.11+14.10.20140606-0ubuntu1_amd64.deb
(Reading database ... 333654 files and directories currently installed.)
Preparing to unpack .../compiz-plugins_1%3a0.9.11+14.10.20140606-0ubuntu1_amd64.deb ...
Unpacking compiz-plugins (1:0.9.11+14.10.20140606-0ubuntu1) over (1:0.9.11+14.04.20140423-0ubuntu1) ...
dpkg: dependency problems prevent configuration of compiz-plugins:
 compiz-plugins depends on compiz-core (= 1:0.9.11+14.10.20140606-0ubuntu1); however:
  Package compiz-core is not configured yet.
 compiz-plugins depends on compiz-plugins-default (= 1:0.9.11+14.10.20140606-0ubuntu1); however:
  Package compiz-plugins-default is not configured yet.
 compiz-plugins depends on libdecoration0 (>= 1:0.9.2.1); however:
  Package libdecoration0 is not configured yet.
 compiz-plugins depends on libxml2 (>= 2.7.4); however:
  Package libxml2:amd64 is not configured yet.

dpkg: error processing package compiz-plugins (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 compiz-plugins
ventrical@ventrical-MS-7798:~$ 

```


so is it borked?

Regards..

---

### Post by mc4man on 2014-06-07
> **ventrical said:**
> Got this:


so is it borked?

Regards..
No, I'm sure you can fix that. Not sure why you got extended issues, here the only thing that happened was the compiz-plugins package broke & was fixed with the com.
An alternative for those who haven't upgraded yet would be to remove the compiz-plugins package, upgrade, then re-install compiz-plugins

---

### Post by ventrical on 2014-06-07
> **mc4man said:**
> No, I'm sure you can fix that. Not sure why you got extended issues, here the only thing that happened was the compiz-plugins package broke & was fixed with the com.
An alternative for those who haven't upgraded yet would be to remove the compiz-plugins package, upgrade, then re-install compiz-plugins


That worked .. but looks like compiz-plugins/settings-manager is in worse shape than I thought.

---

