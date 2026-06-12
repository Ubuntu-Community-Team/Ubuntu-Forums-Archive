---
title: "Update conflict: ubuntu-settings vs. ubuntu-default-settings"
date: 2012-09-15
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by christian.convey on 2012-09-15
I'm getting the same update conflict for the past few days.  I've been surprised to not find anyone else having this issue (via google search).  Anyone know why I'd be gettig the following?

Here's the end of the output from "sudo aptitude update && sudo aptitude upgrade":

```

The following NEW packages will be installed:
  ubuntu-settings{b} 
The following packages will be upgraded:
  ubuntu-desktop 
1 packages upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 7,370 B of archives. After unpacking 36.9 kB will be used.
The following packages have unmet dependencies:
 ubuntu-settings : Conflicts: ubuntu-default-settings (<= 12.10.1) but 12.10.1 is installed.
The following actions will resolve these dependencies:

     Remove the following packages:                       
1)     ubuntu-desktop                                     

     Keep the following packages at their current version:
2)     ubuntu-settings [Not Installed]                    

```

---

### Post by dino99 on 2012-09-15
if you view the changelog into synaptic you will know why :p

ubuntu-settings replace the other package; by the way both can be dropped if you disagree with the ubuntu settings choices. Thats all up to you.

---

### Post by christian.convey on 2012-09-15
> **dino99 said:**
> if you view the changelog into synaptic you will know why :p

ubuntu-settings replace the other package; by the way both can be dropped if you disagree with the ubuntu settings choices. Thats all up to you.

The problem is that aptitude wanted to also remove "ubuntu-desktop", which seemed like overkill.  That sounds like one of those catch-all virtual packages that I want to keep installed.

However, when I used synaptic to do the upgrade, it didn't feel the need to remove "ubuntu-desktop".

Is that a difference between aptitude and synaptic?  Or did I just get lucky timing such that the conflict was resolved by the time I tried synaptic?

---

### Post by cariboo on 2012-09-15
If you are going to use aptitude:

```
man aptitude
```

is a great resource.

If you don't like the changes aptitude may make, you can us:

```
sudo aptitude --s upgrade
```

to run the upgrade, without actually making any changes. If you think the upgrade will remove needed packages that may cause things to fail, use:

```
aptitude safe-upgrade
```

Removing ubuntu-desktop, really isn't going to cause any problems, and can always be re-installed later on.

---

