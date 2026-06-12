---
title: "OSSEC Server Installation Failed"
date: 2015-02-28
forum: Security
---

### Post by Harley_Frank on 2015-02-28
So I followed the tutorial:

I installed the build-essentials and then I ran bash install.sh in the OSSEC folder, I entered in all the options and I get this:

```

5- Installing the system
 - Running the Makefile
INFO: Little endian set.
 *** Making zlib (by Jean-loup Gailly and Mark Adler)  ***
make[1]: Entering directory `/root/ossec-hids-2.8.1/src/external'
cd zlib-1.2.8/; ./configure; make libz.a;
/bin/sh: 1: ./configure: Permission denied
make[2]: Entering directory `/root/ossec-hids-2.8.1/src/external/zlib-1.2.8'
make[2]: *** No rule to make target `libz.a'.  Stop.
make[2]: Leaving directory `/root/ossec-hids-2.8.1/src/external/zlib-1.2.8'
make[1]: *** [libz.a] Error 2
make[1]: Leaving directory `/root/ossec-hids-2.8.1/src/external'
Error Making zlib
make: *** [all] Error 1
 Error 0x5.
 Building error. Unable to finish the installation.


```

I've tried editing the permissions in the bin folder but the same error appears.

---

### Post by bashiergui on 2015-02-28
Run the command with sudo.
If that doesn't work then change the permissions on the folder giving you the authentication errors. ```
sudo chmod 755 path/to/file
```

---

