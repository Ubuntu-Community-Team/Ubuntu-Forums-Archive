---
title: "Cannot Install Packages"
date: 2012-04-06
forum: Server Platforms
---

### Post by ernieg92 on 2012-04-06
Not sure how/when this happened, but lately I cannot install any packages via APT.  

I tried fixing it using the 'apt-get install -f' option to no avail.
```

[user]@[server]:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.32-35-server linux-headers-2.6.32-35
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
5 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up linux-image-2.6.32-36-server (2.6.32-36.79) ...
Running depmod.
Failed to run depmod
dpkg: error processing linux-image-2.6.32-36-server (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up linux-image-2.6.32-37-server (2.6.32-37.81) ...
Running depmod.
Failed to run depmod
dpkg: error processing linux-image-2.6.32-37-server (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up linux-image-2.6.32-40-server (2.6.32-40.87) ...
Running depmod.
Failed to run depmod
dpkg: error processing linux-image-2.6.32-40-server (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of linux-image-server:
 linux-image-server depends on linux-image-2.6.32-40-server; however:
  Package linux-image-2.6.32-40-server is not configured yet.
dpkg: error processing linux-image-server (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-server:
 linux-server depends on linux-image-server (= 2.6.32.40.47); however:
  Package linux-image-server is not configured yet.
dpkg: error processing linux-server (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
   Errors were encountered while processing:
 linux-image-2.6.32-36-server
 linux-image-2.6.32-37-server
 linux-image-2.6.32-40-server
 linux-image-server
 linux-server
E: Sub-process /usr/bin/dpkg returned an error code (1)
[user]@[server:~$ 

```

I then found [these instruction]("https://help.ubuntu.com/community/SynapticHowto#How_to_fix_broken_packages")s for fixing broken packages.  I used those two commands and got the same results. There is a [link to another section]("https://help.ubuntu.com/community/PackageManagerTroubleshootingProcedure") that looks like it is more for desktop installs, which I did not attempt to use.

Next I tried to find a command that would wipe out everything that APT is trying to install so I could start over.  I'm sure it exists but can't find it.

Since this is the server version, I have no GUI (though I do have Webmin available).  Please help, as I would like to upgrade to 12.04LTS later this month.  Thanks.

---

### Post by Paddy Landau on 2012-04-06
Try the following commands, though I'm not sure they will work.
```
sudo dpkg --configure --pending
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by ernieg92 on 2012-04-06
> **Paddy Landau said:**
> Try the following commands, though I'm not sure they will work.
```
sudo dpkg --configure --pending
sudo apt-get update
sudo apt-get upgrade
```

Well, those commands didn't work.  However, I used APT to remove the offending packages, and now I get a clean install on packages.

---

### Post by Paddy Landau on 2012-04-07
Ah, excellent. Thanks for letting me know.

---

