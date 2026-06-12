---
title: "fglrx with kernel 3.4 and 3.5"
date: 2012-05-27
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by jfernyhough on 2012-05-27
The wait is over! A working patch has been posted on [http://ati.cchtml.com/show_bug.cgi?id=495](http://ati.cchtml.com/show_bug.cgi?id=495) by Zenitur.

HINT: /dev/shm makes a nice ramdisk if you have >2GB RAM.

**Latest:** Alberto Milone has pushed an updated 9.860 that has support for kernels 3.4 and 3.5: [https://launchpad.net/ubuntu/quantal/+source/fglrx-installer/2:8.960-0ubuntu2](https://launchpad.net/ubuntu/quantal/+source/fglrx-installer/2:8.960-0ubuntu2) (3.5 support nor working for me, locks as X loads).

Latest beta: Catalyst 12.6 Beta works. Instructions below. If unsure use 12.4. Thanks to [miatawnt2b]("http://ubuntuforums.org/member.php?u=263498") for pointing out the 12.6 beta existed!

**In summary:**
0) Preparation
1) Download and extract [12.6 from AMD]("http://www2.ati.com/drivers/hotfix/catalyst_12.6_hotfixes/amd-driver-installer-8.98-x86.x86_64.zip").
2) Apply the patch attached [URL="http://ati.cchtml.com/attachment.cgi?id=464"]here.
[/URL] 3) Build packages
4) Install
5) Remove watermark

**Details:**
0) If this is the first time you've done this, install the necessary development packages  (normally installed by the installer, if any are missing they will be identified in step 3):
$ sudo apt-get install dpkg-dev debhelper  dh-modaliases execstack

1) Once downloaded (the .run is in a .zip file. I shouldn't have to tell you how to deal with that), extract the installer files so we can patch manually:
$ sh ./amd-driver-installer-12-4-x86.x86_64.run --extract ~/temp/amd

2) Download and apply the attached patch (taken from Arch's catalyst-test):[URL="http://ati.cchtml.com/attachment.cgi?id=464"]
[/URL]$ cd ~/temp/amd
$ patch -p1 <./3.4.patch

3) Build the packages (this will place the packages in the parent directory):
$ ./ati-installer.sh 8.980 --buildpkg Ubuntu/quantal

4) Change to the parent directory and install the debs:
$ cd ..
$ sudo dpkg -i *.deb

5) In order to remove the watermark you will need to add a signature to  /etc/ati/signature . I took the signature from 12.4 as demonstrated  here: [http://wiki.cchtml.com/index.php/Amd_watermark](http://wiki.cchtml.com/index.php/Amd_watermark)

All you have to do is add the following to /etc/ati/signature and restart X (e.g. log out).
```
b67d452b67e1e4baee18b65de7643cc0:8e537c1d56ccd588de2c866886490df38148761a24cca5eea7388168d3560bf9:8e1870185082d5dedb2ed53e835104f8d21877485fd7d282d62e8264d7005af38e4c711350d7d5dbdc2cd53e865159a5d74a76135fd0d2828a2b836bd7065af9
```If you haven't already got an xorg.conf you will need to run:
$ sudo aticonfig --initial
and reboot.

All should work!

*** Beta 12.6 ***

Beta page: [http://support.amd.com/us/kbarticles/Pages/AMDCatalyst126beta.aspx](http://support.amd.com/us/kbarticles/Pages/AMDCatalyst126beta.aspx)
Direct link: [http://www2.ati.com/drivers/hotfix/catalyst_12.6_hotfixes/amd-driver-installer-8.98-x86.x86_64.zip](http://www2.ati.com/drivers/hotfix/catalyst_12.6_hotfixes/amd-driver-installer-8.98-x86.x86_64.zip)

---

### Post by Yellow Pasque on 2012-05-28
It would be funny if AMD pushed out Catalyst 12-5 tomorrow and it supported kernel 3.4

---

### Post by Salane on 2012-05-28
> **jfernyhough said:**
> The wait is over! A working patch has been posted on [http://ati.cchtml.com/show_bug.cgi?id=495](http://ati.cchtml.com/show_bug.cgi?id=495) by Zenitur.

HINT: /dev/shm makes a nice ramdisk if you have >2GB RAM.

**In summary:**
1) Download and extract [12.4 from ]("http://www2.ati.com/drivers/linux/amd-driver-installer-12-4-x86.x86_64.run")[AMD]("http://www2.ati.com/drivers/linux/amd-driver-installer-12-4-x86.x86_64.run").
2) Apply the patch attached [URL="http://ati.cchtml.com/attachment.cgi?id=464"]here.
[/URL] 3) Build packages
4) Install

**Details:**
1) Once downloaded extract the installer files so we can patch manually:
$ sh ./amd-driver-installer-12-4-x86.x86_64.run --extract ~/temp/amd

2) Download and apply the patch from [here]("http://ati.cchtml.com/attachment.cgi?id=464"):[URL="http://ati.cchtml.com/attachment.cgi?id=464"]
[/URL]$ cd ~/temp/amd
$ patch -p1 <./patch_to_fix_compiling_fglrx_12.4_with_linux_3.4.patch

3) Build the packages (this will place the packages in the parent directory):
$ ./ati-installer.sh 8.961 --buildpkg Ubuntu/quantal

4) Change to the parent directory and install the debs:
$ cd ..
$ sudo dpkg -i *.deb

If you haven't already got an xorg.conf you will need to run:
$ sudo aticonfig --initial
and reboot.

All should work!

~/temp/amd$ patch -p1 <./patch_to_fix_compiling_fglrx_12.4_with_linux_3.4.patch
patching file common/lib/modules/fglrx/build_mod/firegl_public.c
patching file common/lib/modules/fglrx/build_mod/kcl_ioctl.c
patch unexpectedly ends in middle of line
Hunk #1 succeeded at 217 with fuzz 1.

and when I go to the next step I get this. 
./ati-installer.sh 8.961 --buildpkg Ubuntu/quantal=====================================================================
 AMD Catalyst(TM) Proprietary Driver Installer/Packager 
=====================================================================
Generating package: Ubuntu/quantal
Error: Distro Version entered incorrectly or not supported, use --listpkg to identify valid distro versions
Error: Distro Version entered incorrectly or not supported, use --listpkg to identify valid distro versions

But no Quantal in --listpkg

Ubuntu Packages:
        Ubuntu/gutsy
        Ubuntu/hardy
        Ubuntu/intrepid
        Ubuntu/jaunty
        Ubuntu/karmic
        Ubuntu/lucid
        Ubuntu/maverick
        Ubuntu/natty
        Ubuntu/oneiric
        Ubuntu/source
        Ubuntu/precise

I copied /temp/amd/packages/Ubuntu/dists/precise to /temp/amd/packages/Ubuntu/dists/quantal and tried again. Further Errors were fixed by installing the following.
sudo apt-get install dpkg-dev debhelper  dh-modaliases execstack

Dep errors on install of created deb files were fixed by
  sudo apt-get -f install

after reboot
glxinfo
name of display: :0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: ATI
server glx version string: 1.4

---

### Post by jfernyhough on 2012-05-28
Ah, forgot about the extra packages. It's not the first time I've had to patch and install. ;)

Added a Step 0. --buildpkg Ubuntu/quantal should work fine; worked for me.

---

### Post by Salane on 2012-05-28
That was a major Duh moment in my haste I forgot to upgrade to quantal on my new install. Oh well at least others may learn of my mistake.

---

### Post by AIPHEE on 2012-06-09
Thank you! Works on Kubuntu 12.10 (even if is not under Canonial anymore).

---

