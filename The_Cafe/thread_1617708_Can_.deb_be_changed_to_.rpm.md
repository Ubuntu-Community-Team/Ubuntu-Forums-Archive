---
title: "Can .deb be changed to .rpm?"
date: 2010-11-09
forum: The Cafe
---

### Post by Artemis Fowl on 2010-11-09
Sorry if this is the wrong forum, I wasn't sure where to put it.
Anyway, one of the reasons I went to Linux is the diversity of distros. Right now, I'm interested in trying Fedora. My question is, can .deb files be changed to .rpm?

---

### Post by lykwydchykyn on 2010-11-09
Alien can do it, though I can't swear that the resulting rpm will actually work:
```

alien -r somedeb.deb

```

---

### Post by Artemis Fowl on 2010-11-09
Thanks. Going to virtualbox fedora now.

---

### Post by loell on 2010-11-09
it's always a hit and miss thing. it's still better to persuade the developer/company to make deb packages if this is close source, and actually compile the soure if this is open.

---

### Post by juancarlospaco on 2010-11-09
Smartpm is a Package Manager developed by Canonical that can handle both .deb AND .rpm, its on repos.

---

### Post by coffeecat on 2010-11-09
> **Artemis Fowl said:**
> Right now, I'm interested in trying Fedora. My question is, can .deb files be changed to .rpm?

Little or no need. The Fedora repositories are probably as extensive as the Ubuntu ones with their own rpm packages, and for all the restricted stuff you have RPMfusion and for libdvdcss there is Atrpms. Useful link for you:

[http://www.mjmwired.net/resources/](http://www.mjmwired.net/resources/)

---

### Post by wojox on 2010-11-09
What's the package?

---

### Post by wojox on 2010-11-09
> **coffeecat said:**
> Little or no need. The Fedora repositories are probably as extensive as the Ubuntu ones with their own rpm packages, and for all the restricted stuff you have RPMfusion and for libdvdcss there is Atrpms. Useful link for you:

[http://www.mjmwired.net/resources/](http://www.mjmwired.net/resources/)

They finally changed it. I've been trying to access the Livna Repo for a week now. :)

---

### Post by Artemis Fowl on 2010-11-09
> **wojox said:**
> What's the package?

None in particular, I was just wondering.

---

