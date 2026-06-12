---
title: "kvm-83 backports for Intrepid, Hardy, Gutsy"
date: 2009-02-08
forum: Virtualisation
---

### Post by IntuitiveNipple on 2009-02-08
I've produced backports of the kvm-83 package for Intrepid, Hardy and Gutsy. I've tested Intrepid and Hardy but not had chance to test Gutsy so far.

They are [available from my PPA](https://edge.launchpad.net/~intuitivenipple/+archive/ppa?field.name_filter=kvm&field.status_filter=published&field.series_filter=any).
```

kvm (1:83+dfsg-0ubuntu2~tj~ppa1i) intrepid; urgency=low

  * Backport for Hardy and Intrepid
  * debian/control: Reduced build-depends to debhelper (>= 5)
                    Removed "Breaks: udev (<< 136-1)"
  * Corrected kvm-source package description to detail updated kernel modules
    need to be installed on older host kernels (pre linux 2.6.26.1) to avoid the
    guest BIOS from spinning on a hlt instruction at the "Press F12 for boot menu"
    prompt (See http://kerneltrap.org/mailarchive/linux-kvm/2008/11/5/3926664/thread).

 -- TJ <ubuntu@tjworld.net>   Fri, 06 Feb 2009 13:00:00 +0000

```

---

### Post by anders_gud on 2009-02-20
Hi IntuitiveNipple!
Do you know where I can get the dsc, source and diff for your 1:74+dfsg-0ubuntu2~ppa5h package - it does not show up in your ppa? (I have problems with the virtio drivers in the latest 1.83, and I need to apply a patch for CapsLock handling [http://www.archivum.info/qemu-devel@nongnu.org/2008-09/msg01456.html](http://www.archivum.info/qemu-devel@nongnu.org/2008-09/msg01456.html) in 1.74 )
Thanks!
Anders

---

### Post by bodhi.zazen on 2009-02-22
@IntuitiveNipple :

First, I would like to thank your for your work on backporting KVM.

I tried your package for hardy (kvm-83).

It installed without any problem, BUT the kvm guests would not boot, even after a reboot.

kvm starts, but hangs on the initial bios page.

I had to downgrade to kvm-62.

---

### Post by IntuitiveNipple on 2009-02-23
I suspect if you're having problems you'll need to build/install the accompanying kernel modules against the running kernel. Things have moved on substantially since the Hardy kernel module was created.

Source-code is available on the PPA archive page. Expand the collapsed package view by clicking on the right-pointing triangle alongside the package name and the expanded view will show them:

Download files from Librarian

    * kvm-source_83+dfsg-0ubuntu2~tj~ppa2h_all.deb (317.8 KiB)
    * kvm_83+dfsg-0ubuntu2~tj~ppa2h.diff.gz (61.9 KiB)
    * kvm_83+dfsg-0ubuntu2~tj~ppa2h.dsc (1.5 KiB)
    * kvm_83+dfsg-0ubuntu2~tj~ppa2h_amd64.deb (1.1 MiB)
    * kvm_83+dfsg-0ubuntu2~tj~ppa2h_i386.deb (1014.1 KiB)
    * kvm_83+dfsg.orig.tar.gz (4.1 MiB)

---