### Post by miatawnt2b on 2012-06-11
anyone know if this works with 12.6 beta?
-J

---

### Post by jfernyhough on 2012-06-11
Took me a little to find the 12.6 beta but it's here: [http://support.amd.com/us/kbarticles/Pages/AMDCatalyst126beta.aspx](http://support.amd.com/us/kbarticles/Pages/AMDCatalyst126beta.aspx)

Without the patch there's no makefile errors, just the same "error: &#8216;cpu_possible_map&#8217; undeclared" when DKMS builds as with 12.4. Trying again with the patch.

--edit
Builds fine with the patch, DKMS doesn't report anything odd. Going to try a reboot.

--edit 2
Display comes up fine, driver seems to be working as I now have a horrible "Testing use only" watermark in the lower-right corner of the screen... :(

--edit 3
Using the signature from 12.4 removes the watermark.
In /etc/ati/signature put the following text: 
```
b67d452b67e1e4baee18b65de7643cc0:8e537c1d56ccd588de2c866886490df38148761a24cca5eea7388168d3560bf9:8e1870185082d5dedb2ed53e835104f8d21877485fd7d282d62e8264d7005af38e4c711350d7d5dbdc2cd53e865159a5d74a76135fd0d2828a2b836bd7065af9
```

--edit 4
Updated op.

---

### Post by jerrylamos on 2012-06-12
CLI to the rescue!  Quantal had my external monitor at 1280x768 and systems settings, displays doesn't work.  My wife in a swimsuit stretched like a fun house mirror.

So....a bit of search on [https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)

xrandr --output CRT1 --mode 1280x1024 --rate 60

and I'm up in business!

Quantal's finally usable.

Jerry

---

### Post by ventrical on 2012-06-15
I just got a seamless install with the daily 'live' (32bit)build on my:

01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI RV350 AQ [Radeon 9600]
01:00.1 Display controller: Advanced Micro Devices [AMD] nee ATI RV350 AQ [Radeon 9600] (Secondary)

---

### Post by Yellow Pasque on 2012-06-15
> **ventrical said:**
> I just got a seamless install with the daily 'live' (32bit)build on my:

01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI RV350 AQ [Radeon 9600]
01:00.1 Display controller: Advanced Micro Devices [AMD] nee ATI RV350 AQ [Radeon 9600] (Secondary)


Since that card hasn't been supported by fglrx/Catalyst in years, that's irrelevant to this thread...

---

### Post by jerrylamos on 2012-06-15
What is relevant?  This is
Advanced Micro Devices [AMD] nee ATI Wrestler [Radeon HD 6310]
on a Acer Aspire 5253 wide screen bought new Oct 2010. Has an external monitor.
As of 15 June update Systems Settings "Displays" is still busted comes up in some wierd resolution and "apply" fails see Bug #1007588 so I have to manually turn off the laptop monitor always boots with Quantal on full bright (ouch) and issue a CLI xrander to get going sort of.
This is on quantal Alpha 32 bit installed then all up to date.  (The Acer will do 64 bit I'll look at that some time.)
Precise "Displays" works just fine.

Jerry

---

### Post by jfernyhough on 2012-06-18
New package pushed by Alberto Milone means manual patching is unnecessary. Also, kernel 3.5 support. Yay!

[https://launchpad.net/ubuntu/quantal/+source/fglrx-installer/2:8.960-0ubuntu2](https://launchpad.net/ubuntu/quantal/+source/fglrx-installer/2:8.960-0ubuntu2)

---

### Post by Gregory Lee on 2012-06-18
Using the KDE plasma desktop (gnome and ubuntu crash), I lost fglrx support in updating to quantal, but today (Mon 6/18 ) I got it back.  I saw some discussion here about how to install fglrx into quantal working from the ATI distribution package, but I decided I'd rather wait and get a working version from the Ubuntu repositories through the regular upgrade process.  So, for anyone in a similar fix, try upgrading again and you may get a working fglrx.  It's nice to have the rotating cube for workspaces and translucent windows back.

---

### Post by kevpan815 on 2012-06-19
Just went to AMD's Website only to find that my ATI Radeon X300 is only Legacy Supported by AMD! This must be the reason why Kernel's 3.4 and 3.5 don't recognize my Video Card.

---

### Post by Yellow Pasque on 2012-06-19
> **kevpan815 said:**
> Just went to AMD's Website only to find that my ATI Radeon X300 is only Legacy Supported by AMD! This must be the reason why Kernel's 3.4 and 3.5 don't recognize my Video Card.
It's been that way for 3 years. I'm not sure what you mean by "kernel doesn't recognize my video card", but you should start your own thread on that (and provide /var/log/Xorg.0.log ).

---

### Post by kevpan815 on 2012-06-19
Ubuntu 12.10 says that I have an Unknown Video Graphics Card, Just fyi.

---

### Post by Yellow Pasque on 2012-06-19
Are you using the sysinfo program? That's a common/known bug with that program. Don't worry about it.

---

### Post by kevpan815 on 2012-06-20
> **jerrylamos said:**
> What is relevant?  This is
Advanced Micro Devices [AMD] nee ATI Wrestler [Radeon HD 6310]
on a Acer Aspire 5253 wide screen bought new Oct 2010. Has an external monitor.
As of 15 June update Systems Settings "Displays" is still busted comes up in some wierd resolution and "apply" fails see Bug #1007588 so I have to manually turn off the laptop monitor always boots with Quantal on full bright (ouch) and issue a CLI xrander to get going sort of.
This is on quantal Alpha 32 bit installed then all up to date.  (The Acer will do 64 bit I'll look at that some time.)
Precise "Displays" works just fine.

Jerry

Hey Jerry, today I tried installing x86 12.10 Daily-Live on all of my other 3 PC's and the only one that had the display problems like the ATI Radeon X300 was my other desktop which has, you guessed it, an ATI Radeon 3200 HD Video Card!

---

### Post by kevpan815 on 2012-06-20
P.S. The NVIDIA and the Intel Video Cards ( in the other two computers) had no problems at all.

---

### Post by jfernyhough on 2012-06-22
It doesn't seem as though the patch for 8.960 to add kernel 3.5 support works correctly - at least for me, either with 8.960 from the repo or manually patching 8.980. Having to go back to 3.4 (liquorix) for now.

---

### Post by Gregory Lee on 2012-06-22
Whatever versions I have (from "aptitude safe-upgrade") seem to be working okay for the kde plasma desktop:
```
# ls -l /var/lib/dkms/fglrx-updates/
total 4
drwxr-xr-x 5 root root 4096 Jun 20 13:55 8.960
lrwxrwxrwx 1 root root   28 Jun 18 15:08 kernel-3.4.0-5-generic-x86_64 -> 8.960/3.4.0-5-generic/x86_64
lrwxrwxrwx 1 root root   28 Jun 20 13:55 kernel-3.5.0-1-generic-x86_64 -> 8.960/3.5.0-1-generic/x86_64
```

---

### Post by blizzari on 2012-06-23
Yeah 3.5.0.1 update is not compatible with the patch :(

*EDIT*

Kernel 3.4 failed to compile 8.960 FGLRX (Unconfirmed)

---

### Post by keon2991 on 2012-07-09
this method doesn't work with kernel 3.5.0-3, though I've installed AMDCCCLE succesffuly. fglrxinfo show me this:
```
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  139 (ATIFGLEXTENSION)
  Minor opcode of failed request:  66 ()
  Serial number of failed request:  13
  Current serial number in output stream:  13
```

---

### Post by jfernyhough on 2012-07-10
Testing new patch for kernel 3.5 from here: [https://bbs.archlinux.org/viewtopic.php?pid=1127407#p1127407](https://bbs.archlinux.org/viewtopic.php?pid=1127407#p1127407)

Credited to Enrico Tagliavini.

Apparently the new legacy beta has 1.12 support too, but I have a 5000-series so can't test it. [http://www2.ati.com/drivers/legacy/amd-driver-installer-12.6-legacy-x86.x86_64.zip](http://www2.ati.com/drivers/legacy/amd-driver-installer-12.6-legacy-x86.x86_64.zip)

--edit
Yup, new patch works nicely. Now running kernel 3.5 with fglrx 8.98.

---

### Post by jfernyhough on 2012-07-10
OK, so until we're able to edit posts new details are here.

**This is only for Radeons from series 5000 onwards.**

Credit for patch collection to Vi0L0 at Arch, 3.5 patch credited to Enrico Tagliavini.
[B]
In summary:[/B]
0) Preparation
1) Download and extract [12.6 from AMD]("http://www2.ati.com/drivers/linux/amd-driver-installer-12-6-x86.x86_64.run").
2) Apply the patches from catalyst-hook attached [here]("http://catalyst.apocalypsus.net/tarball/0_TESTING/catalyst-hook.tar.gz").[URL="http://ati.cchtml.com/attachment.cgi?id=464"]
[/URL] 3) Build packages
4) Install

**Details:**
0) If this is the first time you've done this, install the necessary  development packages  (normally installed by the installer, if any are  missing they will be identified in step 3):
$ sudo apt-get install build-essential debhelper  dh-modaliases execstack

