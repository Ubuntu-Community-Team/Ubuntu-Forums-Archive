---
title: "sudo not working because I edited hostname"
date: 2010-06-11
forum: Server Platforms
---

### Post by ThorRJB on 2010-06-11
HI, I have done something really stupid. I edited the hostname file on my server with: sudo nano /etc/hostname and by accident I commented out ALL the entries. The file now looks like this

#Server /etc/init.d/sh start
#192.168.1.2 Server

I then rebooted my server and I can no longer get 'sudo' in order to edit this file again.

Is there anyway I can edit this file? Or is there any other way to solve this problem?

---

### Post by oldfred on 2010-06-11
I was thinking of changing mine so I saved this. The comment was you have to change both and the order is important as if you change hostname before hosts sudo may not work.

Change Computer name - order important
gksudo gedit /etc/hosts
gksudo gedit /etc/hostname

You'll also want to edit /etc/hosts
127.0.0.1 localhost hostname
127.0.1.1 hostname

If you cannot boot now then you will have to use a liveCD and edit the files.

---

### Post by ThorRJB on 2010-06-11
It would seem that I am still unable to run as sudo.
Is there any other way that I can edit this file?
When I do a sudo -1 password I get this:

*** glibc detected *** sudo: free(): invalid pointer: 0x0805a3c4 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb7611704]
/lib/tls/i686/cmov/libc.so.6(cfree+0x96)[0xb76136b6]
sudo[0x804f904]
sudo[0x804febd]
sudo[0x805054f]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe5)[0xb75b8775]
sudo[0x804a5d1]
======= Memory map: ========
08048000-08063000 r-xp 00000000 fc:00 3932274    /usr/bin/sudo
08063000-08064000 r--p 0001a000 fc:00 3932274    /usr/bin/sudo
08064000-08065000 rw-p 0001b000 fc:00 3932274    /usr/bin/sudo
08065000-08068000 rw-p 08065000 00:00 0
08cd7000-08cf8000 rw-p 08cd7000 00:00 0          [heap]
b7400000-b7421000 rw-p b7400000 00:00 0
b7421000-b7500000 ---p b7421000 00:00 0
b7559000-b7566000 r-xp 00000000 fc:00 4939789    /lib/libgcc_s.so.1
b7566000-b7567000 r--p 0000c000 fc:00 4939789    /lib/libgcc_s.so.1
b7567000-b7568000 rw-p 0000d000 fc:00 4939789    /lib/libgcc_s.so.1
b7568000-b7572000 r-xp 00000000 fc:00 4940097    /lib/tls/i686/cmov/libnss_files-2.9.so
b7572000-b7573000 r--p 00009000 fc:00 4940097    /lib/tls/i686/cmov/libnss_files-2.9.so
b7573000-b7574000 rw-p 0000a000 fc:00 4940097    /lib/tls/i686/cmov/libnss_files-2.9.so
b7574000-b757d000 r-xp 00000000 fc:00 4940099    /lib/tls/i686/cmov/libnss_nis-2.9.so
b757d000-b757e000 r--p 00008000 fc:00 4940099    /lib/tls/i686/cmov/libnss_nis-2.9.so
b757e000-b757f000 rw-p 00009000 fc:00 4940099    /lib/tls/i686/cmov/libnss_nis-2.9.so
b757f000-b7594000 r-xp 00000000 fc:00 4940094    /lib/tls/i686/cmov/libnsl-2.9.so
b7594000-b7595000 r--p 00014000 fc:00 4940094    /lib/tls/i686/cmov/libnsl-2.9.so
b7595000-b7596000 rw-p 00015000 fc:00 4940094    /lib/tls/i686/cmov/libnsl-2.9.so
b7596000-b7598000 rw-p b7596000 00:00 0
b7598000-b759f000 r-xp 00000000 fc:00 4940095    /lib/tls/i686/cmov/libnss_compat-2.9.so
b759f000-b75a0000 r--p 00006000 fc:00 4940095    /lib/tls/i686/cmov/libnss_compat-2.9.so
b75a0000-b75a1000 rw-p 00007000 fc:00 4940095    /lib/tls/i686/cmov/libnss_compat-2.9.so
b75a1000-b75a2000 rw-p b75a1000 00:00 0
b75a2000-b76fe000 r-xp 00000000 fc:00 4940088    /lib/tls/i686/cmov/libc-2.9.so
b76fe000-b76ff000 ---p 0015c000 fc:00 4940088    /lib/tls/i686/cmov/libc-2.9.so
b76ff000-b7701000 r--p 0015c000 fc:00 4940088    /lib/tls/i686/cmov/libc-2.9.so
b7701000-b7702000 rw-p 0015e000 fc:00 4940088    /lib/tls/i686/cmov/libc-2.9.so
b7702000-b7706000 rw-p b7702000 00:00 0
b7706000-b7708000 r-xp 00000000 fc:00 4940091    /lib/tls/i686/cmov/libdl-2.9.so
b7708000-b7709000 r--p 00001000 fc:00 4940091    /lib/tls/i686/cmov/libdl-2.9.so
b7709000-b770a000 rw-p 00002000 fc:00 4940091    /lib/tls/i686/cmov/libdl-2.9.so
b770a000-b7714000 r-xp 00000000 fc:00 4939839    /lib/libpam.so.0.81.12
b7714000-b7715000 r--p 00009000 fc:00 4939839    /lib/libpam.so.0.81.12
b7715000-b7716000 rw-p 0000a000 fc:00 4939839    /lib/libpam.so.0.81.12
b7721000-b7723000 rw-p b7721000 00:00 0
b7723000-b7724000 r-xp b7723000 00:00 0          [vdso]
b7724000-b7740000 r-xp 00000000 fc:00 4939953    /lib/ld-2.9.so
b7740000-b7741000 r--p 0001b000 fc:00 4939953    /lib/ld-2.9.so
b7741000-b7742000 rw-p 0001c000 fc:00 4939953    /lib/ld-2.9.so
bffc4000-bffd9000 rw-p bffeb000 00:00 0          [stack]
Aborted

Regards,

---

### Post by SlugSlug on 2010-06-11
hit escape in grub boot to recovery mode and drop to root shell

from there edit you file again

---

### Post by ThorRJB on 2010-06-11
Many thanks this worked a treat..........

:-)

---

### Post by doas777 on 2010-06-11
for desktop users, 'gksu' will continue to work when sudo won't, so 'gksu gedit /etc/hostname' usually does the trick.

---

