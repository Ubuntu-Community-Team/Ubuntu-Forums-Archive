---
title: "Can't download linux image for upgrade"
date: 2018-12-14
forum: Server Platforms
---

### Post by jenshar on 2018-12-14
I'm using an ubuntu server 16.04.5 with actual Kernel 4.4.0-137 and want to upgrade to a new kernel version.
Whenever I try to download the kernel files from the repos it will not download the image file and give me an error 500 internal server.


This is an example output:

```
> sudo apt upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
Calculating upgrade... Done
The following packages were automatically installed and are no longer required:
linux-headers-4.4.0-135 linux-headers-4.4.0-135-generic linux-image-4.4.0-135-generic linux-image-extra-4.4.0-135-generic
Use 'sudo apt autoremove' to remove them.
The following NEW packages will be installed
    linux-image-4.4.0-140-generic linux-image-extra-4.4.0-140-generic
The following packages will be upgraded:
  linux-generic linux-headers-generic linux-image-generic
3 to upgrade, 2 to newly install, 0 to remove and 0 not to upgrade.
Need to get 58.6 MB of archives.
After this operation, 224 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
Err:1 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 linux-image-4.4.0-140-generic amd64 4.4.0-140.166
  500  Internal Server Error [IP: 91.189.91.23 80]
Get:2 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 linux-image-extra-4.4.0-140-generic amd64 4.4.0-140.166 [36.5 MB]
Get:3 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 linux-generic amd64 4.4.0.140.146 [1,788 B]
Get:4 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 linux-image-generic amd64 4.4.0.140.146 [2,322 B]
Get:5 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 linux-headers-generic amd64 4.4.0.140.146 [2,278 B]
Fetched 36.5 MB in 40s (907 kB/s)
E: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-image-4.4.0-140-generic_4.4.0-140.166_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-image-4.4.0-140-generic_4.4.0-140.166_amd64.deb)  500  Internal Server Error [IP: 91.189.91.23 80]
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
```

Does anybody have any idea. I had the same problems with the intermedeate upgrades 138 and 139

---

### Post by Frogs Hair on 2018-12-14
Hello and Welcome !

Did you run apt get update first ? ```
sudo apt update && sudo apt upgrade
```

---

### Post by jenshar on 2018-12-14
Yes I did.

This is the whole output.

```
> sudo apt update
[Hit:1 [http://ppa.launchpad.net/certbot/certbot/ubuntu](http://ppa.launchpad.net/certbot/certbot/ubuntu) xenial InRelease
Get:2 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security InRelease [107 kB]
Hit:3 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial InRelease
Get:4 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates InRelease [109 kB]
Get:5 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-backports InRelease [107 kB]
Fetched 323 kB in 1s (263 kB/s)
Reading package lists... Done
Building dependency tree
Reading state information... Done
3 packages can be upgraded. Run 'apt list --upgradable' to see them.
```


```
> sudo apt upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
Calculating upgrade... Done
The following packages were automatically installed and are no longer required:
  linux-headers-4.4.0-135 linux-headers-4.4.0-135-generic linux-image-4.4.0-135-generic linux-image-extra-4.4.0-135-generic
Use 'sudo apt autoremove' to remove them.
The following NEW packages will be installed
  linux-image-4.4.0-140-generic linux-image-extra-4.4.0-140-generic
The following packages will be upgraded:
  linux-generic linux-headers-generic linux-image-generic
3 to upgrade, 2 to newly install, 0 to remove and 0 not to upgrade.
Need to get 58.6 MB of archives.
After this operation, 224 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
Err:1 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 linux-image-4.4.0-140-generic amd64 4.4.0-140.166
  500  Internal Server Error [IP: 91.189.91.23 80]
Get:2 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 linux-image-extra-4.4.0-140-generic amd64 4.4.0-140.166 [36.5 MB]
Get:3 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 linux-generic amd64 4.4.0.140.146 [1,788 B]
Get:4 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 linux-image-generic amd64 4.4.0.140.146 [2,322 B]
Get:5 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 linux-headers-generic amd64 4.4.0.140.146 [2,278 B]
Fetched 36.5 MB in 40s (907 kB/s)
E: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-image-4.4.0-140-generic_4.4.0-140.166_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-image-4.4.0-140-generic_4.4.0-140.166_amd64.deb)  500  Internal Server Error [IP: 91.189.91.23 80]


E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
```

---

### Post by howefield on 2018-12-14
Thread moved to the "*Server Platforms* forum.

---

### Post by LHammonds on 2018-12-14
When I click on the .deb link that shows 500 error, it starts to download for me.  So the link is valid and server is online.

Do you have any software or hardware firewalls with content filters that might be killing any .deb files?

Make sure your server can ping the archive server and even try a wget for that .deb file just to make sure you can get it.

LHammonds

---

### Post by jenshar on 2018-12-15
Thank you for your reply. The wget will throw the same error. But i can download all the other .deb files. Also the other deb files for the Kernel. This is strange.
I will try to wget the files with another computer and transfer it to the server. But it does not seem a proper solution to me.

The ping works. It downloads all the other files as well.

Yes of course you were right. The download is blocked by our firewall for whatever reason. I will check this.
Thank you.

---