1) Once downloaded extract the installer files so we can patch  manually:
$ sh ./amd-driver-installer-12-6-x86.x86_64.run --extract ~/temp/amd

2) Download, copy into ~/temp/amd, and apply the attached patches (taken from Vi0L0's catalyst-hook test):[URL="http://ati.cchtml.com/attachment.cgi?id=464"]
[/URL]$ cd ~/temp/amd
$ patch -p1 <./3.4.patch
$ patch -p1 <./3.5-do_mmap.patch

3) Build the packages (this will place the packages in the parent directory):
$ ./ati-installer.sh 8.980 --buildpkg Ubuntu/quantal

4) Change to the parent directory and install the debs:
$ cd ..
$ sudo dpkg -i *.deb

---

### Post by balloons on 2012-07-10
Hmm.. I finally got my hands on a radeon card -- HD 6xxx series. I didn't seem to have any trouble switching out the nvidia card, installing fglrx-updates and removing xorg.conf. Upon reboot everything worked great. Am I just lucky or should I have seen issues? I am having trouble with justifying running the catalyst drivers for this though -- my usecase is running unity desktop, coding, web browsing, testing ;-).. No real gaming.

---

### Post by PelPix on 2012-07-10
> **jfernyhough said:**
> OK, so until we're able to edit posts new details are here.

**This is only for Radeons from series 5000 onwards.**

Credit for patch collection to Vi0L0 at Arch, 3.5 patch credited to Enrico Tagliavini.
[B]
In summary:[/B]
0) Preparation
1) Download and extract [12.6 from AMD]("http://www2.ati.com/drivers/linux/amd-driver-installer-12-6-x86.x86_64.run").
2) Apply the patches from catalyst-hook attached [here]("http://catalyst.apocalypsus.net/tarball/0_TESTING/catalyst-hook.tar.gz").[URL="http://ati.cchtml.com/attachment.cgi?id=464"]
[/URL] 3) Build packages
4) Install

**Details:**
0) If this is the first time you've done this, install the necessary  development packages  (normally installed by the installer, if any are  missing they will be identified in step 3):
$ sudo apt-get install build-essential debhelper  dh-modaliases execstack

1) Once downloaded extract the installer files so we can patch  manually:
$ sh ./amd-driver-installer-12-6-x86.x86_64.run --extract ~/temp/amd

2) Download, copy into ~/temp/amd, and apply the attached patches (taken from Vi0L0's catalyst-hook test):[URL="http://ati.cchtml.com/attachment.cgi?id=464"]
[/URL]$ cd ~/temp/amd
$ patch -p1 <./3.4.patch
$ patch -p1 <./3.5-do_mmap.patch

3) Build the packages (this will place the packages in the parent directory):
$ ./ati-installer.sh 8.980 --buildpkg Ubuntu/quantal

4) Change to the parent directory and install the debs:
$ cd ..
$ sudo dpkg -i *.deb

Still crashing when xorg starts on Xubuntu :(

---

### Post by rbrick49 on 2012-07-11
I dont know how guitara got fglrx -updates working but mine keeps crashing when xorg starts also. i have kernel 3.5.0.4-generic with a 6950 card any answers folks

---

### Post by Niccola on 2012-07-11
> **jfernyhough said:**
> OK, so until we're able to edit posts new details are here.

**This is only for Radeons from series 5000 onwards.**

Credit for patch collection to Vi0L0 at Arch, 3.5 patch credited to Enrico Tagliavini.
[B]
In summary:[/B]
0) Preparation
1) Download and extract [12.6 from AMD]("http://www2.ati.com/drivers/linux/amd-driver-installer-12-6-x86.x86_64.run").
2) Apply the patches from catalyst-hook attached [here]("http://catalyst.apocalypsus.net/tarball/0_TESTING/catalyst-hook.tar.gz").[URL="http://ati.cchtml.com/attachment.cgi?id=464"]
[/URL] 3) Build packages
4) Install

**Details:**
0) If this is the first time you've done this, install the necessary  development packages  (normally installed by the installer, if any are  missing they will be identified in step 3):
$ sudo apt-get install build-essential debhelper  dh-modaliases execstack

1) Once downloaded extract the installer files so we can patch  manually:
$ sh ./amd-driver-installer-12-6-x86.x86_64.run --extract ~/temp/amd

2) Download, copy into ~/temp/amd, and apply the attached patches (taken from Vi0L0's catalyst-hook test):[URL="http://ati.cchtml.com/attachment.cgi?id=464"]
[/URL]$ cd ~/temp/amd
$ patch -p1 <./3.4.patch
$ patch -p1 <./3.5-do_mmap.patch

3) Build the packages (this will place the packages in the parent directory):
$ ./ati-installer.sh 8.980 --buildpkg Ubuntu/quantal

4) Change to the parent directory and install the debs:
$ cd ..
$ sudo dpkg -i *.deb

Works wonderfully in Ubuntu 12.04 precise 64bits with kernel 3.4.0.030400
AMD Radeon HD 6770M + Intel HD 3000

Thanks, and best regards

---

