---
title: "Synaptic shows as update but already updated"
date: 2005-06-08
forum: Repositories &amp; Backports
---

### Post by xalphas on 2005-06-08
Hi to all.. I've been searching forum with different keywords and by surfing through topics but couldn't find an answer to my problem. First of all sorry if i've opened an already answered question. 

```
deb http://us.archive.ubuntu.com/ubuntu hoary main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu hoary main restricted universe multiverse

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://us.archive.ubuntu.com/ubuntu hoary-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu hoary-updates main restricted

deb http://security.ubuntu.com/ubuntu hoary-security main restricted
deb-src http://security.ubuntu.com/ubuntu hoary-security main restricted

# deb http://security.ubuntu.com/ubuntu hoary-security universe
# deb-src http://security.ubuntu.com/ubuntu hoary-security universe

deb ftp://ftp.nerim.net/debian-marillat/ stable main
deb ftp://ftp.nerim.net/debian-marillat/ unstable main
deb ftp://ftp.nerim.net/debian-marillat/ testing main

#Primary Mirror (5/17/2005) overloaded :)
#deb http://backports.ubuntuforums.org/backports hoary-backports main universe multiverse restricted
#deb http://backports.ubuntuforums.org/backports hoary-extras main universe multiverse restricted

#backup Mirror - FAST
deb ftp://ftp2.caliu.info/backports/ hoary-backports main universe multiverse restricted
deb ftp://ftp2.caliu.info/backports/ hoary-extras main universe multiverse restricted
``` 

This is my source.list came from ubuntu-geeks auto script. I've updated gaim and firefox 1.04. But even i refresh from synaptic or apt-get update i always see the updated packages on the list as waiting to be updated. 

I've updated again and it installed normally. Then again it stays checked to be updated. I couldn't solve this issue. Can anybody help me?

Thx.

---

### Post by Sniffer on 2005-06-09
Lock both packages (Gaim and Firefox).

It isn't the ideal solution..but it is one.


PS: it could be also the same version but from different Reposit, for instance nerim and ubuntu ones, and when you install nerim want to update to ubuntu and when you install ubuntu want to update to nerim...

Try to disable nerim Reposit with an # behind the links and reload sources and Test it out.

---

### Post by xalphas on 2005-06-09
Thx for the reply sniffer. I disabled nerim but result is the same. Also i would like to attach a shot from synaptic. Maybe it can tell my problem better way. As the picture below both packages are the same the installed and the latest versions..

---

### Post by Sniffer on 2005-06-12
Very Odd..indeed...

Have tried your source list in my Ubuntu and it works as it is supposed to be....

Can't help you buddy...could be some config file that is leading to that result... :neutral:

---

### Post by Xian on 2005-06-12
Open Synaptic and search to find the package(s) in question.
When you find it, right-click on it and choose 'Mark for Upgrade'.

Does it let you do this?

---

### Post by xalphas on 2005-06-12
Yes it let's me do it. Especially i can use every function of synaptic. The only problem is i always same package updates. 

For to clear about souce.list, it comes from automate script of ubuntugeek. I am thinking this can be header problem maybe not recognize the versions. Anyway just a thought. 

Still need help. 

Thx.

---

### Post by Xian on 2005-06-12
So then you're saying that if you right-click and choose 'Mark for Upgrade', then click 'Apply', and let the upgrade install on your box, that you are then able to go right back in and do the same process again on the same package?

Is the version not updating or does it show as updated?

---

### Post by Sniffer on 2005-06-13
[QUOTE=Xian]So then you're saying that if you right-click and choose 'Mark for Upgrade', then click 'Apply', and let the upgrade install on your box, that you are then able to go right back in and do the same process again on the same package?

Is the version not updating or does it show as updated?[/QUOTE]


He can update the packages..but when finishing and doing the reload appears to update again to the same version..like a cicle....

Just check the screenshot.

Maybe he should make a new file sources.list and see the results..just an idea..instead of using the automatic script that provided that same file..

Just an Idea...

---

### Post by xalphas on 2005-06-13
Thx @sniffer you got my problem. Exactly it is. 

I've also changed sources.list in ubuntuguide.org and tried some other repository addresses but no changes..

---

### Post by Xian on 2005-06-13
Clean out your entire apt cache:

```
$ sudo apt-get clean
```

---

### Post by xalphas on 2005-06-14
Thx Xian but already tried apt-get clean.. No result . Still the same.

---

### Post by xalphas on 2005-06-20
Only added ;

deb [http://acm.cs.umn.edu/ubp/](http://acm.cs.umn.edu/ubp/) hoary-backports main universe multiverse restricted

Now it is ok. No duplicate updates after apt-get update.

---

