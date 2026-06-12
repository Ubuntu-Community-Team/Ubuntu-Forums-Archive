---
title: "Compiling NetworkManager"
date: 2012-11-07
forum: Security
---

### Post by Stonecold1995 on 2012-11-07
NetworkManager doesn't use PIE, which is concerning because it runs as root.

```
alex@kubuntu:~$ hardening-check /usr/sbin/NetworkManager
/usr/sbin/NetworkManager:
 Position Independent Executable: no, normal executable
 Stack protected: yes
 Fortify Source functions: yes (some protected functions found)
 Read-only relocations: yes
 Immediate binding: no, not found
```

So I want to compile it from source, and I have the hardening-wrapper installed and set up.  But I really don't want to mess it up.  Running "./configure --help" after downloading the source gives many more options than usual, and I don't know which ones to select.  Earlier I compiled coreutils with the default options and it installed to /usr/local/bin, when it should have installed to /bin, so I want to learn from mistakes like that and not do the same kind of thing with NetworkManager.  So what options do I set for "configure" so I don't fsck my computer up?

```
alex@kubuntu:/tmp/NetworkManager/NetworkManager-0.9.6.4$ ./configure --help
`configure' configures NetworkManager 0.9.6.4 to adapt to many kinds of systems.

Usage: ./configure [OPTION]... [VAR=VALUE]...

To assign environment variables (e.g., CC, CFLAGS...), specify them as
VAR=VALUE.  See below for descriptions of some of the useful variables.

Defaults for the options are specified in brackets.