### Post by jfernyhough on 2012-07-11
> **PelPix said:**
> Still crashing when xorg starts on Xubuntu :(It will do if you're running xserver 1.12. It's a known issue (possibly something to do with libpciaccess on Debian judging by the reports on [http://ati.cchtml.com/show_bug.cgi?id=522](http://ati.cchtml.com/show_bug.cgi?id=522)).

Workround is to go back to 1.11 for now - or move to Arch! :D

---

### Post by AIPHEE on 2012-07-11
> **jfernyhough said:**
> OK, so until we're able to edit posts new details are here.

.
.
.

3) Build the packages (this will place the packages in the parent directory):
$ ./ati-installer.sh 8.980 --buildpkg Ubuntu/quantal

4) Change to the parent directory and install the debs:
$ cd ..
$ sudo dpkg -i *.deb

I got an error in step 3 :( 
```
# empty ld.so.conf for the fake multi-arch alternative for PXpress
echo "" > "/tmp/fglrx.6oPJEn/debian/fglrx/usr/lib/pxpress/alt_ld.so.conf"
# Generate modaliases
sh -e debian/modaliases/fglrx_supported \
                lib/modules/fglrx/build_mod/fglrxko_pci_ids.h fglrx fglrx > \
                debian/fglrx.modaliases
dh_modaliases
rm debian/fglrx.modaliases
#Run the normal stuff
dh binary-arch
   dh_auto_install -a -Nfglrx -Nfglrx-amdcccle
   dh_install -a -Nfglrx -Nfglrx-amdcccle
   dh_installdocs -a -Nfglrx
   dh_installchangelogs -a -Nfglrx
   dh_installexamples -a -Nfglrx
   dh_installman -a -Nfglrx
   dh_installcatalogs -a -Nfglrx
   dh_installcron -a -Nfglrx
   dh_installdebconf -a -Nfglrx
   dh_installemacsen -a -Nfglrx
   dh_installifupdown -a -Nfglrx
   dh_installinfo -a -Nfglrx
   dh_pysupport -a -Nfglrx
dh_pysupport: This program is deprecated, you should use dh_python2 instead. Migration guide: http://deb.li/dhs2p
   dh_installinit -a -Nfglrx
   dh_installmenu -a -Nfglrx
   dh_installmime -a -Nfglrx
   dh_installmodules -a -Nfglrx
   dh_installlogcheck -a -Nfglrx
   dh_installlogrotate -a -Nfglrx
   dh_installpam -a -Nfglrx
   dh_installppp -a -Nfglrx
   dh_installudev -a -Nfglrx
   dh_installwm -a -Nfglrx
   dh_installxfonts -a -Nfglrx
   dh_installgsettings -a -Nfglrx
   dh_bugfiles -a -Nfglrx
   dh_ucf -a -Nfglrx
   dh_lintian -a -Nfglrx
   dh_gconf -a -Nfglrx
   dh_icons -a -Nfglrx
   dh_perl -a -Nfglrx
   dh_usrlocal -a -Nfglrx
   dh_link -a -Nfglrx
   dh_compress -a
   dh_fixperms -a
   dh_strip -a
   dh_makeshlibs -a
objdump: debian/fglrx/usr/lib/pxpress/ld.so.conf: File format not recognized
objdump: debian/fglrx/usr/lib/pxpress/alt_ld.so.conf: File truncated
objdump: debian/fglrx/usr/lib/fglrx/ld.so.conf: File format not recognized
objdump: debian/fglrx/usr/lib/fglrx/alt_ld.so.conf: File truncated
   debian/rules override_dh_shlibdeps
make[1]: Entering directory `/tmp/fglrx.6oPJEn'
dh_shlibdeps -l/tmp/fglrx.6oPJEn/debian/fglrx/usr/lib/fglrx:/tmp/fglrx.6oPJEn/debian/fglrx/usr/lib32/fglrx -Xlib32
dpkg-shlibdeps: warning: debian/fglrx/usr/lib/fglrx/libAMDXvBA.so.1.0 contains an unresolvable reference to symbol dlsym: it's probably a plugin
dpkg-shlibdeps: warning: 21 other similar warnings have been skipped (use -v to see them all)
dpkg-shlibdeps: warning: debian/fglrx/usr/lib/fglrx/bin/atieventsd contains an unresolvable reference to symbol XauFileName: it's probably a plugin
dpkg-shlibdeps: warning: debian/fglrx/usr/lib/fglrx/libGL.so.1.2 contains an unresolvable reference to symbol XOpenDisplay: it's probably a plugin
dpkg-shlibdeps: warning: 31 other similar warnings have been skipped (use -v to see them all)
dpkg-shlibdeps: error: no dependency information found for /usr/share/ati/lib64/libQtCore.so.4 (used by debian/fglrx/usr/lib/fglrx/bin/amdnotifyui)
dh_shlibdeps: dpkg-shlibdeps -Tdebian/fglrx.substvars debian/fglrx/usr/lib/fglrx/libAMDXvBA.so.1.0 debian/fglrx/usr/lib/fglrx/bin/fglrxinfo debian/fglrx/usr/lib/fglrx/bin/aticonfig debian/fglrx/usr/lib/fglrx/bin/atiodcli debian/fglrx/usr/lib/fglrx/bin/fgl_glxgears debian/fglrx/usr/lib/fglrx/bin/amdnotifyui debian/fglrx/usr/lib/fglrx/bin/atieventsd debian/fglrx/usr/lib/fglrx/bin/atiode debian/fglrx/usr/lib/fglrx/libamdocl64.so debian/fglrx/usr/lib/fglrx/libatiadlxx.so debian/fglrx/usr/lib/fglrx/libaticalrt.so debian/fglrx/usr/lib/fglrx/libSlotMaximizerAg.so debian/fglrx/usr/lib/fglrx/libGL.so.1.2 debian/fglrx/usr/lib/fglrx/libfglrx_dm.so.1.0 debian/fglrx/usr/lib/fglrx/libXvBAW.so.1.0 debian/fglrx/usr/lib/fglrx/dri/fglrx_dri.so debian/fglrx/usr/lib/fglrx/libaticalcl.so debian/fglrx/usr/lib/fglrx/libSlotMaximizerBe.so debian/fglrx/usr/lib/fglrx/libaticaldd.so debian/fglrx/usr/lib/fglrx/libatiuki.so.1.0 debian/fglrx/usr/lib/fglrx/libOpenCL.so.1 debian/fglrx/usr/lib/fglrx/xorg/modules/glesx.so debian/fglrx/usr/lib/fglrx/xorg/modules/extensions/libglx.so debian/fglrx/usr/lib/fglrx/xorg/modules/amdxmm.so debian/fglrx/usr/lib/fglrx/xorg/modules/drivers/fglrx_drv.so debian/fglrx/usr/lib/fglrx/xorg/modules/linux/libfglrxdrm.so returned exit code 2
make[1]: *** [override_dh_shlibdeps] Error 2
make[1]: Leaving directory `/tmp/fglrx.6oPJEn'
make: *** [binary-arch] Error 2
dpkg-buildpackage: error: debian/rules binary gave error exit status 2
```

Xorg 1.12, i cant force version in synaptic, how will i downgrade?

---

### Post by jfernyhough on 2012-07-11
> **AIPHEE said:**
> I got an error in step 3 :( What card do you have?
> [Xorg 1.12, i cant force version in synaptic, how will i downgrade?
Get xserver-xorg and xserver-common from Launchpad, e.g.:
[https://launchpad.net/ubuntu/quantal/amd64/xserver-common/2:1.11.4-0ubuntu11](https://launchpad.net/ubuntu/quantal/amd64/xserver-common/2:1.11.4-0ubuntu11)
[https://launchpad.net/ubuntu/+source/xorg-server/2:1.11.4-0ubuntu11](https://launchpad.net/ubuntu/+source/xorg-server/2:1.11.4-0ubuntu11)

Install manually ($ sudo dpkg -i ), you may end up removing other drivers (video, input); this didn't make much of a difference to me. If in doubt just use the open-source radeon driver (e.g. move your /etx/X11/xorg.conf out of the way, or delete it).

---

### Post by AIPHEE on 2012-07-11
Well, only think i had from that downgrade is dpkg brakege. Im using OS drivers now, but AFAIK they cant downclock and i would like to play HoN and Zero-k sometimes (also psychonauts are in front of me). Well, i guess ill just wait for official drivers and will be switching to Win for games.

---

### Post by cYbercOsmOnauT on 2012-07-23
The patch works for me for Kernel 3.5 but I have another problem. When I create and install the debs from the ati......run file everything works fine but Unity 3D is gone. I always just get Unity 2D. When I use fglrx 8.960 from the repository (which does not support Kernel 3.5) Unity is working in 3D mode. Is there any ways for me to fix this? What is the great difference between the debs from the repository and the ones created out of the .run file? Btw I use Ubuntu 12.04 but I need 27 more posts before I can change my details. ;)

---

### Post by jfernyhough on 2012-07-23
Need a bit more info. What card do you have? (You need a different driver if you have a Radeon 2000, 3000, or 4000-series card.)

---

### Post by cYbercOsmOnauT on 2012-07-23
Sure
```
tekin@Ubuntu-Studio:~$ fglrxinfo 
display: :0  screen: 0
OpenGL vendor string: Advanced Micro Devices, Inc.
OpenGL renderer string: ATI Mobility Radeon HD 4500 Series
OpenGL version string: 3.3.11627 Compatibility Profile Context
```

---

### Post by cYbercOsmOnauT on 2012-07-23
AFAIK the 4500 series are supported and not inside the legacy support.

---

### Post by jfernyhough on 2012-07-23
> **cYbercOsmOnauT said:**
> AFAIK the 4500 series are supported and not inside the legacy support.You need the legacy driver for 12.6 and up: [http://support.amd.com/us/kbarticles/Pages/catalyst126legacyproducts.aspx](http://support.amd.com/us/kbarticles/Pages/catalyst126legacyproducts.aspx)

The kernel 3.5 patch should still work, but I haven't tried it with the legacy driver. ;)

---

### Post by cYbercOsmOnauT on 2012-07-24
> **jfernyhough said:**
> You need the legacy driver for 12.6 and up: [http://support.amd.com/us/kbarticles/Pages/catalyst126legacyproducts.aspx](http://support.amd.com/us/kbarticles/Pages/catalyst126legacyproducts.aspx)

The kernel 3.5 patch should still work, but I haven't tried it with the legacy driver. ;)
I already tried the normal driver. Everything works fine. Just Unity doesn't allow 3D mode.
But okay. Let me try out the legacy one. If that one also doesn't work I will need to stay at the fglrx from the repository and Kernel 3.3.x :'(

---

### Post by ELD on 2012-07-24
If it doesn't allow unity 3D then something is wrong...and you do need the legacy driver as the support for your card was removed from non-legacy he wasn't telling you to use legacy driver for nothing ;)

---

### Post by jfernyhough on 2012-08-16
Good news, everyone!

12.8 has just been released. No more xserver 1.12 crash for amd64 and patches for kernel 3.4 have been included.

So you only need to patch for 3.5! Woo!

Linky: [http://www2.ati.com/drivers/linux/amd-driver-installer-12.8-x86.x86_64.zip](http://www2.ati.com/drivers/linux/amd-driver-installer-12.8-x86.x86_64.zip)

---

### Post by LacerdaPT on 2012-08-21
Hi.

I am using ubuntu 12.04 (precise) under a kernel 3.5.

I'd like to install catalyst 12.8. ok I patched, no problem.

when it comes to build the packages your instrutions state to build them to Ubuntu/quantal. I couldn't do this, and I copied the content os /temp/amd/packages/Ubuntu/dists/precise to  /temp/amd/packages/Ubuntu/dists/quantal, as someone refer on a previous post. This did work.

well, I'm using precise, should I be build to precise instead of to quantal?

Cheers

---

### Post by jfernyhough on 2012-08-21
> **LacerdaPT said:**
> Hi.

I am using ubuntu 12.04 (precise) under a kernel 3.5.
[snip]
> well, I'm using precise, should I be build to precise instead of to quantal?Yes. ;)

---

### Post by woodsman4 on 2012-08-27
> **jfernyhough said:**
> OK, so until we're able to edit posts new details are here.

**This is only for Radeons from series 5000 onwards.**

Credit for patch collection to Vi0L0 at Arch, 3.5 patch credited to Enrico Tagliavini.
[B]
In summary:[/B]
0) Preparation
1) Download and extract [12.6 from AMD]("http://www2.ati.com/drivers/linux/amd-driver-installer-12-6-x86.x86_64.run").
2) Apply the patches from catalyst-hook attached [here]("http://catalyst.apocalypsus.net/tarball/0_TESTING/catalyst-hook.tar.gz").[URL="http://ati.cchtml.com/attachment.cgi?id=464"]
[/URL] 3) Build packages
4) Install

**Details:**
0) If this is the first time you've done this, install the necessary  development packages  (normally installed by the installer, if any are  missing they will be identified in step 3):
$ sudo apt-get install build-essential debhelper  dh-modaliases execstack

1) Once downloaded extract the installer files so we can patch  manually:
$ sh ./amd-driver-installer-12-6-x86.x86_64.run --extract ~/temp/amd

2) Download, copy into ~/temp/amd, and apply the attached patches (taken from Vi0L0's catalyst-hook test):[URL="http://ati.cchtml.com/attachment.cgi?id=464"]
[/URL]$ cd ~/temp/amd
$ patch -p1 <./3.4.patch
$ patch -p1 <./3.5-do_mmap.patch

3) Build the packages (this will place the packages in the parent directory):
$ ./ati-installer.sh 8.980 --buildpkg Ubuntu/quantal

