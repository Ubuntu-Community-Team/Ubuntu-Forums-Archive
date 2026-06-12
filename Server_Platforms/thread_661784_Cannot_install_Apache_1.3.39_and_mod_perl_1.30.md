---
title: "Cannot install Apache 1.3.39 and mod_perl 1.30"
date: 2008-01-08
forum: Server Platforms
---

### Post by auzzie on 2008-01-08
I am currently trying to install the two above mentioned programs from source, i know the apache source is outdated by it is required by the company that i am working with for compatibility reasons with the programs that they run.
running the following command
```
perl Makefile.PL APACHE_SRC=../apache_1.3.39/src APACHE_PREFIX=/home/dinah/APACHE DO_HTTPD=1 USE_APACI=1 APACI_ARGS='--enable-shared=access --enable-shared=alias --enable-shared=auth --enable-shared=env --enable-shared=log_config --enable-shared=mime --enable-shared=dir --enable-module=rewrite --enable-module=so' EVERYTHING=1

```

Has no problems but as soon as i type make i get the following error

(cd ../apache_1.3.39 && PERL5LIB=/home/marc/src/mod_perl-1.30/lib: make)
make[1]: Entering directory `/home/marc/src/apache_1.3.39'
===> src
make[2]: Entering directory `/home/marc/src/apache_1.3.39'
make[3]: Entering directory `/home/marc/src/apache_1.3.39/src'
make[3]: *** No rule to make target `all'. Stop.
make[3]: Leaving directory `/home/marc/src/apache_1.3.39/src'
make[2]: *** [build-std] Error 2
make[2]: Leaving directory `/home/marc/src/apache_1.3.39'
make[1]: *** [build] Error 2
make[1]: Leaving directory `/home/marc/src/apache_1.3.39'
make: *** [apaci_httpd] Error 2

Now i have no idea what is wrong, i have google'd it with no avail so any help would be very much appreciated.

---

### Post by auzzie on 2008-01-11
bump... please, anyone?

---

