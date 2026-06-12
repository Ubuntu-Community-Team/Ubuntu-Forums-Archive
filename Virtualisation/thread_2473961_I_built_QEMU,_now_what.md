---
title: "I built QEMU, now what?"
date: 2022-04-19
forum: Virtualisation
---

### Post by snewby on 2022-04-19
With guides and documentation I have managed to do the hard part first and successfully got a win10 vm running with GPU passthru, however I hit a wall with virtio-fs  After some digging I decided to just build QEMU myself.  However, as I'm a recent windows convertee I am stuck at the seemingly dumb/easy bit: I built the thing, now what?  More specifically, how do I correctly replace stock QEMU implementation with my built version so Virt Manager can use it?  I took a stab in the dark and copied the matching files from $qemu-6.2.0/build to $/bin but that did not seem to work.  Will Jammy LTS be the better fix?   Thanks in advance.

---

### Post by deadflowr on 2022-04-19
You built it, but how?
Give us the command you ran.
So we understand what's what.

---

### Post by snewby on 2022-04-26
Sorry for the delay.


```
$ sudo apt-get install -y ninja-build
$ sudo apt-get install libvde-dev libvdeplug-dev libvte-2.91-dev libxen-dev liblzo2-dev
$ wget https://download.qemu.org/qemu-6.2.0.tar.xz
$ tar xvJf qemu-6.2.0.tar.xz
$ cd qemu-6.2.0
$ ./configure
```


Which reported:
```
The Meson build system
Version: 0.59.3
Program python3 found: YES (/usr/bin/python3)
WARNING: Broken python installation detected. Python files installed by Meson might not be found by python interpreter.
Program cgcc found: NO
Run-time dependency appleframeworks found: NO (tried framework)
Run-time dependency liburing found: NO (tried pkgconfig)
Run-time dependency libxml-2.0 found: NO (tried pkgconfig)
Run-time dependency appleframeworks found: NO (tried framework)
Run-time dependency jack found: NO (tried pkgconfig)
Run-time dependency spice-protocol found: NO (tried pkgconfig)
Run-time dependency spice-server found: NO (tried pkgconfig)
Run-time dependency libzstd found: NO (tried pkgconfig)
Run-time dependency virglrenderer found: NO (tried pkgconfig)
Run-time dependency libudev found: NO (tried pkgconfig)
Library mpathpersist found: NO
sdl2-config found: NO
Run-time dependency sdl2 found: NO (tried pkgconfig and config-tool)
Run-time dependency glusterfs-api found: NO (tried pkgconfig)
Has header "lzfse.h" : NO 
Run-time dependency gbm found: NO (tried pkgconfig)
Dependency gnutls found: NO found 3.6.13 but need: '>=3.6.14'
Run-time dependency gnutls found: NO (tried pkgconfig)
Has header "security/pam_appl.h" : NO 
Run-time dependency libcacard found: NO (tried pkgconfig)
Run-time dependency u2f-emu found: NO (tried pkgconfig)
Run-time dependency libusbredirparser-0.5 found: NO (tried pkgconfig)
Run-time dependency libusb-1.0 found: NO (tried pkgconfig)
Run-time dependency libpmem found: NO (tried pkgconfig)
Run-time dependency libdaxctl found: NO (tried pkgconfig)
Run-time dependency libkeyutils found: NO (tried pkgconfig)
Run-time dependency fuse3 found: NO (tried pkgconfig)
Run-time dependency libbpf found: NO (tried pkgconfig)
Has header "libdrm/drm.h" : NO 
Has header "sys/disk.h" : NO 
Has header "sys/ioccom.h" : NO 
Has header "sys/kcov.h" : NO 
Header <machine/bswap.h> has symbol "bswap32" : NO 
Header <getopt.h> has symbol "optreset" : NO 
Header <netinet/in.h> has symbol "IPPROTO_MPTCP" : NO 
Checking whether type "struct sigevent" has member "sigev_notify_thread_id" : NO 
Run-time dependency capstone found: NO (tried pkgconfig)
Run-time dependency slirp found: NO (tried pkgconfig)
Program qemu-keymap found: NO
Program sphinx-build-3 sphinx-build found: NO

qemu 6.2.0

  Host binaries
    sphinx-build                 : NO

  Configurable features
    Documentation                : NO
    module support               : NO
    fuzzing support              : NO
  
  Compilation
    QEMU_CFLAGS                  : -U_FORTIFY_SOURCE -D_FORTIFY_SOURCE=2 -D_GNU_SOURCE -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -Wstrict-prototypes -Wredundant-decls -Wundef -Wwrite-strings -Wmissing-prototypes -fno-strict-aliasing -fno-common -fwrapv -Wold-style-declaration -Wold-style-definition -Wtype-limits -Wformat-security -Wformat-y2k -Winit-self -Wignored-qualifiers -Wempty-body -Wnested-externs -Wendif-labels -Wexpansion-to-defined -Wimplicit-fallthrough=2 -Wno-missing-include-dirs -Wno-shift-negative-value -Wno-psabi -fstack-protector-strong
    QEMU_LDFLAGS                 : -Wl,--warn-common -Wl,-z,relro -Wl,-z,now  -fstack-protector-strong
    profiler                     : NO
    link-time optimization (LTO) : NO
    static build                 : NO
    membarrier                   : NO
    debug stack usage            : NO
    mutex debugging              : NO
    avx512f optimization         : NO
    gprof enabled                : NO
    gcov                         : NO
    thread sanitizer             : NO
    CFI support                  : NO
    sparse                       : NO
    mingw32 support              : NO

  Targets and accelerators
    HAX support                  : NO
    HVF support                  : NO
    WHPX support                 : NO
    NVMM support                 : NO
    TCG debug enabled            : NO

  Block layer support
    Use block whitelist in tools : NO
    FUSE exports                 : NO

  Crypto
    TLS priority                 : "NORMAL"
    GNUTLS support               : YES 3.6.13
      GNUTLS crypto              : NO
    nettle                       : NO
    crypto afalg                 : NO
    rng-none                     : NO
 
  Dependencies
    SDL support                  : NO
    SDL image support            : NO
    PAM                          : NO
    virgl support                : NO
    Multipath support            : NO
    JACK support                 : NO
    netmap support               : NO
    Linux io_uring support       : NO
    RDMA support                 : NO
    PVRDMA support               : NO
    bpf support                  : NO
    spice protocol support       : NO
    smartcard support            : NO
    U2F support                  : NO
    libusb                       : NO
    usb net redir                : NO
    GBM                          : NO
    GlusterFS support            : NO
    libssh support               : NO
    lzfse support                : NO
    zstd support                 : NO
    libxml2                      : NO
    libpmem support              : NO
    libdaxctl support            : NO
    libudev                      : NO
    FUSE lseek                   : NO


```


