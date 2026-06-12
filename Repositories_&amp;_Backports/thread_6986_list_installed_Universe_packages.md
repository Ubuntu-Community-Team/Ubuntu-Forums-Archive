---
title: "list installed Universe packages"
date: 2004-12-03
forum: Repositories &amp; Backports
---

### Post by M@t on 2004-12-03
Is there a way to have a list of installed packages which belongs to universe ? I remember I saw a very little script which could do that, but I don't know where.

---

### Post by ubuntu_demon on 2004-12-03
you can create a custom filter in synaptic

check the box "installed" and include all universe sections

---

### Post by M@t on 2004-12-03
Ok, thank you. But as Synaptic is just a front end to other packages management tool, is it possible to do that with apt or dpkg ?

---

### Post by ubuntu_demon on 2004-12-03
you could write a script to do that I think

---

### Post by M@t on 2004-12-03
I know I could write a script, but I quickly read man of dpkg, apt-get and apt-cache and still don't know how to do that. I didn't see any command which return the component of the repository (main, restricted, universe or multiverse).

Synaptic is great, but I still prefer command-line ](*,) .

---

### Post by ubuntu_demon on 2004-12-03
I can't help you with that ... try google or apropos or wait for someone else who knows :)

---

### Post by M@t on 2004-12-03
I finally found my answer in this french page: [HTML]http://wiki.frimouvy.org/FaqUbuntuDebian[/HTML].

So to know which are the installed packages which belongs to universe, type the following command:
```
comm -12 <(apt-cache dumpavail | grep-dctrl -nsPackage -FSection universe/ |sort) <(dpkg --get-selections | awk '$2 == "install" { print $1 }' |sort)
```

You could replace universe by any another component of the repository.

---

### Post by ubuntu_demon on 2004-12-03
That's a long command  :p

---

