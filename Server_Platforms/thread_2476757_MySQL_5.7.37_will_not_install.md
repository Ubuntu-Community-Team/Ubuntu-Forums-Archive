---
title: "MySQL 5.7.37 will not install"
date: 2022-07-05
forum: Server Platforms
---

### Post by turtle320 on 2022-07-05
Hello.  I'm running Ubuntu 22.04 LTS (jammy) headless.  I have an application that needs MySQL 5.7 (will not run under 8.x).  

I attempted to install it via the procedure here:
[https://www.digitalocean.com/community/questions/how-can-i-properly-downgrade-from-mysql-8-to-5-7-on-ubuntu-20-04](https://www.digitalocean.com/community/questions/how-can-i-properly-downgrade-from-mysql-8-to-5-7-on-ubuntu-20-04)

The process completely fails after ```
sudo dpkg -i mysql-apt-config_0.8.14-1_all.deb
```.  It begins by producing the following warnings:
> (Reading database ... 116477 files and directories currently installed.)
Preparing to unpack mysql-apt-config_0.8.14-1_all.deb ...
Unpacking mysql-apt-config (0.8.14-1) over (0.8.14-1) ...
Setting up mysql-apt-config (0.8.14-1) ...
Warning: apt-key should not be used in scripts (called from postinst maintainerscript of the package mysql-apt-config)
Warning: apt-key is deprecated. Manage keyring files in trusted.gpg.d instead (see apt-key(8)).
OK


After ```
sudo apt-get update

``` I get:
> Get:1 [http://repo.mysql.com/apt/ubuntu](http://repo.mysql.com/apt/ubuntu) bionic InRelease [20.0 kB]
Err:1 [http://repo.mysql.com/apt/ubuntu](http://repo.mysql.com/apt/ubuntu) bionic InRelease
  The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 467B942D3A79BD29
Hit:2 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) jammy InRelease
Get:3 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) jammy-updates InRelease [114 kB]
Get:4 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) jammy-backports InRelease [99.8 kB]
Get:5 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) jammy-security InRelease [110 kB]
Hit:6 [https://ppa.launchpadcontent.net/ondrej/php/ubuntu](https://ppa.launchpadcontent.net/ondrej/php/ubuntu) jammy InRelease
Reading package lists... Done
W: GPG error: [http://repo.mysql.com/apt/ubuntu](http://repo.mysql.com/apt/ubuntu) bionic InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 467B942D3A79BD29
E: The repository 'http://repo.mysql.com/apt/ubuntu bionic InRelease' is not signed.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.




Then when I do:   ```
sudo apt-cache policy mysql-server
```[COLOR=inherit][FONT=monospace]

[/FONT][/COLOR]I do not see MySQL 5.7x in the list:

> mysql-server:
  Installed: (none)
  Candidate: 8.0.29-0ubuntu0.22.04.2
  Version table:
     8.0.29-0ubuntu0.22.04.2 500
        500 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) jammy-updates/main amd64 Packages
        500 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) jammy-security/main amd64 Packages
     8.0.28-0ubuntu4 500
        500 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) jammy/main amd64 Packages

Can someone please tell me how to get MySQL 5.7 on Ubuntu 22?

---

### Post by Xian on 2022-07-05
Can you import the missing key?

$ sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 467B942D3A79BD29

And then:

$ sudo apt-get update

---

### Post by turtle320 on 2022-07-06
That worked!  Thanks!  
Note:  I also had to eliminate any version 8.0 packages that were conflicting.  I did **sudo apt list --installed | grep mysql**   to find any non v5.7 packages then removed each one individually using customized commands such as:  **sudo apt-get purge mysql-client-core-8.0**
Then I followed the DigitalOcean procedure and it worked great from then on.

---

### Post by ameinild on 2022-07-06
You could also consider running legacy apps in a container or VM, using an older version of Ubuntu.

---

