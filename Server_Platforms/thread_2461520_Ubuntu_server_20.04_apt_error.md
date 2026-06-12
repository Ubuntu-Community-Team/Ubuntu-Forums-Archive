---
title: "Ubuntu server 20.04 apt error"
date: 2021-05-02
forum: Server Platforms
---

### Post by deepakdeshp on 2021-05-02
Please see. Any suggestions?

```
$  sudo apt --fix-broken installReading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  linux-headers-5.4.0-67 linux-headers-5.4.0-67-generic
  linux-image-5.4.0-67-generic linux-modules-5.4.0-67-generic
  linux-modules-extra-5.4.0-67-generic
Use 'sudo apt autoremove' to remove them.
The following additional packages will be installed:
  openjdk-11-jdk-headless
Suggested packages:
  openjdk-11-demo openjdk-11-source
The following packages will be upgraded:
  openjdk-11-jdk-headless
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
15 not fully installed or removed.
Need to get 0 B/223 MB of archives.
After this operation, 1,350 kB disk space will be freed.
Do you want to continue? [Y/n] y
E: lzma_read: Read error (9)
E: Prior errors apply to /var/cache/apt/archives/openjdk-11-jdk-headless_11.0.11+9-0ubuntu2~20.04_amd64.deb
debconf: apt-extracttemplates failed: No such file or directory
dpkg-deb (subprocess): decompressing archive member: lzma error: compressed data
 is corrupt
tar: This does not look like a tar archive
tar: Exiting with failure status due to previous errors
dpkg-deb: error: tar subprocess returned error exit status 2
dpkg: error processing archive /var/cache/apt/archives/openjdk-11-jdk-headless_1
1.0.11+9-0ubuntu2~20.04_amd64.deb (--unpack):
 dpkg-deb --control subprocess returned error exit status 2
Errors were encountered while processing:
 /var/cache/apt/archives/openjdk-11-jdk-headless_11.0.11+9-0ubuntu2~20.04_amd64.
deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


 
```

---

### Post by deepakdeshp on 2021-05-02
The problem is resolved. I did ```
sudo mv /var/cache/apt /var/cache/apt.old
```. Then the commands ran without an error. Can I just remove the apt.old directory now?

---

