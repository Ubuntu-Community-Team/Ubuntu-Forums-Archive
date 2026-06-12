---
title: "Firebird 1.5 on Ubuntu Server 8.04"
date: 2008-08-12
forum: Server Platforms
---

### Post by Jaime Escobal on 2008-08-12
Hi friends.
I need to install Firebird 1.5.5 on an Ubuntu Server (we are replacing a SUSE 10 server). But I cannot find that version of firebird in the repositories. I tried to install from a tarball but had no success... Is anybody using Firebird 1.5 on Ubuntu server?
thanks for any help
Jaime Escobal

---

### Post by BioComputing on 2009-07-22
```
sudo apt-get install libstdc++5
```


from:

[http://www.firebirdsql.org/index.php?op=files&id=engine_155](http://www.firebirdsql.org/index.php?op=files&id=engine_155)



download:

FirebirdSS-1.5.5.4926-0.i686.tar.gz



unpack & open terminal, enter firebird setup directory and execute:



```
sudo ./install.sh
```

Firebird can be restarted with:
```
sudo /etc/init.d/firebird reload
```

Firebird path is:

/opt/firebird

---

