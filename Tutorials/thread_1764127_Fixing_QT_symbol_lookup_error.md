---
title: "Fixing QT symbol lookup error"
date: 2011-05-21
forum: Tutorials
---

### Post by WitchCraft on 2011-05-21
When you have tried to run skype or other QT applications, like VLC, you might have encountered this error message:

```

skype: symbol lookup error: /usr/lib/libQtDBus.so.4: undefined symbol: _ZN14QObjectPrivate15checkWindowRoleEv

```


You might then have done
```

apt-file search libQtDBus.so.4

```

which yields
> 
libqt4-dbg: /usr/lib/debug/usr/lib/libQtDBus.so.4.7.0
libqt4-dbus: /usr/lib/libQtDBus.so.4
libqt4-dbus: /usr/lib/libQtDBus.so.4.7
libqt4-dbus: /usr/lib/libQtDBus.so.4.7.0


And you would then have wrongly assumed that 
```

apt-get install --reinstall libqt4-dbus

```
might solve that problem.


Well, bad luck, it doesn't.

You might then have searched google, and found that this is because of a missing 32-bit library on 64-bit systems.

So the installation of the missing 32-bit library might then solve your problem.

If you're on a 64-bit system, that's most likely the case.

But that's just too bad if you're on a 32 bit system, and you hence can't be missing a 32-bit library.

So you might then have done
```

ldd -r /usr/lib/libQt*.so.*

```
And discovered that the entire qt package is broken.
Well, without you doing anything (well almost).

Here's how to find and fix that kind of bugs:


First, make sure qt4config is installed:
```

apt-get install qt4-qtconfig

```

Now use the linux loader to view which shared libraries are used:
```

ldd /usr/bin/qtconfig-qt4

```

Alternatively, you can also try this on kde4-config
```

ldd /usr/bin/kde4-config 

```


Which should output something like this:
> 
ldd /usr/bin/kde4-config 
	linux-gate.so.1 =>  (0x004e3000)
	libkdecore.so.5 => /usr/lib/libkdecore.so.5 (0x00110000)
	libQtDBus.so.4 => /usr/lib/libQtDBus.so.4 (0x0075e000)
	libQtCore.so.4 => /opt/google/earth/free/libQtCore.so.4 (0x00c32000)
	libpthread.so.0 => /lib/libpthread.so.0 (0x00adf000)
	libstdc++.so.6 => /usr/lib/libstdc++.so.6 (0x007eb000)
	libm.so.6 => /lib/libm.so.6 (0x00396000)
	libgcc_s.so.1 => /lib/libgcc_s.so.1 (0x003bc000)
	libc.so.6 => /lib/libc.so.6 (0x004e4000)
	libQtNetwork.so.4 => /opt/google/earth/free/libQtNetwork.so.4 (0x0094a000)
	libQtXml.so.4 => /usr/lib/libQtXml.so.4 (0x003d8000)
	libz.so.1 => /lib/libz.so.1 (0x0041b000)
	libbz2.so.1.0 => /lib/libbz2.so.1.0 (0x00430000)
	liblzma.so.2 => /usr/lib/liblzma.so.2 (0x00442000)
	libresolv.so.2 => /lib/libresolv.so.2 (0x00465000)
	libdl.so.2 => /lib/libdl.so.2 (0x00479000)
	librt.so.1 => /lib/librt.so.1 (0x0047d000)
	/lib/ld-linux.so.2 (0x0092c000)


Now looking at it, you see:
> 
	libQtDBus.so.4 => /usr/lib/libQtDBus.so.4 (0x0075e000)


And

> 
	libQtCore.so.4 => /opt/google/earth/free/libQtCore.so.4 


The first one looks OK, but the second one is strange, since this is not google-earth, it should use libQtCore from /usr/lib, and not from /opt/google.

One can only follow that the google installer has done something stupid.

So now, in order to fix the problem, you move to
/opt/google/earth

and rename folder "free" to "freeZZZ"

Now you can re-run ldd and you will see that the problem is now fixed (apart from the fact that google-earth doesn't run anymore.


> 
	linux-gate.so.1 =>  (0x001ba000)
	libkdecore.so.5 => /usr/lib/libkdecore.so.5 (0x00b6e000)
	libQtDBus.so.4 => /usr/lib/libQtDBus.so.4 (0x00e8e000)
	libQtCore.so.4 => /usr/lib/libQtCore.so.4 (0x004f5000)
	libpthread.so.0 => /lib/libpthread.so.0 (0x00110000)
	libstdc++.so.6 => /usr/lib/libstdc++.so.6 (0x002aa000)
	libm.so.6 => /lib/libm.so.6 (0x0012a000)
	libgcc_s.so.1 => /lib/libgcc_s.so.1 (0x00150000)
	libc.so.6 => /lib/libc.so.6 (0x00943000)
	libQtNetwork.so.4 => /usr/lib/libQtNetwork.so.4 (0x003c9000)
	libQtXml.so.4 => /usr/lib/libQtXml.so.4 (0x0016c000)
	libz.so.1 => /lib/libz.so.1 (0x001bb000)
	libbz2.so.1.0 => /lib/libbz2.so.1.0 (0x001d0000)
	liblzma.so.2 => /usr/lib/liblzma.so.2 (0x007e1000)
	libresolv.so.2 => /lib/libresolv.so.2 (0x001e2000)
	libdl.so.2 => /lib/libdl.so.2 (0x001af000)
	libgthread-2.0.so.0 => /usr/lib/libgthread-2.0.so.0 (0x00fe3000)
	librt.so.1 => /lib/librt.so.1 (0x00b06000)
	libglib-2.0.so.0 => /lib/libglib-2.0.so.0 (0x00804000)
	/lib/ld-linux.so.2 (0x003ab000)
	libpcre.so.3 => /lib/libpcre.so.3 (0x001f6000)



You will notice that now, Skype and VLC work.
And if you need google-earth again, just rename 
/opt/google/earth/freeZZZ
back to its original name
/opt/google/earth/freeZZZ

and google-earth will run again (but VLC and skype will then again be broken until you rename the folder again).

---

### Post by tutubarra on 2012-04-21
Here is better fix
login as root then go to /etc/ld.so.conf.d
now create vlc.conf
conf file just need this: 
/usr/lib

---

