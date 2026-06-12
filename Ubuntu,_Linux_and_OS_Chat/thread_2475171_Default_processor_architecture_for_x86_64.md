---
title: "Default processor architecture for x86_64"
date: 2022-05-18
forum: Ubuntu, Linux and OS Chat
---

### Post by custra on 2022-05-18
What is the processor architecture that ubuntu is compiled for by default for x86_64 builds? I am referring to the "-march=xxx" option on gcc/clang.
Meaning, what instruction set is supported when you install a package with apt install <package>?
Is this minimum platform enforced in builds even if they are based on configure which tries to guess what's the architecture of the build machine?
If enforced, could you please point to how is this done? Is this done by setting a global CFLAGS/CXXFLAGS?

---

### Post by #&amp;thj^% on 2022-05-18
Very abstract request, (unclear)
I'll bite though.
```
dpkg-architecture -l
DEB_BUILD_ARCH=amd64
DEB_BUILD_ARCH_ABI=base
DEB_BUILD_ARCH_BITS=64
DEB_BUILD_ARCH_CPU=amd64
DEB_BUILD_ARCH_ENDIAN=little
DEB_BUILD_ARCH_LIBC=gnu
DEB_BUILD_ARCH_OS=linux
DEB_BUILD_GNU_CPU=x86_64
DEB_BUILD_GNU_SYSTEM=linux-gnu
DEB_BUILD_GNU_TYPE=x86_64-linux-gnu
DEB_BUILD_MULTIARCH=x86_64-linux-gnu
DEB_HOST_ARCH=amd64
DEB_HOST_ARCH_ABI=base
DEB_HOST_ARCH_BITS=64
DEB_HOST_ARCH_CPU=amd64
DEB_HOST_ARCH_ENDIAN=little
DEB_HOST_ARCH_LIBC=gnu
DEB_HOST_ARCH_OS=linux
DEB_HOST_GNU_CPU=x86_64
DEB_HOST_GNU_SYSTEM=linux-gnu
DEB_HOST_GNU_TYPE=x86_64-linux-gnu
DEB_HOST_MULTIARCH=x86_64-linux-gnu
DEB_TARGET_ARCH=amd64
DEB_TARGET_ARCH_ABI=base
DEB_TARGET_ARCH_BITS=64
DEB_TARGET_ARCH_CPU=amd64
DEB_TARGET_ARCH_ENDIAN=little
DEB_TARGET_ARCH_LIBC=gnu
DEB_TARGET_ARCH_OS=linux
DEB_TARGET_GNU_CPU=x86_64
DEB_TARGET_GNU_SYSTEM=linux-gnu
DEB_TARGET_GNU_TYPE=x86_64-linux-gnu
DEB_TARGET_MULTIARCH=x86_64-linux-gnu

```
Manpage:
```
NAME
       dpkg-architecture - set and determine the architecture for package
       building

SYNOPSIS
       dpkg-architecture [option...] [command]

DESCRIPTION
       dpkg-architecture provides a facility to determine and set the build
       and host architecture for package building.

       The build architecture is always determined by either the
       DEB_BUILD_ARCH variable if set (and --force not being specified) or by
       an external call to dpkg(1), and cannot be set at the command line.

       You can specify the host architecture by providing one or both of the
       options --host-arch and --host-type, otherwise the DEB_HOST_ARCH
       variable is used if set (and --force not being specified). The default
       is determined by an external call to gcc(1), or the same as the build
       architecture if CC or gcc are both not available. One out of
       --host-arch and --host-type is sufficient, the value of the other will
       be set to a usable default. Indeed, it is often better to only specify
       one, because dpkg-architecture will warn you if your choice does not
       match the default.

COMMANDS
       -l, --list
           Print the environment variables, one each line, in the format
           VARIABLE=value. This is the default action.

       -e, --equal architecture
           Check for equality of architecture (since dpkg 1.13.13).  It
           compares the current or specified Debian host architecture against
           architecture, to check if they are equal.  This action will not
           expand the architecture wildcards.  Command finishes with an exit
           status of 0 if matched, 1 if not matched.

       -i, --is architecture-wildcard
           Check for identity of architecture (since dpkg 1.13.13).  It
           compares the current or specified Debian host architecture against
           architecture-wildcard after having expanded it as an architecture
           wildcard, to check if they match.  Command finishes with an exit
           status of 0 if matched, 1 if not matched.

       -q, --query variable-name
           Print the value of a single variable.

       -s, --print-set
           Print an export command. This can be used to set the environment
           variables using the POSIX shell or make eval, depending on the
           output format.

       -u, --print-unset
           Print a similar command to --print-set but to unset all variables.

       -c, --command command-string
           Execute a command-string in an environment which has all variables
           set to the determined value.

       -L, --list-known
           Print a list of valid architecture names.  Possibly restricted by
           one or more of the matching options --match-wildcard, --match-bits
           or --match-endian (since dpkg 1.17.14).

       -?, --help
           Show the usage message and exit.

       --version
           Show the version and exit.

OPTIONS
       -a, --host-arch architecture
           Set the host Debian architecture.

       -t, --host-type gnu-system-type
           Set the host GNU system type.

       -A, --target-arch architecture
           Set the target Debian architecture (since dpkg 1.17.14).

       -T, --target-type gnu-system-type
           Set the target GNU system type (since dpkg 1.17.14).

       -W, --match-wildcard architecture-wildcard
           Restrict the architectures listed by --list-known to ones matching
           the specified architecture wildcard (since dpkg 1.17.14).

       -B, --match-bits architecture-bits
           Restrict the architectures listed by --list-known to ones with the
           specified CPU bits (since dpkg 1.17.14). Either 32 or 64.

       -E, --match-endian architecture-endianness
           Restrict the architectures listed by --list-known to ones with the
           specified endianness (since dpkg 1.17.14). Either little or big.

       --print-format format
           Sets the output format for --print-set and --print-unset (since
           dpkg 1.20.6), to either shell (default) or make.

       -f, --force
           Values set by existing environment variables with the same name as
           used by the scripts are honored (i.e. used by dpkg-architecture),
           except if this force flag is present. This allows the user to
           override a value even when the call to dpkg-architecture is buried
           in some other script (for example dpkg-buildpackage(1)).

TERMS
       build machine
           The machine the package is built on.

       host machine
           The machine the package is built for.

       target machine
           The machine the compiler is building for, or the emulator will run
           code for.  This is only needed when building a cross-toolchain (or
           emulator), one that will be built on the build architecture, to be
           run on the host architecture, and to build (or run emulated) code
           for the target architecture.

       Debian architecture
           The Debian architecture string, which specifies the binary tree in
           the FTP archive. Examples: i386, sparc, hurd-i386.

       Debian architecture tuple
           A Debian architecture tuple is the fully qualified architecture
           with all its components spelled out.  This differs with Debian
           architectures in that at least the cpu component does not embed the
           abi.  The current tuple has the form abi-libc-os-cpu.  Examples:
           base-gnu-linux-amd64, eabihf-musl-linux-arm.

       Debian architecture wildcard
           A Debian architecture wildcard is a special architecture string
           that will match any real architecture being part of it.  The
           general form is a Debian architecture tuple with four or less
           elements, and with at least one of them being any.  Missing
           elements of the tuple are prefixed implicitly as any, and thus the
           following pairs are equivalent:

           any-any-any-any = any
           any-any-os-any = os-any
           any-libc-any-any = libc-any-any

           Examples: linux-any, any-i386, hurd-any, eabi-any-any-arm, musl-
           any-any.

       GNU system type
           An architecture specification string consisting of two parts
           separated by a hyphen: cpu and system.  Examples: i586-linux-gnu,
           sparc-linux-gnu, i686-gnu, x86_64-netbsd.

       multiarch triplet
           The clarified GNU system type, used for filesystem paths.  This
           triplet does not change even when the baseline ISA gets bumped, so
           that the resulting paths are stable over time.  The only current
           difference with the GNU system type is that the CPU part for i386
           based systems is always i386.  Examples: i386-linux-gnu,
           x86_64-linux-gnu.  Example paths: /lib/powerpc64le-linux-gnu/,
           /usr/lib/i386-kfreebsd-gnu/.

VARIABLES
       The following variables are read from the environment (unless --force
       has been specified) and set by dpkg-architecture (see the TERMS section
       for a description of the naming scheme):

       DEB_BUILD_ARCH
           The Debian architecture of the build machine.

       DEB_BUILD_ARCH_ABI
           The Debian ABI name of the build machine (since dpkg 1.18.11).

       DEB_BUILD_ARCH_LIBC
           The Debian libc name of the build machine (since dpkg 1.18.11).

       DEB_BUILD_ARCH_OS
           The Debian system name of the build machine (since dpkg 1.13.2).

       DEB_BUILD_ARCH_CPU
           The Debian CPU name of the build machine (since dpkg 1.13.2).

       DEB_BUILD_ARCH_BITS
           The pointer size of the build machine (in bits; since dpkg 1.15.4).

       DEB_BUILD_ARCH_ENDIAN
           The endianness of the build machine (little / big; since dpkg
           1.15.4).

       DEB_BUILD_GNU_CPU
           The GNU CPU part of DEB_BUILD_GNU_TYPE.

       DEB_BUILD_GNU_SYSTEM
           The GNU system part of DEB_BUILD_GNU_TYPE.

       DEB_BUILD_GNU_TYPE
           The GNU system type of the build machine.

       DEB_BUILD_MULTIARCH
           The clarified GNU system type of the build machine, used for
           filesystem paths (since dpkg 1.16.0).

       DEB_HOST_ARCH
           The Debian architecture of the host machine.

       DEB_HOST_ARCH_ABI
           The Debian ABI name of the host machine (since dpkg 1.18.11).

       DEB_HOST_ARCH_LIBC
           The Debian libc name of the host machine (since dpkg 1.18.11).

       DEB_HOST_ARCH_OS
           The Debian system name of the host machine (since dpkg 1.13.2).

       DEB_HOST_ARCH_CPU
           The Debian CPU name of the host machine (since dpkg 1.13.2).

       DEB_HOST_ARCH_BITS
           The pointer size of the host machine (in bits; since dpkg 1.15.4).

       DEB_HOST_ARCH_ENDIAN
           The endianness of the host machine (little / big; since dpkg
           1.15.4).

       DEB_HOST_GNU_CPU
           The GNU CPU part of DEB_HOST_GNU_TYPE.

       DEB_HOST_GNU_SYSTEM
           The GNU system part of DEB_HOST_GNU_TYPE.

       DEB_HOST_GNU_TYPE
           The GNU system type of the host machine.

       DEB_HOST_MULTIARCH
           The clarified GNU system type of the host machine, used for
           filesystem paths (since dpkg 1.16.0).

       DEB_TARGET_ARCH
           The Debian architecture of the target machine (since dpkg 1.17.14).

       DEB_TARGET_ARCH_ABI
           The Debian ABI name of the target machine (since dpkg 1.18.11).

       DEB_TARGET_ARCH_LIBC
           The Debian libc name of the target machine (since dpkg 1.18.11).

       DEB_TARGET_ARCH_OS
           The Debian system name of the target machine (since dpkg 1.17.14).

       DEB_TARGET_ARCH_CPU
           The Debian CPU name of the target machine (since dpkg 1.17.14).

       DEB_TARGET_ARCH_BITS
           The pointer size of the target machine (in bits; since dpkg
           1.17.14).

       DEB_TARGET_ARCH_ENDIAN
           The endianness of the target machine (little / big; since dpkg
           1.17.14).

       DEB_TARGET_GNU_CPU
           The GNU CPU part of DEB_TARGET_GNU_TYPE (since dpkg 1.17.14).

       DEB_TARGET_GNU_SYSTEM
           The GNU system part of DEB_TARGET_GNU_TYPE (since dpkg 1.17.14).

       DEB_TARGET_GNU_TYPE
           The GNU system type of the target machine (since dpkg 1.17.14).

       DEB_TARGET_MULTIARCH
           The clarified GNU system type of the target machine, used for
           filesystem paths (since dpkg 1.17.14).

FILES
   Architecture tables
       All these files have to be present for dpkg-architecture to work. Their
       location can be overridden at runtime with the environment variable
       DPKG_DATADIR.  These tables contain a format Version pseudo-field on
       their first line to mark their format, so that parsers can check if
       they understand it, such as "# Version=1.0".

       /usr/share/dpkg/cputable
           Table of known CPU names and mapping to their GNU name.  Format
           version 1.0 (since dpkg 1.13.2).

       /usr/share/dpkg/ostable
           Table of known operating system names and mapping to their GNU
           name.  Format version 2.0 (since dpkg 1.18.11).

       /usr/share/dpkg/tupletable
           Mapping between Debian architecture tuples and Debian architecture
           names.  Format version 1.0 (since dpkg 1.18.11).

       /usr/share/dpkg/abitable
           Table of Debian architecture ABI attribute overrides.  Format
           version 2.0 (since dpkg 1.18.11).

   Packaging support
       /usr/share/dpkg/architecture.mk
           Makefile snippet that properly sets and exports all the variables
           that dpkg-architecture outputs (since dpkg 1.16.1).

EXAMPLES
       dpkg-buildpackage accepts the -a option and passes it to dpkg-
       architecture. Other examples:

        CC=i386-gnu-gcc dpkg-architecture -c debian/rules build

        eval $(dpkg-architecture -u)

       Check if the current or specified host architecture is equal to an
       architecture:

        dpkg-architecture -elinux-alpha

        dpkg-architecture -amips -elinux-mips

       Check if the current or specified host architecture is a Linux system:

        dpkg-architecture -ilinux-any

        dpkg-architecture -ai386 -ilinux-any

   Usage in debian/rules
       The environment variables set by dpkg-architecture are passed to
       debian/rules as make variables (see make documentation). However, you
       should not rely on them, as this breaks manual invocation of the
       script. Instead, you should always initialize them using dpkg-
       architecture with the -q option. Here are some examples, which also
       show how you can improve the cross compilation support in your package:

       Retrieving the GNU system type and forwarding it to ./configure:

        DEB_BUILD_GNU_TYPE ?= $(shell dpkg-architecture -qDEB_BUILD_GNU_TYPE)
        DEB_HOST_GNU_TYPE ?= $(shell dpkg-architecture -qDEB_HOST_GNU_TYPE)
        [...]
        ifeq ($(DEB_BUILD_GNU_TYPE), $(DEB_HOST_GNU_TYPE))
          confflags += --build=$(DEB_HOST_GNU_TYPE)
        else
          confflags += --build=$(DEB_BUILD_GNU_TYPE) \
                       --host=$(DEB_HOST_GNU_TYPE)
        endif
        [...]
        ./configure $(confflags)

       Doing something only for a specific architecture:

        DEB_HOST_ARCH ?= $(shell dpkg-architecture -qDEB_HOST_ARCH)

        ifeq ($(DEB_HOST_ARCH),alpha)
          [...]
        endif

       or if you only need to check the CPU or OS type, use the
       DEB_HOST_ARCH_CPU or DEB_HOST_ARCH_OS variables.

       Note that you can also rely on an external Makefile snippet to properly
       set all the variables that dpkg-architecture can provide:

        include /usr/share/dpkg/architecture.mk

        ifeq ($(DEB_HOST_ARCH),alpha)
          [...]
        endif

       In any case, you should never use dpkg --print-architecture to get
       architecture information during a package build.

ENVIRONMENT
       DPKG_DATADIR
           If set, it will be used as the dpkg data directory, where the
           architecture tables are located (since dpkg 1.14.17).  Defaults to
           \u00ab/usr/share/dpkg\u00bb.

       DPKG_COLORS
           Sets the color mode (since dpkg 1.18.5).  The currently accepted
           values are: auto (default), always and never.

       DPKG_NLS
           If set, it will be used to decide whether to activate Native
           Language Support, also known as internationalization (or i18n)
           support (since dpkg 1.19.0).  The accepted values are: 0 and 1
           (default).

NOTES
       All long command and option names available only since dpkg 1.17.17.

SEE ALSO
       dpkg-buildpackage(1).

1.21.1                            2022-04-06              dpkg-architecture(1)
```

