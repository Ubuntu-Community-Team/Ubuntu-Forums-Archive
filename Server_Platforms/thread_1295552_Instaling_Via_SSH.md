---
title: "Instaling Via SSH"
date: 2009-10-19
forum: Server Platforms
---

### Post by josephmcnelis on 2009-10-19
Hey All,

This is probably a horribly simple question but how do i install programs onto my Hardy VPS.

Im wanting to set up Nessus but i have been told to install Hydra before hand, but how do i download the files onto my vps and not my local machine?

-Cheers

---

### Post by Sub101 on 2009-10-19
Whilst at the terminal of your server you could use wget to download files from a web address. ie.

```
wget www.some.co.uk/image.jpg
```

---

### Post by Bachstelze on 2009-10-19
You can use wget:

```
wget http://somewhere.org/something.tar.gz
```

---

### Post by josephmcnelis on 2009-10-20
Thanks that will definitely make my life much easier ^_^

---

### Post by Lars Noodén on 2009-10-20
> **josephmcnelis said:**
> Thanks that will definitely make my life much easier ^_^

It will be even easier using the package manager.  That will keep track of the versions, let you easily upgrade or patch, and will take care of any dependencies.  

You can use the [aptitude](http://manpages.ubuntu.com/manpages/karmic/en/man8/aptitude.8.html) or [apt-get](http://linux.die.net/man/8/apt-get)

```

apt-get autoremove
apt-get update
apt-cache search apache | sort | less
apt-get install libapache-dbi-perl

```

or 

```

apt-get update && apt-get install tidy

```

or

```

apt-get update \
 && apt-get upgrade \
 && apt-get dist-upgrade

```

or

```

apt-get update
aptitude install tidy

```

and so on.

---

