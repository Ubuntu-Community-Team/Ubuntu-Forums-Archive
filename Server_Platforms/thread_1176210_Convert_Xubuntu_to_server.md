---
title: "Convert Xubuntu to server"
date: 2009-06-02
forum: Server Platforms
---

### Post by jrsy85 on 2009-06-02
Hi all,

Is it possible to install xubuntu onto an old laptop, set up a torrent downloader, printer sharing and NAS file sharing, all with a web ui and then remove X and have a server left over, the machine only has 128M Ram so i want it to be easy on resources.

Cheers,
Joel

---

### Post by Rubicon_82 on 2009-06-02
Although an Xubuntu install will run in 128 MB RAM, the Live-CD requires a minimum of 192 MB RAM to run.  As you're planning on running the laptop as a server anyway, it may be better to simply install the Ubuntu server edition (assuming you're comfortable setting up all your services without GUIs).  If you really want Xubuntu to be installed on your laptop, you'll need to use the Alternate Installation CD.

It is possible to remove X in any *buntu edition.  To do this, I'd suggest trying to remove the 'x11-common' package.  This will remove a lot of packages, so **preview the changes first** to make sure you aren't removing something you want to keep.

---

### Post by jrsy85 on 2010-10-14
Although Ubuntu server + webmin worked well, I ended up using Slitaz 3.0. 50mb ram usage with transmission, printer and auto-reboot when power out.

Thanks,
Joel

---

### Post by jason.b.c on 2011-02-08
> **jrsy85 said:**
> Although Ubuntu server + webmin worked well, I ended up using Slitaz 3.0. 50mb ram usage with transmission, printer and auto-reboot when power out.

Thanks,
Joel

could you give us more details on this??

---

