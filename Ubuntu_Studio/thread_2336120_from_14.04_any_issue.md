---
title: "from 14.04 any issue"
date: 2016-09-04
forum: Ubuntu Studio
---

### Post by uwe-bungto on 2016-09-04
Upgrading Ubuntu Studio 16.04 has been around for a while. Is there any issues upgrading from 14.04?
Curious if I should go the upgrade path or a clean install. I usually do a clean install; getting lazier in my old age.:)

---

### Post by ajgreeny on 2016-09-05
There is no quick and easy answer to that question; many users have had problems doing the upgrade but many others have had a smooth transition.  Some users doing a clean installation of 16.04 have had problems as well, so I'm afraid it's a case of try it out and if it works well that's great; if it goes wrong you can still overwrite with a clean install.

General points to bear in mind:-
[LIST]
[*]The closer your current system is to a standard installation the more likely you are to be successful.
[*]Remove or disable any non-standard repositories before starting an upgrade, eg any PPAs you have added.
[*]Remove any proprietary graphics drivers before upgrading.
[*]Try the live system before doing either a clean install or an upgrade; that will allow you to see any potential problems before going ahead.
[/LIST]


Good luck whichever method you choose.

---

### Post by uwe-bungto on 2016-09-05
Thanks.
I think the clean install is less problem. 

I found a script ages ago but never used it. it generates a list of installed apps
which can be used to build the system as it was before new install.

Has anyone tried this??

> HowTo: Create a list of installed packages
```
sudo dpkg --get-selections > installed-software
```
And if you wanted to use the list to reinstall this software on a fresh ubuntu setup,
```
sudo dpkg --set-selections < installed-software
```
followed by
```
sudo dselect
```



---

### Post by ajgreeny on 2016-09-05
> **uwe-bungto said:**
> Thanks.
I think the clean install is less problem. 

I found a script ages ago but never used it. it generates a list of installed apps
which can be used to build the system as it was before new install.

Has anyone tried this??
sudo dpkg --get-selections > installed-software
sudo dpkg --set-selections < installed-software
sudo dselect

No I've never bothered.
I always clean install as well, but have a separate /home partition (with backups just in case), so that is quick and easy; I then install codecs and other packages that I know I'll need as I find I need them.

---

### Post by uwe-bungto on 2016-09-05
> **ajgreeny said:**
> No I've never bothered.
I always clean install as well, but have a separate /home partition (with backups just in case), so that is quick and easy; I then install codecs and other packages that I know I'll need as I find I need them.

Same here /home has its own partition. I use backintime to backup to an external drive, 

Thanks
 I guess it is solved

---

