---
title: "problems installing freeradius in ubuntu 8.04.1 lts server edition"
date: 2009-02-25
forum: Server Platforms
---

### Post by linuxisnotmyfriend on 2009-02-25
Hi I am not very good with linux. I have only be working with it for about 3 months. I am trying to put freeradius on my ubuntu system but everything I try it says that it can't find the package. If anyone has any advice please help. I would greatly appreciate it.

---

### Post by terazen on 2009-02-25
The package is listed in [http://packages.ubuntu.com/hardy/allpackages](http://packages.ubuntu.com/hardy/allpackages) so it should be there.

Have you ran it like this?
```
sudo apt-get update
sudo apt-get install freeradius
```

The config file for this is /etc/apt/sources.list and it just needs to have the correct repositories enabled.  If you edit your sources.list make sure the first deb and deb-src lines are uncommented (remove the # sign).

Also you may want to check this for other packages you might need, ie freeradius-ldap...
```
sudo apt-cache search freeradius
```

---

### Post by linuxisnotmyfriend on 2009-02-26
Thanks for reply and I tried all of those and it keeps giving me this error.

E: Couldn't find package freeradius


I don't know where to go from here. If you could please give me some more options I would greatly appreciate it. Thanks again.

---

### Post by terazen on 2009-03-02
In your /etc/apt/sources.list file you are missing a needed repository.  At a minimum the "main" repository will need to be enabled so your file looks like this with no # sign in front:

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy main restricted

You can enable other repositories as needed.  This page explains it in a little more detail.

[http://www.psychocats.net/ubuntu/sources.php](http://www.psychocats.net/ubuntu/sources.php)

---

