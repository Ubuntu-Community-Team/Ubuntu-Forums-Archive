---
title: "Calc ods file not loadable"
date: 2018-12-03
forum: Ubuntu Development Version
---

### Post by dino99 on 2018-12-03
Since a couple days, i cant open/load an ods file with Disco, at load time a popup warns about libreoffice have crashed, and its related to its .~locl.myfile.ods#
Deleting that lock file does not help, its again the same problem with the new created one.
The same file load as expected with a bionic session.

As its a silent load crash, with no found log, i wonder about the possible cause.

---

### Post by corradoventu on 2018-12-03
i have no problem with:
```
corrado@corrado-p5-dd-1123:~$ apt policy libreoffice-cal*
libreoffice-calc:
  Installed: 1:6.1.3-0ubuntu3
  Candidate: 1:6.1.3-0ubuntu3
  Version table:
 *** 1:6.1.3-0ubuntu3 500
        500 http://archive.ubuntu.com/ubuntu disco/main amd64 Packages
        100 /var/lib/dpkg/status
corrado@corrado-p5-dd-1123:~$ 

```which libreoffice do you have?

---

### Post by dino99 on 2018-12-03
Mine is from 'proposed' (the devil might be there; will test later as im outside for a while)

libreoffice (1:6.1.3-0ubuntu6) disco; urgency=medium

  [ Evangelos Foutras ]
  * poppler-fix-build-0-70.patch: fix build failure with poppler >= 0.70

  [ Olivier Tilloy ]
  * debian/patches/poppler-dropped-gbool.patch: updated to patch an additional
    source file (sdext/source/pdfimport/xpdfwrapper/wrapper_gpl.cxx)

 -- Olivier Tilloy <email address hidden>  Mon, 26 Nov 2018 16:48:41 +0100

---

### Post by Smask on 2018-12-03
> **dino99 said:**
> Mine is from 'proposed' (the devil might be there; will test later as im outside for a while)

libreoffice (1:6.1.3-0ubuntu6) disco; urgency=medium

Wut? Maybe they removed 1:6.1.3-0ubuntu6 for some reason, because I've got the same version as Corrado and I have proposed enabled on both machines here.

---

### Post by dino99 on 2018-12-03
As you can see, it is still proposed. But it seem locked and have not reached the Disco download list. (amd64 & arm64 packages have failed at built time)
( my system is a "amd64" one, so still using the previous version)

