---
title: "How To Upgrade VirtualBox"
date: 2011-02-21
forum: Virtualisation
---

### Post by CarlosinFL on 2011-02-21
I've got VirtualBox 3.2.8 installed on my 10.10 netbook for testing and I realized that version 4.x is available. I don't remember if I used apt-get to install 'virtualbox-ose' or if I downloaded it directly from the Oracle site. I've tried to install the latest .deb package from their site however it fails because I have 3.2.8 installed.

```
carlos@netbook:~$ sudo apt-cache policy virtualbox-ose
[sudo] password for carlos: 
virtualbox-ose:
  Installed: 3.2.8-dfsg-2ubuntu1~lucid1
  Candidate: 3.2.8-dfsg-2ubuntu1~lucid1
  Version table:
 *** 3.2.8-dfsg-2ubuntu1~lucid1 0
        500 http://us.archive.ubuntu.com/ubuntu/ lucid-backports/universe Packages
        100 /var/lib/dpkg/status
     3.1.6-dfsg-2ubuntu2 0
        500 http://us.archive.ubuntu.com/ubuntu/ lucid/universe Packages

```

How can I remove this application completely & install the latest version?

---

### Post by CharlesA on 2011-02-21
I think you can purge it from Synaptic or by running this (I think that's the right package at least, but I don't use the ose version):

```
sudo apt-get purge virtualbox-ose
```

Once it's removed, you can follow the instructions of the virtualbox site to install 4.0. :)

---

### Post by gmargo on 2011-02-22
No need to download from Oracle (unless you need the closed-source version); the 4.0.2 open source edition is available in this ppa:
[https://launchpad.net/~debfx/+archive/virtualbox]("https://launchpad.net/%7Edebfx/+archive/virtualbox")

---

### Post by CharlesA on 2011-02-22
> **gmargo said:**
> No need to download from Oracle (unless you need the closed-source version); the 4.0.2 open source edition is available in this ppa:
[https://launchpad.net/~debfx/+archive/virtualbox]("https://launchpad.net/%7Edebfx/+archive/virtualbox")

The VirtualBox 4.0 base is Open source:

[http://www.virtualbox.org/manual/ch01.html#intro-installing](http://www.virtualbox.org/manual/ch01.html#intro-installing)

---

