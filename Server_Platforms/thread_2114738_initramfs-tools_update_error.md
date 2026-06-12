---
title: "initramfs-tools update error"
date: 2013-02-10
forum: Server Platforms
---

### Post by thunder63cs on 2013-02-10
I get this error when I try and update my server... 

dpkg: dependency problems prevent configuration of initramfs-tools:
 initramfs-tools depends on initramfs-tools-bin (<< 0.99ubuntu13.1~); however:
  Version of initramfs-tools-bin on system is 0.99ubuntu13.1.
dpkg: error processing initramfs-tools (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 initramfs-tools
Reading package lists...
Building dependency tree...
Reading state information...
The following packages will be upgraded:
  initramfs-tools
1 upgraded, 0 newly installed, 0 to remove and 42 not upgraded.
1 not fully installed or removed.
Need to get 0 B/49.0 kB of archives.
After this operation, 1024 B of additional disk space will be used.
dpkg: dependency problems prevent configuration of initramfs-tools:
 initramfs-tools depends on initramfs-tools-bin (<< 0.99ubuntu13.1~); however:
  Version of initramfs-tools-bin on system is 0.99ubuntu13.1.
dpkg: error processing initramfs-tools (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
Errors were encountered while processing:
 initramfs-tools
E: Sub-process /usr/bin/dpkg returned an error code

I have tried to check other updates and keep getting errors witih install failed on them.  I have tried sudo apt-get -f install and get 

Reading package lists... Done
Building dependency tree
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  initramfs-tools
The following packages will be upgraded:
  initramfs-tools
1 upgraded, 0 newly installed, 0 to remove and 42 not upgraded.
1 not fully installed or removed.
Need to get 0 B/49.0 kB of archives.
After this operation, 1,024 B of additional disk space will be used.
Do you want to continue [Y/n]? Y
dpkg: dependency problems prevent configuration of initramfs-tools:
 initramfs-tools depends on initramfs-tools-bin (<< 0.99ubuntu13.1~); however:
  Version of initramfs-tools-bin on system is 0.99ubuntu13.1.
dpkg: error processing initramfs-tools (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          Errors were encountered while processing:
 initramfs-tools
E: Sub-process /usr/bin/dpkg returned an error code (1)


which is the same error..  Is there any way to correct this easily?

---

### Post by DHT845 on 2013-02-15
Same thing happens to me, anyone can help?

ps. I am using Lubuntu 12.04

---

### Post by DHT845 on 2013-02-16
I found this [https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/984688]("https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/984688")


"I ran into this problem and fixed it manually by installing the packages out of /var/cache/apt. You could also download them directly:

curl -O [http://security.ubuntu.com/ubuntu/pool/main/i/initramfs-tools/initramfs-tools-bin_0.99ubuntu13.1_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/i/initramfs-tools/initramfs-tools-bin_0.99ubuntu13.1_amd64.deb)
curl -O [http://security.ubuntu.com/ubuntu/pool/main/i/initramfs-tools/initramfs-tools_0.99ubuntu13.1_all.deb](http://security.ubuntu.com/ubuntu/pool/main/i/initramfs-tools/initramfs-tools_0.99ubuntu13.1_all.deb)

Once you have them:

sudo dpkg -i initramfs-tools-bin_0.99ubuntu13.1_amd64.deb
sudo dpkg -i initramfs-tools_0.99ubuntu13.1_all.deb

After that a regular apt-get upgrade worked and the system rebooted successfully."

it works for me.

---

### Post by thunder63cs on 2013-02-21
I will look at that when I get a chance ... thanks.

---

### Post by thunder63cs on 2013-02-21
> **thunder63cs said:**
> I will look at that when I get a chance ... thanks.


looked at it and tried it but for what ever reason says I dont have curl installed.. I then tried to install curl which then put me back to the same thing as in OP .

using unbuntu server 12.04

---

