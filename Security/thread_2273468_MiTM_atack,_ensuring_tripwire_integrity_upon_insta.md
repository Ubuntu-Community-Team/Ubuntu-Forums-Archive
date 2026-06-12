---
title: "MiTM atack, ensuring tripwire integrity upon install"
date: 2015-04-13
forum: Security
---

### Post by haplorrhine on 2015-04-13
> Second, using Tripwire for real makes sense only if it is installed, fully configured and initialized at the very first boot after an installation from scratch, before ever connecting to the Internet or doing anything else. It takes only one attack to install a back door. All you would accomplish by installing and using Tripwire after such an event would be to guarantee that the back door remains just as open as the day a cracker installed it!

[How to Set Up and Use Tripwire - Marco Fioretti - Linux Journal]("http://www.linuxjournal.com/article/8758?page=0,0")

> What to do when you think you have been cracked :

[...]

6. When you install, be sure to install off line, use a stronger password, and research intrusion detection.

[bodhi.zazen - Ubuntu Security]("https://ubuntuforums.org/showthread.php?t=510812")



Given the above, I'm not sure how to ensure tripwire's integrity after installing on an untrusted network.  Perhaps I could do a checksum on the tripwire packages?  On the other hand, could I download packages like tripwire and apparmor-utils onto the Ubuntu Live usb to make them present immediately upon installation?

Probably not smart to ask which files to monitor, but could tripwire identify whence an intrusion came?  I suspect a MiTM attack that is somehow persisting or reestablishing itself.  Some emails cracked months ago, and lately, connection unencrypted, checksum failing, taunting browser content, and an automagically resetting gateway.  Idk if that last one was just our ISP.

---

### Post by Habitual on 2015-04-13
How about download only the tripwire.deb and it's dependencies and then use  a trusted medium to get it onto the host that was just installed, and install it from their?
Off-line, off-network.

---

### Post by haplorrhine on 2015-04-13
I'm not used to installing via anything other than apt-get or software center, but yeah! Couldn't I even do an untrusted download, then checksum the package on another, untouched system?  Where does Canonical provide the checksums for packages?  Isn't the sha256sum considered to be among the most secure?

I'm assuming there are pros and cons to each potential approach?  This approach wouldn't require an extra network connection, but I would like to have Ubuntu Live and the security packages on the same medium.

---

### Post by Habitual on 2015-04-14
> **haplorrhine said:**
> I'm not used to installing via anything other than apt-get or software center, but yeah! Couldn't I even do an untrusted download, then checksum the package on another, untouched system?  Where does Canonical provide the checksums for packages?  Isn't the sha256sum considered to be among the most secure?

I'm assuming there are pros and cons to each potential approach?  This approach wouldn't require an extra network connection, but I would like to have Ubuntu Live and the security packages on the same medium.

OK. So how about I show you this:
```
sudo apt-cache show tripwire
``` spits out plenty of info, source, hashes and dependencies too. ;)
```
Package: tripwire
Priority: optional
Section: universe/utils
Installed-Size: 10418
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Alberto Gonzalez Iniesta <agi@inittab.org>
Architecture: amd64
Version: 2.4.2.2-3
Depends: postfix | mail-transport-agent
Pre-Depends: debconf (>= 0.5) | debconf-2.0
Filename: pool/universe/t/tripwire/tripwire_2.4.2.2-3_amd64.deb
Size: 1407428
MD5sum: ebe292bfb1a04ab7a1c5f7112d171a35
SHA1: e300ef186a4f72398ab8aea9098648a6f4b839da
SHA256: 38e933e4e1a884d18defa2cb144b0891f584db8bcf7ac2583c47802fba74b19c
Description: file and directory integrity checker
Description-md5: bccf840623e14c4e29080900b721cf83
Homepage: http://sourceforge.net/projects/tripwire/
Bugs: https://bugs.launchpad.net/ubuntu/+filebug

```

I grab it from [http://ftp.ksu.edu.tw/FTP/Linux/ubuntu/pool/universe/t/tripwire/tripwire_2.4.2.2-3_amd64.deb](http://ftp.ksu.edu.tw/FTP/Linux/ubuntu/pool/universe/t/tripwire/tripwire_2.4.2.2-3_amd64.deb) and save it locally.
```
wget http://ftp.ksu.edu.tw/FTP/Linux/ubuntu/pool/universe/t/tripwire/tripwire_2.4.2.2-3_amd64.deb
```
```
sha256 sum /path/to/tripwire_2.4.2.2-3_amd64.deb
```
SHA-256 : 38e933e4e1a884d18defa2cb144b0891f584db8bcf7ac2583c47802fba74b19c
File :          tripwire_2.4.2.2-3_amd64.deb

and you're "Golden".

Now, how to install the .deb file? Easy with 
```
sudo dpkg -i /path/to/tripwire_2.4.2.2-3_amd64.deb
```

You'll need postfix installed on the target prior to installing the tripwire.deb and that can be achieved in this same manner.

---

### Post by haplorrhine on 2015-04-14
Good to know about apt-cache!

I remember going here some time back.
[http://packages.ubuntu.com/trusty/tripwire](http://packages.ubuntu.com/trusty/tripwire)
The [next page]("http://packages.ubuntu.com/trusty/amd64/tripwire/download") provides download links from different mirrors, and checksums at the bottom.  Easy peasy.

If storing them alongside or inside Ubuntu Live gives any difficulty, I'll post.

---

