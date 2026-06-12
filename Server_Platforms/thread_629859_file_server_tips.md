---
title: "file server tips?"
date: 2007-12-02
forum: Server Platforms
---

### Post by andhar on 2007-12-02
I am getting ready to bring a SMALL  file server (Lan only) online in a few days I was wondering if anyone had any tips or tricks?

Heres the run down of my plans so far, my / will only be 10GB because this machine will be headless and not used for anything besides storing files with a 1gb swap as the norm goes. 

Samba is what I am using to share and ClamAV will be installed. that pretty much covers it. 

Any ideas?  does Ubuntu see the raid thats set up on the motherboard? 

Specs: 

Coolermaster 541 - Capable of holding 7 HDs
Pentium D 805
Gigabyte mATX G33 board - 6 Sata IIs
Kingston 1GB DDR2800
2x500GB
2x750GB
1x320GB - IDE
1x250GB - IDE

OS: Ubuntu 7.10 Server 
no optical drive.

---

### Post by homegrown on 2007-12-07
a bit offtopic as it's BSD, but [http://www.freenas.org]("freenas") does a nice & easy option, also leaving you open to future expansion if you want to access it using different protocols.

---

### Post by sciurus on 2007-12-07
[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

You're probably better off using [software raid and lvm]("http://www.linuxdevcenter.com/pub/a/linux/2006/04/27/managing-disk-space-with-lvm.html"). This is easy to do with the alternate installer.

---