4) Change to the parent directory and install the debs:
$ cd ..
$ sudo dpkg -i *.deb

any word on whether this will work with the 12.6 legacy driver?

---

### Post by yaji on 2012-09-02
I tried it with 12.6.legacy and I got:

```
patch -p1 <./3.4.patch
patching file common/lib/modules/fglrx/build_mod/firegl_public.c
Hunk #1 succeeded at 191 with fuzz 2 (offset 3 lines).
**Hunk #2 FAILED at 4160.**
1 out of 2 hunks FAILED -- saving rejects to file common/lib/modules/fglrx/build_mod/firegl_public.c.rej
patching file common/lib/modules/fglrx/build_mod/kcl_ioctl.c
patch unexpectedly ends in middle of line
Hunk #1 succeeded at 220 with fuzz 1 (offset 3 lines).

```

and

```
patch -p1 <./3.5-do_mmap.patch
patching file common/lib/modules/fglrx/build_mod/firegl_public.c
Hunk #1 succeeded at 2142 (offset 36 lines).
Hunk #2 succeeded at 2159 (offset 36 lines).
Hunk #3 succeeded at 2176 (offset 36 lines).
Hunk #4 succeeded at 2189 (offset 36 lines).

```

Will it work ?

---

### Post by jfernyhough on 2012-09-02
Install it and find out. ;)

You can always install the version from the repository. :)

---

### Post by yaji on 2012-09-03
Its working :)

---

### Post by neon2k8 on 2012-09-03
Hello everyone. I followed all the steps described for patching but used 12.6 legacy drivers (I have a Mobility Radeon 4330 graphics card). Instead of "./ati-installer.sh 8.98 etc." I only got an "ati-installer.sh" file so i used this for building quantal package. Problem is that:
Quantal didn't exist in dists folders so i tried " --buildpkg Ubuntu/precise" but again nothing.... all i get is this:

Unrecognized parameter 'Ubuntu/precise' to ati-installer.sh
This script supports the following arguments:
--help                                        : print help messages
--listpkg                                     : print out a list of generatable packages
--buildpkg [package] [--dryrun]               : if generatable, the package will be created
--buildandinstallpkg [package] [--dryrun] [--force] : if generatable, the package will be creadted and installed
--install     

Please help, everything seemed to be ok, patching and everything, I just stuck at that last step!!!! Did I do something wrong?

---

### Post by jfernyhough on 2012-09-03
> **neon2k8 said:**
> Hello everyone. I followed all the steps described for patching but used 12.6 legacy drivers (I have a Mobility Radeon 4330 graphics card). No, you didn't. But never mind. Let's step through.

