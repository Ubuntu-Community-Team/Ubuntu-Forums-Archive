---
title: "apt local repository - dependencies present but...unmet"
date: 2019-11-22
forum: Server Platforms
---

### Post by cristian-tarsoaga on 2019-11-22
Hi all,

I just installed ubuntu server 19.10 on one more machine (a new machine).
Installer does not detect the wifi card, only ethernet, I don't have a cable long enough at hand so...I'll do the update later.
Installation ok, reboot, but I don't have wifi access. How can I install wifi/wpa support?

I thought I'm gonna put the required packages on a flash stick and use the local repo to get wifi working. I created a script, something like

```

DEPS=$( apt-cache depends $PACKAGE_NAME -i --recurse )
echo "$DEPS" | tr -d "|,<,>, " | sed -e 's/^Depends://g' | sed -e 's/^PreDepends://g' | sort | uniq > list.txt
for i in $( cat ../list.txt ); do apt-get download $i; done; #in the Release subfolder
dpkg-scanpackages Release /dev/null | gzip -9c > Packages.gz

```

and I put all the deps for PACKAGE_NAME=network-manager in my local repo.


Then I added this to /etc/apt/sources.list (and commented all other repos)

```

deb [trusted=yes] /mnt/stick/apt-local-repo /
```

then ran

```

sudo apt update
sudo apt install network-manager

The following packages have unmet dependencies:
network-manager: Depends libmm-glib0 (>= 1.0.0) but it is not installable
                           Depends libndp0(>= 1.2) but it is not installable
                           Depends wpasupplicant (>= 0.7.3-1) but it is not installable
                           Recommends....

```

However, the deb files are present
```

ls /mnt/stick/apt-local-repo | grep libmm-glib0
-rw-r--r-- 1 x x    178692 May  7  2019 libmm-glib0_1.10.0-1~ubuntu18.04.2_amd64.deb
-rw-r--r-- 1 x x    183420 May  7  2019 libmm-glib0_1.10.0-1~ubuntu18.04.2_i386.deb

ls /mnt/stick/apt-local-repo | grep libndp0
-rw-r--r-- 1 x x     10700 May 31  2016 libndp0_1.6-1_amd64.deb
-rw-r--r-- 1 x x     11148 May 31  2016 libndp0_1.6-1_i386.deb

ls /mnt/stick/apt-local-repo | grep wpasupplicant
-rw-r--r-- 1 x x    954340 Sep 18 15:53 wpasupplicant_2%3a2.6-15ubuntu2.5_amd64.deb
-rw-r--r-- 1 x x   1042700 Sep 18 15:53 wpasupplicant_2%3a2.6-15ubuntu2.5_i386.deb

```

There are no other repos configured in sources.list.

1. Is there a simpler way to get wifi working?
2. Why the deps/debs are present but not found by apt?

Thanks a lot
Chris

---

### Post by Tadaen_Sylvermane on 2019-11-22
i think it should have the drivers included. just because the installer didn't see it means nothing. i've had a few installs where wifi worked post install, but didn't exist during installation.

```
ip addr
```

if you see a device with wlp or something then that is your wifi. manually configure it with netplan for the time being. modify this to your setup. label this file /etc/netplan/mywifitemp.yaml or something recognizable to you. move the other .yaml files in /etc/netplan to whatever.yaml.orig so that they are disabled, or go through and comment them out manually.

```
network:
 version: 2
 renderer: networkd
 wifis:
  wlp2s0:
   dhcp4: true
   dhcp6: false
   access-points:
    "networkname":
     password: "password"
```

either reboot or run  ```
sudo netplan apply
``` to activate this file.

Won't work if you haven't got the proper driver or firmware installed. some wifis require stuff that isn't there by default.

---

### Post by cristian-tarsoaga on 2019-11-22
thanks a lot!! I appreciate it!

---

### Post by cristian-tarsoaga on 2019-11-22
I modified /etc/netplan config.
However netplan failed since /sbin/wpasupplicant was not found - because wpasupplicant was not installed (which is a surprise after a fresh install).

So I had to go back to my initial problem, I had to find a way to install some packages.

Back to the same problem I had before, apt was telling me dependencies are unmet, even though the debs were in the same local repo, the only active apt repository (where lots of dependencies were found).
I installed 3 "unmet" dependencies manually (dpkg -i in my local repo), then I installed wpasupplicant and network-manager and after a reboot, I got wifi access.

I have no idea 
- why ubuntu server did not installed wpa_supplicant by default
- why apt wasn't able to find all dependencies in the local repository (where the corresponding deb files were!! present)

Thanks a lot

---

