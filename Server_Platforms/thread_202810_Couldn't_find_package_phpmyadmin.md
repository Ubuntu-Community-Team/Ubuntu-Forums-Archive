---
title: "Couldn't find package phpmyadmin"
date: 2006-06-24
forum: Server Platforms
---

### Post by CheeseAndToast on 2006-06-24
When trying to install phpmyadmin, i get the following error:

Couldn't find package phpmyadmin

I get a similar error when installing mysql-admin

I didn't install LAMP when installing Dapper, i dont recall seeing the option.  I've installed, mysql5. and php5 , and the dependacies to go with it.  I couldn't find mysql4 or php4, but not to bothered.

Any idea?

Thanks

---

### Post by tisse on 2006-06-24
That package is in Universe, have you looked in /etc/apt/sources.list that universe is enabled?

---

### Post by CheeseAndToast on 2006-06-24
I thought I had, i've updated the source.list.  It can now see phpmyadmin, but in synaptic, when apply to install i get this message:
E: The package index files are corrupted. No Filename: field for package phpmyadmin.
E: Unable to lock the download directory

how do I enable that universe?

Cheers.

---

### Post by rpaller on 2006-06-27
[QUOTE=CheeseAndToast]
how do I enable that universe?
[/QUOTE]

```
 sudo cp /etc/apt/sources.list /etc/apt/sources.orig
sudo gedit /etc/apt/sources.list

```

Remove the #'s that appear before the repositories:

```

deb http://archive.ubuntu.com/ubuntu dapper universe
deb-src http://archive.ubuntu.com/ubuntu dapper universe

```

Close and save. Then

```
 sudo apt-get update
```

---

### Post by CheeseAndToast on 2006-06-27
thanks for the reply, i exactly that before - thought i was doing it wrong! Its installed now, I had to reinstall dapper as I tried to configure dual boot on my ATI, but all  sorts of problems occured, so I reformatted!!

First thing I did when got the dapper installed is install LAMP!!  

Sorted now. Thanks

---

