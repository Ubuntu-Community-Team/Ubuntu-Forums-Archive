---
title: "apache2.conf"
date: 2005-11-27
forum: Server Platforms
---

### Post by davebradford on 2005-11-27
i really need some help, i used to use fedora and being silly i just copied over my httpd.conf and renamed it apache2.conf for ubuntu.. which has casued some problems as now i have no backup and all the locations are different, and it's going to take ages to change them all back, just woundering if anybody knows where to find a default apache2.conf that i can just replease in?

any ideas?

---

### Post by davebradford on 2005-11-27
no one got ne ideas??

---

### Post by pingswept on 2005-11-27
Idea:

apt-get remove apache2

apt-get install apache2

---

### Post by davebradford on 2005-11-27
i dont know why but wen i do this it doesnt replease the old conf with the default.. i even tried it again but i deleted apache2.conf then:

apt-get remove apache2
apt-get install apache2

but for some reason it still doesnt give me a new conf?? any more ideas??

---

### Post by invalid on 2005-11-27
There is an option in synaptic to "remove completly", where it will remove all configuration files included with the package.. you might try this.

Cheers,
Cb

---

### Post by endurion on 2007-09-26
The option to completely dump Apache2 and all of its config files is:

```
sudo apt-get remove --purge apache2 apache2-common
```

You can then reinstall apache2 by

```
sudo apt-get install apache2
```

And all will be default.

---

### Post by muppis on 2007-10-29
> **endurion said:**
> The option to completely dump Apache2 and all of its config files is:

```
sudo apt-get remove --purge apache2 apache2-common
```

You can then reinstall apache2 by

```
sudo apt-get install apache2
```

And all will be default.
I tried this, but didn't worked for me.
Instead also purging apache2.2-common made it work.

---

### Post by netlogic on 2007-10-29
Have you tried to purge using dpkg?

apt-get remove package
dpkg --purge packagename

---

