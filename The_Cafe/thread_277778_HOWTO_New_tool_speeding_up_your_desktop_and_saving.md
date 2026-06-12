---
title: "HOWTO: New tool speeding up your desktop and saving disk space"
date: 2006-10-15
forum: The Cafe
---

### Post by PCMan on 2006-10-15
I wrote a new set of tools yesterday: trans-purge
It's inspired by localepurge

In our current desktop environment, there are a lot of 
useless translations, apart from locales.
Many of them are in *.desktop files installed by each application.
Another place containing useless translations is the mime-database

Normally we only use English and our own native languages,
but there are often translations for more than 10 locales in these files,
which is a waste of disk space, and make our system slower.

There are currently 3 tools contained: desktop-purge, mime-purge, and gconf-purge.

desktop-purge will scan all installed *.desktop files on the system, 
remove useless translations, and then save it back.
Usage: Run desktop-purge directly with root access.
The main programs which benefit from this is gnome-panel and other desktop panels.
The effect is apprant. The file size loaded at system startup decrease
from 2 MB to 2xx KB.

mime-purge removes unnecessary translations from mime-database
The main programs which benefit from this are file managers.
Usage: Run mime-purge directly with root access.

gconf-purge will remove useless translations in gconf schema, which saves 20 MB or so on my system.
Usage: Run gconf-purge directly with root access.

All unnecessary translations will be removed (Without backup)
The reserved translations contains English and the locale currently used.

