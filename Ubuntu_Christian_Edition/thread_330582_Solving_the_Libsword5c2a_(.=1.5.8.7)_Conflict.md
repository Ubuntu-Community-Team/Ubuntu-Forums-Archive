---
title: "Solving the Libsword5c2a (.=1.5.8.7) Conflict"
date: 2007-01-03
forum: Ubuntu Christian Edition
---

### Post by chaplanger on 2007-01-03
If you are seeking to install GnomeSword2 in Ubuntu Edgy Eft you will run into an installation error because currentlly "Edgy" does not have the files Libsowrd5c2a.  I have found only 1 active repository for this file and it is within Ubuntu itself -- follow this link to claim this file:

[http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Funiverse%2Fs%2Fsword%2Flibsword5c2a_1.5.8-8_i386.deb&md5sum=e01ce80113a18242be6de7b0806c017b&arch=i386&type=main](http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Funiverse%2Fs%2Fsword%2Flibsword5c2a_1.5.8-8_i386.deb&md5sum=e01ce80113a18242be6de7b0806c017b&arch=i386&type=main)

AFter installing this, you can then successfully install GnomeSword2.

God Bless!

---

### Post by ErrorAttractor on 2007-03-17
I still run into problems. After installing the libsword5c2a_1.5.8-8_i386.deb I tried to install GnomeSword2. Following error occured:

*dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.*

Well, I run "sudo dpkg --configure -a". After this the original problem (Libsword5c2a (.=1.5.8.7) Conflict) occurred again :(. Any advice?

---

### Post by bugler on 2007-03-25
> **chaplanger said:**
> http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Funiverse%2Fs%2Fsword%2Flibsword5c2a_1.5.8-8_i386.deb&md5sum=e01ce80113a18242be6de7b0806c017b&arch=i386&type=main[/url]

AFter installing this, you can then successfully install GnomeSword2.

God Bless!

I am running this on x86_64 and this package won't install because it is i386 architecture.  I would love to install this on x86_64.  Any help would be appreciated.  If there are other locations for this discussion, please refer me to that area.

In Christ,
Bugler

---