Some info on clang and gcc: [https://clang.llvm.org/docs/CrossCompilation.html](https://clang.llvm.org/docs/CrossCompilation.html)

---

### Post by Doug S on 2022-05-18
From "/var/log/kern.log":

```
May 16 07:53:13 s19 kernel: [    0.000000] KERNEL supported cpus:
May 16 07:53:13 s19 kernel: [    0.000000]   Intel GenuineIntel
May 16 07:53:13 s19 kernel: [    0.000000]   AMD AuthenticAMD
May 16 07:53:13 s19 kernel: [    0.000000]   Hygon HygonGenuine
May 16 07:53:13 s19 kernel: [    0.000000]   Centaur CentaurHauls
May 16 07:53:13 s19 kernel: [    0.000000]   zhaoxin   Shanghai
```A bunch of other capabilities, and if enabled or not via BIOS, would be determined further along the boot process. A couple of a great many examples:
```
May 16 07:53:13 s19 kernel: [    0.139272] x86/cpu: SGX disabled by BIOS.
May 16 07:53:13 s19 kernel: [    0.139277] CPU0: Thermal monitoring enabled (TM1)
May 16 07:53:13 s19 kernel: [    0.139306] process: using mwait in idle threads
```

EDIT: I didn't see 1fallens reply, as I wrote mine.

---

### Post by custra on 2022-05-18
I guess a more focused question would be: what instruction sets are targeted? 
I want to know how old of a machine can you install Ubuntu on. I know that core2 works. But does that mean that all Ubuntu x86_64 packages do not have any SIMD extensions enabled?

---

### Post by #&amp;thj^% on 2022-05-18
> **custra said:**
> I guess a more focused question would be: what instruction sets are targeted? 
I want to know how old of a machine can you install Ubuntu on. I know that core2 works. But does that mean that all Ubuntu x86_64 packages do not have any SIMD extensions enabled?

See this guide: [https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)

Also, These days you should normally just include **<immintrin.h>.** It includes everything.

GCC and clang will stop you from using intrinsics for instructions if you haven't enabled at compile time (e.g. with **-march=native or -mavx2 -mbmi2 -mpopcnt -mfma -mcx16 -mtune=znver1 **or whatever.)

MSVC and ICC will let you use intrinsics without enabling anything at compile time
EDIT: The SIMDe header-only library provides fast, portable implementations of SIMD intrinsics on hardware which doesn't natively support them, such as calling SSE functions on ARM. There is no performance penalty if the hardware supports the native implementation (e.g., SSE/AVX runs at full speed on x86, NEON on ARM, etc.).
source: [https://github.com/simd-everywhere/simde](https://github.com/simd-everywhere/simde)
he keeps his page more up to date.

---

### Post by custra on 2022-05-18
Are all those instruction sets enabled on Ubuntu? I dont think so.

---

### Post by #&amp;thj^% on 2022-05-18
You think correctly on that.
EDIT: I showed you what was enabled on 22.04
```
**_dpkg-architecture -l_**
DEB_BUILD_ARCH=amd64
DEB_BUILD_ARCH_ABI=base
DEB_BUILD_ARCH_BITS=64
DEB_BUILD_ARCH_CPU=amd64
DEB_BUILD_ARCH_ENDIAN=little
DEB_BUILD_ARCH_LIBC=gnu
DEB_BUILD_ARCH_OS=linux
DEB_BUILD_GNU_CPU=x86_64
DEB_BUILD_GNU_SYSTEM=linux-gnu
DEB_BUILD_GNU_TYPE=x86_64-linux-gnu
DEB_BUILD_MULTIARCH=x86_64-linux-gnu
DEB_HOST_ARCH=amd64
DEB_HOST_ARCH_ABI=base
DEB_HOST_ARCH_BITS=64
DEB_HOST_ARCH_CPU=amd64
DEB_HOST_ARCH_ENDIAN=little
DEB_HOST_ARCH_LIBC=gnu
DEB_HOST_ARCH_OS=linux
DEB_HOST_GNU_CPU=x86_64
DEB_HOST_GNU_SYSTEM=linux-gnu
DEB_HOST_GNU_TYPE=x86_64-linux-gnu
DEB_HOST_MULTIARCH=x86_64-linux-gnu
DEB_TARGET_ARCH=amd64
DEB_TARGET_ARCH_ABI=base
DEB_TARGET_ARCH_BITS=64
DEB_TARGET_ARCH_CPU=amd64
DEB_TARGET_ARCH_ENDIAN=little
DEB_TARGET_ARCH_LIBC=gnu
DEB_TARGET_ARCH_OS=linux
DEB_TARGET_GNU_CPU=x86_64
DEB_TARGET_GNU_SYSTEM=linux-gnu
DEB_TARGET_GNU_TYPE=x86_64-linux-gnu
DEB_TARGET_MULTIARCH=x86_64-linux-gnu
```
Or just CPU Info
```
processor	: 0
vendor_id	: AuthenticAMD
cpu family	: 23
model		: 96
model name	: AMD Ryzen 5 4600H with Radeon Graphics
stepping	: 1
microcode	: 0x8600103
cpu MHz		: 2994.402
cache size	: 512 KB
physical id	: 0
siblings	: 1
core id		: 0
cpu cores	: 1
apicid		: 0
initial apicid	: 0
fpu		: yes
fpu_exception	: yes
cpuid level	: 16
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm rep_good nopl cpuid extd_apicid tsc_known_freq pni pclmulqdq ssse3 fma cx16 sse4_1 sse4_2 x2apic movbe popcnt tsc_deadline_timer aes xsave avx f16c rdrand hypervisor lahf_lm cmp_legacy svm cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw perfctr_core ssbd ibrs ibpb stibp vmmcall fsgsbase tsc_adjust bmi1 avx2 smep bmi2 rdseed adx smap clflushopt clwb sha_ni xsaveopt xsavec xgetbv1 xsaves clzero xsaveerptr wbnoinvd arat npt nrip_save tsc_scale vmcb_clean umip rdpid arch_capabilities
bugs		: sysret_ss_attrs null_seg spectre_v1 spectre_v2 spec_store_bypass
bogomips	: 5988.80
TLB size	: 1024 4K pages
clflush size	: 64
cache_alignment	: 64
address sizes	: 48 bits physical, 48 bits virtual
power management:

processor	: 1
vendor_id	: AuthenticAMD
cpu family	: 23
model		: 96
model name	: AMD Ryzen 5 4600H with Radeon Graphics
stepping	: 1
microcode	: 0x8600103
cpu MHz		: 2994.402
cache size	: 512 KB
physical id	: 1
siblings	: 1
core id		: 0
cpu cores	: 1
apicid		: 1
initial apicid	: 1
fpu		: yes
fpu_exception	: yes
cpuid level	: 16
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm rep_good nopl cpuid extd_apicid tsc_known_freq pni pclmulqdq ssse3 fma cx16 sse4_1 sse4_2 x2apic movbe popcnt tsc_deadline_timer aes xsave avx f16c rdrand hypervisor lahf_lm cmp_legacy svm cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw perfctr_core ssbd ibrs ibpb stibp vmmcall fsgsbase tsc_adjust bmi1 avx2 smep bmi2 rdseed adx smap clflushopt clwb sha_ni xsaveopt xsavec xgetbv1 xsaves clzero xsaveerptr wbnoinvd arat npt nrip_save tsc_scale vmcb_clean umip rdpid arch_capabilities
bugs		: sysret_ss_attrs null_seg spectre_v1 spectre_v2 spec_store_bypass
bogomips	: 5988.80
TLB size	: 1024 4K pages
clflush size	: 64
cache_alignment	: 64
address sizes	: 48 bits physical, 48 bits virtual
power management:

processor	: 2
vendor_id	: AuthenticAMD
cpu family	: 23
model		: 96
model name	: AMD Ryzen 5 4600H with Radeon Graphics
stepping	: 1
microcode	: 0x8600103
cpu MHz		: 2994.402
cache size	: 512 KB
physical id	: 2
siblings	: 1
core id		: 0
cpu cores	: 1
apicid		: 2
initial apicid	: 2
fpu		: yes
fpu_exception	: yes
cpuid level	: 16
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm rep_good nopl cpuid extd_apicid tsc_known_freq pni pclmulqdq ssse3 fma cx16 sse4_1 sse4_2 x2apic movbe popcnt tsc_deadline_timer aes xsave avx f16c rdrand hypervisor lahf_lm cmp_legacy svm cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw perfctr_core ssbd ibrs ibpb stibp vmmcall fsgsbase tsc_adjust bmi1 avx2 smep bmi2 rdseed adx smap clflushopt clwb sha_ni xsaveopt xsavec xgetbv1 xsaves clzero xsaveerptr wbnoinvd arat npt nrip_save tsc_scale vmcb_clean umip rdpid arch_capabilities
bugs		: sysret_ss_attrs null_seg spectre_v1 spectre_v2 spec_store_bypass
bogomips	: 5988.80
TLB size	: 1024 4K pages
clflush size	: 64
cache_alignment	: 64
address sizes	: 48 bits physical, 48 bits virtual
power management:

processor	: 3
vendor_id	: AuthenticAMD
cpu family	: 23
model		: 96
model name	: AMD Ryzen 5 4600H with Radeon Graphics
stepping	: 1
microcode	: 0x8600103
cpu MHz		: 2994.402
cache size	: 512 KB
physical id	: 3
siblings	: 1
core id		: 0
cpu cores	: 1
apicid		: 3
initial apicid	: 3
fpu		: yes
fpu_exception	: yes
cpuid level	: 16
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm rep_good nopl cpuid extd_apicid tsc_known_freq pni pclmulqdq ssse3 fma cx16 sse4_1 sse4_2 x2apic movbe popcnt tsc_deadline_timer aes xsave avx f16c rdrand hypervisor lahf_lm cmp_legacy svm cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw perfctr_core ssbd ibrs ibpb stibp vmmcall fsgsbase tsc_adjust bmi1 avx2 smep bmi2 rdseed adx smap clflushopt clwb sha_ni xsaveopt xsavec xgetbv1 xsaves clzero xsaveerptr wbnoinvd arat npt nrip_save tsc_scale vmcb_clean umip rdpid arch_capabilities
bugs		: sysret_ss_attrs null_seg spectre_v1 spectre_v2 spec_store_bypass
bogomips	: 5988.80
TLB size	: 1024 4K pages
clflush size	: 64
cache_alignment	: 64
address sizes	: 48 bits physical, 48 bits virtual
power management:

```
or a different view:
```
lscpu
Architecture:            x86_64
  CPU op-mode(s):        32-bit, 64-bit
  Address sizes:         48 bits physical, 48 bits virtual
  Byte Order:            Little Endian
CPU(s):                  4
  On-line CPU(s) list:   0-3
Vendor ID:               AuthenticAMD
  Model name:            AMD Ryzen 5 4600H with Radeon Graphics
    CPU family:          23
    Model:               96
    Thread(s) per core:  1
    Core(s) per socket:  1
    Socket(s):           4
    Stepping:            1
    BogoMIPS:            5988.80
    Flags:               fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mc
                         a cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx m
                         mxext fxsr_opt pdpe1gb rdtscp lm rep_good nopl cpuid ex
                         td_apicid tsc_known_freq pni pclmulqdq ssse3 fma cx16 s
                         se4_1 sse4_2 x2apic movbe popcnt tsc_deadline_timer aes
                          xsave avx f16c rdrand hypervisor lahf_lm cmp_legacy sv
                         m cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw p
                         erfctr_core ssbd ibrs ibpb stibp vmmcall fsgsbase tsc_a
                         djust bmi1 avx2 smep bmi2 rdseed adx smap clflushopt cl
                         wb sha_ni xsaveopt xsavec xgetbv1 xsaves clzero xsaveer
                         ptr wbnoinvd arat npt nrip_save tsc_scale vmcb_clean um
                         ip rdpid arch_capabilities
Virtualization features: 
  Virtualization:        AMD-V
  Hypervisor vendor:     KVM
  Virtualization type:   full
Caches (sum of all):     
  L1d:                   256 KiB (4 instances)
  L1i:                   256 KiB (4 instances)
  L2:                    2 MiB (4 instances)
  L3:                    64 MiB (4 instances)
NUMA:                    
  NUMA node(s):          1
  NUMA node0 CPU(s):     0-3
Vulnerabilities:         
  Itlb multihit:         Not affected
  L1tf:                  Not affected
  Mds:                   Not affected
  Meltdown:              Not affected
  Spec store bypass:     Mitigation; Speculative Store Bypass disabled via prctl
  Spectre v1:            Mitigation; usercopy/swapgs barriers and __user pointer
                          sanitization
  Spectre v2:            Mitigation; Retpolines, IBPB conditional, IBRS_FW, STIB
                         P disabled, RSB filling
  Srbds:                 Not affected
  Tsx async abort:       Not affected

```

---

### Post by custra on 2022-05-18
dude this is only on your machine

I am asking about what flags are enabled on a canonical build of Ubuntu packages.

---

### Post by TheFu on 2022-05-18
The Linux kernel dynamically determines which CPU features are supported and makes use of those that the kernel team can.  The lscpu output shows the results of that determination.  There is a base set, amd64, which applies to all Intel and AMD x86-64 computers.  Specific CPUs have more instructions and those may not be included initially. Some get added months to years later, if demands for a specific CPU warrant those additions. Of course, companies can fund a kernel developer to add CPU extensions that haven't been added, if they like.

There is a command that can be run against any compiled program that will return the instructions used inside. Sorry, but I don't remember it.

Or perhaps I don't understand the question.  It has been almost 2 decades since I did any serious C programming, and longer since I touched any kernel code, so I'm a little rusty.  Google says that **objdump --disassemble** can be used.

If you grab the source package for almost any program, the compile options will be inside it, somewhere. Probably want to get the source for the specific kernel and look at those build options.

---

### Post by custra on 2022-05-18
Im not asking about the kernel. I'm querying about all ubuntu packages in general. 
If a package is compiled with "-march=native"  on a Skylake box, it will crash and burn when installed on a Corei2 box. 
I did run apt source on zlib1g (libz) and recompiled it but the architecture was not selected. If it is not selected, -march=x86_64 is selected.  

x86_64-linux-gnu-gcc -mx32 -g -O2 -fdebug-prefix-map=/tmp/zlib/zlib-1.2.11.dfsg/debian/x32=. -fstack-protector-strong -Wformat -Werror=format-security -Wdate-time -D_FORTIFY_SOURCE=2 -Wall -D_REENTRANT -O3 -DUNALIGNED_OK -D_LARGEFILE64_SOURCE=1 -DHAVE_HIDDEN  -c -o gzread.o gzread.c

So part of my question is that if this is on purpose and if this is part of the review process when accepting a package into the Ubuntu repository

---

### Post by #&amp;thj^% on 2022-05-19
You'll probaly not get very far bad mouthing anyone. [https://www.reddit.com/r/Ubuntu/comments/us5hbu/default_processor_architecture_for_x86_64/](https://www.reddit.com/r/Ubuntu/comments/us5hbu/default_processor_architecture_for_x86_64/)
> It's useless. That Foundations says it is not a place for "support" questions and pointed to Ubuntu forums.

On ubuntuforums these guys are sending me screenshots of lscpu and /var/log running on their boxes. WTF

[https://ubuntuforums.org/showthread.php?t=2475171&p=14096168#post14096168](https://ubuntuforums.org/showthread.php?t=2475171&p=14096168#post14096168)
BTW I don't recall seeing any screenshots, just code used in effort to help.
Details mater here, your query's can go in so many different directions.
I would imagine you could ask the same on any "public" forum, and get as many of the same reply's back.;)

here's another list of the same Supported Architectures. [https://help.ubuntu.com/community/SupportedArchitectures](https://help.ubuntu.com/community/SupportedArchitectures)
Sorry you found us less than useful.
I wish you well

---

### Post by TheFu on 2022-05-19
Considering that Ubuntu/Canonical doesn't produce 32-bit OSes on AMD or x86 anymore, it really isn't much of an issue.  19.10 was the last 32-bit version and support ended for it in 2020.

Even years ago, I had a VIA C2 that wasn't supported with the 32-bit version of Ubuntu at the time, because they had an i686 Intel as the minimal. The VIA CPU was 32-bit x86, but didn't have all the CPU extensions that a true i686 provided.

Nearly all software comes through the Debian approval processes, except some snap packages.  Snap packages seem to derail any part of QA or validation that I can see. That could just be my poor experiences with many snaps failing to work on my systems.

Please realize that NOBODY HERE WORKS FOR CANONICAL.  The best way to chat with Canonical that I've found is via IRC.

Like that link 1fallen:
> the Ubuntu people may or may not be helpful in getting you going - no promises here. 

What's a Corei2?

---

