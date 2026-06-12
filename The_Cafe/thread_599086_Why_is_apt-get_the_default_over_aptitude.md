---
title: "Why is apt-get the default over aptitude?"
date: 2007-10-31
forum: The Cafe
---

### Post by sunexplodes on 2007-10-31
Everytime I see a post on Ubuntuforums where someone gives terminal instructions, they always use apt-get. But from what I understand, aptitude is a more powerful and better organized application. So why is apt-get still the go-to command?


Just a curiosity.

---

### Post by vexorian on 2007-10-31
If I understand, aptitude will simply remove dependencies that are not necessary anymore, that's the only difference.

I would go for apt-get cause the thing is that more often than not, if you needed a dependency once you are most likely going to need it again. So it saves some download time in the future, dependencies tend not to take too much size, and you can even go to synaptic to browse for packages that are not required anymore if you need to save space (although most of my space issues come from downloaded videos and ISO images rather than installed packages)

---

### Post by aysiu on 2007-10-31
Sometimes *aptitude* thinks it's smarter than it really is and starts removing a ton of stuff the user doesn't want removed. That's why people recommend *apt-get* instead. Now that *apt-get* has the *autoremove* feature, the advantages of *aptitude* over *apt-get* are dubious.

---

### Post by D-EJ915 on 2007-10-31
apt-get is much easier to type (at least for me) and takes less time to type...it's shorter too

---

### Post by TeraDyne on 2007-11-01
> **aysiu said:**
> Sometimes *aptitude* thinks it's smarter than it really is and starts removing a ton of stuff the user doesn't want removed. That's why people recommend *apt-get* instead.

Like the time *aptitude* wanted to get rid of KOffice when I just wanted to remove "ubuntu-desktop" and anything relating to the Gnome desktop GNOME. That right there made me switch to *apt-get*.

---

### Post by FredB on 2007-11-01
I'm using aptitude for installing softaware, apt-get to remove software.

Depends on my feelings :)

---

### Post by xat_ on 2007-11-01
From a friend -
> 
23:24 <_> first, aptitude can identify auto-installed packages which are no longer needed - but only if you install everything via aptitude
23:24 <_> (newer versions of apt-get have introduced this functionality as well, but it's not in stable yet)
23:24 <_> it also handles certain degenerate cases of dependency resolution that apt-get doesn't
23:25 <_> particular if you're mixing distro versions, and the package dependencies aren't fully consistent (ie, packages which should be co-installable aren't) it'll suggest downgrades as needed
23:25 <_> there are some other dependency issues it handles better, I don't know the techncial details


---

### Post by gradedcheese on 2007-11-01
well, apt-get has special cow powers...

---

### Post by some_random_noob on 2007-11-01
> **TeraDyne said:**
> Like the time *aptitude* wanted to get rid of KOffice when I just wanted to remove "ubuntu-desktop" and anything relating to the Gnome desktop GNOME. That right there made me switch to *apt-get*.

Yes. That appears to be the problem. Why remove "obsolete" packages when most people have plenty of HD space anyway? A "cleanup" isn't worth it when you risk losing software/packages that you will need in the future.

---

### Post by mysticmatrix on 2007-11-01
> **aysiu said:**
> Sometimes *aptitude* thinks it's smarter than it really is and starts removing a ton of stuff the user doesn't want removed. That's why people recommend *apt-get* instead. Now that *apt-get* has the *autoremove* feature, the advantages of *aptitude* over *apt-get* are dubious.

Grandpa debian recommends Aptitude. Look here [http://www.debian.org/doc/manuals/reference/ch-package.en.html](http://www.debian.org/doc/manuals/reference/ch-package.en.html)

> aptitude is now the preferred text front end for APT, the Advanced Package Tool. It remembers which packages you deliberately installed and which packages were pulled in through dependencies; the latter packages are automatically de-installed by aptitude when they are no longer needed by any deliberately installed packages. It has advanced package-filtering features but these can be difficult to configure

Also, the problem occur usually when one tries to mix Aptitude and Apt-get. If everything is installed via Aptitude, it is quite good at not to nuke things unnecessarily. 
BTW, we are stuck with apt-get as ubuntu default install uses it right from installation of base package.
Also, I found that its lot easier to install large meta packages like kubuntu-desktop with aptitude as it does remembers to clean up mess if one wants to uninstall KDE later.

Also, as dependencies are usually in apt cache anyway, so there is no point in keeping them for futute just in hope that they MIGHT be useful some other day. Sorta reminds me how I keep precious "waste" for years in my house.

---

### Post by qazwsx on 2007-11-01
aptitude needs apt .

aptitude is also very bad choice for debian unstable.

If you are using aptitude it might want to remove a package you don't want to install. I hate that.

---

### Post by bruce89 on 2007-11-01
> Why is apt-get the default over aptitude?

People are misguided.

---

### Post by capink on 2007-11-01
> **mysticmatrix said:**
> 
Also, the problem occur usually when one tries to mix Aptitude and Apt-get. If everything is installed via Aptitude, it is quite good at not to nuke things unnecessarily. 
.

I second that. And if someone is using apt-get and want to use aptitude without having it remove anything just run the following command before using aptitude

```
sudo aptitude keep-all
```

---

### Post by Billy_McBong on 2007-11-01
> **gradedcheese said:**
> well, apt-get has special cow powers...
```
$ apt-get moo
         (__) 
         (oo) 
   /------\/ 
  / |    ||   
 *  /\---/\ 
    ~~   ~~   
...."Have you mooed today?"...
```
[COLOR="Blue"]i use apt-get[/COLOR]

---

### Post by bruce89 on 2007-11-01
```
bruce@Scooby-Dum:~$ aptitude moo
There are no Easter Eggs in this program.
bruce@Scooby-Dum:~$ aptitude -v moo
There really are no Easter Eggs in this program.
bruce@Scooby-Dum:~$ aptitude -vv moo
Didn't I already tell you that there are no Easter Eggs in this program?
bruce@Scooby-Dum:~$ aptitude -vvv moo
Stop it!
bruce@Scooby-Dum:~$ aptitude -vvvv moo
Okay, okay, if I give you an Easter Egg, will you go away?
bruce@Scooby-Dum:~$ aptitude -vvvvv moo
All right, you win.

                               /----\
                       -------/      \
                      /               \
                     /                |
   -----------------/                  --------\
   ----------------------------------------------
bruce@Scooby-Dum:~$ aptitude -vvvvvv moo
What is it?  It's an elephant being eaten by a snake, of course.
```

-v adds verbosity.

---

