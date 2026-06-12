---
title: "*** stack smashing detected ***: CCcam terminated?"
date: 2009-05-18
forum: Server Platforms
---

### Post by sorosh2 on 2009-05-18
HI
MY UBUNTU TERMINAL ERORO PLEAS HELP


stack smashing detected ***: CCcam terminated
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6(__fortify_fail+0x48)[0xb7e30da8]
/lib/tls/i686/cmov/libc.so.6(__fortify_fail+0x0)[0xb7e30d60]
CCcam[0x809180a]
[0x18368dbc]
======= Memory map: ========
08048000-080f1000 r-xp 00000000 08:06 32952 /usr/bin/CCcam
080f1000-080f3000 rw-p 000a9000 08:06 32952 /usr/bin/CCcam
080f3000-080f8000 rw-p 080f3000 00:00 0 
0937e000-0942a000 rw-p 0937e000 00:00 0 [heap]
b22fe000-b22ff000 ---p b22fe000 00:00 0 
b22ff000-b2aff000 rw-p b22ff000 00:00 0 
b2aff000-b2b00000 ---p b2aff000 00:00 0 
b2b00000-b3300000 rw-p b2b00000 00:00 0 
b3300000-b3321000 rw-p b3300000 00:00 0 
b3321000-b3400000 ---p b3321000 00:00 0 
b34da000-b34db000 ---p b34da000 00:00 0 
b34db000-b3cdb000 rw-p b34db000 00:00 0 
b3cdb000-b3cdc000 ---p b3cdb000 00:00 0 
b3cdc000-b44dc000 rw-p b3cdc000 00:00 0 
b44dc000-b44dd000 ---p b44dc000 00:00 0 
b44dd000-b4cdd000 rw-p b44dd000 00:00 0 
b4cdd000-b4cde000 ---p b4cdd000 00:00 0 
b4cde000-b54de000 rw-p b4cde000 00:00 0 
b54de000-b54df000 ---p b54de000 00:00 0 
b54df000-b5cdf000 rw-p b54df000 00:00 0 
b5cdf000-b5ce0000 ---p b5cdf000 00:00 0 
b5ce0000-b64e0000 rw-p b5ce0000 00:00 0 
b64e0000-b64f2000 r-xp 00000000 08:06 8765 /lib/tls/i686/cmov/libresolv-2.9.so
b64f2000-b64f3000 r--p 00011000 08:06 8765 /lib/tls/i686/cmov/libresolv-2.9.so
b64f3000-b64f4000 rw-p 00012000 08:06 8765 /lib/tls/i686/cmov/libresolv-2.9.so
b64f4000-b64f6000 rw-p b64f4000 00:00 0 
b64f6000-b64fb000 r-xp 00000000 08:06 8752 /lib/tls/i686/cmov/libnss_dns-2.9.so
b64fb000-b64fc000 r--p 00004000 08:06 8752 /lib/tls/i686/cmov/libnss_dns-2.9.so
b64fc000-b64fd000 rw-p 00005000 08:06 8752 /lib/tls/i686/cmov/libnss_dns-2.9.so
b64fd000-b64ff000 r-xp 00000000 08:06 136911 /lib/libnss_mdns4_minimal.so.2
b64ff000-b6500000 rw-p 00001000 08:06 136911 /lib/libnss_mdns4_minimal.so.2
b650d000-b650e000 ---p b650d000 00:00 0 
b650e000-b6d0e000 rw-p b650e000 00:00 0 
b6d0e000-b6d0f000 ---p b6d0e000 00:00 0 
b6d0f000-b7530000 rw-p b6d0f000 00:00 0 
b7530000-b7531000 ---p b7530000 00:00 0 
b7531000-b7d33000 rw-p b7531000 00:00 0 
b7d33000-b7e8f000 r-xp 00000000 08:06 8737 /lib/tls/i686/cmov/libc-2.9.so
b7e8f000-b7e90000 ---p 0015c000 08:06 8737 /lib/tls/i686/cmov/libc-2.9.so
b7e90000-b7e92000 r--p 0015c000 08:06 8737 /lib/tls/i686/cmov/libc-2.9.so
b7e92000-b7e93000 rw-p 0015e000 08:06 8737 /lib/tls/i686/cmov/libc-2.9.so
b7e93000-b7e96000 rw-p b7e93000 00:00 0 
b7e96000-b7ea3000 r-xp 00000000 08:06 136881 /lib/libgcc_s.so.1
b7ea3000-b7ea4000 r--p 0000c000 08:06 136881 /lib/libgcc_s.so.1
b7ea4000-b7ea5000 rw-p 0000d000 08:06 136881 /lib/libgcc_s.so.1
b7ea5000-b7ec9000 r-xp 00000000 08:06 8745 /lib/tls/i686/cmov/libm-2.9.so
b7ec9000-b7eca000 r--p 00023000 08:06 8745 /lib/tls/i686/cmov/libm-2.9.so
b7eca000-b7ecb000 rw-p 00024000 08:06 8745 /lib/tls/i686/cmov/libm-2.9.so
b7ecb000-b7faf000 r-xp 00000000 08:06 34662 /usr/lib/libstdc++.so.6.0.10
b7faf000-b7fb3000 r--p 000e3000 08:06 34662 /usr/lib/libstdc++.so.6.0.10
b7fb3000-b7fb4000 rw-p 000e7000 08:06 34662 /usr/lib/libstdc++.so.6.0.10
b7fb4000-b7fbb000 rw-p b7fb4000 00:00 0 
b7fbb000-b7fd0000 r-xp 00000000 08:06 8763 /lib/tls/i686/cmov/libpthread-2.9.so
b7fd0000-b7fd1000 r--p 00014000 08:06 8763 /lib/tls/i686/cmov/libpthread-2.9.so
b7fd1000-b7fd2000 rw-p 00015000 08:06 8763 /lib/tls/i686/cmov/libpthread-2.9.so
b7fd2000-b7fd4000 rw-p b7fd2000 00:00 0 
b7fd4000-b7fdd000 r-xp 00000000 08:06 8741 /lib/tls/i686/cmov/libcrypt-2.9.so
b7fdd000-b7fde000 r--p 00008000 08:06 8741 /lib/tls/i686/cmov/libcrypt-2.9.so
b7fde000-b7fdf000 rw-p 00009000 08:06 8741 /lib/tls/i686/cmov/libcrypt-2.9.so
b7fdf000-b8006000 rw-p b7fdf000 00:00 0 
b8006000-b8010000 r-xp 00000000 08:06 875Aborted
root@gulfsat-desktop:~#
TANKS

---

