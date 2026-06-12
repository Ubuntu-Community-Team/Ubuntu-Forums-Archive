---
title: "[SOLVED] NXserver connection problem EVP_Cipher undefined"
date: 2008-01-03
forum: Server Platforms
---

### Post by taigaChi on 2008-01-03
Hello there,

this is my first post, but I've spend the last 5 hours working on this and thought someone else might be interested in my hack.  Incidentally if someone has a cleaner solution, please let me know, I'd like to learn how to fix this kind of problem *correctly*.

I've been trying to get NXserver (NoMachines FreeEdition) to work on my Kubuntu Feisty server, but with very little success. I downloaded the latest .deb packages and did the following:

```
sudo dpkg -i nxclient_3.1.0-2_i386.deb
sudo dpkg -i nxnode_3.1.0-3_i386.deb
sudo dpkg -i nxserver_3.1.0-2_i386.deb
```

I also followed all the advice regarding setting the authorized_keys2 setting in /etc/ssh/sshd_config.

When I tried to connect from another machine, to the newly set up nxserver, I would get these errors:

```
nxssh: symbol lookup error: nxssh: undefined symbol: EVP_Cipher
```

I've added /usr/NX/lib to my LD_LIBRARY_PATH in my .bashrc, ran "sudo ldconfig" and nothing helped, until I checked to see the library dependencies for nxssh:

```
ldd `which nxssh`
        linux-gate.so.1 =>  (0xffffe000)
        libresolv.so.2 => /lib/tls/i686/cmov/libresolv.so.2 (0xb7f3e000)
===>    libcrypto.so.0.9.8 => /usr/lib/i686/cmov/libcrypto.so.0.9.8 (0xb7e2f000)
        libutil.so.1 => /lib/tls/i686/cmov/libutil.so.1 (0xb7e2b000)
        libz.so.1 => /usr/lib/libz.so.1 (0xb7e17000)
        libnsl.so.1 => /lib/tls/i686/cmov/libnsl.so.1 (0xb7e00000)
        libjpeg.so.62 => /usr/lib/libjpeg.so.62 (0xb7de1000)
        libm.so.6 => /lib/tls/i686/cmov/libm.so.6 (0xb7dba000)
        libcrypt.so.1 => /lib/tls/i686/cmov/libcrypt.so.1 (0xb7d8b000)
        libXcomp.so.3 => /usr/NX/lib/libXcomp.so.3 (0xb7ca3000)
        libstdc++.so.6 => /usr/lib/libstdc++.so.6 (0xb7bc4000)
        libpng12.so.0 => /usr/lib/libpng12.so.0 (0xb7ba0000)
        libc.so.6 => /lib/tls/i686/cmov/libc.so.6 (0xb7a5f000)
        libdl.so.2 => /lib/tls/i686/cmov/libdl.so.2 (0xb7a5b000)
        /lib/ld-linux.so.2 (0xb7f71000)
        libgcc_s.so.1 => /lib/libgcc_s.so.1 (0xb7a4f000)
```

The funny bit is marked by the arrow there. the third line spells trouble since the openssl version included in /usr/NX/lib is 0.9.8e, whereas the Ubuntu Feisty one is still at 0.9.8c

[LIST]
[*]Adding /usr/NX/lib to LD_LIBRARY_PATH in .bashrc won't help
[*]Neither will adding /usr/NX/lib in /etc/ld.so.conf
[*]Worst solution is to replace the lib at /usr/lib/i686/cmov/libcrypto.so.0.9.8 with NX's
[/LIST]

Since *order* does matter, and nxssh will try to load this /usr/lib/i686/cmov/libcrypto.so.0.9.8
instead of /usr/NX/lib/libcrypto.so.0.9.8

**SOLUTION:**

here's where my hack comes into play, that solves this mess with a cludge:

Trick is to binary edit the dependency in nxssh to point to some non-existing version of
libcrypto.so which then is a copied version within /usr/NX/lib/ so do these steps:
```

sudo cp /usr/NX/bin/nxssh /usr/NX/bin/nxssh.orig
```

       for safety make a backup copy of the original binary, then use your favorite editor capable of doing binary edits (mine is vi and the -b option ensures that there are no funny line breaks, etc...)
```

sudo vi -b /usr/NX/bin/nxssh
```

       search for "libcrypto.so.0.9.8"  and change to "libcrypto.so.0.9.6"
       save the modified binary

```
sudo cp /usr/NX/lib/libcrypto.so.0.9.8 /usr/NX/lib/libcrypto.so.0.9.6
```

       create a "fake" version of libcrypto.so.0.9.8 with the new renamed libcrypto.so.0.9.6, since there is no version 0.9.6 of libcrypto  in /usr/lib or /lib, it will look for it in the /usr/NX/lib directory which is where I want it to look. Next we can check that it found the right library by checking with ldd again:

```
ldd `which nxssh`
```

       should now show that the desired library within /usr/NX/lib will be used:
   ```
     linux-gate.so.1 =>  (0xffffe000)
        libresolv.so.2 => /lib/tls/i686/cmov/libresolv.so.2 (0xb7f2a000)
===>!   libcrypto.so.0.9.6 => /usr/NX/lib/libcrypto.so.0.9.6 (0xb7e1b000)
        libutil.so.1 => /lib/tls/i686/cmov/libutil.so.1 (0xb7e17000)
        libz.so.1 => /usr/lib/libz.so.1 (0xb7e03000)
        libnsl.so.1 => /lib/tls/i686/cmov/libnsl.so.1 (0xb7dec000)
        libjpeg.so.62 => /usr/lib/libjpeg.so.62 (0xb7dcd000)
        libm.so.6 => /lib/tls/i686/cmov/libm.so.6 (0xb7da6000)
        libcrypt.so.1 => /lib/tls/i686/cmov/libcrypt.so.1 (0xb7d77000)
        libXcomp.so.3 => /usr/NX/lib/libXcomp.so.3 (0xb7c8f000)
        libstdc++.so.6 => /usr/lib/libstdc++.so.6 (0xb7ba5000)
        libpng12.so.0 => /usr/lib/libpng12.so.0 (0xb7b82000)
        libc.so.6 => /lib/tls/i686/cmov/libc.so.6 (0xb7a41000)
        libdl.so.2 => /lib/tls/i686/cmov/libdl.so.2 (0xb7a3d000)
        /lib/ld-linux.so.2 (0xb7f5f000)
        libgcc_s.so.1 => /lib/libgcc_s.so.1 (0xb7a30000)

```

And voila! the third line shows that my "fake" libcrypto.so.0.9.6 is used here, then when I try to reconnect everything works like butter.

Cheers and hope this helps some of you there,

taigaChi

---