Download URL:
[http://pcman.sayya.org/desktop-purge.c](http://pcman.sayya.org/desktop-purge.c)
[http://pcman.sayya.org/mime-purge.c](http://pcman.sayya.org/mime-purge.c)
[http://pcman.sayya.org/gconf-purge.c](http://pcman.sayya.org/gconf-purge.c)

To compile, type following commands:

gcc `pkg-config glib-2.0 --cflags --libs` -o desktop-purge desktop-purge.c

gcc `pkg-config glib-2.0 --cflags --libs` -o mime-purge mime-purge.c

gcc `pkg-config glib-2.0 --cflags --libs` -o gconf-purge gconf-purge.c

Then copy these files to /usr/bin.

Finally, I provide an automatic way.
Create this file manually: /etc/apt/apt.conf.d/99-transpurge,
and add following contents to it.

DPkg
{
Post-Invoke {"if [ $(ps w -p "$PPID" | grep -c remove) != 1 ]; then /usr/bin/desktop-purge > /dev/null; /usr/bin/mime-purge >/dev/null; /usr/bin/gconf-purge > /dev/null ; else exit 0; fi";};
};

This will purge unnecessary translations after installing packages with apt.

Warnings:
This program is released under GPL without any warranty. Use it at your own risk. (Theoratically, the most serious side-effect is translations in your language is accidentally removed, and only English left. This could happen under incorrect locale settings.)

I tested it on my system, and fonud it effective.
If you run the programs manually, it will show you how much disk space is saved.

Hope someone can create deb package for this, if there are not apparent bugs.
The package name can be trans-purge.  Cheers!

---

### Post by Nonno Bassotto on 2006-10-15
I think this is a really good idea, but I'm a little scared that I will mess things up. Moreover, will this cause any problems during upgrades?

---

### Post by PCMan on 2006-10-15
You can backup following directories, and see if it cause problems.
/usr/share/applications
/usr/share/mime
/usr/local/share/applications
/usr/local/share/mime
~/.local/share/applications
~/.local/share/mime

That's all.
Actually most people only use the first 2 directories.

If your locale is set up correctly, this should work without proplems; otherwise, only English will be left. Except this, there shouldn't be any other problem, but there is no warranty)

---

### Post by vayu on 2006-10-15
I hope this is the lag I experience with nautilus.

---

### Post by PCMan on 2006-10-15
Here comes a new tool, gconf-purge.
This can remove unnecessary translations from schema files of gconf.

---

### Post by ww2 on 2006-10-15
I installed Ubuntu in US english language. Not having any other language package present (supposedly), is this *completely* safe to use?

---

### Post by Somenoob on 2006-10-15
My Ubuntu is in English, but my keyboard is not. Will this affect the keyboard settings?

---

### Post by ww2 on 2006-10-15
> **Somenoob said:**
> My Ubuntu is in English, but my keyboard is not. Will this affect the keyboard settings?

Just compiled and used it. I also have a non-english keyboard and, as one might expect, it didn't interfere.

No noticeable performance improvement either. Probably because I have a fast computer.

---

### Post by H.E. Pennypacker on 2006-10-22
I'll download this as soon as there is precompiled version.  Thanks.

---

### Post by ~LoKe on 2006-10-22
Worked for me, no problems thus far.

---

### Post by Makyver on 2006-10-24
I keep getting that no package glib-2.0 found errors when trying to compile this ... and I don't know exactly which package to install to fix this. Has anyone else had this problem?

---

### Post by PCMan on 2006-10-26
sudo apt-get install libglib2.0-dev

---

### Post by Peepsalot on 2006-10-26
Compiled and ran ok for me.  I can't tell if there is really any difference, but I figured it couldn't hurt.  It removed ~23mb overall for me.
Cheers.

---

### Post by cic007 on 2007-03-14
Hey guys,

I'm running Edgy USBuntu (basically pretty much a copy across from the live CD with a few modifications I think) from a USB pen right now (I've got a proper ubuntu install. I simply use this as it beats using windows xp on the uni computers.

I'm hitting problems with running this. I'm not sure if it's something to do with some files someone has cut out in order to make ubuntu fit on a pen drive (hence the reason I'm trying to cut down on size).

Anyone know what I need to install to fix the following error?

```
ubuntu@ubuntu:~/Desktop$ sudo gcc `pkg-config glib-2.0 --cflags --libs` -o desktop-purge desktop-purge.c
Package glib-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `glib-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'glib-2.0' found
desktop-purge.c:27:18: error: glib.h: No such file or directory
desktop-purge.c:28:23: error: sys/types.h: No such file or directory
desktop-purge.c:29:22: error: sys/stat.h: No such file or directory
desktop-purge.c:30:19: error: fcntl.h: No such file or directory
desktop-purge.c:31:19: error: errno.h: No such file or directory
desktop-purge.c:36: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;saved_size&#8217;
desktop-purge.c:38: error: expected declaration specifiers or &#8216;...&#8217; before &#8216;gpointer&#8217;
desktop-purge.c: In function &#8216;do_purge&#8217;:
desktop-purge.c:41: error: &#8216;GDir&#8217; undeclared (first use in this function)
desktop-purge.c:41: error: (Each undeclared identifier is reported only once
desktop-purge.c:41: error: for each function it appears in.)
desktop-purge.c:41: error: &#8216;dir&#8217; undeclared (first use in this function)
desktop-purge.c:42: error: &#8216;GKeyFile&#8217; undeclared (first use in this function)
desktop-purge.c:42: error: &#8216;file&#8217; undeclared (first use in this function)
desktop-purge.c:43: error: storage size of &#8216;statbuf&#8217; isn&#8217;t known
desktop-purge.c:45: error: &#8216;NULL&#8217; undeclared (first use in this function)
desktop-purge.c:47: warning: assignment makes pointer from integer without a cast
desktop-purge.c:51: warning: assignment makes pointer from integer without a cast
desktop-purge.c:59: error: &#8216;user_data&#8217; undeclared (first use in this function)
desktop-purge.c:59: error: too many arguments to function &#8216;do_purge&#8217;
desktop-purge.c:60: error: &#8216;G_KEY_FILE_KEEP_COMMENTS&#8217; undeclared (first use in this function)
desktop-purge.c:62: error: &#8216;gsize&#8217; undeclared (first use in this function)
desktop-purge.c:62: error: expected &#8216;;&#8217; before &#8216;len&#8217;
desktop-purge.c:71: error: &#8216;len&#8217; undeclared (first use in this function)
desktop-purge.c:71: warning: assignment makes pointer from integer without a cast
desktop-purge.c:82: error: &#8216;O_CREAT&#8217; undeclared (first use in this function)
desktop-purge.c:82: error: &#8216;O_WRONLY&#8217; undeclared (first use in this function)
desktop-purge.c:82: error: &#8216;O_TRUNC&#8217; undeclared (first use in this function)
desktop-purge.c:88: error: &#8216;saved_size&#8217; undeclared (first use in this function)
desktop-purge.c:92: error: &#8216;errno&#8217; undeclared (first use in this function)
desktop-purge.c: At top level:
desktop-purge.c:114: error: expected &#8216;)&#8217; before &#8216;func&#8217;
desktop-purge.c: In function &#8216;main&#8217;:
desktop-purge.c:137: error: &#8216;NULL&#8217; undeclared (first use in this function)
desktop-purge.c:138: error: &#8216;saved_size&#8217; undeclared (first use in this function)
```

---

### Post by K.Mandla on 2007-03-26
I got the same errors compiling them under Feisty. Installing [libglib2.0-dev]("http://packages.ubuntu.com/feisty/libdevel/libglib2.0-dev") fixed it.

---

### Post by karellen on 2007-03-26
I think the speed improvement it's almost unnoticeable...and space it's neither a big problem. better delete a movie or an old .iso distro image

---

### Post by xyz on 2007-03-26
Just to make sure. I get this...is it normal? Thnx.
> th@luser:~/Desktop$ gcc `pkg-config glib-2.0 --cflags --libs` -o desktop-purge desktop-purge.c
desktop-purge.c: In function ‘do_purge’:
desktop-purge.c:47: warning: assignment discards qualifiers from pointer target type
desktop-purge.c: In function ‘main’:
desktop-purge.c:137: warning: passing argument 1 of ‘app_dirs_foreach’ from incompatible pointer type
th@luser:~/Desktop$ gcc `pkg-config glib-2.0 --cflags --libs` -o desktop-purge desktop-purge.c
desktop-purge.c: In function ‘do_purge’:
desktop-purge.c:47: warning: assignment discards qualifiers from pointer target type
desktop-purge.c: In function ‘main’:
desktop-purge.c:137: warning: passing argument 1 of ‘app_dirs_foreach’ from incompatible pointer type
th@luser:~/Desktop$ gcc `pkg-config glib-2.0 --cflags --libs` -o mime-purge mime-purge.c
mime-purge.c: In function ‘purge_file’:
mime-purge.c:49: warning: assignment makes pointer from integer without a cast
mime-purge.c:55: warning: incompatible implicit declaration of built-in function ‘strstr’
mime-purge.c:69: warning: assignment discards qualifiers from pointer target type
mime-purge.c:80: warning: assignment makes pointer from integer without a cast
mime-purge.c: In function ‘do_purge’:
mime-purge.c:116: warning: assignment discards qualifiers from pointer target type
mime-purge.c: In function ‘main’:
mime-purge.c:163: warning: passing argument 1 of ‘mime_dir_foreach’ from incompatible pointer type
th@luser:~/Desktop$ gcc `pkg-config glib-2.0 --cflags --libs` -o gconf-purge gconf-purge.c
gconf-purge.c: In function ‘purge_file’:
gconf-purge.c:48: warning: assignment makes pointer from integer without a cast
gconf-purge.c:55: warning: incompatible implicit declaration of built-in function ‘strstr’
gconf-purge.c:81: warning: assignment discards qualifiers from pointer target type
gconf-purge.c:96: warning: assignment makes pointer from integer without a cast
gconf-purge.c: In function ‘do_purge’:
gconf-purge.c:134: warning: assignment discards qualifiers from pointer target type


---

### Post by K.Mandla on 2007-04-15
> **karellen said:**
> I think the speed improvement it's almost unnoticeable...and space it's neither a big problem. better delete a movie or an old .iso distro image
Perhaps on a newer system, but if you're trying to prop up an old system or if you're working in a confined space, these can be very useful. (I mean, if your computer is working with a confined space. Not you personally. :roll: :biggrin: )

> **xyz said:**
> Just to make sure. I get this...is it normal? Thnx.
Yup. Those are okay. As long as you don't get errors, the warnings should be fine.

---

### Post by nikoola on 2008-10-19
On AMD64 Ubuntu 8.10 beta:
Desktop-purge pass OK!
Mime-purge gets Segmentation fault on file:
/usr/share/mime/packages/freedesktop.org.xml
Gconf-purge gets Segmentation fault too.

On i386 Ubuntu 8.04:
Evrithing works fine!
Thanks.

---

