---
title: "alien will not convert vmware workstation rpm to deb"
date: 2009-05-12
forum: Virtualisation
---

### Post by col48 on 2009-05-12
I am trying to install an evaluation of vmware workstation to run windows95 as a virtual machine.  I believe I need to instal from a deb file.  So I download the rpm (a deb is not available), all 376Mb of it.  I now try to run alien to convert this to a deb as follows

[download folder]$ sudo alien -d --veryverbose VMware-Workstation-6.5.1-126130.i386.rpm

but it fails.  The last screenfull of the output is this (I ran veryverbose in the hope it would shed more light but it didn't, at least to me).  The failed Assertion and the Error 134 near the end - what do they mean?  Does anyone have an idea where to go from here?


   mkdir VMware-Workstation-6.5.1/debian
   hostname -f
[me]

   date -R
Tue, 12 May 2009 13:35:24 +0100

   hostname -f
[me]

   date -R
Tue, 12 May 2009 13:35:24 +0100

   chmod 755 VMware-Workstation-6.5.1/debian/rules
   debian/rules binary 2>&1
dh_testdir
dh_testdir
dh_testroot
dh_clean -k -d
dh_installdirs
dh_installdocs
dh_installchangelogs
find . -maxdepth 1 -mindepth 1 -not -name debian -print0 | \
       xargs -0 -r -i cp -a {} debian/vmware-workstation
xargs: xargs.c:443: main: Assertion `bc_ctl.arg_max <= (131072-2048)' failed.
Aborted
make: *** [binary-arch] Error 134

Package build failed. Here's the log:
dh_testdir
dh_testdir
dh_testroot
dh_clean -k -d
dh_installdirs
dh_installdocs
dh_installchangelogs
find . -maxdepth 1 -mindepth 1 -not -name debian -print0 | \
       xargs -0 -r -i cp -a {} debian/vmware-workstation
xargs: xargs.c:443: main: Assertion `bc_ctl.arg_max <= (131072-2048)' failed.
Aborted
make: *** [binary-arch] Error 134
   find VMware-Workstation-6.5.1 -type d -exec chmod 755 {} ;
find: VMware-Workstation-6.5.1: No such file or directory
   rm -rf VMware-Workstation-6.5.1

---

### Post by binbash on 2009-05-12
Download the bundle one, install via it :  sh asdasdasd.bundle

---

### Post by col48 on 2009-05-13
Thanks binbash.  Unfortuantely I am too close to my download limit for the month.

Yahoo search on 'bc_ctl' suggests this is a bug in Hardy (specifically findutils) which can be fixed by installing the Intrepid version.  The following method is suggested:

edit /etc/apt/sources.list  replacing all instances of hardy with intrepid.
then
aptitude update
aptitude install findutils
then reedit sources.list to restore references to hardy.

Has anyone any comment on this procedure?  Has anyone seen it work?  Are there any unwanted side-effects?  Does Synaptic cope afterwards?

---

### Post by u-slayer on 2009-05-14
Use virtual box instead. They have ready made .deb installers.

[http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)

---

### Post by col48 on 2009-05-15
Thanks u-slayer.
I had had a go at VirtualBox and failed to get the guest machine up and running, which is why I had turned to vmware.  But armed with the vmware experience I had another go at VirtualBox and :D not only got it going but was able to move from the default VGA to SVGA.  Doubtless other issues await me.

So I won't be pursuing vmware further.

But someone else might like any thoughts on the wider issue of using intrepid bits in hardy, if anyone has any.

---

### Post by hoangbv15 on 2009-06-03
> Download the bundle one, install via it : sh asdasdasd.bundle

No need to download, that will waste your brandwidth. Open the .rpm file with archive manager, the .bundle file is in there.

---

