---
title: "Catalyst 12.2 released (fglrx 8.950)"
date: 2012-03-07
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by jfernyhough on 2012-03-07
Download:
[http://www2.ati.com/drivers/linux/amd-driver-installer-12-2-x86.x86_64.run](http://www2.ati.com/drivers/linux/amd-driver-installer-12-2-x86.x86_64.run)

As normal, I run:

$ chmod +x amd-driver-installer-12-2-x86.x86_64.run
$ ./amd-driver-installer-12-2-x86.x86_64.run --buildpkg Ubuntu/precise
$ sudo dpkg -i *.deb

then copy the .debs somewhere for safekeeping.

Builds OK, installs OK.

To the reboot button!

-edit
[s]Arg. Not working. For any kernel (3.2.0-18, mainline 3.3-rc6, Liquorix 3.2.9).[/s]
```

$ glxinfo
name of display: :0
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  139 (ATIFGLEXTENSION)
  Minor opcode of failed request:  66 ()
  Serial number of failed request:  13
  Current serial number in output stream:  13

```Normally reinstalling under the running kernel sorts this. Going to try another reboot just to make certain.

--edit 2
OK, so DKMS will build it correctly for 3.2.0-18 while running 3.2.0-18. Apparently DKMS can't find the headers for any other kernel despite them being installed. Hmm.

So yeah, working for the Ubuntu kernel.

---edit 3
OK, so I managed somehow not to install both kernel header .debs (both -amd64.deb and -all.deb). After I installed them DKMS builds the fglrx module correctly. Gah.

---

### Post by zika on 2012-03-07
> **jfernyhough said:**
> Download:
[http://www2.ati.com/drivers/linux/amd-driver-installer-12-2-x86.x86_64.run](http://www2.ati.com/drivers/linux/amd-driver-installer-12-2-x86.x86_64.run)

As normal, I run:

$ chmod +x amd-driver-installer-12-2-x86.x86_64.run
$ ./amd-driver-installer-12-2-x86.x86_64.run --buildpkg Ubuntu/precise
$ sudo dpkg -i *.deb

then copy the .debs somewhere for safekeeping.

Builds OK, installs OK.

To the reboot button!

-edit
Arg. Not working. For any kernel (3.2.0-18, mainline 3.3-rc6, Liquorix 3.2.9).
```

$ glxinfo
name of display: :0
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  139 (ATIFGLEXTENSION)
  Minor opcode of failed request:  66 ()
  Serial number of failed request:  13
  Current serial number in output stream:  13

```Normally reinstalling under the running kernel sorts this. Going to try another reboot just to make certain.
```
[COLOR=Black]sudo [/COLOR][COLOR=Black]aticonfig --initial[/COLOR]
```no more?
It was long ago that I've used ATI driver... ;)

---

### Post by kaldor on 2012-03-07
> **zika said:**
> ```
[COLOR=Black]sudo [/COLOR][COLOR=Black]aticonfig --initial[/COLOR]
```no more?
It was long ago that I've used ATI driver... ;)

I believe it's no longer needed, yeah.

---

### Post by jfernyhough on 2012-03-07
I always forget about aticonfig. I think I ran it the first time I installed fglrx and haven't touched my xorg.conf since. If fglrx isn't working it's always worth a go doing $ sudo aticonfig --initial

---

### Post by ratcheer on 2012-03-07
I installed it in Oneiric, it's working great. Now to install it in Precise. Then, I'll have to wait for a new package for my Arch Linux.

Thanks!

Tim

---

### Post by ratcheer on 2012-03-07
Uh oh! The run file is failing in Precise.

Here are the messages:

```
Generating package: Ubuntu/oneiric
apt 0.8.16~exp12ubuntu5 for amd64 compiled on Mar  6 2012 17:02:43
Usage: apt-get [options] command
       apt-get [options] install|remove pkg1 [pkg2 ...]
       apt-get [options] source pkg1 [pkg2 ...]

apt-get is a simple command line interface for downloading and
installing packages. The most frequently used commands are update
and install.

Commands:
   update - Retrieve new lists of packages
   upgrade - Perform an upgrade
   install - Install new packages (pkg is libc6 not libc6.deb)
   remove - Remove packages
   autoremove - Remove automatically all unused packages
   purge - Remove packages and config files
   source - Download source archives
   build-dep - Configure build-dependencies for source packages
   dist-upgrade - Distribution upgrade, see apt-get(8)
   dselect-upgrade - Follow dselect selections
   clean - Erase downloaded archive files
   autoclean - Erase old downloaded archive files
   check - Verify that there are no broken dependencies
   changelog - Download and display the changelog for the given package
   download - Download the binary package into the current directory

Options:
  -h  This help text.
  -q  Loggable output - no progress indicator
  -qq No output except for errors
  -d  Download only - do NOT install or unpack archives
  -s  No-act. Perform ordering simulation
  -y  Assume Yes to all queries and do not prompt
  -f  Attempt to correct a system with broken dependencies in place
  -m  Attempt to continue if archives are unlocatable
  -u  Show a list of upgraded packages as well
  -b  Build the source package after fetching it
  -V  Show verbose version numbers
  -c=? Read this configuration file
  -o=? Set an arbitrary configuration option, eg -o dir::cache=/tmp
See the apt-get(8), sources.list(5) and apt.conf(5) manual
pages for more information and options.
                       This APT has Super Cow Powers.
Unable to install dpkg-dev.  Please manually install and try again.
Package build failed!
Package build utility output:
./packages/Ubuntu/ati-packager.sh: 294: ./packages/Ubuntu/ati-packager.sh: debclean: not found
./packages/Ubuntu/ati-packager.sh: 295: ./packages/Ubuntu/ati-packager.sh: dpkg-buildpackage: not found
./packages/Ubuntu/ati-packager.sh: 294: ./packages/Ubuntu/ati-packager.sh: debclean: not found
./packages/Ubuntu/ati-packager.sh: 295: ./packages/Ubuntu/ati-packager.sh: dpkg-buildpackage: not found
Removing temporary directory: fglrx-install.UYoHYc
```

Something seems to be missing. Any ideas how to fix this?

Tim

---

### Post by ratcheer on 2012-03-07
Dern! My 12.10 system was apparently missing all of the dpkg stuff. I installed dpkg-dev which installed a lot of packages.

I'll try the amd run file, again.

Tim

---

### Post by ratcheer on 2012-03-07
Nope. It's still a mess. I'll go look in the Precise forum and see what I can find.

Oh. This is the Precise forum.
[B]
Does anyone know what my system is missing and how I can fix it?[/B]

Tim

---

### Post by jfernyhough on 2012-03-07
Are you building the precise package or the oneiric package? The log you posted suggests you're building the oneriric package in precise!

---

### Post by ratcheer on 2012-03-07
I am fairly sure I put "--buildpkg Ubuntu/precise". Although one time after it failed, I did try Ubuntu/oneiric to see if it would work. Maybe that is the one I posted the messages from, but the messages are the same no matter which way I run it.

I will run it again and post the command and all output:

```

tim@tim-Z68A-D3-B3:~/catalyst12.2$ sudo sh amd-driver-installer-12-2-x86.x86_64.run --buildpkg Ubuntu/precise
[sudo] password for tim: 
Created directory fglrx-install.E1enVh
Verifying archive integrity... All good.
Uncompressing AMD Catalyst(TM) Proprietary Driver-8.95....................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
=====================================================================
 AMD Catalyst(TM) Proprietary Driver Installer/Packager 
=====================================================================
Generating package: Ubuntu/precise
Resolving build dependencies...
apt 0.8.16~exp12ubuntu5 for amd64 compiled on Mar  6 2012 17:02:43
Usage: apt-get [options] command
       apt-get [options] install|remove pkg1 [pkg2 ...]
       apt-get [options] source pkg1 [pkg2 ...]

apt-get is a simple command line interface for downloading and
installing packages. The most frequently used commands are update
and install.

Commands:
   update - Retrieve new lists of packages
   upgrade - Perform an upgrade
   install - Install new packages (pkg is libc6 not libc6.deb)
   remove - Remove packages
   autoremove - Remove automatically all unused packages
   purge - Remove packages and config files
   source - Download source archives
   build-dep - Configure build-dependencies for source packages
   dist-upgrade - Distribution upgrade, see apt-get(8)
   dselect-upgrade - Follow dselect selections
   clean - Erase downloaded archive files
   autoclean - Erase old downloaded archive files
   check - Verify that there are no broken dependencies
   changelog - Download and display the changelog for the given package
   download - Download the binary package into the current directory

Options:
  -h  This help text.
  -q  Loggable output - no progress indicator
  -qq No output except for errors
  -d  Download only - do NOT install or unpack archives
  -s  No-act. Perform ordering simulation
  -y  Assume Yes to all queries and do not prompt
  -f  Attempt to correct a system with broken dependencies in place
  -m  Attempt to continue if archives are unlocatable
  -u  Show a list of upgraded packages as well
  -b  Build the source package after fetching it
  -V  Show verbose version numbers
  -c=? Read this configuration file
  -o=? Set an arbitrary configuration option, eg -o dir::cache=/tmp
See the apt-get(8), sources.list(5) and apt.conf(5) manual
pages for more information and options.
                       This APT has Super Cow Powers.
Unable to resolve  dh-modaliases execstack.  Please manually install and try again.
Package build failed!
Package build utility output:
./packages/Ubuntu/ati-packager.sh: 294: ./packages/Ubuntu/ati-packager.sh: debclean: not found
dpkg-buildpackage: export CFLAGS from dpkg-buildflags (origin: vendor): -g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Wformat-security
dpkg-buildpackage: export CPPFLAGS from dpkg-buildflags (origin: vendor): -D_FORTIFY_SOURCE=2
dpkg-buildpackage: export CXXFLAGS from dpkg-buildflags (origin: vendor): -g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Wformat-security
dpkg-buildpackage: export FFLAGS from dpkg-buildflags (origin: vendor): -g -O2
dpkg-buildpackage: export LDFLAGS from dpkg-buildflags (origin: vendor): -Wl,-Bsymbolic-functions -Wl,-z,relro
dpkg-buildpackage: source package fglrx-installer
dpkg-buildpackage: source version 2:8.950-0ubuntu1
dpkg-buildpackage: source changed by AMD: Advanced Micro Devices. <http://ati.amd.com/support/driver.html>
 dpkg-source --before-build fglrx.jw7hFt
dpkg-buildpackage: host architecture amd64
 debian/rules build
#Create important strings
for i in 10fglrx \
             dkms.conf \
             fglrx.install \
             fglrx-dev.install \
             fglrx-dev.links \
             fglrx-amdcccle.install \
             fglrx.grub-gfxpayload \
             fglrx.dirs \
             fglrx.links \
             fglrx.postinst \
             fglrx.postrm \
             fglrx.preinst \
             fglrx.prerm \
             overrides/fglrx; do \
        sed -e "s|#PKGXMODDIR#|usr/lib/fglrx/xorg/modules|g" \
            -e "s|#LIBDIR#|usr/lib|g" \
            -e "s|#LIBDIR32#|usr/lib32|g" \
            -e "s|#BINDIR#|usr/bin|g" \
            -e "s|#SYSCONFDIR#|etc|g" \
            -e "s|#MANDIR#|usr/share/man/man1|g" \
            -e "s|#LDSOCONF#|usr/lib/fglrx/ld.so.conf|g" \
            -e "s|#ALTLDSOCONF#|usr/lib/fglrx/alt_ld.so.conf|g" \
            -e "s|#ALTPRIORITY#|1000|g" \
            -e "s|#PXALTPRIORITY#|900|g" \
            -e "s|#AUTOSTARTDIR#|etc/xdg/autostart|g" \
            -e "s|#DATADIR#|usr/share|g" \
            -e "s|#PKGDESKDIR#|usr/share/fglrx|g" \
            -e "s|#PKGDATADIR#|usr/share/fglrx|g" \
            -e "s|#PKGCONFIGDIR#|usr/lib/fglrx|g" \
            -e "s|#PKGBINDIR#|usr/lib/fglrx/bin|g" \
            -e "s|#PKGLIBDIR#|usr/lib/fglrx|g" \
            -e "s|#PKGLIBDIR32#|usr/lib32/fglrx|g" \
            -e "s|#PKGDRIVERSDIR#|usr/lib/fglrx/xorg|g" \
            -e "s|#XORGEXTRA#|usr/lib/x86_64-linux-gnu/xorg/extra-modules|g" \
            -e "s|#PKGEXTENSIONDIR#|usr/lib/fglrx/xorg|g" \
            -e "s|#XORGEXTENSIONSDIR#|usr/lib/xorg/modules/extensions|g" \
            -e "s|#DRIVERNAME#|fglrx|g" \
            -e "s|#DRIVERDEVNAME#|fglrx-dev|g" \
            -e "s|#DRIVERSRCNAME#||g" \
            -e "s|#INCLUDEDIR#|usr/include|g" \
            -e "s|#PKGLIBCONFDIR#|lib/fglrx|g" \
            -e "s|#GRUBBLKLISTDIR#|usr/share/grub-gfxpayload-lists/blacklist|g" \
            -e "s|#PKGXMODDIR#|usr/lib/fglrx/xorg/modules|g" \
            -e "s|#PXDIR#|usr/lib/pxpress|g" \
            -e "s|#PXDIR32#|usr/lib32/pxpress|g" \
            -e "s|#PXXMODDIR#|usr/lib/pxpress/xorg/modules|g" \
            -e "s|#PXDIRNAME#|pxpress|g" \
            -e "s|#PXLIBDIR#|usr/lib/pxpress/lib|g" \
            -e "s|#PXLIBDIR32#|usr/lib32/pxpress/lib|g" \
            -e "s|#PXLDSOCONF#|usr/lib/pxpress/ld.so.conf|g" \
            -e "s|#ALTPXLDSOCONF#|usr/lib/pxpress/alt_ld.so.conf|g" \
            -e "s|#CVERSION#|8.950|g" \
            -e "s|#SRCXARCH#|xpic_64a|g" \
            -e "s|#SRCARCH#|x86_64|g" \
            -e "s|#SRCLIBDIR#|lib64|g" \
            -e "s|#DEB_HOST_MULTIARCH#|x86_64-linux-gnu|g" \
            -e "s|#OTHER_ARCH#|i386-linux-gnu|g" \
            debian/$i.in > debian/$i;      \
    done
# remove exec bit on everything
find arch \
        etc \
        lib \
        module \
        usr \
        xpic_64a     -type f | xargs chmod -x
find: `module': No such file or directory
# set executable on user apps
find arch/x86_64/usr/sbin \
        arch/x86_64/usr/X11R6/bin \
        usr/sbin/ -type f | xargs chmod a+x
# set exec bit on scripts
find lib etc debian -name "*.sh" -type f | xargs chmod +x
# set the permissions on the pxpress scripts
chmod 744 debian/pxpress/switch*
dh build
   dh_testdir
   dh_auto_configure
   dh_auto_build
   dh_auto_test
 debian/rules binary
# refresh copyright file
cat debian/copyright_stub_0 > debian/copyright
cat usr/share/doc/fglrx/LICENSE.TXT >> debian/copyright
cat debian/copyright_stub_1 >> debian/copyright
#Steps that we can't easily represent in debhelper files or .in files yet
# Remove any libraries that may be caught by shell expansion
find . -name libGLE* | xargs rm -f
find . -name libEGL* | xargs rm -f
dh_install -pfglrx    "arch/x86/usr/X11R6/lib/libAMD*.so*"           "usr/lib32/fglrx"
dh_install -pfglrx "arch/x86/usr/X11R6/lib/*.so*"           "usr/lib32/fglrx"
dh_install -pfglrx "arch/x86/usr/X11R6/lib/fglrx/*.so*"     "usr/lib32/fglrx"
dh_installdirs -pfglrx "usr/lib32/fglrx"
dh_install -pfglrx "arch/x86/usr/X11R6/lib/modules/dri"     "usr/lib32/fglrx"
dh_install -pfglrx "arch/x86/usr/lib/*.so*"                 "usr/lib32/fglrx"
for i in \
            debian/fglrx/usr/lib32/fglrx/dri/fglrx_dri.so \
            debian/fglrx/usr/lib32/fglrx/*libGL.so.* \
            ; do execstack -q $i; execstack -c $i; done
/bin/sh: 4: execstack: not found
/bin/sh: 4: execstack: not found
/bin/sh: 4: execstack: not found
/bin/sh: 4: execstack: not found
make: *** [binary-arch] Error 127
dpkg-buildpackage: error: debian/rules binary gave error exit status 2
./packages/Ubuntu/ati-packager.sh: 294: ./packages/Ubuntu/ati-packager.sh: debclean: not found
dpkg-buildpackage: export CFLAGS from dpkg-buildflags (origin: vendor): -g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Wformat-security
dpkg-buildpackage: export CPPFLAGS from dpkg-buildflags (origin: vendor): -D_FORTIFY_SOURCE=2
dpkg-buildpackage: export CXXFLAGS from dpkg-buildflags (origin: vendor): -g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Wformat-security
dpkg-buildpackage: export FFLAGS from dpkg-buildflags (origin: vendor): -g -O2
dpkg-buildpackage: export LDFLAGS from dpkg-buildflags (origin: vendor): -Wl,-Bsymbolic-functions -Wl,-z,relro
dpkg-buildpackage: source package fglrx-installer
dpkg-buildpackage: source version 2:8.950-0ubuntu1
dpkg-buildpackage: source changed by AMD: Advanced Micro Devices. <http://ati.amd.com/support/driver.html>
 dpkg-source --before-build fglrx.QjL5xJ
dpkg-buildpackage: host architecture amd64
 debian/rules build
#Create important strings
for i in 10fglrx \
             dkms.conf \
             fglrx.install \
             fglrx-dev.install \
             fglrx-dev.links \
             fglrx-amdcccle.install \
             fglrx.grub-gfxpayload \
             fglrx.dirs \
             fglrx.links \
             fglrx.postinst \
             fglrx.postrm \
             fglrx.preinst \
             fglrx.prerm \
             overrides/fglrx; do \
        sed -e "s|#PKGXMODDIR#|usr/lib/fglrx/xorg/modules|g" \
            -e "s|#LIBDIR#|usr/lib|g" \
            -e "s|#LIBDIR32#|usr/lib32|g" \
            -e "s|#BINDIR#|usr/bin|g" \
            -e "s|#SYSCONFDIR#|etc|g" \
            -e "s|#MANDIR#|usr/share/man/man1|g" \
            -e "s|#LDSOCONF#|usr/lib/fglrx/ld.so.conf|g" \
            -e "s|#ALTLDSOCONF#|usr/lib/fglrx/alt_ld.so.conf|g" \
            -e "s|#ALTPRIORITY#|1000|g" \
            -e "s|#PXALTPRIORITY#|900|g" \
            -e "s|#AUTOSTARTDIR#|etc/xdg/autostart|g" \
            -e "s|#DATADIR#|usr/share|g" \
            -e "s|#PKGDESKDIR#|usr/share/fglrx|g" \
            -e "s|#PKGDATADIR#|usr/share/fglrx|g" \
            -e "s|#PKGCONFIGDIR#|usr/lib/fglrx|g" \
            -e "s|#PKGBINDIR#|usr/lib/fglrx/bin|g" \
            -e "s|#PKGLIBDIR#|usr/lib/fglrx|g" \
            -e "s|#PKGLIBDIR32#|usr/lib32/fglrx|g" \
            -e "s|#PKGDRIVERSDIR#|usr/lib/fglrx/xorg|g" \
            -e "s|#XORGEXTRA#|usr/lib/x86_64-linux-gnu/xorg/extra-modules|g" \
            -e "s|#PKGEXTENSIONDIR#|usr/lib/fglrx/xorg|g" \
            -e "s|#XORGEXTENSIONSDIR#|usr/lib/xorg/modules/extensions|g" \
            -e "s|#DRIVERNAME#|fglrx|g" \
            -e "s|#DRIVERDEVNAME#|fglrx-dev|g" \
            -e "s|#DRIVERSRCNAME#||g" \
            -e "s|#INCLUDEDIR#|usr/include|g" \
            -e "s|#PKGLIBCONFDIR#|lib/fglrx|g" \
            -e "s|#GRUBBLKLISTDIR#|usr/share/grub-gfxpayload-lists/blacklist|g" \
            -e "s|#PKGXMODDIR#|usr/lib/fglrx/xorg/modules|g" \
            -e "s|#PXDIR#|usr/lib/pxpress|g" \
            -e "s|#PXDIR32#|usr/lib32/pxpress|g" \
            -e "s|#PXXMODDIR#|usr/lib/pxpress/xorg/modules|g" \
            -e "s|#PXDIRNAME#|pxpress|g" \
            -e "s|#PXLIBDIR#|usr/lib/pxpress/lib|g" \
            -e "s|#PXLIBDIR32#|usr/lib32/pxpress/lib|g" \
            -e "s|#PXLDSOCONF#|usr/lib/pxpress/ld.so.conf|g" \
            -e "s|#ALTPXLDSOCONF#|usr/lib/pxpress/alt_ld.so.conf|g" \
            -e "s|#CVERSION#|8.950|g" \
            -e "s|#SRCXARCH#|xpic_64a|g" \
            -e "s|#SRCARCH#|x86_64|g" \
            -e "s|#SRCLIBDIR#|lib64|g" \
            -e "s|#DEB_HOST_MULTIARCH#|x86_64-linux-gnu|g" \
            -e "s|#OTHER_ARCH#|i386-linux-gnu|g" \
            debian/$i.in > debian/$i;      \
    done
# remove exec bit on everything
find arch \
        etc \
        lib \
        module \
        usr \
        xpic_64a     -type f | xargs chmod -x
find: `module': No such file or directory
# set executable on user apps
find arch/x86_64/usr/sbin \
        arch/x86_64/usr/X11R6/bin \
        usr/sbin/ -type f | xargs chmod a+x
# set exec bit on scripts
find lib etc debian -name "*.sh" -type f | xargs chmod +x
# set the permissions on the pxpress scripts
chmod 744 debian/pxpress/switch*
dh build
   dh_testdir
   dh_auto_configure
   dh_auto_build
   dh_auto_test
 debian/rules binary
# refresh copyright file
cat debian/copyright_stub_0 > debian/copyright
cat usr/share/doc/fglrx/LICENSE.TXT >> debian/copyright
cat debian/copyright_stub_1 >> debian/copyright
#Steps that we can't easily represent in debhelper files or .in files yet
# Remove any libraries that may be caught by shell expansion
find . -name libGLE* | xargs rm -f
find . -name libEGL* | xargs rm -f
dh_install -pfglrx    "arch/x86/usr/X11R6/lib/libAMD*.so*"           "usr/lib32/fglrx"
dh_install -pfglrx "arch/x86/usr/X11R6/lib/*.so*"           "usr/lib32/fglrx"
dh_install -pfglrx "arch/x86/usr/X11R6/lib/fglrx/*.so*"     "usr/lib32/fglrx"
dh_installdirs -pfglrx "usr/lib32/fglrx"
dh_install -pfglrx "arch/x86/usr/X11R6/lib/modules/dri"     "usr/lib32/fglrx"
dh_install -pfglrx "arch/x86/usr/lib/*.so*"                 "usr/lib32/fglrx"
for i in \
            debian/fglrx/usr/lib32/fglrx/dri/fglrx_dri.so \
            debian/fglrx/usr/lib32/fglrx/*libGL.so.* \
            ; do execstack -q $i; execstack -c $i; done
/bin/sh: 4: execstack: not found
/bin/sh: 4: execstack: not found
/bin/sh: 4: execstack: not found
/bin/sh: 4: execstack: not found
make: *** [binary-arch] Error 127
dpkg-buildpackage: error: debian/rules binary gave error exit status 2
Removing temporary directory: fglrx-install.E1enVh


```

PS - It gives more output since I added dpkg-dev, but it is giving the same errors, then continuing with additional output and errors.

Thanks,
Tim

---

### Post by travisf on 2012-03-07
On a brand new install of Precise beta1 (Toshiba L630/hd5400series) I had to install ia32libs for the driver to compile. Installing ia32libs removed libvisual-0.4-plugins. This created the deb files ok but they would not install/configure properly because of a lib32gcc1 dependency. Installed lib32gcc1 which also installed libc6-i386 and the driver configured ok.

Computer is now using the driver but I really haven't tested it yet.

---

### Post by ratcheer on 2012-03-07
> **travisf said:**
> On a brand new install of Precise beta1 (Toshiba L630/hd5400series) I had to install ia32libs for the driver to compile. Installing ia32libs removed libvisual-0.4-plugins. This created the deb files ok but they would not install/configure properly because of a lib32gcc1 dependency. Installed lib32gcc1 which also installed libc6-i386 and the driver configured ok.

Computer is now using the driver but I really haven't tested it yet.

Yes, what a mess. I looked at installing ia32-libs-multiarch, but it listed so many conflicts I bailed out.

Why does a 64-bit driver need 32-bit libraries? I will note, however, that I do have ia32-libs-multiarch installed on 11.10, where the driver installed without a hitch. I think I had to install that library one time when I was messing with Skype, or something like that.

Tim

---

### Post by ratcheer on 2012-03-07
Installing ia32-libs-multiarch didn't help.

I give up. I have made so many system changes trying to fix this, I think I'm going to reinstall Precise. Tomorrow.

Good night, everybody.

Tim

---

### Post by sacridex on 2012-03-08
> **ratcheer said:**
> 
I will run it again and post the command and all output:

```

./packages/Ubuntu/ati-packager.sh: 294: ./packages/Ubuntu/ati-packager.sh: debclean: not found
/bin/sh: 4: execstack: not found

```
Did you even read the error output?
You need to install debclean(its in the package devscripts) and execstack.

I can install fglrx 12.2 but then i cannot start Unity3D anymore and Unity2D crashes and i have no Shell. I have the desktop background and my desktop items shown but no Unity. I can start a terminal via ctrl+alt+t and start programs with it. But window moving is so ******* slow and i dont have any effects... Had to switch back to the old fglrx... 11.8 or smth like that...

---

### Post by northwestern on 2012-03-08
I too have downloaded catalyst 12.2 with kernel 3.2.0.18 , and now i cannot login to unity 3d, I have tried reloading the driver two times but with no success.

Any advice please?

Regards
Northwestern

---

### Post by zika on 2012-03-08
> **jfernyhough said:**
> I always forget about aticonfig. I think I ran it the first time I installed fglrx and haven't touched my xorg.conf since. If fglrx isn't working it's always worth a go doing $ sudo aticonfig --initialAticonfig changes not only xorg.conf. There is a thread about that (I've started it 3 years ago)... [http://ubuntuforums.org/showthread.php?t=1074593](http://ubuntuforums.org/showthread.php?t=1074593) ...
Yes I'm a bit rusty about ATI proprietary drivers (gave them up years ago...) ...
I've never used method of making .deb files but (instead) I've used```
sudo sh ./ati...driver.run
```

---

### Post by ratcheer on 2012-03-08
> **sacridex said:**
> Did you even read the error output?
You need to install debclean(its in the package devscripts) and execstack.



I saw those messages, but I did not know they are packages that need to be installed.

First, why are they not part of the standard 12.04 installation? I have been installing fglrx for several Ubuntu releases and never had to install all of this stuff manually, before.

I can go with debclean, though I don't understand why it wouldn't have been included with dpkg-dev. How would I have known about devscripts?

But execstack sounds more like an internal system call than a package.

Is there some documentation somewhere that instructs me on all the additional packages that have to be installed to install a driver? Again, this all sounds new for 12.04, to me. They have obviously left stuff out that was included, before.

Tim

---

### Post by ratcheer on 2012-03-08
Besides devscripts and execstack, I also had to install something called dh-modaliases. Now, the deb packages have finally built, successfully.

Tim

---

### Post by ratcheer on 2012-03-08
The new driver is working pretty well. amdcccle crashes when I try to make certain changes. Sometimes the screen goes black (e.g., when I need to enter the administrator password for amdcccle), but then it goes back to normal.

Also, all the digital artifact mess after entering the logon password, before Unity comes up, is gone. That is very good.

Tim

---

### Post by wireded on 2012-03-08
I tried to install the new 12.2 today. Installation seemed to work quite well. But take look at this:

> $ uname -a
Linux TEST 3.2.0-18-generic #28-Ubuntu SMP Fri Mar 2 20:02:50 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux> $ sudo apt-cache policy fglrx fglrx-dev fglrx-amdcccle
fglrx:
  Installed: 2:8.950-0ubuntu1
  Candidate: 2:8.950-0ubuntu1
  Version table:
 *** 2:8.950-0ubuntu1 0
        100 /var/lib/dpkg/status
     2:8.911-0ubuntu2 0
        500 [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) precise/restricted amd64 Packages
fglrx-dev:
  Installed: 2:8.950-0ubuntu1
  Candidate: 2:8.950-0ubuntu1
  Version table:
 *** 2:8.950-0ubuntu1 0
        100 /var/lib/dpkg/status
     2:8.911-0ubuntu2 0
        500 [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) precise/restricted amd64 Packages
fglrx-amdcccle:
  Installed: 2:8.950-0ubuntu1
  Candidate: 2:8.950-0ubuntu1
  Version table:
 *** 2:8.950-0ubuntu1 0
        100 /var/lib/dpkg/status
     2:8.911-0ubuntu2 0
        500 [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) precise/restricted amd64 PackagesUp to this everything looks alright. But then:

[IMG]http://dl.dropbox.com/u/1469136/amdccc_wrongversion.png[/IMG]

@ratcheer
What Catalyst Version is showing on your amdcccle?

Does anybody know if there is another possibility to find out which catalyst version is running? Any ideas? Or did AMD simply forgot to update version string in their fglrx.ko?

And yes, I restarted the box to make sure the new fglrx module is loaded.

---

### Post by ratcheer on 2012-03-08
@wireded: It is fairly common that the driver version does not get updated in the display by amdcccle. Did you run "sudo aticonfig --initial -f"?

************

I should not have been so fast to say that my system was doing fine, now. I have been thrown into Unity2D. glxgears fails with "X Error of failed request:  BadRequest (invalid request code or no such operation)".

I have checked Xorg.0.log and the new 64-bit driver seems to be loaded. But then it seems to go to some fallback thing:

```
[    20.038] (II) LoadModule: "fglrx"
[    20.038] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/extra-modules.dpkg-tmp/modules/drivers/fglrx_drv.so
[    20.047] (II) Module fglrx: vendor="FireGL - ATI Technologies Inc."
[    20.047]    compiled for 1.4.99.906, module version = 8.95.3
[    20.047]    Module class: X.Org Video Driver
[    20.047] (II) Loading sub module "fglrxdrm"
[    20.047] (II) LoadModule: "fglrxdrm"
[    20.047] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/extra-modules.dpkg-tmp/modules/linux/libfglrxdrm.so
[    20.047] (II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
[    20.047]    compiled for 1.4.99.906, module version = 8.95.3
[    20.047] (II) ATI Proprietary Linux Driver Version Identifier:8.95.3
[    20.047] (II) ATI Proprietary Linux Driver Release Identifier: 8.95
[    20.047] (II) ATI Proprietary Linux Driver Build Date: Feb 14 2012 21:05:02
[    20.047] (++) using VT number 7

[    20.047] (WW) Falling back to old probe method for fglrx
[    20.053] (II) Loading PCS database from /etc/ati/amdpcsdb
[    20.054] (--) Chipset Supported AMD Graphics Processor (0x68BA) found
[    20.054] (WW) fglrx: No matching Device section for instance (BusID PCI:0@1:0:1) found
[    20.054] (II) AMD Video driver is running on a device belonging to a group targeted for this release
[    20.054] (II) AMD Video driver is signed
[    20.055] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/extra-modules.dpkg-tmp/modules/drivers/fglrx_drv.so
[    20.055] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/extra-modules.dpkg-tmp/modules/linux/libfglrxdrm.so
[    20.055] (II) fglrx(0): pEnt->device->identifier=0x7fc5bc413070
[    20.055] (II) fglrx(0): === [xdl_xs111_atiddxPreInit] === begin

```I am trying to troubleshoot, but no progress, yet.

Tim

PS - This may be identical to the trouble @northwestern is having (post #15).

---

### Post by travisf on 2012-03-08
> **wireded said:**
> I tried to install the new 12.2 today. Installation seemed to work quite well. But take look at this:

Up to this everything looks alright. But then:



@ratcheer
What Catalyst Version is showing on your amdcccle?

.

Mine shows the correct version.

Perhaps you needed to purge the earlier version or installed the earlier by mistake.

On my install window controls (close, min, max) are not highlighted when hovering over them.

---

### Post by ratcheer on 2012-03-08
To determine exactly what Catalyst video driver version your system is using, examine /var/log/Xorg.0.log. Search for fglrx

Tim

---

### Post by ratcheer on 2012-03-08
Ok, I give up. I uninstalled Catalyst 12.2 and reinstalled 11.11 from the main repository. My desktop is now Unity 3D and glxgears runs without problems.

Tim

---

### Post by northwestern on 2012-03-09
I think I have cracked it!
In despair I tried to reload 11.11 without success, then I did the following.
sudo sh /usr/share/ati/fglrx-uninstall.sh sudo apt-get remove --purge fglrx fglrx_* fglrx-amdcccle* fglrx-dev*
sudo apt-get remove --purge xserver-xorg-video-ati xserver-xorg-video-radeon sudo apt-get install xserver-xorg-video-ati sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup sudo rm -rf /etc/ati
sudo apt-get install build-essential cdbs fakeroot dh-make debhelper debconf libstdc++6 dkms libqtgui4 wget execstack libelfg0 dh-modaliases linux-headers-generic
Then I went to system settings, additional drivers, activated the FGLX graphics driver then restarted.
I was expecting 11.8 but lo and behold it down loaded 12.2 and working like a charm.

Regards
Northwestern

Ps
After you have restarted in the terminal type gksu amdcccle
select your desired configuration and restart.

---

### Post by Yellow Pasque on 2012-03-09
> **ratcheer said:**
> I saw those messages, but I did not know they are packages that need to be installed. First, why are they not part of the standard 12.04 installation?
Limited space on livecd...

> Is there some documentation somewhere that instructs me on all the additional packages that have to be installed to install a driver?

[http://wiki.cchtml.com/index.php/Ubuntu_Oneiric_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Oneiric_Installation_Guide)

---

### Post by ratcheer on 2012-03-09
Thanks very much, @Temujin.

Tim

---

### Post by ratcheer on 2012-03-09
> **Temüjin said:**
> Limited space on livecd...



[http://wiki.cchtml.com/index.php/Ubuntu_Oneiric_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Oneiric_Installation_Guide)

Ok, I installed all of the prerequisites listed on the Wiki, deleted the .deb files, recreated them, and installed them. Ran aticonfig, as instructed.

The new drivers installed just fine, but Precise still comes back up in Unity2D. :( :( :(

Tim

---

### Post by kaldor on 2012-03-09
> **ratcheer said:**
> Ok, I installed all of the prerequisites listed on the Wiki, deleted the .deb files, recreated them, and installed them. Ran aticonfig, as instructed.

The new drivers installed just fine, but Precise still comes back up in Unity2D. :( :( :(

Tim

This probably isn't a helpful post on my part, but do you really need the blob? If the specs are as shown in your signature, I'd expect that the default open source driver would be great if you don't do heavy 3d stuff. The open source driver also has much less tearing and corruption than fglrx.

If you aren't doing any gaming (or use HDMI audio, etc) then I'd recommend just using the default driver. It would probably work out better.

---

### Post by larrypg on 2012-03-09
Hello,

I use the fglrx drivers because the open source drivers make the fan spin fast non-stop.  Very quiet (unless needed) with fglrx.

---

### Post by kaldor on 2012-03-09
> **larrypg said:**
> Hello,

I use the fglrx drivers because the open source drivers make the fan spin fast non-stop.  Very quiet (unless needed) with fglrx.

Ah, right. I forgot about that. I use a Radeon 6450, which is a very low end and quiet GPU, so there's no noise or anything like that when using the open source driver.

---

### Post by tehowe on 2012-03-11
> **zika said:**
> Aticonfig changes not only xorg.conf. There is a thread about that (I've started it 3 years ago)... [http://ubuntuforums.org/showthread.php?t=1074593](http://ubuntuforums.org/showthread.php?t=1074593) ...
Yes I'm a bit rusty about ATI proprietary drivers (gave them up years ago...) ...
I've never used method of making .deb files but (instead) I've used```
sudo sh ./ati...driver.run
```

I ran the driver with ```
sudo sh ./amd-driver-installer-12-2-x86.x86_64.run
``` as the poster above suggested in a clean Precise Beta 1 installation and it worked for me. The Oneiric guide on the Catalyst Wiki did not.

---

### Post by larrypg on 2012-03-13
Hello,

Just to let other's know what I have done that worked...

First I downloaded the cayalyst 12.2 drivers.  I then uninstalled the propriatary drivers via system settings and then turned off the computer.  

I then started ubuntu up and made sure it was working.  Next i went to my Downloads and did sudo sh ./amd*.run.

Once they were installed I did sudo aticonfig --initial -f and then shutdown the computer.

Restarted and everything works and showing correct version number.

---

### Post by Noesitium on 2012-03-20
Hello this is my first post!

Just started using Ubuntu and why not start the hard way with a beta release :)

Anyway.. On a clean Ubuntu 12.04 install here is what I did to install these drivers.

I used this guide **[BinaryDriverHowtoATI]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI")**

Changing

sudo sh amd-driver-installer-12-2-x86.x86_64.run --buildpkg Ubuntu/oneiric

to

sudo sh amd-driver-installer-12-2-x86.x86_64.run --buildpkg Ubuntu/precise

During the install I ran into some missing things (again this was done on a total fresh 12.04 installation)

All the steps I did:

sudo apt-get update
sudo sh amd-driver-installer-12-2-x86.x86_64.run --buildpkg Ubuntu/precise
- That didn't work at first. I had to install 3 dependencies.
sudo apt-get install dpkg-dev
sudo apt-get install debhelper
sudo apt-get install dh-modaliases execstack

So far so good .. Now it created the 3 deb files

fglrx_8.950-0ubuntu1_amd64.deb
fglrx-dev_8.950-0ubuntu1_amd64.deb
fglrx-amdcccle_8.950-0ubuntu1_amd64.deb

sudo dpkg -i *.deb (failed because of lib32gcc1 and libc6-i386)
sudo apt-get install lib32gcc1 (failed so I did)
sudo apt-get -f install

Finally! It's done!

sudo apt-get -f install

sudo reboot
 
After reboot running fglrxinfo gave me:

display: :0.0  screen: 0
OpenGL vendor string: Advanced Micro Devices, Inc.
OpenGL renderer string: ATI Mobility Radeon HD 5800 Series
OpenGL version string: 4.2.11554 Compatibility Profile Context

I hope this info can be useful for those having issues installing the drivers for ATI Graphics :)

---

### Post by Gregory Lee on 2012-03-20
This looks very useful -- thanks for the help.  The older fglrx driver is working well enough for me to run Unity 3d and Gnome 3, though not to play videos.  I haven't decided yet whether to try Catalyst 12.2.

---

### Post by ratcheer on 2012-03-20
Would some of those who have successfully installed 12.2 answer specifically whether Unity 3D is working for them? I have the driver installed, but I can only run Unity 2D in Precise. Again, 3D works fine with the 11.11 driver from the repository.

Tim

---

### Post by tehowe on 2012-03-20
> **ratcheer said:**
> Would some of those who have successfully installed 12.2 answer specifically whether Unity 3D is working for them? I have the driver installed, but I can only run Unity 2D in Precise. Again, 3D works fine with the 11.11 driver from the repository.

Tim

I can run Unity 3D fine. See reply 32 in this thread - I just unpacked and ran from the shell (no additional compiling etc required). I have a 5850.

---

### Post by v4mpiro on 2012-03-21
For me, Unity 3D runs very slow and choppy with 12.2 drivers. That's why I also use Unity 2D.

---

### Post by yaji on 2012-03-22
[http://developer.amd.com/Downloads/OpenCL1.2betadriversLinux.tgz](http://developer.amd.com/Downloads/OpenCL1.2betadriversLinux.tgz)

Some new beta driver with OpenCL1.2. Anyone tested them yet ?

---

### Post by R33D3M33R on 2012-03-22
I did test them on 3.2.0 64-bit kernel, Debian Squeeze and HD 7750. They work great. I tested Unigine Tropics and got FPS i was expecting. The KDE desktop effects are smooth (finally). I hope ZeroCore Power works.

---

### Post by zika on 2012-03-22
Would 12.2 work with xserver-xorg-core 2:1.12.0+git20120308+server-1.12-branch.b1be72c5-0ubuntu0ricotz ?

---

### Post by Yellow Pasque on 2012-03-22
> **zika said:**
> Would 12.2 work with xserver-xorg-core 2:1.12.0+git20120308+server-1.12-branch.b1be72c5-0ubuntu0ricotz ?
No. Xserver 1.12 is not yet supported: [http://www.phoronix.com/scan.php?page=news_item&px=MTA2Nzc](http://www.phoronix.com/scan.php?page=news_item&px=MTA2Nzc)

---

### Post by zika on 2012-03-22
> **Temüjin said:**
> No. Xserver 1.12 is not yet supported: [http://www.phoronix.com/scan.php?page=news_item&px=MTA2Nzc](http://www.phoronix.com/scan.php?page=news_item&px=MTA2Nzc)Thank You!

---

### Post by kaldor on 2012-03-22
> **R33D3M33R said:**
> I did test them on 3.2.0 64-bit kernel, Debian Squeeze and HD 7750. They work great. I tested Unigine Tropics and got FPS i was expecting. The KDE desktop effects are smooth (finally). I hope ZeroCore Power works.

I'm considering buying a 7750 as an upgrade to my 6450. The low power requirements, but high performance, is really appealing to me. I just need something that would be a relatively decent boost over my current GPU.

Can you comment on how well it works on Linux overall? I intend to use it with both GNOME Shell and Unity as well as some Quake 4-era games. I'm using the default 11.3 (11.4?) driver that came with Natty, and it's not that smooth. Is it as smooth as Radeon when compared to the default driver (tearing, effects, etc)?

---

### Post by synaptix on 2012-03-22
[delete me]

---

### Post by R33D3M33R on 2012-03-23
> **kaldor said:**
> I'm considering buying a 7750 as an upgrade to my 6450. The low power requirements, but high performance, is really appealing to me. I just need something that would be a relatively decent boost over my current GPU.

Can you comment on how well it works on Linux overall? I intend to use it with both GNOME Shell and Unity as well as some Quake 4-era games. I'm using the default 11.3 (11.4?) driver that came with Natty, and it's not that smooth. Is it as smooth as Radeon when compared to the default driver (tearing, effects, etc)?

I had HD4670 before and HD7750 doubled my performance, so you should see a 3-times increase in speed. Mine works well, but I'm using it with an pretty old X.org version ATM. I didn't had the chance to test it on newer distributions yet. As said KDE effects (windows popup/minimize, alt+tabbing, etc.) are smooth to me, but it's not perfect yet. It might behave differently under Gnome Shell/Unity. I also have no problems with video playback and flash content -> TBH i also didn't have these problems with the HD4670. I'm not using HDMI/DP, but the VGA port and just leaving everything at default install values.

The price of the card was a bit high, but it was worth it, because it's the best performance/watt card available ATM.

---

### Post by ELD on 2012-03-23
So what is the current state of official drivers and Ubuntu 12.04 do they work?

---

### Post by kaldor on 2012-03-23
> **R33D3M33R said:**
> I had HD4670 before and HD7750 doubled my performance, so you should see a 3-times increase in speed. Mine works well, but I'm using it with an pretty old X.org version ATM. I didn't had the chance to test it on newer distributions yet. As said KDE effects (windows popup/minimize, alt+tabbing, etc.) are smooth to me, but it's not perfect yet. It might behave differently under Gnome Shell/Unity. I also have no problems with video playback and flash content -> TBH i also didn't have these problems with the HD4670. I'm not using HDMI/DP, but the VGA port and just leaving everything at default install values.

The price of the card was a bit high, but it was worth it, because it's the best performance/watt card available ATM.

Awesome. Thanks for the reply :)


> **ELD said:**
> So what is the current state of official drivers and Ubuntu 12.04 do they work?

Assuming you mean Fglrx? It all depends on what your card is, really.

---

### Post by ELD on 2012-03-27
Okay so 12.3 is apprently around is there a way to get it?

---

### Post by jfernyhough on 2012-03-27
Allegedly it's a 12.4 beta (fglrx 8.960) and it's already in the repos.

If you want the standalone download you can get it from here: [http://developer.amd.com/Downloads/OpenCL1.2betadriversLinux.tgz](http://developer.amd.com/Downloads/OpenCL1.2betadriversLinux.tgz)

---

### Post by konspirasi on 2012-04-05
i have HP DV4-3023tx, it has hybrid VGA (Intel HD 3000 and ATI 6750)

right now i'm using ubuntu 10.04 lucid kernel:
> Linux bt 3.2.6 #1 SMP Fri Feb 17 10:34:20 EST 2012 x86_64 GNU/Linux

i have successfully installed the Catalyst 12.2 released by using:
```
./amd-driver-installer-12-2-x86.x86_64.run --buildpkg Ubuntu/lucid
```

then installing fglrx*.deb with errors but i manage it by using apt-get -f install

reboot and startx, when i tried to run the AMD Catalyst Control Center it says this:
[IMG]http://i40.tinypic.com/vf9nac.png[/IMG]

i tried to look at glxinfo, it says:
> name of display: :0.0
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  135 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  12
  Current serial number in output stream:  12


so i run aticonfig --initial -f and then aticonfig --pxl shows:
> PowerXpress: Discrete GPU is active (High-Performance mode).

but when i tried to startx it just shows blank screen, i have to reboot it and remove the xorg.conf to get back using startx again

any step did i made wrong? any suggestion or answer will be appreciated
thanks

---

### Post by zika on 2012-04-08
> **Temüjin said:**
> No. Xserver 1.12 is not yet supported: [http://www.phoronix.com/scan.php?page=news_item&px=MTA2Nzc](http://www.phoronix.com/scan.php?page=news_item&px=MTA2Nzc)I see fglrx version: 2:8.960-0ubuntu1+xedgers~precise1 ...
Does that &#8222;xedgers&#8220; mean that it became compatible with 1.12?
(xserver-xorg-dev (>= 2:1.10.0))

Update: Not it doesn't. At least at this place (without tweaking)... Funny, they are from the same PPA...

---

### Post by Scoobin on 2012-04-20
> **ratcheer said:**
> Would some of those who have successfully installed 12.2 answer specifically whether Unity 3D is working for them? I have the driver installed, but I can only run Unity 2D in Precise. Again, 3D works fine with the 11.11 driver from the repository.

Tim

I've just installed 12.3 and Unity is running fine. I'm using Ubuntu 11.10. However, I upgraded from Catalyst 11.11 and Unity's performance has taken a hit while Gnome-Shell's performance is very snappy now (whereas it didn't work correctly for me with 11.11).

I am using an HD 2600 mobile graphics chip.

---

### Post by ratcheer on 2012-04-21
> **Scoobin said:**
> I've just installed 12.3 and Unity is running fine. I'm using Ubuntu 11.10. However, I upgraded from Catalyst 11.11 and Unity's performance has taken a hit while Gnome-Shell's performance is very snappy now (whereas it didn't work correctly for me with 11.11).

I am using an HD 2600 mobile graphics chip.

Sorry, I may have failed to report that with the latest versions of everything installed, Unity 3D has been working fine for me in Precise for the past few weeks. I would have thought I mentioned that. I probably did, in another thread.

Tim

---

### Post by miatawnt2b on 2012-04-22
I've noticed much greater power consumption with 12.3.  On my Samsung Chronos, I draw 26.7 watts with catalyst 12.3, but only 19.2 watts with 12.2.

I'm falling back to 12.2

-J

---

