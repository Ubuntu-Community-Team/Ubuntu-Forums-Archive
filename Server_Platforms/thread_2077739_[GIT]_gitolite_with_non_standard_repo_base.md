---
title: "[GIT] gitolite with non standard repo base"
date: 2012-10-29
forum: Server Platforms
---

### Post by fri.K on 2012-10-29
Hi
I'm trying to set my own git repository. I was fallowing this [how-to]("http://blog.countableset.ch/2012/04/29/ubuntu-12-dot-04-installing-gitolite-and-gitweb"), but I had to change
```
$REPO_BASE="/some/path/git/repositories";
``` in ..gitolite.rc. My whole config is in ```
/home/git/
```I'm able to clone repository testing and gitolite-admin, but when I try add new repository by adding in ```
vim /home/git/.gitolite/conf/gitolite.conf
``` new def: ```
repo    test
        RW+     =   @all
         R         = gitweb
```And then ```
git commit -a -m "Add test repository"
``` gives an error: ```
fatal: Not a git repository (or any parent up to mount parent )
Stopping at filesystem boundary (GIT_DISCOVERY_ACROSS_FILESYSTEM not set).
```I [found]("http://www.bigfastblog.com/gitolite-installation-step-by-step") that it can be ```
git commit .gitolite/conf/gitolite.conf -m "Add test repository"
``` but it also gives same error.
What am I doing wrong?
---
Edit
/home/git and /media/git/repositories are on different partitions
----
Edit2
My bad. I spouse to clone gitolite-admin on client side, make changes, commit and pushed it. Everything works great.

---

### Post by Crafty Kisses on 2012-10-29
Ah, nice. That's what I thought it was, I just seen you solved it towards the bottom.

---

### Post by fri.K on 2012-10-31
> **Crafty Kisses said:**
>  I just seen you solved it towards the bottom. Yes, I figured  out by myself, but thanks for good intentions :)
Regards

---

