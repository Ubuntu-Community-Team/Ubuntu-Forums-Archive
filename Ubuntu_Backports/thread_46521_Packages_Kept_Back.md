---
title: "Packages Kept Back"
date: 2005-07-05
forum: Ubuntu Backports
---

### Post by larry on 2005-07-05
Dear All,
I have recentely added the backport repositores, and though many packages were updated, 3 of them are always kept back.
This is the output of sudo apt-get upgrade:

Reading package lists... Done
Building dependency tree... Done
The following packages have been kept back:
  acroread mozilla-firefox mozilla-firefox-gnome-support
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.

What does it mean that these packages never get upgraded? Is it for security/stability reasons or not? Would it be reasonably safe, if possible, to upgrade them?
Cheers
Larry

---

### Post by Xian on 2005-07-05
If you will instruct apt to install a pkg specifically it will give you a more detailed error output. In that way you might have a better idea of what is causing a pkg to be held back. For example, 
```
$ sudo apt-get install acroread
```

---

### Post by larry on 2005-07-05
Thanks for your interest.
This is the result of what you suggest:

 sudo apt-get install acroread
Password:
Reading package lists... Done
Building dependency tree... Done
Suggested packages:
  mozilla-acroread
Recommended packages:
  acroread-plugins
The following packages will be REMOVED:
  acroread-debian-files
The following packages will be upgraded:
  acroread
1 upgraded, 0 newly installed, 1 to remove and 2 not upgraded.
Need to get 23.4MB of archives.
After unpacking 29.1MB of additional disk space will be used.
Do you want to continue [Y/n]? n
Abort.

I did not feel like trying my luck right now, but it seems that the package can be updated.  I get a similar output with the other two held-back packages.
I would like to know simply if it is safe to install/update them (I do not want to end up with a broken system).
Cheers
Larry

---

### Post by Xian on 2005-07-05
[QUOTE=larry]Thanks for your interest.
This is the result of what you suggest:[/QUOTE]
The reason this package (and possibly the others as well) was being held back, is because in order to install it another package, which in this case is 'acroread-debian-files', needs to be removed. Apt is simply wanting your confirmation before continuing with the process of installing acroread. It wants you to confirm that you do not need the to-be removed package for some necessary and local purpose.

---

### Post by larry on 2005-07-06
I see. I updated the system and everything seems fine. I simply had to confirm I wanted to use packages which could not be verified (I do not recall the exact expression).
Probably it has to do with the backport repositories; is there a way to make the system accept them as "trusted" repositories?
Cheers
Larry

---

### Post by manicka on 2005-07-06
I don't mind that message. It's a quick reminder that what you are installing comes from backports. You can always back out at this stage if you're unsure

---

