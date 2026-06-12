---
title: "How to re-install my.conf from mysql-common?"
date: 2006-08-23
forum: Server Platforms
---

### Post by abonnema on 2006-08-23
HI All,

I accidentally deleted /etc/mysql which also contains my.cnf. Now I know the package mysql-common has a perfectly sane default version of my.cnf.

Can anyone tell me how I can reinstall all configuration files from mysql-common?

Help is appreciated.

Guus.

---

### Post by mlind on 2006-08-23
You can either purge & install package, or download the .deb and extract the file you need from it

a) Purge & install:
```

sudo dpkg -P --force-depends mysql-common
sudo aptitude install mysql-common

```
(Note: **aptitude reinstall** doesn't seem to replace configuration files, so you need to purge package first.)

b) Download & copy:
```

mkdir /tmp/mysql
cd /tmp/mysql
aptitude download mysql-common
dpkg -x mysql-common*.deb .
sudo cp etc/mysql/my.cnf /etc/mysql

```

---

### Post by abonnema on 2006-08-24
> **mlind said:**
> You can either purge & install package, or download the .deb and extract the file you need from it

a) Purge & install:
```

sudo dpkg -P --force-depends mysql-common
sudo aptitude install mysql-common

``` (Note: **aptitude reinstall** doesn't seem to replace configuration files, so you need to purge package first.)

Yes, I discovered this too.  "sudo apt-get --reinstall install" does  not replace or create any configuration files. 
So, I purged and installed the package. 
The downside is that I had to reinstall some other packages that depend on mysql-common. This turned out to be easier than I thought, because of the inherent dependencies. After installing the two main packages, the rest was "drawn" in.....
> **mlind said:**
> 
b) Download & copy:
```

mkdir /tmp/mysql
cd /tmp/mysql
aptitude download mysql-common
dpkg -x mysql-common*.deb .
sudo cp etc/mysql/my.cnf /etc/mysql

```

This I should have known before I purged. Is a lot easier than reinstalling (although it wasn't too bad).

The knowledge will come in handy anyway, so thanks.
It is always an easy approach to just extract a file.

For the readers, if you want to know how to find which package contains a specific file do:
```

sudo apt-file update 
sudo apt-file search <filename>
``` 

The first line is to make sure apt-file has recent info.

Anyway, thanks for the info.

---

### Post by mlind on 2006-08-24
I should have probably said this with the purge thingy, but I forgot. If you want to remove (purge) a single package, so that its dependencies are not removed (by breaking the dependency chain actually)
```

sudo dpkg -P --force-depends mysql-common
sudo aptitude install mysql-common

```

This way you remove only a single package, and install it back so that all dependencis are satisfied again.

---

### Post by abonnema on 2006-08-24
> **mlind said:**
> I should have probably said this with the purge thingy, but I forgot. If you want to remove (purge) a single package, so that its dependencies are not removed (by breaking the dependency chain actually)
```

sudo dpkg -P --force-depends mysql-common
sudo aptitude install mysql-common

``` 
This way you remove only a single package, and install it back so that all dependencis are satisfied again.

Thanks m8, This one is useful too. I admit I saw this one, just didn't trust the breaking dependencies bit. 

It still seems odd you can break dependencies -- legitimately -- Anyway, if you reinstall right after that it should be ok.

---

### Post by mlind on 2006-08-24
> **abonnema said:**
> Thanks m8, This one is useful too. I admit I saw this one, just didn't trust the breaking dependencies bit. 

It still seems odd you can break dependencies -- legitimately -- Anyway, if you reinstall right after that it should be ok.

From dpkg manual page :mrgreen: 
> 
Warning: These options are mostly intended to be used  by
experts  only.  Using  them  without  fully understanding
their effects may break your whole system.


Warning is there for a reason: some of the --force commands may do nice bit of damage to your system, but this one is great for those (rare) conditions when you don't want to remove ten other packages just fix one package.

I use it everytime in a situation that you were facing on the first post.

---

