---
title: "gzip: compressed data not written to a terminal error in rebuilding openoffice.org"
date: 2007-01-03
forum: Repositories &amp; Backports
---

### Post by paulajulienne on 2007-01-03
I am rebuilding openoffice.org in kubuntu dapper, I was able to build it at first, but after I tried to rebuild it again it pru\oduces this error:
gzip: compressed data not written to a terminal. Use -f to force compression.
I've tried upgrading gzip, but it's no use....     
Does anyone know how to resolve this error?  I will really appreciate your help.
Thanks.
Please see the output below:

> 
#mv debian/openoffice.org-base/usr/share/applications/ooo-base.desk
top debian/openoffice.org-core/usr/share/applications
#rm -r debian/openoffice.org-base
# compress manpages
for i in calc math draw writer impress base; do \
                find debian/openoffice.org-$i -type f -name "*.1" |                                                                         xargs gzip -9; \
        done
gzip: compressed data not written to a terminal. Use -f to force compression.
For help, type: gzip -h
gzip: compressed data not written to a terminal. Use -f to force compression.
For help, type: gzip -h
gzip: compressed data not written to a terminal. Use -f to force compression.
For help, type: gzip -h
gzip: compressed data not written to a terminal. Use -f to force compression.
For help, type: gzip -h
gzip: compressed data not written to a terminal. Use -f to force compression.
For help, type: gzip -h
gzip: compressed data not written to a terminal. Use -f to force compression.
For help, type: gzip -h
make: *** [debian/stampdir/install-arch] Error 123
[/color]


---

