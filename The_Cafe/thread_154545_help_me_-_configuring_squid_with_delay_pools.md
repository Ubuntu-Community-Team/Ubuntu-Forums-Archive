---
title: "help me - configuring squid with delay pools"
date: 2006-04-03
forum: The Cafe
---

### Post by manishsingh4u on 2006-04-03
Hi,
    I am new to Kubuntu. I am using 5.10 Breezy Badger. I want to limit the bandwidth usage on per pc basis as one of my room mates is eating all the bandwith we have. Among the 4 PCs, mine is the only Linux box (and hence the best to be made a server...lol).

    I have successfully configured and used squid over Fedora Core 1 and SuSE 9.1 by following this article ->
[http://www.linuxsecurity.com/resource_files/firewalls/Bandwidth-Limiting-HOWTO/install.html](http://www.linuxsecurity.com/resource_files/firewalls/Bandwidth-Limiting-HOWTO/install.html)

 I am using the same procedure which I did for them with Kubuntu. But I am getting some gcc errors. I have installed gcc by using apt-get install gcc. Here's what I get on the konsole.
```

root@Manish:/usr/squid# ./configure --prefix=/opt/squid --exec-prefix=/opt/squid --enable-delay-pools --enable-cache-digests --enable-poll --disable-ident-lookups --enable-truncate --enable-removal-policies
loading cache ./config.cache
checking host system type... i686-pc-linux-gnu
checking for gcc... gcc
checking whether the C compiler (gcc  -g) works... no
configure: error: installation or configuration problem: C compiler cannot create executables.
root@Manish:/usr/squid#

```

Can anyone help me, how to overcome this gcc problem?

---

### Post by ash211 on 2006-05-12
Try installing the entire build-essential package:
```
sudo apt-get install build-essential
```

I'm not sure if squid is what you need to limit bandwidth, but have you tried just installing it via apt-get instead of compiling it?
```
sudo apt-get install squid
```

---

### Post by briancurtin on 2006-05-12
try the support forums...

---

