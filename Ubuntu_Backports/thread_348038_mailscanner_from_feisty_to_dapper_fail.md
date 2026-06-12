---
title: "mailscanner from feisty to dapper fail"
date: 2007-01-28
forum: Ubuntu Backports
---

### Post by frhack on 2007-01-28
Hi,
I'm trying to backport mailscanner from feisty to dapper, using "prevu mailscanner" but there is an error building the man pages (see below).
Can someone help me to solve this problem ?
Is there a way to tell prevu  to skip the man creation? 

thanks
Francesco   
---
dh_testdir
make -C debian/man
make[1]: Entering directory `/var/cache/prevu/src/3656/mailscanner-4.57.6/debian/man'
if [ ! -d build ]; then mkdir build; fi
cp Makefile.DocBook build/Makefile
xsltproc  \
 --stringparam files "MailScanner.xml d2mbox.xml df2mbox.xml update_phishing_sites.xml update_virus_scanners.xml" \
 --stringparam chunk.size 20 \
 combine.xsl combine.xsl
make -C build man \
        MAN_PARAMS="--stringparam man.output.quietly 1 \
           --stringparam refentry.meta.get.quietly 1 \
           --stringparam man.charmap.enabled 0"
I/O error : Attempt to load network entity [http://www.oasis-open.org/docbook/xml/4.4/docbookx.dtd](http://www.oasis-open.org/docbook/xml/4.4/docbookx.dtd)
../MailScanner.xml:23: warning: failed to load external entity "http://www.oasis-open.org/docbook/xml/4.4/docbookx.dtd"
]>
  ^
I/O error : Attempt to load network entity [http://www.oasis-open.org/docbook/xml/4.2/docbookx.dtd](http://www.oasis-open.org/docbook/xml/4.2/docbookx.dtd)
../d2mbox.xml:45: warning: failed to load external entity "http://www.oasis-open.org/docbook/xml/4.2/docbookx.dtd"
]>
  ^
I/O error : Attempt to load network entity [http://www.oasis-open.org/docbook/xml/4.2/docbookx.dtd](http://www.oasis-open.org/docbook/xml/4.2/docbookx.dtd)
../df2mbox.xml:45: warning: failed to load external entity "http://www.oasis-open.org/docbook/xml/4.2/docbookx.dtd"
]>

[...]

dh_installman
debian/man/build/man/man8/MailScanner.8: No such file or directory at /usr/bin/dh_installman line 116.
make: *** [binary-indep] Error 2
Copying back the cached apt archive contents
 -> unmounting dev/pts filesystem
 -> unmounting proc filesystem
 -> unmounting /var/cache/prevu/dapper-debs filesystem
 -> unmounting /var/cache/prevu/src/3656 filesystem
 -> cleaning the build env
    -> removing directory /var/cache/prevu/builds/3718 and its subdirectories
Traceback (most recent call last):
  File "/usr/bin/prevu", line 177, in ?
    BackportFromAPT(sys.argv[1],DIST).backport()
  File "/usr/bin/prevu", line 115, in backport
    self.do_compile()
  File "/usr/bin/prevu", line 96, in do_compile
    raise ValueError("Build failed.")
ValueError: Build failed.

---