Configuration:
  -h, --help              display this help and exit
      --help=short        display options specific to this package
      --help=recursive    display the short help of all the included packages
  -V, --version           display version information and exit
  -q, --quiet, --silent   do not print `checking ...' messages
      --cache-file=FILE   cache test results in FILE [disabled]
  -C, --config-cache      alias for `--cache-file=config.cache'
  -n, --no-create         do not create output files
      --srcdir=DIR        find the sources in DIR [configure dir or `..']

Installation directories:
  --prefix=PREFIX         install architecture-independent files in PREFIX
                          [/usr/local]
  --exec-prefix=EPREFIX   install architecture-dependent files in EPREFIX
                          [PREFIX]

By default, `make install' will install all the files in
`/usr/local/bin', `/usr/local/lib' etc.  You can specify
an installation prefix other than `/usr/local' using `--prefix',
for instance `--prefix=$HOME'.

For better control, use the options below.

Fine tuning of the installation directories:
  --bindir=DIR            user executables [EPREFIX/bin]
  --sbindir=DIR           system admin executables [EPREFIX/sbin]
  --libexecdir=DIR        program executables [EPREFIX/libexec]
  --sysconfdir=DIR        read-only single-machine data [PREFIX/etc]
  --sharedstatedir=DIR    modifiable architecture-independent data [PREFIX/com]
  --localstatedir=DIR     modifiable single-machine data [PREFIX/var]
  --libdir=DIR            object code libraries [EPREFIX/lib]
  --includedir=DIR        C header files [PREFIX/include]
  --oldincludedir=DIR     C header files for non-gcc [/usr/include]
  --datarootdir=DIR       read-only arch.-independent data root [PREFIX/share]
  --datadir=DIR           read-only architecture-independent data [DATAROOTDIR]
  --infodir=DIR           info documentation [DATAROOTDIR/info]
  --localedir=DIR         locale-dependent data [DATAROOTDIR/locale]
  --mandir=DIR            man documentation [DATAROOTDIR/man]
  --docdir=DIR            documentation root [DATAROOTDIR/doc/NetworkManager]
  --htmldir=DIR           html documentation [DOCDIR]
  --dvidir=DIR            dvi documentation [DOCDIR]
  --pdfdir=DIR            pdf documentation [DOCDIR]
  --psdir=DIR             ps documentation [DOCDIR]

Program names:
  --program-prefix=PREFIX            prepend PREFIX to installed program names
  --program-suffix=SUFFIX            append SUFFIX to installed program names
  --program-transform-name=PROGRAM   run sed PROGRAM on installed program names

System types:
  --build=BUILD     configure for building on BUILD [guessed]
  --host=HOST       cross-compile to build programs to run on HOST [BUILD]

Optional Features:
  --disable-option-checking  ignore unrecognized --enable/--with options
  --disable-FEATURE       do not include FEATURE (same as --enable-FEATURE=no)
  --enable-FEATURE[=ARG]  include FEATURE [ARG=yes]
  --disable-maintainer-mode  disable make rules and dependencies not useful
                          (and sometimes confusing) to the casual installer
  --enable-silent-rules          less verbose build output (undo: `make V=1')
  --disable-silent-rules         verbose build output (undo: `make V=0')
  --disable-dependency-tracking  speeds up one-time build
  --enable-dependency-tracking   do not reject slow dependency extractors
  --enable-static[=PKGS]  build static libraries [default=no]
  --enable-shared[=PKGS]  build shared libraries [default=yes]
  --enable-fast-install[=PKGS]
                          optimize for fast installation [default=yes]
  --disable-libtool-lock  avoid locking (might break parallel builds)
  --disable-nls           do not use Native Language Support
  --disable-rpath         do not hardcode runtime library paths
  --enable-introspection=[no/auto/yes]
                          Enable introspection for this build
  --enable-qt             enable Qt examples
  --enable-wimax          enable WiMAX support
  --enable-polkit         enable PolicyKit support
  --enable-ppp            enable PPP/PPPoE support
  --disable-crashtrace    Disable GNU backtrace extensions
  --enable-concheck       enable connectivity checking support
  --enable-more-warnings  Possible values: no/yes/error
  --enable-gtk-doc        use gtk-doc to build documentation [[default=no]]
  --enable-gtk-doc-html   build documentation in html format [[default=yes]]
  --enable-gtk-doc-pdf    build documentation in pdf format [[default=no]]
  --enable-vala=[no/auto/yes]
                          build Vala bindings [[default=auto]]

Optional Packages:
  --with-PACKAGE[=ARG]    use PACKAGE [ARG=yes]
  --without-PACKAGE       do not use PACKAGE (same as --with-PACKAGE=no)
  --with-pic[=PKGS]       try to use only PIC/non-PIC objects [default=use
                          both]
  --with-gnu-ld           assume the C compiler uses GNU ld [default=no]
  --with-sysroot=DIR Search for dependent libraries within DIR
                        (or the compiler's sysroot if not specified).
  --with-gnu-ld           assume the C compiler uses GNU ld default=no
  --with-libiconv-prefix[=DIR]  search for libiconv in DIR/include and DIR/lib
  --without-libiconv-prefix     don't search for libiconv in includedir and libdir
  --with-libintl-prefix[=DIR]  search for libintl in DIR/include and DIR/lib
  --without-libintl-prefix     don't search for libintl in includedir and libdir
  --with-docs             Build NetworkManager documentation
  --with-distro=DISTRO    Specify the Linux distribution to target: One of
                          redhat, suse, gentoo, debian, arch, slackware,
                          paldo, mandriva, pardus, linexa, exherbo or lfs
  --with-dist-version=<NM-distribution-version>
                          Define the NM's distribution version string
  --with-wext=yes         Enable or disable Linux Wireless Extensions
  --with-udev-dir=DIR     where the udev base directory is
  --with-systemdsystemunitdir=DIR
                          Directory for systemd service files
  --with-session-tracking=systemd|ck|none
                          Build NetworkManager with specific session tracking
                          support
  --with-crypto=nss|gnutls
                          Cryptography library to use for certificate and key
                          operations
  --with-dbus-sys-dir=DIR where D-BUS system.d directory is
  --with-pppd-plugin-dir=DIR
                          path to the pppd plugins directory
  --with-dhclient=yes|no|path
                          Enable dhclient 4.x support
  --with-dhcpcd=yes|no|path
                          Enable dhcpcd 4.x support
  --with-resolvconf=yes|no|path
                          Enable resolvconf support
  --with-iptables=/path/to/iptables
                          path to iptables
  --with-system-ca-path=/path/to/ssl/certs
                          path to system CA certificates
  --with-kernel-firmware-dir=DIR
                          where kernel firmware directory is (default is
                          /lib/firmware)
  --with-html-dir=PATH    path to installed docs
  --with-tests            Build NetworkManager tests

Some influential environment variables:
  CC          C compiler command
  CFLAGS      C compiler flags
  LDFLAGS     linker flags, e.g. -L<lib dir> if you have libraries in a
              nonstandard directory <lib dir>
  LIBS        libraries to pass to the linker, e.g. -l<library>
  CPPFLAGS    (Objective) C/C++ preprocessor flags, e.g. -I<include dir> if
              you have headers in a nonstandard directory <include dir>
  CPP         C preprocessor
  CXX         C++ compiler command
  CXXFLAGS    C++ compiler flags
  CXXCPP      C++ preprocessor
  PKG_CONFIG  path to pkg-config utility
  PKG_CONFIG_PATH
              directories to add to pkg-config's search path
  PKG_CONFIG_LIBDIR
              path overriding pkg-config's built-in search path
  DBUS_CFLAGS C compiler flags for DBUS, overriding pkg-config
  DBUS_LIBS   linker flags for DBUS, overriding pkg-config
  GLIB_CFLAGS C compiler flags for GLIB, overriding pkg-config
  GLIB_LIBS   linker flags for GLIB, overriding pkg-config
  GMODULE_CFLAGS
              C compiler flags for GMODULE, overriding pkg-config
  GMODULE_LIBS
              linker flags for GMODULE, overriding pkg-config
  GUDEV_CFLAGS
              C compiler flags for GUDEV, overriding pkg-config
  GUDEV_LIBS  linker flags for GUDEV, overriding pkg-config
  GIO_CFLAGS  C compiler flags for GIO, overriding pkg-config
  GIO_LIBS    linker flags for GIO, overriding pkg-config
  QT_CFLAGS   C compiler flags for QT, overriding pkg-config
  QT_LIBS     linker flags for QT, overriding pkg-config
  SYSTEMD_CFLAGS
              C compiler flags for SYSTEMD, overriding pkg-config
  SYSTEMD_LIBS
              linker flags for SYSTEMD, overriding pkg-config
  LIBNL3_CFLAGS
              C compiler flags for LIBNL3, overriding pkg-config
  LIBNL3_LIBS linker flags for LIBNL3, overriding pkg-config
  LIBNL_ROUTE3_CFLAGS
              C compiler flags for LIBNL_ROUTE3, overriding pkg-config
  LIBNL_ROUTE3_LIBS
              linker flags for LIBNL_ROUTE3, overriding pkg-config
  LIBNL_GENL3_CFLAGS
              C compiler flags for LIBNL_GENL3, overriding pkg-config
  LIBNL_GENL3_LIBS
              linker flags for LIBNL_GENL3, overriding pkg-config
  LIBNL2_CFLAGS
              C compiler flags for LIBNL2, overriding pkg-config
  LIBNL2_LIBS linker flags for LIBNL2, overriding pkg-config
  LIBNL1_CFLAGS
              C compiler flags for LIBNL1, overriding pkg-config
  LIBNL1_LIBS linker flags for LIBNL1, overriding pkg-config
  UUID_CFLAGS C compiler flags for UUID, overriding pkg-config
  UUID_LIBS   linker flags for UUID, overriding pkg-config
  IWMX_SDK_CFLAGS
              C compiler flags for IWMX_SDK, overriding pkg-config
  IWMX_SDK_LIBS
              linker flags for IWMX_SDK, overriding pkg-config
  POLKIT_CFLAGS
              C compiler flags for POLKIT, overriding pkg-config
  POLKIT_LIBS linker flags for POLKIT, overriding pkg-config
  NSS_CFLAGS  C compiler flags for NSS, overriding pkg-config
  NSS_LIBS    linker flags for NSS, overriding pkg-config
  GNUTLS_CFLAGS
              C compiler flags for GNUTLS, overriding pkg-config
  GNUTLS_LIBS linker flags for GNUTLS, overriding pkg-config
  LIBSOUP_CFLAGS
              C compiler flags for LIBSOUP, overriding pkg-config
  LIBSOUP_LIBS
              linker flags for LIBSOUP, overriding pkg-config
  GTKDOC_DEPS_CFLAGS
              C compiler flags for GTKDOC_DEPS, overriding pkg-config
  GTKDOC_DEPS_LIBS
              linker flags for GTKDOC_DEPS, overriding pkg-config

Use these variables to override the choices made by `configure' or to help
it to find libraries and programs with nonstandard names/locations.

Report bugs to <http://bugzilla.gnome.org/enter_bug.cgi?product=NetworkManager>.
```

```
alex@kubuntu:/tmp/NetworkManager/NetworkManager-0.9.6.4$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking how to create a ustar tar archive... gnutar
checking whether to enable maintainer-specific portions of Makefiles... yes
checking whether make supports nested variables... yes
checking for style of include used by make... GNU
checking for gcc... gcc
checking whether the C compiler works... yes
checking for C compiler default output file name... a.out
checking for suffix of executables... 
checking whether we are cross compiling... no
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking dependency style of gcc... gcc3
checking how to run the C preprocessor... gcc -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking minix/config.h usability... no
checking minix/config.h presence... no
checking for minix/config.h... no
checking whether it is safe to define __EXTENSIONS__... yes
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking whether gcc and cc understand -c and -o together... yes
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking how to print strings... printf
checking for a sed that does not truncate output... /bin/sed
checking for fgrep... /bin/grep -F
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for BSD- or MS-compatible name lister (nm)... /usr/bin/nm -B
checking the name lister (/usr/bin/nm -B) interface... BSD nm
checking whether ln -s works... yes
checking the maximum length of command line arguments... 1572864
checking whether the shell understands some XSI constructs... yes
checking whether the shell understands "+="... yes
checking how to convert x86_64-unknown-linux-gnu file names to x86_64-unknown-linux-gnu format... func_convert_file_noop
checking how to convert x86_64-unknown-linux-gnu file names to toolchain format... func_convert_file_noop
checking for /usr/bin/ld option to reload object files... -r
checking for objdump... objdump
checking how to recognize dependent libraries... pass_all
checking for dlltool... no
checking how to associate runtime and link libraries... printf %s\n
checking for ar... ar
checking for archiver @FILE support... @
checking for strip... strip
checking for ranlib... ranlib
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking for sysroot... no
checking for mt... mt
checking if mt is a manifest tool... no
checking for dlfcn.h... yes
checking for objdir... .libs
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC -DPIC
checking if gcc PIC flag -fPIC -DPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking if gcc supports -c -o file.o... (cached) yes
checking whether the gcc linker (/usr/bin/ld -m elf_x86_64) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... no
checking how to run the C++ preprocessor... g++ -E
checking for ld used by g++... /usr/bin/ld -m elf_x86_64
checking if the linker (/usr/bin/ld -m elf_x86_64) is GNU ld... yes
checking whether the g++ linker (/usr/bin/ld -m elf_x86_64) supports shared libraries... yes
checking for g++ option to produce PIC... -fPIC -DPIC
checking if g++ PIC flag -fPIC -DPIC works... yes
checking if g++ static flag -static works... yes
checking if g++ supports -c -o file.o... yes
checking if g++ supports -c -o file.o... (cached) yes
checking whether the g++ linker (/usr/bin/ld -m elf_x86_64) supports shared libraries... yes
checking dynamic linker characteristics... (cached) GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking for ANSI C header files... (cached) yes
checking fcntl.h usability... yes
checking fcntl.h presence... yes
checking for fcntl.h... yes
checking paths.h usability... yes
checking paths.h presence... yes
checking for paths.h... yes
checking sys/ioctl.h usability... yes
checking sys/ioctl.h presence... yes
checking for sys/ioctl.h... yes
checking sys/time.h usability... yes
checking sys/time.h presence... yes
checking for sys/time.h... yes
checking syslog.h usability... yes
checking syslog.h presence... yes
checking for syslog.h... yes
checking for unistd.h... (cached) yes
checking for mode_t... yes
checking for pid_t... yes
checking whether time.h and sys/time.h may both be included... yes
checking whether gcc needs -traditional... no
checking for working memcmp... yes
checking for select... yes
checking for socket... yes
checking for uname... yes
checking whether NLS is requested... yes
checking for intltool >= 0.40.0... 0.50.2 found
checking for intltool-update... /usr/bin/intltool-update
checking for intltool-merge... /usr/bin/intltool-merge
checking for intltool-extract... /usr/bin/intltool-extract
checking for xgettext... /usr/bin/xgettext
checking for msgmerge... /usr/bin/msgmerge
checking for msgfmt... /usr/bin/msgfmt
checking for gmsgfmt... /usr/bin/msgfmt
checking for perl... /usr/bin/perl
checking for perl >= 5.8.1... 5.14.2
checking for XML::Parser... ok
checking for msgfmt... (cached) /usr/bin/msgfmt
checking for gmsgfmt... (cached) /usr/bin/msgfmt
checking for xgettext... (cached) /usr/bin/xgettext
checking for msgmerge... (cached) /usr/bin/msgmerge
checking for ld used by GCC... /usr/bin/ld -m elf_x86_64
checking if the linker (/usr/bin/ld -m elf_x86_64) is GNU ld... yes
checking for shared library run path origin... done
checking for CFPreferencesCopyAppValue... no
checking for CFLocaleCopyCurrent... no
checking for GNU gettext in libc... yes
checking whether to use NLS... yes
checking where the gettext function comes from... libc
checking whether byte ordering is bigendian... no
checking for /etc/redhat-release... no
checking for /etc/SuSE-release... no
checking for /etc/fedora-release... no
checking for /etc/gentoo-release... no
checking for /etc/debian_version... yes
checking for /etc/arch-release... no
checking for /etc/slackware-version... no
checking for /etc/frugalware-release... no
checking for /etc/mandriva-release... no
checking for /etc/pardus-release... no
checking for /etc/linexa-release... no
checking for /etc/exherbo-release... no
checking for /etc/lfs-release... no
checking Linux kernel WEXT headers... yes
checking Linux kernel nl80211 headers... yes
checking Linux kernel VLAN_FLAG_LOOSE_BINDING enum value... yes
checking for cos in -lm... yes
checking for dladdr in -ldl... yes
checking for dbus_glib_global_set_disable_legacy_property_access in -ldbus-glib-1... no
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for DBUS... no
configure: error: Package requirements (dbus-1 >= 1.1 dbus-glib-1 >= 0.94) were not met:

No package 'dbus-glib-1' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables DBUS_CFLAGS
and DBUS_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.
```

---

### Post by kevdog on 2012-11-08
By standard, all system programs a user compiles are supposed to go in /usr/local/bin.  System programs compiled by those that go in the distribution go in /bin.  Frankly it doesn't matter, I'm just telling you the convention.  /usr/local/bin is usually searched for first because its listed first in the $PATH statement before /bin.  

As far as some of the configuration options -- whether to include certain options, you might want to see if Network Manager has an irc channel and ask there.  It seems like you are missing some proper dbus libraries.  One of the challenges about compiling source code, is newer source code is often dependent on newer versions of accompanying libraries.  You might need to either find an updated dbus library or compile this library from source code as well.  

Hang in there -- you'll get it!

---