> Instead of "./ati-installer.sh 8.98 etc." I only got an "ati-installer.sh" file so i used this for building quantal package. The command is correct. You need all three elements: the executable, the driver version, and the distribution. Otherwise the command will not run.

> Problem is that:
Quantal didn't exist in dists folders so i tried " --buildpkg Ubuntu/precise" This doesn't matter. As far as I can tell Ubuntu/quantal uses the files from Ubuntu/source. Ubuntu/precise should work fine but there may be tweaks specifically for package versions in Precise (this is why I specify quantal, YMMV).

> but again nothing.... all i get is this:

Unrecognized parameter 'Ubuntu/precise' to ati-installer.shThis is because ati-installer.sh needs two arguments: the driver version and the distribution.

> Please help, everything seemed to be ok, patching and everything, I just stuck at that last step!!!! Did I do something wrong?
Try again but use the correct command.

---

### Post by ashwinrao on 2012-09-04
I'm struggling with Radeon HD 4250 with Ubuntu 12.10. Any idea this method would work for me? 
```
~$ lspci -v | grep -i vga
01:05.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI RS880 [Radeon HD 4250] (prog-if 00 [VGA controller])

```Tried with the method but still no good.  Graphics identified as VESA: RS880 in my machine. Display option is 'Laptop' and only has two modes. How can I achieve higher resolutions and have proper display driver?

I didn't had any issues with Ubuntu precise version and amdcccle works fine in it.

---

### Post by ashwinrao on 2012-09-05
Got the desired resolutions using xorg.conf file with Vesa driver. However, I'm still wondering whether any chance of getting proprietary AMD drivers with 12.10 for Radeon HD 4250 in future?

---

### Post by defconoii on 2012-09-06
> **ashwinrao said:**
> Got the desired resolutions using xorg.conf file with Vesa driver. However, I'm still wondering whether any chance of getting proprietary AMD drivers with 12.10 for Radeon HD 4250 in future?

I'd like to know this too :)

---

### Post by tienvx on 2012-09-07
> **ashwinrao said:**
> Got the desired resolutions using xorg.conf file with Vesa driver. However, I'm still wondering whether any chance of getting proprietary AMD drivers with 12.10 for Radeon HD 4250 in future?
I have Radeon HD Mobility 4250 too.
Catalyst 12.6 legacy work with Ubuntu 12.10 beta 1 by downgrade xserver to 1.11 (precise).
But I have very annoying bug: when play movie with totem, every go in/out of fullscreen mode, the screen is flicker, and the same problem when playback menu appear and disappear in fullscreen mode. I try some settings in compiz config settings manager but no luck.

Sorry for my English! Please fix me!

---

### Post by ashwinrao on 2012-09-08
In my case, I had to purge all the instances of **fglrx **and go with the custom built xorg.conf file with VESA driver.  It gives the desired resolutions. However, the experience is not good enough. Waiting for some one with more knowledgeable person to crack this..please.

---

### Post by scruffyeagle on 2012-09-09
> **Salane said:**
> ~/temp/amd$ patch -p1 <./patch_to_fix_compiling_fglrx_12.4_with_linux_3.4.patch
patching file common/lib/modules/fglrx/build_mod/firegl_public.c
patching file common/lib/modules/fglrx/build_mod/kcl_ioctl.c
patch unexpectedly ends in middle of line
Hunk #1 succeeded at 217 with fuzz 1.

and when I go to the next step I get this. 
./ati-installer.sh 8.961 --buildpkg Ubuntu/quantal=====================================================================
 AMD Catalyst(TM) Proprietary Driver Installer/Packager 
=====================================================================
Generating package: Ubuntu/quantal
Error: Distro Version entered incorrectly or not supported, use --listpkg to identify valid distro versions
Error: Distro Version entered incorrectly or not supported, use --listpkg to identify valid distro versions

But no Quantal in --listpkg

Ubuntu Packages:
        Ubuntu/gutsy
        Ubuntu/hardy
        Ubuntu/intrepid
        Ubuntu/jaunty
        Ubuntu/karmic
        Ubuntu/lucid
        Ubuntu/maverick
        Ubuntu/natty
        Ubuntu/oneiric
        Ubuntu/source
        Ubuntu/precise

I copied /temp/amd/packages/Ubuntu/dists/precise to /temp/amd/packages/Ubuntu/dists/quantal and tried again. Further Errors were fixed by installing the following.
sudo apt-get install dpkg-dev debhelper  dh-modaliases execstack

Dep errors on install of created deb files were fixed by
  sudo apt-get -f install

after reboot
glxinfo
name of display: :0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: ATI
server glx version string: 1.4

If this was exactly as it was entered into your system, there's probably a problem re. that 1st line; i.e., a typo, inserting a space between the "p" & the "a" in the word "patch".

---

### Post by jfernyhough on 2012-09-09
> **scruffyeagle said:**
> If this was exactly as it was entered into your system, there's probably a problem re. that 1st line; i.e., a typo, inserting a space between the "p" & the "a" in the word "patch".It wasn't. The patch went fine. The issue was he was trying to build for quantal on a precise box (which he mentioned two posts later). It's also a bit out-of-date as the patch was necessary for kernel 3.4 support. AMD have since added this to their driver so we only need to patch for kernel 3.5.

---

### Post by jfernyhough on 2012-09-10
There are new packages available for fglrx 8.982 (Catalyst 12.8 ):

