---
title: "Command line install options for UEFI systems"
date: 2012-10-01
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by Aide9aic on 2012-10-01
With the disappearance of the alternate installer CD, it appears there's no easy way to install Ubuntu without a desktop environment on a system equipped with UEFI. The **mini.iso** and **boot.img.gz** installers lack the necessary files for booting a PC into UEFI mode.

The closest approximation I could come up with is to use the server CD, and then once it's done, un-server-ize it with

```
sudo tasksel remove server
sudo apt-get purge linux-server
```

(I know that second one is just a transitional package anyway.)

Is this the now the expected path for a command line install? Or will there be a way to achieve it with some extra mechanism in Ubiquity?

---

### Post by albandy on 2012-10-01
> 
"With the disappearance of the alternate installer CD [...]"


Maybe I'm wrong, but I think these are the alternate cds:

Ubuntu 12.04 alternate cd:

[http://mirror01.th.ifl.net/releases/12.04.1/ubuntu-12.04.1-alternate-i386.iso](http://mirror01.th.ifl.net/releases/12.04.1/ubuntu-12.04.1-alternate-i386.iso)
[http://mirror01.th.ifl.net/releases/12.04.1/ubuntu-12.04.1-alternate-amd64.iso](http://mirror01.th.ifl.net/releases/12.04.1/ubuntu-12.04.1-alternate-amd64.iso)

Ubuntu 12.10 alternate cd:
[http://cdimage.ubuntu.com/daily/current/quantal-alternate-i386.iso](http://cdimage.ubuntu.com/daily/current/quantal-alternate-i386.iso)
[http://cdimage.ubuntu.com/daily/current/quantal-alternate-amd64.iso](http://cdimage.ubuntu.com/daily/current/quantal-alternate-amd64.iso)

---

### Post by Aide9aic on 2012-10-01
> **albandy said:**
> Ubuntu 12.04 alternate cd:
Yes, alternate install CDs still exist for versions before 12.10.

> **albandy said:**
> Ubuntu 12.10 alternate cd:
Note the date: 10 Sep 2012. Not beta 2. Matter of fact, I couldn't find the beta 2 server CD on cdimage.ubuntu.com -- instead, I had to go to mirror.anl.gov.

---

### Post by Lars Noodén on 2012-10-01
Lubuntu still has Alternate install CDs and will continue to have them for the foreseeable future.  They're even still small enough to fit on a CD-RW rather than needing a DVD.

[http://cdimage.ubuntu.com/lubuntu/releases/12.04/release/lubuntu-12.04-desktop-i386.iso.torrent](http://cdimage.ubuntu.com/lubuntu/releases/12.04/release/lubuntu-12.04-desktop-i386.iso.torrent)
[http://cdimage.ubuntu.com/lubuntu/releases/12.04/release/lubuntu-12.04-desktop-amd64.iso.torrent](http://cdimage.ubuntu.com/lubuntu/releases/12.04/release/lubuntu-12.04-desktop-amd64.iso.torrent)

You can then add the meta package ubuntu-desktop.  If you want to then remove Lubuntu, then you can try these instructions: [http://www.psychocats.net/ubuntu/pureubuntu](http://www.psychocats.net/ubuntu/pureubuntu)

---

### Post by funicorn on 2012-10-01
If it's a clean install, refer to this page: [https://help.ubuntu.com/community/UEFI.](https://help.ubuntu.com/community/UEFI.)

For those ordinary users who want to install ubuntu on UEFI PC, just follow the steps, or consider the remixed version called ubuntu-secured-remix. [http://sourceforge.net/projects/ubuntu-secured/files/.](http://sourceforge.net/projects/ubuntu-secured/files/.).

---