After a bunch of package downloading I got it whittled down to:
```
The Meson build system
Version: 0.59.3
Build type: native build
Project name: qemu
Project version: 6.2.0
WARNING: Broken python installation detected. Python files installed by Meson might not be found by python interpreter.
Run-time dependency appleframeworks found: NO (tried framework)   - iOS requirement?
Run-time dependency liburing found: NO (tried pkgconfig) - exploitable so skip? https://www.graplsecurity.com/post/iou-ring-exploiting-the-linux-kernel
Run-time dependency appleframeworks found: NO (tried framework) - iOS requirement?
Run-time dependency spice-protocol found: NO (tried pkgconfig)  - doing pci passthru so dont need spice?
Run-time dependency spice-server found: NO (tried pkgconfig)
Run-time dependency virglrenderer found: NO (tried pkgconfig) - not needed? virtual GPU (https://zingmars.info/2018/07/15/Virgl-with-qemu-and-libvirt-on-ubuntu/)
Run-time dependency glusterfs-api found: NO (tried pkgconfig) - dont use gluster file system so not needed
Has header "lzfse.h" : NO - iOS compression format n/a

Dependency gnutls found: NO found 3.6.13 but need: '>=3.6.14'  - not sure how to force update this
Run-time dependency gnutls found: NO (tried pkgconfig)
Run-time dependency gnutls found: YES 3.6.13

Has header "security/pam_appl.h" : NO - iOS again
Run-time dependency libcacard found: NO (tried pkgconfig) - not using a CAC so skip
Run-time dependency u2f-emu found: NO (tried pkgconfig) - seems to be libpam-u2F, not needed?

Run-time dependency libbpf found: NO (tried pkgconfig) - found 'libbpfcc' in syn but is old and needs built/updated to work?  https://githubhelp.com/libbpf

Has header "sys/disk.h" : NO - ?
Has header "sys/ioccom.h" : NO  - part of freebsd-glue - emulate FreeBSD.  skipping
Has header "sys/kcov.h" : NO - tried enabling in package manager, looks like debugging 
Header <machine/bswap.h> has symbol "bswap32" : NO 
Header <getopt.h> has symbol "optreset" : NO 
Header <netinet/in.h> has symbol "IPPROTO_MPTCP" : NO 
Checking whether type "struct sigevent" has member "sigev_notify_thread_id" : NO 

Dependency capstone found: NO found 3.0.5 but need: '>=4.0'
Run-time dependency capstone found: NO (tried pkgconfig)
Configuring capstone-defs.h using configuration

Program qemu-keymap found: NO


qemu 6.2.0

   Configurable features
    module support               : NO
    fuzzing support              : NO
    
  Compilation
    QEMU_CFLAGS                  : -U_FORTIFY_SOURCE -D_FORTIFY_SOURCE=2 -D_GNU_SOURCE -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -Wstrict-prototypes -Wredundant-decls -Wundef -Wwrite-strings -Wmissing-prototypes -fno-strict-aliasing -fno-common -fwrapv -Wold-style-declaration -Wold-style-definition -Wtype-limits -Wformat-security -Wformat-y2k -Winit-self -Wignored-qualifiers -Wempty-body -Wnested-externs -Wendif-labels -Wexpansion-to-defined -Wimplicit-fallthrough=2 -Wno-missing-include-dirs -Wno-shift-negative-value -Wno-psabi -fstack-protector-strong
    QEMU_LDFLAGS                 : -Wl,--warn-common -Wl,-z,relro -Wl,-z,now  -fstack-protector-strong
    profiler                     : NO
    link-time optimization (LTO) : NO
    static build                 : NO
    membarrier                   : NO
    debug stack usage            : NO
    mutex debugging              : NO
    memory allocator             : system
    avx512f optimization         : NO
    gprof enabled                : NO
    gcov                         : NO
    thread sanitizer             : NO
    CFI support                  : NO
    sparse                       : /usr/bin/cgcc
    mingw32 support              : NO
    x86_64 tests                 : cc

  Targets and accelerators
    HAX support                  : NO
    HVF support                  : NO
    WHPX support                 : NO
    NVMM support                 : NO
    TCG debug enabled            : NO
    target list                  : aarch64-softmmu alpha-softmmu arm-softmmu avr-softmmu cris-softmmu hppa-softmmu i386-softmmu m68k-softmmu microblaze-softmmu microblazeel-softmmu mips-softmmu mips64-softmmu mips64el-softmmu mipsel-softmmu nios2-softmmu or1k-softmmu ppc-softmmu ppc64-softmmu riscv32-softmmu riscv64-softmmu rx-softmmu s390x-softmmu sh4-softmmu sh4eb-softmmu sparc-softmmu sparc64-softmmu tricore-softmmu x86_64-softmmu xtensa-softmmu xtensaeb-softmmu aarch64-linux-user aarch64_be-linux-user alpha-linux-user arm-linux-user armeb-linux-user cris-linux-user hexagon-linux-user hppa-linux-user i386-linux-user m68k-linux-user microblaze-linux-user microblazeel-linux-user mips-linux-user mips64-linux-user mips64el-linux-user mipsel-linux-user mipsn32-linux-user mipsn32el-linux-user nios2-linux-user or1k-linux-user ppc-linux-user ppc64-linux-user ppc64le-linux-user riscv32-linux-user riscv64-linux-user s390x-linux-user sh4-linux-user sh4eb-linux-user sparc-linux-user sparc32plus-linux-user sparc64-linux-user x86_64-linux-user xtensa-linux-user xtensaeb-linux-user


  Block layer support
    coroutine backend            : ucontext
    coroutine pool               : YES
    Block whitelist (rw)         : 
    Block whitelist (ro)         : 
    Use block whitelist in tools : NO

  Crypto
    TLS priority                 : "NORMAL"
    GNUTLS support               : YES 3.6.13
      GNUTLS crypto              : NO
    libgcrypt                    : YES 1.8.5
    nettle                       : NO
    crypto afalg                 : NO
    rng-none                     : NO
    Linux keyring                : YES

  Dependencies
    SDL support                  : YES
    SDL image support            : NO
    PAM                          : NO
    virgl support                : NO
    netmap support               : NO
    Linux io_uring support       : NO
    RDMA support                 : NO
    PVRDMA support               : NO
    fdt support                  : system
    bpf support                  : NO
    spice protocol support       : NO
    smartcard support            : NO
    U2F support                  : NO
    GlusterFS support            : NO
    libssh support               : NO
    lzfse support                : NO
    capstone                     : internal

```


