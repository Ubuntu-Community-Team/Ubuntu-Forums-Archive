---
title: "[SOLVED] gutenprint 5.1.7 drivers"
date: 2008-05-05
forum: Server Platforms
---

### Post by Nxion on 2008-05-05
OK, I setup a CUPS server and the issue I have is that once I setup my printer on the server it added fine. The problem is when I print something or just a test print, It just spits out page after page of blank. I did some digging and it looks like the 5.0.2 drivers that come with CUPS is the cause of the issue.

I downloaded the gutenprint 5.1.7 driver and i ran ./configure and make then make install. all looks well after it completes. When I restart the CUPS server the new deivers do not show up. Am I doing something wrong ? Am I missing a step?

The other thing I noticed is when I do a ./configure the output is this:
```

Configuration Summary:
------------- --------

If you have any problems, please report the information below to
gimp-print-devel@lists.sourceforge.net

================================================================
  Release: gutenprint 5.1.7 generated on 05 Mar 2008

  Features:
    Build CUPS:                                 no
    Build Ghostscript IJS driver:               no
    Build Foomatic data:                        no
    Build enhanced Print plugin for GIMP:       no
    Build EPSON Stylus utility:                 yes
    Build test programs:                        yes
    Build testpattern generator:                yes

Installation summary:
    Installation prefix:                        /usr/local
    Data directory:                             /usr/local/share/gutenprint
    Library directory:                          /usr/local/lib/gutenprint
    XML data directory:                         /usr/local/share/gutenprint/5.1.7/xml
    Module directory:                           /usr/local/lib/gutenprint/5.1.7/modules
    Install sample images:                      yes

General configuration:
    Compiler options:                           -Disfinite=finite  -O6  -Wall -Wcast-align -Wstrict-prototypes -Wmissing-prototypes -Wmissing-declarations -Wnested-externs -Wwrite-strings -Werror-implicit-function-declaration -Winline -Wformat=2 -finline-limit=131072
    Build static libraries:                     yes
    Build shared libraries:                     yes
    Maintainer mode:                            no
    Use i18n:                                   yes
    Generate profiling information:             no
    Generate debugging symbols:                 no
    Use modules:                                static
    Use readline libraries:                     yes
================================================================

Finished configuring.  Please review the configuration summary above.
Type 'make clean' followed by 'make' to build the package
then 'make install' to install it.
```

Can it be it is not adding the drivers because it is not running "Build CUPS:" Or am I wrong.

Thanks

---

### Post by Nxion on 2008-05-09
Any one?

---

### Post by Nxion on 2008-08-18
Looks like I will just have to buy a new printer, one that is more compatible with Ubuntu.

---

