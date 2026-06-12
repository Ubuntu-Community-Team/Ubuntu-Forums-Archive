---
title: "Berkeley DB Installation Problem"
date: 2008-10-13
forum: Server Platforms
---

### Post by wgregori on 2008-10-13
I'm trying to install "Berkeley DB" on my ubuntu server.  The docs for Berkeley DB specify to run the make command... When I do I get the following message:
make: *** No targets specified and no makefile found.  Stop.

I've never used the Make command... to install the command I dis "apt-get make install"  Are there additional steps too?

~~~~~~~~~~~~~~ snippet from Berkeley DB Install Docs ~~~~~~~~

The Berkeley DB distribution uses the Free Software Foundation's autoconf and libtool tools to build on UNIX platforms. In general, the standard configuration and installation options for these tools apply to the Berkeley DB distribution.

To do a standard UNIX build of Berkeley DB, change to the build_unix directory and then enter the following two commands:

    ../dist/configure
    make
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


Thanks,
Wayne

---

### Post by lykwydchykyn on 2008-10-13
Did you do dist/configure first?  And did it complete without errors?

---

### Post by wgregori on 2008-10-13
> **lykwydchykyn said:**
> Did you do dist/configure first?  And did it complete without errors?

Funny you asked... it did not complete successfully (thought it did)

configure: error: no acceptable C compiler found in $PATH
See `config.log' for more details.

I'm trying to load a C compiler now... you don't happen to have the necessary apt-get command line?

Thank you.
Wayne

---

### Post by wgregori on 2008-10-13
I found what I need to do this compile

apt-get install build-essential

Thanks

---

