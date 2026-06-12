---
title: "LD_LIBRARY_PATH problem with Apache"
date: 2010-08-05
forum: Server Platforms
---

### Post by Saorex on 2010-08-05
Hi guys.

I compiled a PHP module named sapnwrfc, and this module needs the environment variable LD_LIBRARY_PATH to be set to:

```
LD_LIBRARY_PATH=/usr/sap/nwrfcsdk/lib/
```

So I tried editing the .bashrc file in my home directory adding the following at the end (then loging out and loging in):

```
LD_LIBRARY_PATH=/usr/sap/nwrfcsdk/lib/
export LD_LIBRARY_PATH
```

When I type "env" in a bash shell, the variable is set. But whenever I try running my PHP script from Firefox, I get a missing files error message in Apache's error.log, ending with:

```
LD_LIBRARY_PATH is currently set to <not set>
```

My guess is that I should not set the variable in .bashrc, but somewhere else. I just don't know where.

Thanks a lot for your help, as always.

---

### Post by Saorex on 2010-08-05
Ok... Still working on this problem, I added the following in my PHP script:

```
putenv("LD_LIBRARY_PATH=/usr/sap/nwrfcsdk/")
```

And also chmodded all required library files to 755. Now I the error message I get is:

> The following files must be in the path described by
   the environment variable "LD_LIBRARY_PATH":
   libicuuc.so.34, libicudata.so.34, libicui18n.so.34 [nlsui0_mt.c 1529] pid = 28958
LD_LIBRARY_PATH is currently set to /usr/sap/nwrfcsdk/lib/

And I really don't get it because this path leads directly to the required libraries...

Any clues?

---

### Post by Saorex on 2010-08-05
I just tried

```
ldd sapnwrfc.so
```

and got this for output:

```

	linux-vdso.so.1 =>  (0x00007fffd3fff000)
	libsapucum.so => /usr/sap/nwrfcsdk/lib/libsapucum.so (0x00007f8651d99000)
	libsapnwrfc.so => /usr/sap/nwrfcsdk/lib/libsapnwrfc.so (0x00007f865169b000)
	libc.so.6 => /lib/libc.so.6 (0x00007f86512fd000)
	libdl.so.2 => /lib/libdl.so.2 (0x00007f86510f9000)
	librt.so.1 => /lib/librt.so.1 (0x00007f8650ef1000)
	libstdc++.so.6 => /usr/lib/libstdc++.so.6 (0x00007f8650bdc000)
	libm.so.6 => /lib/libm.so.6 (0x00007f8650959000)
	libgcc_s.so.1 => /lib/libgcc_s.so.1 (0x00007f8650742000)
	libpthread.so.0 => /lib/libpthread.so.0 (0x00007f8650524000)
	/lib64/ld-linux-x86-64.so.2 (0x00007f8652133000)
```

...so none of these libs cause the problem. But now that I look into this, shouldn't libicuuc.so.34, libicudata.so.34, and libicui18n.so.34 be in this list?

Thanks for any idea you might have.

---

### Post by Saorex on 2010-08-05
Hoping this might help someone someday, here's how I fixed the problem with the precious help of Pierce Harding, the module's author.

I created a file:

```
/etc/ld.so.conf.d/sapnwrfc.conf
```

containing this one and only line:

```
/usr/sap/nwrfcsdk/lib
```

Then:

```
sudo ldconfig
sudo /etc/init.d/apache2 restart
```

Now it works like a charm.

---

