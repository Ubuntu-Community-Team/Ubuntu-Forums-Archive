---
title: "after upgrade from 16.10 to 17.04 the system version is still the old one"
date: 2017-01-10
forum: Ubuntu Development Version
---

### Post by 243750496 on 2017-01-10
what happend ???  do that is a bug?
[ATTACH=CONFIG]273128[/ATTACH]

Q1:how to fix it?does it really matter?

---

### Post by TheFu on 2017-01-10
Considering that 17.04 won't be released until April, either
a) you should post this issue in the "development release" subforum; unreleased versions don't get general support.
b) stop using pre-alpha releases.

Maybe a moderator will move this for you?

---

### Post by oldfred on 2017-01-10
Moved.

It still is being updated. I think graphics may be last on list to things the developers work on.

---

### Post by 243750496 on 2017-01-10
the step i upgrade is 

$ sudo apt-get update && sudo apt-get upgrade
 
2.install update-manager-core&#65306;
$ sudo apt-get install update-manager-core
 
3.change /etc/update-manager/release-upgrades&#65292;from Prompt to normal&#65306;
 
                  		
	

then
$ sudo do-release-upgrade -d

---

