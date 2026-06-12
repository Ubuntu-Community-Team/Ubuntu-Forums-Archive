---
title: "VMWare install requires &quot;make&quot;"
date: 2009-03-23
forum: Server Platforms
---

### Post by BradleyAtkins on 2009-03-23
Hi

Still trying to install VMWare, I am now stuck as vmware-config.pl cannot find "make"

[B]Before running VMware Server for the first time, you need to configure it by invoking the following command: "/usr/bin/vmware-config.pl". Do you want this program to invoke the command for you now? [yes]

Setup is unable to find the "make" program on your machine.  Please make sure it is installed.  Do you want to specify the location of this program by hand?[/B]

I have no man entry for make nor does 'which' find it. Is this part of gcc by any chance, do I need to find and install something else first?

Thanks

Brad

---

### Post by SuperSonic4 on 2009-03-23
the build-essential packages has make in it as well as everything you need to compile from source

```
sudo apt-get install build-essential
```

If you want make on it's own;

```
sudo apt-get install make
```

---

### Post by BradleyAtkins on 2009-03-23
Thanks

I found make but will try the build-essential as well as it sounds err well essential :D

cheers

---

