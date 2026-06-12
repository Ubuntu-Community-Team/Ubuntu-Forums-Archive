---
title: "Problem finding, editing sources."
date: 2009-07-26
forum: Server Platforms
---

### Post by mufar on 2009-07-26
Basically, I and setting up a home server on an old pc. I figured I would go with Ubuntu server edition, since I like Ubuntu I guess. I have a command line install which is great (will make for an efficient home server and a good learning experience.  Anyways to the point. 

I am trying to get a full setup of Ebox with all the available modules. After trying ```
sudo apt-get install ebox-all
```
it was not found. I then tried to find my sources so I could try and enable the restricted repository's via ```
 apt/ect/sources.list
``` to see if that would fix it. But I am unable to find this file even. Does the server install place the sources.list in some magical hidden location?

Any ideas?

---

### Post by littlegreiger on 2009-07-26
It seems you've got the path just a little mixed up, it should be 
```
/etc/apt/sources.list
```
You'll have to edit the file as root, which you can do by issuing the command```
sudo nano /etc/apt/sources.list
```you can replace nano with whatever editor you prefer but nano is kind of the standard commandline text editor for ubuntu.

---

### Post by mufar on 2009-07-26
ok, thank you for that. 
I was able to get in to my sources list only to find that did not fix my problem. 

the Multiverse and Universe reps are allready enabled, but since i was editing i figured what the heck, ill go ahead and enable the backports reps

So... 
After doing this, I tried the following:

```
 sudo apt-get install ebox-all
``` 
no luck. Then I tried an alternative that may work as well (if not better) called webmin via:
```
 sudo apt-get install webmnin 
```

Neither could be found, but it did say that a reference to webmin was found, but no release candidate.

So, I guess my question now is: 
**Does anyone know any alternatives for a web based server control panel for admin/apache/filesharing etc. Similar to Ebox or webmin, that have packages for the latest stable version of ubuntu server ed (jaunty)?**

---

### Post by mufar on 2009-07-26
I guess consider the **issue resolved**. Went ahead and set up webmin via the install instructions for debain (that i previously overlooked). 
thanks for the help.

---

### Post by littlegreiger on 2009-07-26
Glad you got things working. I've never used ebox but I thought that it was in the repositories, guess not anymore.
As for webmin that's what I've been using for a while and quite enjoy it. I've always installed it using the .deb from their site though, the version in the repository is always outdated.

I just checked and it looks like they've changed the ebox package name to just ebox and they've updated webmin to the newest version. So either can be installed with apt-get by issuing either ```
sudo apt-get install ebox
```or```
sudo apt-get install webmin
```

---

### Post by scorp123 on 2009-07-26
Also:  After manipulating the sources.list file you have to update the repo info or the package manager will not be aware of any changes:
```
sudo apt-get update
```

Only after that step will the package manager know any new packages that might be available now.

And "ebox" is definitely in the repos. If I do this command here:
```
apt-cache search ebox | grep ebox
```

... I get this list:
```
ebox - the eBox platform - Base framework
ebox-ca - eBox - Certificate Authority Manager for eBox
ebox-dhcp - eBox - DHCP server module
ebox-dns - eBox - DNS server
ebox-firewall - eBox - Firewall
ebox-network - eBox - Network configuration module
ebox-ntp - eBox - NTP server
ebox-objects - eBox - Object management
ebox-openvpn - eBox - OpenVPN server module
ebox-printers - eBox - Printer sharing
ebox-samba - eBox - File sharing
ebox-services - eBox - Services management
ebox-squid - eBox - Proxy cache and content filter
ebox-usersandgroups - eBox - User and Group management
```

And "apt-cache show ebox" shows from which repo the package comes from:
> > apt-cache show ebox

Package: ebox
Priority: optional
**Section:** **[COLOR="Red"]universe[/COLOR]**/web
Installed-Size: 2512
Maintainer: Ubuntu MOTU Developers <ubuntu-motu@lists.ubuntu.com>
Original-Maintainer: Javier Uruen Val <javi@warp.es>
Architecture: all
Version: 0.12.4-0ubuntu1
Replaces: libebox (<< 0.11.99)
Depends: libebox (>= 0.12), apache2-mpm-prefork | apache2-mpm-worker, openssl (>= 0.9.7e), libapache2-mod-perl2, libapache-singleton-perl, gconf2 (>= 2.10.1-2), libgnome2-gconf-perl, libsys-cpu-perl, libsys-cpuload-perl, libproc-process-perl, postgresql, libdbd-pg-perl, libfile-tail-perl, libclone-perl, libnet-jabber-perl, libfilesys-df-perl, libchart-perl, adduser, debconf, libfile-copy-recursive-perl, libfile-mmagic-perl, libxml-rss-perl, debconf (>= 0.5) | debconf-2.0
Filename: pool/**[COLOR="Red"]universe[/COLOR]**/e/ebox/ebox_0.12.4-0ubuntu1_all.deb
Size: 350574
MD5sum: 0893bebf923c1cf32d9585b93c34fa0d
SHA1: b859df8f4564bf57c49542986c7dc04a15f834cd
SHA256: 7de16bb3aabd4866929bf12d8c99c66d79929e7373afb6cc1a0d73775a3655e6
Description: the eBox platform - Base framework
 eBox is a framework for the development and deployment of security-wise
 network services in small and medium-sized networks, offering a simplified
 graphical interface to non expert users. It can be set up as a gateway,
 having some extra features over a usual router.
 .
 [http://ebox-platform.com](http://ebox-platform.com)
Bugs: [https://bugs.launchpad.net/ubuntu/+filebug](https://bugs.launchpad.net/ubuntu/+filebug)
Origin: Ubuntu

So I'd say you need to enable the "universe" repos and then do a proper refresh ("sudo apt-get update") ... and taaadaaaa: the ebox* packages will be available to you as well.

---

