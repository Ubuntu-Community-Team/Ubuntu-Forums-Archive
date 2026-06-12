---
title: "all the dependencies in one package"
date: 2008-10-23
forum: Ubuntu Brainstorm
---

### Post by jayanthan on 2008-10-23
:idea:

well for linux users with no internet or dial-up as in the case of developing countries, its a very difficult task to install packages.
they have to get all the dependencies satisfied to install one package and this is **totally exhausting.**

to go some friends home or cafe,
download packages and find dependencies and download them also,
bring them home,
install and if some goes wrong,
trace it and get a solution.

its a reason why open source doesnt get enough users.

so why dont someone (i dont know linux development and if try it'd take years) come forward with some solution; like the installation files in windows.


**_OR_**

if there is will u say?

---

### Post by cdenley on 2008-10-23
I think Ubuntu's package management is more efficient than binary installers. The reason dependencies are seperated into seperate packages is because several packages often share the same dependencies. If packages were packaged with their dependencies, you would end up installing the same libraries ten times. This would use more bandwidth and disk space.

---

### Post by smartboyathome on 2008-10-23
The web interface for packages.ubuntu.com needs to be better so that you can get packages easily from it imo (ie, it needs a "packaging list" type featuree in which you can click something like "add to list" next to the packages you want to add to a list to download, then when you are ready it will let you download them with all it's dependancies easily). Once you had all the packages, you could use aptoncd (I think its called) to make a repo CD for your computer(s).

The reason the all in one package can't be done with debian (technically, it can, but it would be painful) is because if two packages have the same dependancies, and you try to install both, one will try to install it's dependancies over the other. When a package tries to do this, Debian's package management system won't let the package install. I know this could

---

### Post by cdenley on 2008-10-23
> **smartboyathome said:**
> The web interface for packages.ubuntu.com needs to be better so that you can get packages easily from it imo (ie, it needs a "packaging list" type featuree in which you can click something like "add to list" next to the packages you want to add to a list to download, then when you are ready it will let you download them with all it's dependancies easily). Once you had all the packages, you could use aptoncd (I think its called) to make a repo CD for your computer(s).

The reason the all in one package can't be done with debian (technically, it can, but it would be painful) is because if two packages have the same dependancies, and you try to install both, one will try to install it's dependancies over the other. When a package tries to do this, Debian's package management system won't let the package install. I know this could

I think that's a gread idea, so I added it to ubuntu brainstorm.
[[IMG]http://brainstorm.ubuntu.com/idea/14748/image/1/[/IMG]](http://brainstorm.ubuntu.com/idea/14748/)

---

### Post by smartboyathome on 2008-10-23
> **cdenley said:**
> I think that's a gread idea, so I added it to ubuntu brainstorm.
[[IMG]http://brainstorm.ubuntu.com/idea/14748/image/1/[/IMG]](http://brainstorm.ubuntu.com/idea/14748/)

Voted for it. :KS

---

