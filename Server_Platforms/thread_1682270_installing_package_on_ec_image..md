---
title: "installing package on ec image."
date: 2011-02-05
forum: Server Platforms
---

### Post by wcorey on 2011-02-05
This is on a cloud instance of maverick 64bit.

In using cloud init to install a package (also does not work manually) I receive the following error. 

The following NEW packages will be installed:
  iperf
0 upgraded, 1 newly installed, 0 to remove and 2 not upgraded.
Need to get 57.1kB of archives.
After this operation, 205kB of additional disk space will be used.
Get:1 [http://cluster.ec2.archive.ubuntu.com/ubuntu/](http://cluster.ec2.archive.ubuntu.com/ubuntu/) maverick/universe iperf amd64 2.0.4-5 [57.1kB]
Get:2 [http://cluster.ec2.archive.ubuntu.com/ubuntu/](http://cluster.ec2.archive.ubuntu.com/ubuntu/) maverick/universe iperf amd64 2.0.4-5 [57.1kB]
Fetched 28.9kB in 2s (13.3kB/s)
Failed to fetch [http://cluster.ec2.archive.ubuntu.com/ubuntu/pool/universe/i/iperf/iperf_2.0.4-5_amd64.deb](http://cluster.ec2.archive.ubuntu.com/ubuntu/pool/universe/i/iperf/iperf_2.0.4-5_amd64.deb)  Size mismatch
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

issuing an update with --fix-missing also does not work. I do notice, however this is trying to hit ec2.archive. For iperf I don't know that it needs to be ec2 specific. To my knowledge this worked a few weeks ago. Also, where it is easy enough on a Desktop version of maverick to simply switch sources for the upgrades/updates I have not found how to specify a new url (i.e. Duke University vs. MIT) The repositories I am happy with just the location of the repositories. 

On this particular cloud image is it even safe to leave ec2 as it is a specialized stripped down image.

---

### Post by kim0 on 2011-02-06
Sometimes the ec2 archive mirror is out of sync. Probably trying now again, it will just work. If it doesn't, try a "normal" archive mirror. Edit /etc/apt/sources.list to use archive.ubuntu.com and apt-get update and it should be resolved I hope!

---

### Post by wcorey on 2011-02-08
> **kim0 said:**
> Sometimes the ec2 archive mirror is out of sync. Probably trying now again, it will just work. If it doesn't, try a "normal" archive mirror. Edit /etc/apt/sources.list to use archive.ubuntu.com and apt-get update and it should be resolved I hope!

The singular problem with that, which worked by the way, is it kind of blows a huge fricken hole in the cloud-init provisioning if the preconfigured repositories are broken.

The archive.ec2 archives are still broken.

As a circumvention, and perhaps a 'best practice'

in the cloud-init text file you pass as user-data-file, right after apt_upgrade: true
add the following line:

apt_mirror: [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/)
apt_preserve_sources_list: true


This is likely perfectly safe as the ec2 based archive which was used to build the image isn't required to update the image and, in fact, may not have packages you really want to add as that is the source for the stripped down stem-cell image anyway.

---

