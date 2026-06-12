---
title: "lxc and ubuntu"
date: 2014-10-28
forum: Virtualisation
---

### Post by c-vijaya-durga on 2014-10-28
hello all,

I am trying to create a container using lxc on ubuntu virtual machine. host OS is ububtu 13.04
when I try running the command **sudo lxc-create -t ubuntu -n rs **the command fails with below error. The sources in sources.list on host vm have all been to point to [http://old-releases.ubuntu.xyz](http://old-releases.ubuntu.xyz) and I am not really sure how I can fix the below error, any help is appreciated
[ATTACH=CONFIG]257542[/ATTACH]

---

### Post by Bucky Ball on 2014-10-28
13.04 has reached end-of-life and is no longer supported by Canonical or these forums. Please use a supported release, either 12.04 LTS, 14.04 LTS or 14.10 (I would advise 14.04 LTS supported until 2019) and then report back with any further issues.

Also, see [HERE]("https://help.ubuntu.com/community/EOLUpgrades"). 

The repositories for 13.04 are closed and you will not be able to update, upgrade, or find many of the packages and dependencies you are looking for.

---

### Post by c-vijaya-durga on 2014-10-28
Thank you. 
I retried creating containers on 12.04 and the command works just fine.

---

### Post by Bucky Ball on 2014-10-28
Excellent news and thanks for sharing the fix and marking as solved. Good luck. ;)

---

