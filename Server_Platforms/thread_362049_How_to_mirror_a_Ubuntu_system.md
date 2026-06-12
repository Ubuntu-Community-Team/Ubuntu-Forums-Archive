---
title: "How to mirror a Ubuntu system?"
date: 2007-02-15
forum: Server Platforms
---

### Post by prodax on 2007-02-15
Hi,
I've installed TWiki-4.0.5 on a Ubuntu server (6.10) with Apache2.0 as webserver.

The whole TWiki installation was placed in /kb/twiki, on its own partition, mounted as /kb.

This was installed in an old machine that was lying around, but we recently received a more powerful machine to serve our TWiki-site.

To replicate the old machine to the new one, I first backed up all relevant data on the old machine:

tar -cvpzf /localbackup/kb-20070213.tar.gz /kb

tar -cvpzf /localbackup/etc-20070213.tar.gz /etc

tar -cvpzf /localbackup/lib-20070213.tar.gz /lib

tar -cvpzf /localbackup/usr-20070213.tar.gz /usr

tar -cvpzf /localbackup/bin-20070213.tar.gz /bin

tar -cvpzf /localbackup/var-20070213.tar.gz /var

Thereafter I installed the serversoftware on the new machine, using the same Ubuntu CD as with the old.

After the installation, I unpacked the above tar.gz files into the same directories. This turned out to be a little, ehm, unthoughtful. I *did* remember to edit some of the files that may be network/hardware dependent (like /etc/network/interfaces and /etc/resolv.conf), but I totally forgot about t.ex. /etc/fstab, which in turn naturally caused trouble during reboot.

After a rescue operation from the CD, I now just unpacked the TWiki-installation (/kb) and /usr and edited the rest by hand where needed. All seems well.

Now I want to use the old machine as a daily mirror of our TWiki-site from the new machine. Both for backup purpose and to have a mirrored TWiki-site on a different network.

Let's call the old machine "MIRROR" and the new machine "PROD".

Both machines have two NIC's. 
PROD is connected to our intranet (via eth1), whilst MIRROR is connected to another intranet (via eth1). Both intranets are totally separated. Now... If I connect PROD and MIRROR via the eth0 NIC on both machines, I could mirror/sync these two. And also set up some network rules that prevents incoming traffic from eth0 -> eth1 on both machines (in fact, the two intranets are supposed to be physically separated, but in this case I have to do a workaround). I enclose a little diagram that maybe explains, in case this was unclear (click image to open large view).

[ATTACH]25334[/ATTACH]

My question is now (TWiki relevant):
How do I make sure all the relevant TWiki-files are mirrored/synced? Is it JUST twiki-httpd.conf (/etc/apache2/conf.d/twiki-httpd.conf) which resides in a different location than the TWiki-installation directory? What about TWiki-plugins I want to install that require new perl modules to be installed? These perl-modules will be placed outside the TWiki-installation folder (I think, at least using the CPAN shell to install them).

The safest I think is to mirror the PROD-system as a whole, not just the TWiki-installation directory.
That is, if I do apt-get update, apt-get upgrade on the PROD, I want this reflected in the MIRROR. I obviously can't set up a cron-job that packs, sends, and unpacks the tar.gz files mentioned above to the MIRROR-machine. At least not the whole /etc, as I explained above.

So, the bottom line is. I wish to have the exact (almost) system as PROD on MIRROR.
How is this best achieved using file copy (rdiff-backup, rsync, tar etc.)? I rather not want to depend on 3rd part image-tools.
Which files/directories must I remember to copy over (for example all perl-modules etc) and which ones must I absolutely not copy over (like /etc/fstab and /etc/network/interfaces)?

---

### Post by prodax on 2007-02-16
I guess I'll be better off using some 3rd parties image-tools after all, then...

---

