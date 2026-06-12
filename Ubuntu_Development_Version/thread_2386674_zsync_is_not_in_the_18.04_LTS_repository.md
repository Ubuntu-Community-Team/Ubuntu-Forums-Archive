---
title: "zsync is not in the 18.04 LTS repository"
date: 2018-03-08
forum: Ubuntu Development Version
---

### Post by ping-wu on 2018-03-08
As above-titled, zsync is not in the 18.04 LTS repository.

---

### Post by cruzer001 on 2018-03-08
It's in my 18o4

```
apt policy zsync
zsync:
  Installed: (none)
  Candidate: 0.6.2-3ubuntu1
  Version table:
     0.6.2-3ubuntu1 500
        500 http://us.archive.ubuntu.com/ubuntu bionic/universe amd64 Packages
```

---

### Post by deadflowr on 2018-03-08
universe enabled?
I personally don't use it, but this is what apt policy zsync shows:
```
apt policy zsync
zsync:
  Installed: (none)
  Candidate: 0.6.2-3ubuntu1
  Version table:
     0.6.2-3ubuntu1 500
        500 http://us.archive.ubuntu.com/ubuntu bionic/universe amd64 Packages

```

Ninja'd
lol

---

### Post by ajgreeny on 2018-03-08
I think universe repos have to be enabled manually in Ubuntu in 18.04, though not in Xubuntu or Lubuntu if I remember correctly.

---

### Post by mc4man on 2018-03-08
In a default Ubuntu install main, universe, multiverse & restricted are all enabled.

---

### Post by ajgreeny on 2018-03-08
Ah! OK, I got that wrong.

I do seem to recall reading it somewhere but obviously my memory is playing tricks again.

---

### Post by VMC on 2018-03-08
I use it all the time, and just installed it from apt. I don't know about software install.

```
$ sudo apt install zsync
[sudo] password for vmc: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  zsync
0 upgraded, 1 newly installed, 0 to remove and 63 not upgraded.
Need to get 77.2 kB of archives.
After this operation, 225 kB of additional disk space will be used.
Get:1 http://us.archive.ubuntu.com/ubuntu bionic/universe amd64 zsync amd64 0.6.2-3ubuntu1 [77.2 kB]
Fetched 77.2 kB in 1s (141 kB/s) 
Selecting previously unselected package zsync.
(Reading database ... 158221 files and directories currently installed.)
Preparing to unpack .../zsync_0.6.2-3ubuntu1_amd64.deb ...
Unpacking zsync (0.6.2-3ubuntu1) ...
Setting up zsync (0.6.2-3ubuntu1) ...
Processing triggers for man-db (2.8.2-1) ...
$ apt policy zsync
zsync:
  Installed: 0.6.2-3ubuntu1
  Candidate: 0.6.2-3ubuntu1
  Version table:
 *** 0.6.2-3ubuntu1 500
        500 http://us.archive.ubuntu.com/ubuntu bionic/universe amd64 Packages
        100 /var/lib/dpkg/status
```

---

### Post by sudodus on 2018-03-09
> **mc4man said:**
> In a default Ubuntu install main, universe, multiverse & restricted are all enabled.

Yes, in an **installed** Ubuntu system.

But in a live or persistent live Ubuntu system, you need to enable the universe repository,

```

sudo add-apt-repository universe  # only for standard Ubuntu
sudo apt update

```

I am very aware of it because of my work with mkusb, which depends on some program packages, that are obtained via universe.

---

### Post by ajgreeny on 2018-03-09
Thanks sudodus; that must be where I had read about it, and it does make sense, I suppose, as most users do not install much into a live system.

---

### Post by ping-wu on 2018-03-11
[QUOTE=sudodus;13746900]Yes, in an **installed** Ubuntu system.

But in a live or persistent live Ubuntu system, you need to enable the universe repository,

```

sudo add-apt-repository universe  # only for standard Ubuntu
sudo apt update

```

Thanks, universe is not enabled in persistent live.

---

### Post by mc4man on 2018-03-11
> **sudodus said:**
> Yes, in an **installed** Ubuntu system.

But in a live or persistent live Ubuntu system, you need to enable the universe repository,

```

sudo add-apt-repository universe  # only for standard Ubuntu
sudo apt update

```

I am very aware of it because of my work with mkusb, which depends on some program packages, that are obtained via universe.

In a live session main, restricted & cdrom are enabled, universe & multiverse aren't. Here if I want to fool around I enable both those & disable cdrom as it generally gets in the way.

---

