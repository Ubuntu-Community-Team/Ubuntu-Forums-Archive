---
title: "Anyone Know Anything about Apache?"
date: 2007-12-30
forum: Server Platforms
---

### Post by Wangsta on 2007-12-30
Well, I'm trying to install Apache on a Xubuntu Gusty desktop I'm planning to use as a server. I downloaded and extracted Apache 2.2.6. But when I try to configure it, I get this:

```

 $ sudo ./configure --prefix=/usr/local/apache2 --enable-module=so
checking for chosen layout... Apache
checking for working mkdir -p... yes
checking build system type... i686-pc-linux-gnulibc1
checking host system type... i686-pc-linux-gnulibc1
checking target system type... i686-pc-linux-gnulibc1

Configuring Apache Portable Runtime library ...

checking for APR... reconfig
configuring package in srclib/apr now
checking build system type... i686-pc-linux-gnulibc1
checking host system type... i686-pc-linux-gnulibc1
checking target system type... i686-pc-linux-gnulibc1
Configuring APR library
Platform: i686-pc-linux-gnulibc1
checking for working mkdir -p... yes
APR Version: 1.2.11
checking for chosen layout... apr
checking for gcc... gcc
[B]checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.
configure failed for srclib/apr[/B]

```

does anyone know how to make my "C compiler" create executables, 
or how to fix this?
:confused::confused::confused:

---

### Post by tehet on 2007-12-30
Do you have any reason not to install the one from the repository?

---

### Post by Wangsta on 2007-12-30
I want to have "mod_so" compiled into apache, but I don't know how to do that. 
Could you enlighten me on this topic?

---

### Post by PartickThistle on 2007-12-30
mod_so is already compiled into the repo version.  

```
sudo apt-get install apache2
``` to install.

---

### Post by Wangsta on 2007-12-31
oh great!
thanks

---