[https://launchpad.net/ubuntu/quantal/+source/fglrx-installer/2:8.982-0ubuntu1](https://launchpad.net/ubuntu/quantal/+source/fglrx-installer/2:8.982-0ubuntu1)
[https://launchpad.net/ubuntu/quantal/+source/fglrx-installer-updates/2:8.982-0ubuntu1](https://launchpad.net/ubuntu/quantal/+source/fglrx-installer-updates/2:8.982-0ubuntu1)

This should make manual patching unnecessary. Note that there's no support yet for xserver 1.13 (X ABI support is still at 11).

---

### Post by deeinmetrodc on 2012-09-10
I'm frustrated I have an amd 6520g chipset and i very much want the amd driver for my laptop but the launchpad drivers do not appear to be working.  The 12.6 drivers crash on start-up - compiz won't work.  The 12.8 drivers won't install with an unmet dependency for for an ab11 file from xorg that's not in the repository.

I very much want the unity 3d of ubuntu but if i can't have my  amd drivers and moonlight (that's the next bug in my butt to work on)  then I feel ubuntu just isn't the thing.

Ya know?

I tried to patch the driver but that din't turn out well.  I used to be pretty good at building packages.

the fglxr packages in synaptic give me a red arrow beside them and won't install because of broken packages.  i uninstalled the ati and radeon xorg nonsense that i was sure would conflict.  nothing helps.

Some one throw me a lifeline here please....

---

### Post by deeinmetrodc on 2012-09-10
Ya know what, never mind.  I installed precise and used the launchpad amd drivers and that worked so I am happy with that.

---

### Post by QIII on 2012-09-10
> **ashwinrao said:**
> Got the desired resolutions using xorg.conf file with Vesa driver. However, I'm still wondering whether any chance of getting proprietary AMD drivers with 12.10 for Radeon HD 4250 in future?

For several years AMD/ATI has made sure that the xx.4 and xx.10 drivers have worked for Ubuntu and made them available for Canonical to get them in the repo about the time of the RC.  As one writer put it, you can bet AMD will do whatever they need to do to meet Ubuntu's needs.

I hope it continues and we can expect Catalyst 12.10 to work just fine.  We wouldn't want AMD to deprive Phoronix of their semi-annual article complaining about Ubuntu getting the goods before anyone else!  ;)

---

### Post by ashwinrao on 2012-09-11
Thanks a lot for your clarification. Will wait for the official Ubuntu AMD drivers. 12.10 is additional OS I have installed for testing purpose. The main OS in my machine is 12.04.

---

### Post by ecolom1269 on 2012-09-14
add me to the list of radeon 4250ers with no 3d graphics capibility: ( its a shame cuz there are lots and lots of great active desktops out there for ubunto 12.04 lts.
 
the radeon 4200 series is listed as compatible in the open source support but I don't know how to install the open source PPA driver :( 
 
[COLOR=red]does anyone have the steps??? ... instructions i read are killing me.[/COLOR]
 
I am new to PPA drivers. unless someone has a depository way?](*,)really would like to blow my wifes desktop away with some killer graphics until I can, I will never get her off of a windows machine.

---

### Post by suprman2020 on 2012-09-15
Looks like Catalyst 12.9 is out. [http://www.phoronix.com/scan.php?page=news_item&px=MTE4NDk](http://www.phoronix.com/scan.php?page=news_item&px=MTE4NDk)

Has anybody tried it?

---

### Post by nardusg on 2012-09-17
Did not work for me. It is for embedded devices apparently. I am on HD6xxx

---

### Post by jfernyhough on 2012-09-17
Before anyone asks: Catalyst 12.9 is not compatible with cards earlier than HD5000.

If it doesn't work with your (HD5000 or later) hardware try the control file from here: [http://catalyst.apocalypsus.net/files/control-12.8/](http://catalyst.apocalypsus.net/files/control-12.8/) 

and read Arch AUR page here: [https://aur.archlinux.org/packages.php?ID=34773](https://aur.archlinux.org/packages.php?ID=34773)

There is reported support for kernel 3.5 and early 3.6rc, which is nice. No xserver 1.13 support.

My progress:
Downloaded installer and built the debs. **done**
$ sh ./amd-driver-installer-9.00-x86.x86_64.run --buildpkg Ubuntu/quantal
Packages generated. **done**
Install and DKMS module build. **done**
$ sudo dpkg -i *.deb
Reboot. **done**

OK, so it installs, builds, and loads fine for me with xserver 1.12 and kernel 3.5. I have a lovely "Unsupported hardware" watermark but I guess the 12.8 control file will sort that out. Now to download and test kernel 3.6-rc6!

Rebooted and running successfully with kernel 3.6-rc6, and with the 12.8 control file copied to /etc/ati/control the watermark is gone.

**Success!**

---

### Post by jfernyhough on 2012-09-26
Catalyst 12.9 beta is out: 
[http://www2.ati.com/drivers/beta/amd-driver-installer-12-9-beta-x86.x86_64.zip](http://www2.ati.com/drivers/beta/amd-driver-installer-12-9-beta-x86.x86_64.zip)

Downloading now. :)

Packages build, install, DKMS look fine as for the embedded release. Let's see if a reboot leads to a watermark...

--edit
Nope, watermark is back. Same procedure to fix, copy across the 12.8 control file.

---

### Post by odror on 2012-09-26
> **jfernyhough said:**
> Catalyst 12.9 beta is out: 
[http://www2.ati.com/drivers/beta/amd-driver-installer-12-9-beta-x86.x86_64.zip](http://www2.ati.com/drivers/beta/amd-driver-installer-12-9-beta-x86.x86_64.zip)

Downloading now. :)

Is this compatible with ubuntu 12.10 ?

The one in the ppa and the repo is'nt

---

### Post by jfernyhough on 2012-09-26
I doubt it. It has the same number (9.000) as the embedded release. For full support we'll probably have to wait for Catalyst 12.10 around the release date of Quantal.

--edit
I thought that perhaps the embedded and beta releases might be the same so I checked the md5sum for each:

e643cad1cb458e8bb179cc837d7cd513  amd-driver-installer-9.00-x86.x86_64.run
7754c50a19e8402b5863d2061bae5482  amd-driver-installer-12-9-beta-x86.x86_64.run

Different, so probably some minor changes.

--edit 2
Just three files changed in /etc/ati to support more GPUs [[1]("https://bbs.archlinux.org/viewtopic.php?pid=1166894#p1166894")]:
amdpcsdb.default  control  signature

--edit 3
Changelog:
[http://support.amd.com/us/kbarticles/Pages/AMDCatalyst129betadriver.aspx](http://support.amd.com/us/kbarticles/Pages/AMDCatalyst129betadriver.aspx)

---

### Post by jfernyhough on 2012-09-27
I tried upgrading to xserver 1.13. Not working, as expected.

I had to go through Launchpad and manually select debs to get X running again. I've bundled them together in case it's useful for someone else:

[https://dl.dropbox.com/u/172275/xorg-xserver-1.12.amd64.tar.xz](https://dl.dropbox.com/u/172275/xorg-xserver-1.12.amd64.tar.xz)

Just extract somewhere and
$ sudo dpkg -i *.deb

---

### Post by Ubunterrific on 2012-09-27
> **jfernyhough said:**
> I tried upgrading to xserver 1.13. Not working, as expected.

I had to go through Launchpad and manually select debs to get X running again. I've bundled them together in case it's useful for someone else:

[https://dl.dropbox.com/u/172275/xorg-xserver-1.12.amd64.tar.xz](https://dl.dropbox.com/u/172275/xorg-xserver-1.12.amd64.tar.xz)

Just extract somewhere and
$ sudo dpkg -i *.deb

Exemplary assistance. I was debating waiting until an xserver 1.13 compatible version for my Mobility Radeon 4200 HD card but i guess i could downgrade for now and get the power management perks that come with fglrx. 

I've tried all manner of things like disabling kernel modesetting, creating an xorg.conf with ClockGating and ForceLowPowerMode, to no avail. Idle, the radeon module is great but it loves creeping up about 20 degrees whereas fglrx stays consistently around 55 degrees. Shame really, because that's the only real issue i have with the open source driver; it looks great visually.

Do you know what the situation is going to be for pre-5000 cards: are the repos going to contain an 'fglrx' package and something like 'fglrx-legacy' for the 'legacy' (ha!) cards?

---

### Post by jfernyhough on 2012-09-27
New fglrx packages from Alberto Milone: [https://launchpad.net/ubuntu/quantal/+source/fglrx-installer/2:9.000-0ubuntu1](https://launchpad.net/ubuntu/quantal/+source/fglrx-installer/2:9.000-0ubuntu1)

The second bullet-point of the changelog is tantalising... :D

Must try 1.13 again.

```

* New upstream release (LP: #1032672).
  * debian/dkms.conf.in:
    - Do not apply any kernel patch.
  * debian/rules:
    - Make it possible to set the xserver ABIs in debian/substvars.
  * Merge fixes from the upstream installer:
    - Fix openCL issues running x86 binaries on x86_64.
    - Make sure that dh_shlibdeps doesn't complain about missing qt
      libraries.
```> Do you know what the situation is going to be for pre-5000 cards: are the repos going to contain an 'fglrx' package and something like 'fglrx-legacy' for the 'legacy' (ha!) cards? I don't know; I assume something similar to the Nvidia system would be adopted with an fglrx-current and fglrx-legacy.

> Exemplary assistance.I may call on you to support an Ubuntu membership application next time I apply. ;) :lolflag:

--edit
Just got an email from Launchpad, this update fixes bug 1032672 ("fglrx-updates broken dependency with xorg-video-abi-12"): [https://bugs.launchpad.net/bugs/1032672](https://bugs.launchpad.net/bugs/1032672)

This is looking good. :D

--edit 2
Arg, package builds in one hour. :( Well, I guess I'll try to build it from the source. :)

--edit 3
Hmm, pbuilder made that easier than builds I've done before. I like it. 8 minutes to official build, but I want to try my own build. :D

--edit 4
Success! xserver 1.13 running! :D

amd64 packages are built, so have at it! [https://launchpad.net/ubuntu/+source/fglrx-installer/2:9.000-0ubuntu1/+build/3860478](https://launchpad.net/ubuntu/+source/fglrx-installer/2:9.000-0ubuntu1/+build/3860478)
i386 are coming in 45 mins: [https://launchpad.net/ubuntu/+source/fglrx-installer/2:9.000-0ubuntu1/+build/3860479](https://launchpad.net/ubuntu/+source/fglrx-installer/2:9.000-0ubuntu1/+build/3860479)

---

### Post by Ubunterrific on 2012-09-27
Well aren't you bursting with life? XD :p

Excellent! Love to see progress trickling down from upstream :D

Now before i go getting too pleased - would i be right in thinking that fglrx 9.000-0ubuntu1 is not going to work for pre-5000 gpus? Is amd planning on releasing a separate fglrx legacy with xserver 1.13 compatibility, or can i run this new version? 

OR is this new revision to the code  "- Make it possible to set the xserver ABIs in debian/substvars." (and others of course, this one being paramount to dependency corrections) to be carried over into the legacy version, and all we pre-5000 users have to do is simply wait until this has been done shortly?

---

### Post by jfernyhough on 2012-09-27
As far as i know fglrx 9.00 doesn't work with pre-HD5000 cards. I'm not sure what AMDs plans are, there's not been anything recently from Andrew D ([https://twitter.com/CatalystCreator/](https://twitter.com/CatalystCreator/)) except notifying about the latest legacy release for Windows 8 which is still based on the 12.6 legacy beta...

---

### Post by erickwill on 2012-09-28
> **jfernyhough said:**
> As far as i know fglrx 9.00 doesn't work with pre-HD5000 cards. I'm not sure what AMDs plans are, there's not been anything recently from Andrew D ([https://twitter.com/CatalystCreator/](https://twitter.com/CatalystCreator/)) except notifying about the latest legacy release for Windows 8 which is still based on the 12.6 legacy beta...

Hi, sorry for my newb question, but so, this new driver supposed to don't work on a Mobility HD 4650?
Thanks

---

### Post by Ubunterrific on 2012-09-28
> **erickwill said:**
> Hi, sorry for my newb question, but so, this new driver supposed to don't work on a Mobility HD 4650?
Thanks


I'm afraid this new version doesn't work on pre-HD5000 gpus (i tested it quickly to be absolutely sure), sorry :( Does that mean a legacy version will be released by amd soon? who knows. We need x 1.13 support (and kernel 3.5 support of course) in the next legacy module or we'll have to make do as is.

Anyone know when the next legacy driver is due? Some time in october? Hopefully before prime time for ubuntu 12.10 :)

---

### Post by odror on 2012-09-29
I have installed the new driver. It is working fine.

but catalyst does not work. When I type
amdcccle

Nothing happens.

Any ideas why

Thanks

---

### Post by luk1don on 2012-09-29
Is there support for xserver 1.13? I don't think so.
Drivers are suitable for the Ubuntu 12.10 and kernel but not to the newest xserver...

---

### Post by luk1don on 2012-09-29
NVIDIA drivers support X.org 1.13...

---

### Post by luk1don on 2012-09-29
OK. I take that back:P
Drivers from Quantal repositories works like a charm and looks like supports xserver version.

---

### Post by jfernyhough on 2012-09-29
> **odror said:**
> When I type
amdcccle

Nothing happens.I'm assuming you have amdcccle installed? There are two fglrx packages, one with the driver, one with the control panel.

---

### Post by rbrick49 on 2012-09-29
mine is working fine except for scaling,I have to go back to catalyst and reajust scaling to get full screen

---

### Post by erickwill on 2012-09-29
Any news about ATI RADEON Mobility HD 4XXX drivers? Bit old huh? But anyways.. we can't upgrade a laptop video card.. :D

---

### Post by odror on 2012-09-29
> **jfernyhough said:**
> I'm assuming you have amdcccle installed? There are two fglrx packages, one with the driver, one with the control panel.

I found the problem. I had two version of that file. one in /usr/local/bin that took precedence.

---

### Post by exploder on 2012-09-29
I have an HP DV6 laptop that has ATI discrete graphics or whatever they call it. I had problems with installing the proprietary drivers in 12.04, they would fail and even when I got them installed there were issues remaining. One of the processor cores kept spiking and there were weird issues with menus displaying strange at random.

I installed 12.10 beta 2 on the laptop a couple of days ago. The proprietary drivers installed without issue and the problems I saw in 12.04 are gone. Everything seems very stable and consistent now, memory use is a bit higher but that may change seeing that 12.10 still has a ways to go before the final release.

Something I should mention, when using the open source ATI drivers there was a problem with not being able to get to the greeter every few boots, it would just sit there with a purple screen... In 12.04 I would get 9 garbled images of the greeter. In either case the proprietary drivers were needed to have things working reliably. 

I do not know why Canonical decided to put hardware drivers in the software sources, this might make things more difficult for new users. Both the open source NVidea and ATI drivers are just not mature enough in my opinion to use, there are just too many issues remaining with them.

12.10 seems to be the answer to the problems I was having on my laptop and I do like most of the refinements that have been made to Unity.

---

### Post by Ubunterrific on 2012-10-02
> **erickwill said:**
> Any news about ATI RADEON Mobility HD 4XXX drivers? Bit old huh? But anyways.. we can't upgrade a laptop video card.. :D

That's what i'm using. When i tested fglrx last (about a week ago), at the time i did have a screwed up xorg.conf i was testing (back when i was testing radeon without kernel modesetting), and i did have problems, but that may have been why. 
If you try the sudo aticonfig --initial command you're encouraged to do when you first install fglrx, i get something like 'no suitable adapters found'. 

So is the bottom line that this new fglrx DOES work for pre-HD5000 gpus BUT you lose out by having no CCC? Bit silly...:p

I checked again by installing fglrx and fglrx-amdcccle, it's no dice, the fglrx module doesn't get loaded, it falls back onto vesa which has even worse performance than radeon.

---

### Post by MadNachos on 2012-10-02
The new version that was recently made available works very well on my rig with a HD6870 with dual displays. Very nice.

---

### Post by odror on 2012-10-02
> **MadNachos said:**
> The new version that was recently made available works very well on my rig with a HD6870 with dual displays. Very nice.

Do you have the issue of the CPU jumping to 100% when the display is sleeping. I have that issue with the 6850. The other issue is that unity is sluggish (It is worse when I add the 4th display)

---

### Post by QIII on 2012-10-04
12.9 Beta driver still works like doo-doo on Xubuntu with Compiz and 3D effects.  All sorts of artifacts and freezes.

---

### Post by yaji on 2012-10-10
Ok, it seems that quantal's fglrx does not work withmy graphic card. How dose one use opensource radeon driver? I removed the blob, then installed xserver-xorg-video-radeon package, and then replaced fglrx with radeon in my xorg.conf file. But after runing 
```
glxinfo | grep "renderer string"

```

I got:

```
OpenGL renderer string: Gallium 0.4 on llvmpipe (LLVM 0x301)

```

The performacne is horrid, screen resolution is wrong, and Additionak Drivers tab is empty. Help.

edit.

Stupid me, it looks like i blacklisted radeon driver some time ago...

---

