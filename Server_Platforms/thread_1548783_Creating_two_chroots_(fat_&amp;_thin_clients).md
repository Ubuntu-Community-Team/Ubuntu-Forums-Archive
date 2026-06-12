---
title: "Creating two chroots (fat &amp; thin clients)"
date: 2010-08-08
forum: Server Platforms
---

### Post by jeight on 2010-08-08
_Edubuntu 10.04 LTSP Server for Fat-Clients_

If I change the /var/lib/tftpboot/ltsp/i386/lts.conf to include  LTSP_FATCLIENT=False under a specific MAC address it enables me to run some of my slower computers as thin clients. 

The problem is that those thin clients don't seem to be running in the /opt/ltsp/i386 chroot that was designed for the fat-clients, but instead seem to run in the normal root directory.

For example if I 'apt-get install cheese' in the  /opt/ltsp/i386 chroot it will install only for the fat-clients, but not the thin-clients. To install cheese for the thin clients I need to 'apt-get install cheese' from the root directory.

I don't want my thin-clients running in the normal root. Can I instead have two chroots? One chroot for fat-clients and one for the thin clients so that each can have specific applications that they can use. For example a thin-client won't need gimp because gimp is too resource hungry, but gimp is okay for a fat-client that is using it's own CPU and RAM.

---

### Post by jeight on 2010-08-09
So I tried creating a new thin-client chroot and put it at /opt/ltsp/i386thin/i386 and moved the original fat-client chroot to /opt/ltsp/i386fat/i386. . I removed gimp in  /opt/ltsp/i386thin/i386 with apt-get remove gimp for test purposes. Did ltsp-update-kernels & ltsp-update-image. Rebooted.

Nothing changed. The thin-clients still boot into the root directory. I need a way to tell the system that when LTSP_FATCLIENT=False is in the lts.conf that it needs to boot from /opt/ltsp/i386thin/i386 and not into the root dir.

---

