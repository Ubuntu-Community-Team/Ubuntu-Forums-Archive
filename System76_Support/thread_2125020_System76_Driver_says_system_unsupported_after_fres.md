---
title: "System76 Driver says system unsupported after fresh 12.04 install"
date: 2013-03-12
forum: System76 Support
---

### Post by nadamsieee on 2013-03-12
My system76 meerkat recently suffered a hard drive crash.

After replacing the hard drive, I installed a fresh copy of Ubuntu 12.04.

I then tried install the System76 Driver (version 3.2.3) but got this message:

[INDENT]Your System is unsupported.
This application is desgined for System76 computers running Ubuntu versions 6.06 through 12.10. It appears your system fails one or both of these requirements. 

If you are running one of these Ubuntu versions on a System76 computer, please contact support at [www.system76.com/support](www.system76.com/support)[/INDENT]

To be clear, I got this error message after installing the system76 deb file and then trying to run the system76 application.

Halp?

**SOLVED:**

I was able to "fix" this by editing /opt/system76/system76-driver/src/model.py to accept 'To Be Filled By O.E.M.' for ment2.

It would be nice to figure out how to reset system-product-name and system-version to their expected values though.

---

### Post by nadamsieee on 2013-03-12
Here is what I get trying to run the system76-driver application from the console:
```
$ system76-driver 
NOTE: 11.10 or later detected! Running GTK3 version.
NOTE: 11.10 or later detected! Running GTK3 version.
  File "/opt/system76/system76-driver/src/System76Drivergtk3.py", line 267, in <module>
    os.system(os.system('rm /tmp/sys76-username 2>/dev/null'))
TypeError: must be string, not int
```

---

### Post by nadamsieee on 2013-03-12
Apparently the BIOS got reset?

```
$ sudo dmidecode -s system-uuid
03000200-0400-0500-0006-000700080009
$ sudo dmidecode -s system-product-name
To Be Filled By O.E.M.
$ sudo dmidecode -s system-version
To Be Filled By O.E.M.
```

Anyone know how to set these values in the BIOS?

Any harm in editing /opt/system76/system76-driver/src/model.py to accept 'To Be Filled By O.E.M.'?

---

### Post by isantop on 2013-03-13
What type of Meerkat do you have? Is it a Meerkat ION?

---

### Post by nadamsieee on 2013-03-14
> **isantop said:**
> What type of Meerkat do you have? Is it a Meerkat ION?

ment2

---

### Post by isantop on 2013-03-14
I believe you have the one system that doesn't run the System76 driver. That said, all of the drivers for your Meerkat are provided by Ubuntu, so the System76 Driver wouldn't install anything anyway.

---