[https://launchpad.net/ubuntu/+source/libreoffice](https://launchpad.net/ubuntu/+source/libreoffice)

So i still use libreoffice (1:6.1.3-0ubuntu3) disco; urgency=medium

  * No-change rebuild for icu soname changes.

 -- Matthias Klose <doko@ubuntu.com>  Tue, 13 Nov 2018 08:30:22 +0000
--------------------------------------------------------------------------------------------------------------------------
Maybe the problem is due to:

icu (63.1-5) unstable; urgency=medium

  * Build without Paragraph Layout API.
  * Remove libiculx63 package, no longer needed (closes: #898571).

 -- Laszlo Boszormenyi (GCS) <gcs@debian.org>  Sun, 02 Dec 2018 10:31:22 +0000

------------------------------------------------------------------------------------------------------------------------------
but reinstalling libiculx63 is not possible as that remove lot of packages.

---

### Post by VMC on 2018-12-03
Open from terminal and see if any errors appears other than perhaps java:

$ soffice whatever.ods

---

### Post by dino99 on 2018-12-04
I have already tested loading that ods file via the terminal:
- there is no output at all
- only create the -~lock file, then a recovery popup is shown, but even not list that file !!!; so its useless.

---

### Post by dino99 on 2018-12-06
Finally solved that issue via the hard way:
- purged all the libreoffice* packages and the dependencies
- try reinstallation via synaptic: impossible as the libreoffice* packages fails due to broken dependencies  !!!!  but succeed via the terminal (very strange)
- then starting soffice via le terminal  and got the previous popup about an 'untitled1' faulty package to restore, and the restoration has been accepted that time. But searching about that file accross the whole system and user space (even the hidden ones) does not succeed !!! A real ghost.

Is that an example of the Debian/Ubuntu  delta configuration/packaging ?

---

### Post by dino99 on 2018-12-06
Next problem:

After the previous post, i have opened the calc settings to set some bigger font size (+2) for an easier menu reading. And on the next calc opening, the menu, columns number and raws are not displayed at all.
So its impossible to set the options back via the calc menu. Going to dconf editor does not help either.  Then i was hoping to redo the purging/reinstalling process to get back a usable interface; but still fails, and the initial problem is now back again.
I cant beleive that purging all the libreoffice installation, and deleting the .config dir too, still does not purge the previous conflicting settings. What a mess ](*,).
Searching for possible libreoffice/calc hidden settings left behind also fails. So where they can be hidden ?

---

### Post by dino99 on 2019-01-28
Disco still has that problem; and i'm not alone  [https://bugs.launchpad.net/ubuntu/+source/libreoffice/+bug/1813506](https://bugs.launchpad.net/ubuntu/+source/libreoffice/+bug/1813506)

This is a soffice pure problem (tested via a terminal)

Confirm the comment from the report: purging libreoffice-gnome/libreoffice-gtk3, then soffice can be used as expected.

---

### Post by dino99 on 2019-01-30
when libreoffice-gtk3 is installed, the console output is:

```
oem@oem-desktop:~$ soffice --norestore --safe-mode
Application Error


Fatal exception: Signal 6
Stack:
/usr/lib/libreoffice/program/libuno_sal.so.3(+0x3d593)[0x7f5b4c3c7593]
/usr/lib/libreoffice/program/libuno_sal.so.3(+0x3d7a3)[0x7f5b4c3c77a3]
/lib/x86_64-linux-gnu/libc.so.6(+0x41100)[0x7f5b4c1cd100]
/lib/x86_64-linux-gnu/libc.so.6(gsignal+0xc7)[0x7f5b4c1cd077]
/lib/x86_64-linux-gnu/libc.so.6(abort+0x121)[0x7f5b4c1ae535]
/usr/lib/libreoffice/program/libmergedlo.so(+0x11ed45c)[0x7f5b4d5d545c]
/usr/lib/libreoffice/program/libmergedlo.so(_ZN11Application5AbortERKN3rtl8OUStringE+0x90)[0x7f5b4f223200]
/usr/lib/libreoffice/program/libmergedlo.so(+0x1efd0e7)[0x7f5b4e2e50e7]
/usr/lib/libreoffice/program/libmergedlo.so(+0x2e407cb)[0x7f5b4f2287cb]
/usr/lib/libreoffice/program/libuno_sal.so.3(+0x17782)[0x7f5b4c3a1782]
/usr/lib/libreoffice/program/libuno_sal.so.3(+0x3d66f)[0x7f5b4c3c766f]
/lib/x86_64-linux-gnu/libc.so.6(+0x41100)[0x7f5b4c1cd100]
/lib/x86_64-linux-gnu/libc.so.6(+0x183f11)[0x7f5b4c30ff11]
/usr/lib/x86_64-linux-gnu/libgio-2.0.so.0(g_dbus_node_info_new_for_xml+0x124)[0x7f5b4bb8aa94]
/usr/lib/libreoffice/program/libmergedlo.so(+0x2ebad3f)[0x7f5b4f2a2d3f]
/usr/lib/x86_64-linux-gnu/libgio-2.0.so.0(+0x101ac6)[0x7f5b4bb7fac6]
/usr/lib/x86_64-linux-gnu/libgio-2.0.so.0(+0x101cf8)[0x7f5b4bb7fcf8]
/usr/lib/x86_64-linux-gnu/libgio-2.0.so.0(+0xa2499)[0x7f5b4bb20499]
/usr/lib/x86_64-linux-gnu/libgio-2.0.so.0(+0xa2ff6)[0x7f5b4bb20ff6]
/usr/lib/x86_64-linux-gnu/libgio-2.0.so.0(+0xf96fa)[0x7f5b4bb776fa]
/usr/lib/x86_64-linux-gnu/libgio-2.0.so.0(+0xa2499)[0x7f5b4bb20499]
/usr/lib/x86_64-linux-gnu/libgio-2.0.so.0(+0xa24d9)[0x7f5b4bb204d9]
/usr/lib/x86_64-linux-gnu/libglib-2.0.so.0(g_main_context_dispatch+0x158)[0x7f5b4b956858]
/usr/lib/x86_64-linux-gnu/libglib-2.0.so.0(+0x4ec48)[0x7f5b4b956c48]
/usr/lib/x86_64-linux-gnu/libglib-2.0.so.0(g_main_context_iteration+0x2c)[0x7f5b4b956cdc]
/usr/lib/libreoffice/program/libvclplug_gtk3lo.so(+0x899e3)[0x7f5b44a3d9e3]
/usr/lib/libreoffice/program/libmergedlo.so(_ZN11Application5YieldEv+0x2e)[0x7f5b4f2236de]
/usr/lib/libreoffice/program/libmergedlo.so(_ZN6Dialog7ExecuteEv+0x6e)[0x7f5b4ef7300e]
/usr/lib/libreoffice/program/libmergedlo.so(+0x22a06d9)[0x7f5b4e6886d9]
/usr/lib/libreoffice/program/libmergedlo.so(+0x1f00263)[0x7f5b4e2e8263]
/usr/lib/libreoffice/program/libmergedlo.so(+0x1f015da)[0x7f5b4e2e95da]
/usr/lib/libreoffice/program/libmergedlo.so(+0x2c1fa38)[0x7f5b4f007a38]
/usr/lib/libreoffice/program/libmergedlo.so(_ZN16SalUserEventList18DispatchUserEventsEb+0x187)[0x7f5b4f205467]
/usr/lib/libreoffice/program/libvclplug_gtk3lo.so(+0x886e9)[0x7f5b44a3c6e9]
/usr/lib/x86_64-linux-gnu/libglib-2.0.so.0(g_main_context_dispatch+0x158)[0x7f5b4b956858]
/usr/lib/x86_64-linux-gnu/libglib-2.0.so.0(+0x4ec48)[0x7f5b4b956c48]
/usr/lib/x86_64-linux-gnu/libglib-2.0.so.0(g_main_context_iteration+0x2c)[0x7f5b4b956cdc]
/usr/lib/libreoffice/program/libvclplug_gtk3lo.so(+0x899e3)[0x7f5b44a3d9e3]
/usr/lib/libreoffice/program/libmergedlo.so(_ZN11Application5YieldEv+0x2e)[0x7f5b4f2236de]
/usr/lib/libreoffice/program/libmergedlo.so(_ZN11Application7ExecuteEv+0x45)[0x7f5b4f224e55]
/usr/lib/libreoffice/program/libmergedlo.so(+0x1f02a46)[0x7f5b4e2eaa46]
/usr/lib/libreoffice/program/libmergedlo.so(+0x2e41f56)[0x7f5b4f229f56]
/usr/lib/libreoffice/program/libmergedlo.so(_Z6SVMainv+0x30)[0x7f5b4f22a050]
/usr/lib/libreoffice/program/libmergedlo.so(soffice_main+0x91)[0x7f5b4e306d91]
/usr/lib/libreoffice/program/soffice.bin(+0x107b)[0x559c1dc9307b]
/lib/x86_64-linux-gnu/libc.so.6(__libc_start_main+0xeb)[0x7f5b4c1b009b]
/usr/lib/libreoffice/program/soffice.bin(+0x10ba)[0x559c1dc930ba]
```

Digging around i've found [https://bugs.documentfoundation.org/show_bug.cgi?id=122116#c26](https://bugs.documentfoundation.org/show_bug.cgi?id=122116#c26)
which suggest a libcpdb removal: purged libcpdb-libs-common1  and cpdb-backend-cups as dependant.

After reinstalling libreoffice-gnome  and restarted the session (gnome-shell on xorg), now soffice start as expected.

Looks like LO needs to be rebuilt with that library, [https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=911345](https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=911345)

---

### Post by slickymaster on 2019-01-30
@dino99:

Please use code tags when posting output.

---

### Post by makitso on 2019-02-02
[FONT=Helvetica]See if you have cpdb-backend-gcp and libcpdb-libs-common1 installed. By purging these two libraries Libreoffice starts correctly.[/FONT]

---

### Post by dino99 on 2019-02-05
Fixed with the coming 6.20   'ppa:osomon/lo-test'

---

### Post by dino99 on 2019-11-12
Get again the same problem after the Nov 11th upgrades; Does not get error from a terminal.
Only get a dialog box telling calc has silently crashed and will then try to recover the ods file: but there is no file listed to recover.
Indeed that ods file load/open as usual with version prior to Focal.

---

