---
title: "How to install OpenSSL from source?"
date: 2010-05-09
forum: Server Platforms
---

### Post by bovcan on 2010-05-09
Hi!
I saw, there is a new OpenSSL v 1.0.0 and I wanna ask how to install it.
I have this server now Apache/2.2.14 (Ubuntu) PHP/5.2.10-2ubuntu6.4 with Suhosin-Patch mod_ssl/2.2.14 OpenSSL/0.9.8k

And I try to install by reading the Install file in the package but I still have 0.9.8k.
  $ ./config
  $ make
  $ make test
  $ make install

Did I forgot something?

---

### Post by bovcan on 2010-05-09
So, no idea?

---

### Post by windependence on 2010-05-09
Latest and greatest isn't always the best. You won't have package management if you install it this way. The included version works just fine for me, maybe you want to reconsider?

-Tim

---

### Post by drewjw81 on 2010-06-03
If you absolutely need the latest version of openssl then here's how to go about installing it.  You're going to have to remove openssl & libssl-dev first and this might force other packages to be removed.  So don't do this unless you know what you're doing and pay attention to what's happening.

Also this can and will cause problems with postfix and the ssl-cert packages so if you need those packages then don't do this.

First remove the currently installed version of openssl completely
```

sudo aptitude remove openssl libssl-dev

```

Now compile & install a new copy of openssl from source
```

cd
wget http://www.openssl.org/source/openssl-1.0.0a.tar.gz
tar -xvzf openssl-1.0.0a.tar.gz
cd openssl-1.0.0a/
./config --prefix=/usr
sudo make
sudo checkinstall

```

---

### Post by 4004 on 2010-09-08
I followed the instruction from drewjw81, except that I installed openssl-1.0.0a at /usr/local/ssl. When I tested with "openssl version", I got openssl-1.0.0a and applied some system update after that but after restarting the system, I got back 0.9.8k
I removed the 0.9.8k and tried reinstalling 1.0.0a but after the whole process was completed, on typing 'openssl version',  I got;

prom@Host1:~$ openssl version
The program 'openssl' is currently not installed.  You can install it by typing:
sudo apt-get install openssl
prom@Host1:~$

Even 'sudo apt-get install openssl' reinstalled 0.9.8.k. Could anyone tell me how to really get 1.0.0a working in Ubuntu 10.0 as well as how to apply patch for 1.0.0a

Thanking you in advance.

---

### Post by nealmcb on 2010-12-22
It seems that you got it to build and run fine from source the first time, and ran into some problem the second time you tried that.  So try again.

More details for linking against it are here: [http://stackoverflow.com/questions/3153114/how-do-i-install-and-build-against-openssl-1-0-0-on-ubuntu](http://stackoverflow.com/questions/3153114/how-do-i-install-and-build-against-openssl-1-0-0-on-ubuntu)

Note that any time you use apt-get or other Ubuntu package management commands to install it, you're going to get the Ubuntu version 0.9.8.k.  Based on the stackexchange answer that should be ok (and probably keeps the other Ubuntu dependencies happy).

---

### Post by Todamont on 2012-04-19
according to this security announcement from OpenSSL: 
[http://www.openssl.org/news/secadv_20120419.txt](http://www.openssl.org/news/secadv_20120419.txt)

Users should now be running at least version 1.0.1a for security reasons. So... How do we get this thing repackaged into the LTS Lucid repositories?

---

### Post by flurospar on 2012-04-19
It won't get repackaged.

If you don't want to install from source, you can get the packages of Natty or Oneiric by manual download from packages.ubuntu.com (as well as their dependencies) and install them manually by using dpkg.

---

### Post by Todamont on 2012-04-19
I thought repackaging binaries to fix security issues was sort of the entire point of "LTS"...

---

### Post by marc12 on 2012-04-19
> **Todamont said:**
> I thought repackaging binaries to fix security issues was sort of the entire point of "LTS"...

this. I cant believe that a critical(!) vulnerability in one of the core packages of every server would go unpatched leaving tons of servers vulnerable. not only is this critical, its also urgent because you typically dont have to wait too long to see openssl exploits spread like wildfire...

---

### Post by SeijiSensei on 2012-04-19
> **Todamont said:**
> according to this security announcement from OpenSSL: 
[http://www.openssl.org/news/secadv_20120419.txt](http://www.openssl.org/news/secadv_20120419.txt)

Users should now be running at least version 1.0.1a for security reasons. So... How do we get this thing repackaged into the LTS Lucid repositories?

Did you file a bug report?

[https://bugs.launchpad.net/ubuntu/+source/openssl](https://bugs.launchpad.net/ubuntu/+source/openssl)

---

### Post by Todamont on 2012-04-19
Thanks for the link there.
[https://bugs.launchpad.net/ubuntu/+source/openssl/+bug/985870](https://bugs.launchpad.net/ubuntu/+source/openssl/+bug/985870)

reported as a bug. Cheers~

---

### Post by stmiller on 2012-04-19
Backported in an update:

[http://www.ubuntu.com/usn/usn-1424-1/](http://www.ubuntu.com/usn/usn-1424-1/)

```

sudo apt-get update && sudo apt-get upgrade

```

---

