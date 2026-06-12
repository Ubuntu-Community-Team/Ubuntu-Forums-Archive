---
title: "php 5.2 for 6.10?"
date: 2006-12-02
forum: Repositories &amp; Backports
---

### Post by dodgyville on 2006-12-02
Hi,

I was wondering the best way to get php 5.2 installed on my ubuntu edgy eft machine? I notice in the repository there's only php 5.1.6.

Is there a package available from somewhere or is it possible to do it from source without hosing apt?

Regards,
Luke

---

### Post by mlind on 2006-12-05
> **dodgyville said:**
> Hi,

I was wondering the best way to get php 5.2 installed on my ubuntu edgy eft machine? I notice in the repository there's only php 5.1.6.

Is there a package available from somewhere or is it possible to do it from source without hosing apt?

Regards,
Luke

You can take the source package from Debian unstable and use it to build binaries (.deb packages) for your distribution.
Some build dependencies need to be relaxed for Edgy, so it's not just a trivial rebuild process.

I need php 5.2 for Edgy and I'm going to do this tomorrow. I'll provide the binaries for you once I get it done.

---

### Post by bond00 on 2006-12-15
any binaries? I'm in need of PHP 5.2 too!! I was also thinking of adding either an Edgy or Fawn repository to add it that way. What do you think? Do you know what the repo would be for those?

---

### Post by k7k0 on 2007-01-08
Taken from [linuxcompatible.org]("http://www.linuxcompatible.org/PHP_5.2.0_for_Debian_3.1_updated_s75722.html"):

Here the apt source for /etc/apt/sources.list: 
```
deb http://packages.dotdeb.org stable all
deb-src http://packages.dotdeb.org stable all
```

---

### Post by SubWolf on 2007-01-15
Installed from dotdeb, worked beautifully.

For those not sure how to specify the exact version:

```
sudo apt-get install php5=5.2.0-0.dotdeb.3
```

---
```

~# php -i
phpinfo()
PHP Version => 5.2.0-0.dotdeb.3
```

---

### Post by counterpoint on 2007-04-05
Is there an update to this?  The last suggestion seems not to work now.

---

### Post by Koobi on 2007-04-11
> **counterpoint said:**
> Is there an update to this?  The last suggestion seems not to work now.

thatm might be due to an absence in the GPG key.

i tried to fix that using this:
```

wget http://medibuntu.sos-sts.com/repo/medibuntu-key.gpg -O- | sudo apt-key add -

```


but it didn't work.

Is there another way?

---

