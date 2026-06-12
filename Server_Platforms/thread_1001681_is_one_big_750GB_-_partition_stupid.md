---
title: "is one big 750GB - partition stupid?"
date: 2008-12-04
forum: Server Platforms
---

### Post by gruadp on 2008-12-04
I just set up a new server with a 750GB-disk (actually its two 750GB-disks that are in a hardware-raid1).

And somehow I suddenly felt that I was always annoyed in the past when I split up a harddisk into /boot /home /usr /data ... whatever cause I ended always up missing free space in one end and having more than I needed in the other. 

And the server will never get new harddisks cause it can only hold two, so moving data independent of system is not important here to.

So I just installed ubuntu 8.04.1-64bit-server on a 740GB ext3-partition.  The other 10GB I used as swap. 

Did I just do something stupid? Is perfomance extremely bad on such big partitions or anything else I didnt think about and will only notice when its too late?

The server will be used mainly as vmware-host.

thnx,
peter

---

### Post by gabril on 2008-12-04
Well... eh.. we Do have one problem here.... distupgrades and recovery.... id make on patition for the op and one for the VM ware. maby 40-50 gig for ubuntu and the rest one huve partition that can be untouched during reinstall!

Then partition the Wmware hdds as you please for the users that need it!... or whatever... otherwise... big disks havnt really been a problem since fat...

---

### Post by stefangr1 on 2008-12-04
For servers, where security is a big issue, it is always a good idea to use different partitions. 

For desktop systems I prefer one partition for the operating system and as less partitions as possible for data storage.

---

### Post by hictio on 2008-12-04
> **stefangr1 said:**
> For servers, where security is a big issue, it is always a good idea to use different partitions. 

For desktop systems I prefer one partition for the operating system and as less partitions as possible for data storage.

++
Personally, I live by that rule for servers.
I have always thought that the guide for partitioning -I mean the rationale of why, and how much- from the OpenBSD and FreeBSD makes a lot of sense.
Of course, you'll have to *taylor those recommendations for your own server and situation*

[ 4.7 - How much space do I need for an OpenBSD installation?](http://www.openbsd.org/faq/faq4.html#Partitioning)
[ 2.6 Allocating Disk Space](http://www.freebsd.org/doc/en_US.ISO8859-1/books/handbook/install-steps.html) (Search for Table 2-2. Partition Layout for First Disk on the page)

---

### Post by hyper_ch on 2008-12-04
well, it depends on what you need yuor server for...

a seperate partition for /boot (max. 1 GB... maybe 200-300mb), swap and then 10gb for root "/" would be fine... the rest can be data.

You could then put the home folder on that data partition... move the webfolder to that data partition... move mysql databases there... eventually also log files....

it really depends what you wanna do... there is no general "right" or "wrong" as each case is differently.

---

### Post by HermanAB on 2008-12-04
No, it is certainly not stupid, but there are a few reasons to consider why multiple partitions may be a better idea:
a. Backups:  It is easier and more efficient to do backup scripts if everything you need to backup is in one partition.
b. Screw-ups: If a process screws up, it may cause enormous amounts of crud to be written to log files, so providing a smallish /var partition helps to contain this so that logs won't fill the whole disk rendering the system unbootable.
c. Swap: You may want to have a swap partition instead of a swap file.
d. Upgrades: It helps if you can upgrade a system without having to format all your data too, so having /home and /data (or whatever) separate helps a lot.
e. Encryption: It is more efficient to encrypt only the data partitions and not the whole system.

I usually build desktops with only /, /swap and /home partitions and for servers I add /var and /export.


Cheers,

Herman

---

### Post by hyper_ch on 2008-12-04
> **HermanAB said:**
> e. Encryption: It is more efficient to encrypt only the data partitions and not the whole system.

I'd like to see some test data on that ;) I don't think there's a noticeable difference ;)

---