and changing fuse version gave me:
```
Selecting previously unselected package libfuse3-3:amd64.
(Reading database ... 450384 files and directories currently installed.)
Preparing to unpack .../libfuse3-3_3.9.0-2_amd64.deb ...
Unpacking libfuse3-3:amd64 (3.9.0-2) ...
dpkg: fuse: dependency problems, but removing anyway as you requested:
 xdg-desktop-portal depends on fuse; however:
  Package fuse is to be removed.
 sshfs depends on fuse.
 ntfs-3g depends on fuse.
 ifuse depends on fuse.
 gvfs-fuse depends on fuse.
 exfat-fuse depends on fuse.
```


Finally I ran $ make with no additional operators

---

### Post by TheFu on 2022-04-26
For some reason, I thought the version of qemu and libvirt were dependencies.  virt-manager --> libvirt ---> qemu-system-x86_64 -enable-kvm
It isn't like an old version of libvirt will magically pass parameters through to qemu-kvm.  At a minimum, you'll need to edit the XML file for the VM to add options that libvirt and whatever GUI program(s) are using libvirt.

I've never used virt-fs.  If it were me, I'd research finding a pre-built PPA with the dependencies for virt-manager, libvirt, qemu, and any other needed things. This is a fairly steep learning curve for someone already Unix-savvy. About the same as for someone who knows C/C++ and building software, but not Unix, I'd guess.  The IDEs on that-other-OS hide many details, if they 'just work'.

I see that 22.04 is using 6.2 of qemu, so if you look at the make-install target for the makefile, it should show what gets installed after the build is completed.  That is a list of things you may want to replace ... and I'd probably put a 'hold' on the package to prevent unwanted updates for it. Use apt-mark for that.   You'll need to watch the package for updates manually. There have been some nasty remote access/takeover attacks in qemu over the years. Don't just swap it in and forget about it. That will likely become bad in a few months.

OTOH, my qemu version is 2.11, so what do I know?

---

