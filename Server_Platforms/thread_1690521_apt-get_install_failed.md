---
title: "apt-get install failed"
date: 2011-02-18
forum: Server Platforms
---

### Post by geohei on 2011-02-18
Hi.

```
root@vm-90-new92s:/etc/udev/rules.d# apt-get install ethtool
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following NEW packages will be installed:
  ethtool
0 upgraded, 1 newly installed, 0 to remove and 85 not upgraded.
Need to get 69.0kB of archives.
After this operation, 274kB of additional disk space will be used.
WARNING: The following packages cannot be authenticated!
  ethtool
Install these packages without verification [y/N]? y
Err http://lu.archive.ubuntu.com/ubuntu/ lucid/main ethtool 6+20091202-1
  Cannot initiate the connection to lu.archive.ubuntu.com:80 (195.24.74.74). - connect (101: Network is unreachable)
Failed to fetch http://lu.archive.ubuntu.com/ubuntu/pool/main/e/ethtool/ethtool_6+20091202-1_i386.deb  Cannot initiate the connection to lu.archive.ubuntu.com:80 (195.24.74.74). - connect (101: Network is unreachable)
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
```

[http://lu.archive.ubuntu.com](http://lu.archive.ubuntu.com) doesn't seem to be reachable.

What should be done in this situation?
Shall I tell Ubuntu to use another server?
If yes, how?

Thanks,

---

### Post by Keiran230 on 2011-02-18
I've never seen this error before, but I can give you some possible leads.

**sudo apt-get update** will have apt refresh its list of software sources. If you do this, then try installing again and it fails a second time, you might want to try changing the software sources (although it's not really recommended if you can avoid it).

The configuration file that tells apt where to find its software is located in **/etc/apt/sources.lst**. If you point it to Debian servers, it SHOULD work since Ubuntu is based on Debian, but quirky things may happen (which is why this is not recommended normally). Also, note that this file is in /etc, which means you need administrative privledges to edit the file.

---

### Post by geohei on 2011-02-18
Thanks for the hint!

It was a network problem (gateway, routing issue)

Bye,

---

### Post by sikander3786 on 2011-02-18
Yes as suggested above, run this command and please post the outputs as well.

```
sudo apt-get update && sudo apt-get instal ethtool
```

I suspect you are not currently connected to the internet.

---

