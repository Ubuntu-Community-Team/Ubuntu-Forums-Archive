---
title: "Recovering data from old postgresql install"
date: 2010-05-05
forum: Server Platforms
---

### Post by mjrmua on 2010-05-05
I was previously running postgresql 8.3, but upgrading to Ubuntu 10.04, has installed postgresql 8.4 and I'm now unable to start 8.3.

I don't mind using 8.4, but I need to recover the data from my 8.3 installation, But I'm not sure how to do this as I can't start the 8.3 server, and 8.4 can't read my old data directory.

Please help!

---

### Post by FrankTank on 2010-05-06
Unfortunately I found myself in the same situation. I was unable to find a solution on my PC.

The solution for me was moving my data folder to another PC with 8.3 installed, creating dumps of the relevant db's, copying them back to my PC and restoring them...

---

### Post by k3mist on 2010-05-10
Pretty easy fix actually.

Add the following to your /etc/apt/sources.list:
```
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic main restricted universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic main restricted universe
```

Then type:
```
apt-get update && apt-get install postgresql-8.3
```

If pg8.4 is running, dpkg will report an error that the port is already in use, so I would stop 8.4 first or the installation wont be completed. (dpkg has to run an init script to start the server for installation to be successful)

---

