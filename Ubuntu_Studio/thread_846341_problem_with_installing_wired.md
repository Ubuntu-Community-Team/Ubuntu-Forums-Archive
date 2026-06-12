---
title: "problem with installing wired"
date: 2008-07-01
forum: Ubuntu Studio
---

### Post by tsillbill on 2008-07-01
when i use the ./autogen.sh command in the terminal the last line say 

Copying file config/mkinstalldirs
+ aclocal --force -I config/m4
./autogen.sh: 1: aclocal: not found
+ set +x

afther that when i try to use ./configure it says bash: ./configure: No such file or directory the folder has a configure.ac faile in it.

what could be the problem?

---

### Post by Stochastic on 2008-07-01
You've given the last line of the ./autogen.sh file, but what you should be looking for is the first error message.  The output should look something in the format:

things going fine
things going fine
things going fine
things going fine
things going fine
things going fine
things going fine
Oh no, error: file not found!   <- tell us this line
Oh no, error: file not found!
Oh no, error: file not found!
Oh no, error: file not found!
Oh no, error: file not found!
Oh no, error: file not found!
Oh no, error: file not found!

What you should give us is that first error message.  Fix all error messages before continuing with the install (i.e. before you try ./configure).

---

### Post by tsillbill on 2008-07-02
i didnt see eny more errors.

heres the the text
silver@silver-laptop:~$ cd '/home/silver/Dokumendid/wired-0.6' 
silver@silver-laptop:~/Dokumendid/wired-0.6$ ./autogen.sh
+ rm -rf config
+ rm -f aclocal.m4 configure config.log config.status
+ rm -rf autom4te*.cache
+ rm -f libtool
+ rm -f ABOUT-NLS
+ rm -rf intl
+ mkdir config
+ mkdir intl
+ autopoint -f
Copying file ABOUT-NLS
Copying file config/config.rpath
Copying file intl/ChangeLog
Copying file intl/Makefile.in
Copying file intl/VERSION
Copying file intl/bindtextdom.c
Copying file intl/config.charset
Copying file intl/dcgettext.c
Copying file intl/dcigettext.c
Copying file intl/dcngettext.c
Copying file intl/dgettext.c
Copying file intl/dngettext.c
Copying file intl/eval-plural.h
Copying file intl/explodename.c
Copying file intl/finddomain.c
Copying file intl/gettext.c
Copying file intl/gettextP.h
Copying file intl/gmo.h
Copying file intl/hash-string.h
Copying file intl/intl-compat.c
Copying file intl/l10nflist.c
Copying file intl/langprefs.c
Copying file intl/libgnuintl.h.in
Copying file intl/loadinfo.h
Copying file intl/loadmsgcat.c
Copying file intl/localcharset.c
Copying file intl/localcharset.h
Copying file intl/locale.alias
Copying file intl/localealias.c
Copying file intl/localename.c
Copying file intl/log.c
Copying file intl/ngettext.c
Copying file intl/os2compat.c
Copying file intl/os2compat.h
Copying file intl/osdep.c
Copying file intl/plural-exp.c
Copying file intl/plural-exp.h
Copying file intl/plural.c
Copying file intl/plural.y
Copying file intl/printf-args.c
Copying file intl/printf-args.h
Copying file intl/printf-parse.c
Copying file intl/printf-parse.h
Copying file intl/printf.c
Copying file intl/ref-add.sin
Copying file intl/ref-del.sin
Copying file intl/relocatable.c
Copying file intl/relocatable.h
Copying file intl/textdomain.c
Copying file intl/vasnprintf.c
Copying file intl/vasnprintf.h
Copying file intl/vasnwprintf.h
Copying file intl/wprintf-parse.h
Copying file intl/xsize.h
Creating directory config/m4
Copying file config/m4/codeset.m4
Copying file config/m4/gettext.m4
Copying file config/m4/glibc2.m4
Copying file config/m4/glibc21.m4
Copying file config/m4/iconv.m4
Copying file config/m4/intdiv0.m4
Copying file config/m4/intmax.m4
Copying file config/m4/inttypes-pri.m4
Copying file config/m4/inttypes.m4
Copying file config/m4/inttypes_h.m4
Copying file config/m4/isc-posix.m4
Copying file config/m4/lcmessage.m4
Copying file config/m4/lib-ld.m4
Copying file config/m4/lib-link.m4
Copying file config/m4/lib-prefix.m4
Copying file config/m4/longdouble.m4
Copying file config/m4/longlong.m4
Copying file config/m4/nls.m4
Copying file config/m4/po.m4
Copying file config/m4/printf-posix.m4
Copying file config/m4/progtest.m4
Copying file config/m4/signed.m4
Copying file config/m4/size_max.m4
Copying file config/m4/stdint_h.m4
Copying file config/m4/uintmax_t.m4
Copying file config/m4/ulonglong.m4
Copying file config/m4/wchar_t.m4
Copying file config/m4/wint_t.m4
Copying file config/m4/xsize.m4
Copying file config/mkinstalldirs
+ aclocal --force -I config/m4
./autogen.sh: 1: aclocal: not found
+ set +x
silver@silver-laptop:~/Dokumendid/wired-0.6$

---

### Post by tsillbill on 2008-07-03
bump

still need help.

---

### Post by Stochastic on 2008-07-03
looks like you need to install aclocal, which is part of the automake package ```
sudo apt-get install automake
```

---

### Post by ghostandmachine on 2008-08-10
I've been having the same problems. apt-get automake and now I'm getting this error.

```
+ aclocal --force -I config/m4
+ libtoolize --force -c
./autogen.sh: 1: libtoolize: not found
+ set +x

```

been looking around. can't even find any info on what libtoolize is/does.

---

### Post by theblackkat on 2008-08-11
apt-get install libtool
(or was it libtools?)
anyway, this will solve your problem, but you'll problably end up having this one, like me:
[http://ubuntuforums.org/showthread.php?t=851277&highlight=wired](http://ubuntuforums.org/showthread.php?t=851277&highlight=wired)
:(

---

