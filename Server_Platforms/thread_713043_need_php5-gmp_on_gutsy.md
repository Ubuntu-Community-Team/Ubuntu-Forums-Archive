---
title: "need php5-gmp on gutsy"
date: 2008-03-02
forum: Server Platforms
---

### Post by scragar on 2008-03-02
I tried following the steps on [http://ubuntuforums.org/showthread.php?t=351873](http://ubuntuforums.org/showthread.php?t=351873) to try and install GMP, but although I got a package and installed it I still can't use the GMP functions within PHP.

so I'm guessing my question is:
Does anyone know of a method of getting gmp functions in PHP on gutsy, or will I have to upgrade to hardy?

---

### Post by faulkes on 2008-03-02
> **scragar said:**
> I tried following the steps on [http://ubuntuforums.org/showthread.php?t=351873](http://ubuntuforums.org/showthread.php?t=351873) to try and install GMP, but although I got a package and installed it I still can't use the GMP functions within PHP.

so I'm guessing my question is:
Does anyone know of a method of getting gmp functions in PHP on gutsy, or will I have to upgrade to hardy?

Which steps in there, as there are numerous people posting suggestions.

If you installed a package, what was the packages name?

Have you restarted apache since installing the package?

Faulkes

---

### Post by scragar on 2008-03-02
I used these steps(post 9 on the tread) [http://ubuntuforums.org/showpost.php?p=3198941&postcount=9](http://ubuntuforums.org/showpost.php?p=3198941&postcount=9)
and also installed "libgmp3c2" and "libgmp3-dev" as suggested by the last post on the thread.

---

### Post by BL00dFox on 2008-03-02
Have you tried:

```
sudo apt-get install php-gmp
```

Might not work, but give it a go

---

### Post by scragar on 2008-03-03
there is no GMP package for PHP on gutsy, only hardy. That's why I tried to create my own, but after installing it and restarting apache the GMP functions in PHP still cause errors about undefined functions.

---

