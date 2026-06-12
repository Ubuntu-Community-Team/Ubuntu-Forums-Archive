---
title: "Riddle me this (kernel compile)"
date: 2006-12-20
forum: Server Platforms
---

### Post by Mithrilhall on 2006-12-20
I've downloaded the vanilla kernel linux-2.6.18.6.tar.gz , extracted it and changed into the directory of it.

Then I did:

```
cp /boot/config-`uname -r` ./.config
```

Then

```
make menuconfig
```

I then make changes and save the new kernel configuration.

Then I do the following and it starts to compile the new kernel.

```

make-kpkg clean
fakeroot make-kpkg --initrd --append-to-version=-newbuild1.0 kernel_image kernel_headers

```

During the new kernel compile it hangs on this
**```
CC [M] crypto/twofish.o
```**

Any clue why it hangs on this?

---

### Post by Mithrilhall on 2006-12-20
Link to config file: [.config]("http://www.apartmenthost.com/network/config.txt")

---

### Post by bernied on 2006-12-20
Are you sure it's hung, or is it just taking a long time? I believe that's a cryptographic cipher, and unless you particularly want that one, you could easily remove it from the config.

---

### Post by Mithrilhall on 2006-12-20
Well I've removed it and my compile failed.

This is last part I see of my compile errort:

```

CC [M] drivers/char/sysnclinkmp.o
drivers/char/synclinkmp.c:5648: internal compiler error: in pop_scope, at c-decl.c:837
Please submit a full bug report,
with preprocessed source if appropriate.
See <URL:http://gcc.gnu.org/bugs.html> for instructions.
For Debian GNU/Linux specific bug reporting instructions,
see <URL:file://usr/share/doc/gcc-4.0/README.Bugs>.
make[3]: *** [drivers/char/synclinkmp.o] Error1
make[2]: *** [drivers/char] Error 2
make[1]: *** [drivers] Error 2
make[1]: Leaving directory '/usr/src/linux-2.6.18.6'
make: *** [stamp-build] Error 2

```

---

### Post by bernied on 2006-12-20
Why are you compiling for every piece of hardware ever made? I think this is asking for trouble. Do you have a reason for building your own kernel? Enabling every driver will not make for a better system, it will just make for a confused system. This is the description for that particular diver (do you have this device?) ...
> config SYNCLINKMP
	tristate "SyncLink Multiport support"
	depends on SERIAL_NONSTANDARD
	help
	  Enable support for the SyncLink Multiport (2 or 4 ports)
	  serial adapter, running asynchronous and HDLC communications up
	  to 2.048Mbps. Each ports is independently selectable for
	  RS-232, V.35, RS-449, RS-530, and X.21

	  This driver may be built as a module ( = code which can be
	  inserted in and removed from the running kernel whenever you want).
	  The module will be called synclinkmp.  If you want to do that, say M
	  here.

---

### Post by Mithrilhall on 2006-12-21
I was under the impression that the config only had what I needed.

I'll start stripping stuff out then. ](*,)

---

### Post by Mithrilhall on 2006-12-21
I've downloaded a vanilla kernel and patched it with Linux layer 7 packet classifier.

I know that I need to download iptables source and patch it and compile it as well but do I need to patch and compile the kernel before I patch and compile iptables?

I know I have to at least patch the kernel first before I patch iptables.

---

### Post by bernied on 2006-12-21
Is it this kind of thing that you are doing?
[http://l7-filter.sourceforge.net/HOWTO-kernel](http://l7-filter.sourceforge.net/HOWTO-kernel)

If it is then it's patch and compile the kernel, then patch and compile iptables. But I doubt that the order really matters.

---

### Post by Mithrilhall on 2006-12-21
That is exactly what I'm doing.

What I've done so far is patch the kernel and compile it. I've also patched iptables and installed it.

I just wanted to make sure I was doing it correctly.

Thanks :-k

---

