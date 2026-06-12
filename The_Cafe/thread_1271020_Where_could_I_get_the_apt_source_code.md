---
title: "Where could I get the apt source code??"
date: 2009-09-20
forum: The Cafe
---

### Post by dragos240 on 2009-09-20
Just wondering. This is not a support question.

---

### Post by ibuclaw on 2009-09-20
```
apt-get source apt
```
It is written in C++, and you need to have deb-src repositories enabled to download it using the above command.

---

### Post by Tibuda on 2009-09-20
You can get any package source code in Ubuntu by typing (without sudo):
```
apt-get source packagename
```

---

### Post by dragos240 on 2009-09-20
What if I don't have ubuntu or a debian based system? I mean, the src in tar.gz or bz2 format.

---

### Post by sisco311 on 2009-09-20
you can download the packages from: [http://packages.ubuntu.com/]("http://packages.ubuntu.com/")


i.e. apt:
[http://packages.ubuntu.com/source/karmic/apt]("http://packages.ubuntu.com/source/karmic/apt")

---

### Post by dragos240 on 2009-09-20
I dont have apt, remember?

---

### Post by sisco311 on 2009-09-20
> **dragos240 said:**
> I dont have apt, remember?
you only need a web browser and a working internet connection. ;)

just go to: [http://packages.ubuntu.com/]("http://packages.ubuntu.com/") 
and search for the source package you want to download:
[img]http://www.upload3r.com/serve/200909/1253459519.png[/img]

---

### Post by Tibuda on 2009-09-20
> **dragos240 said:**
> I dont have apt, remember?

That's why he suggested HTTP.

---

### Post by itreius on 2009-09-20
> **dragos240 said:**
> I dont have apt, remember?

The pages he linked to contain URLs from where you can download the source.

---

### Post by FuturePilot on 2009-09-20
> **dragos240 said:**
> I dont have apt, remember?

At the bottom of the page

> **sisco311 said:**
> 
[http://packages.ubuntu.com/source/karmic/apt]("http://packages.ubuntu.com/source/karmic/apt")

---

### Post by dragos240 on 2009-09-20
oops. Thanks!

---

### Post by dragos240 on 2009-09-20
Any way I can get around this?
```

checking debian architecture... ./configure: line 4834: dpkg-architecture: command not found
configure: error: failed: use --host= or output from dpkg-architecture

```

---

### Post by ibuclaw on 2009-09-20
What OS are you using?

I think Fedora and Slackware distributions have their own port of apt.

If you aren't using a variant of the above mentioned systems, you could try the following:
```
sed -i '4834{s/^\(archset=\).*$/\1"i386"/}' configure
```
and then run **./configure**.

The above assumes you are running a 32bit x86 system though.

Regards
Iain

---

### Post by Bachstelze on 2009-09-20
> **dragos240 said:**
> Any way I can get around this?
```

checking debian architecture... ./configure: line 4834: dpkg-architecture: command not found
configure: error: failed: use --host= or output from dpkg-architecture

```

You need to install dpkg first.

---

### Post by dragos240 on 2009-09-20
> **tinivole said:**
> What OS are you using?

I think Fedora and Slackware distributions have their own port of apt.

If you aren't using a variant of the above mentioned systems, you could try the following:
```
sed -i '4834{s/^\(archset=\).*$/\1"i386"/}' configure
```and then run **./configure**.

The above assumes you are running a 32bit x86 system though.

Regards
Iain

That worked!

EDIT: I'm using 64 bit archlinux. I need a few apt packages. Just to make it a little easier. Pacman is good and all.... but the ubuntu repo has some packages I would like.

---

### Post by Bachstelze on 2009-09-20
> **dragos240 said:**
> That worked!

Apt is not going to work anyway without dpkg...

---

### Post by dragos240 on 2009-09-20
> **Bachstelze said:**
> You need to install dpkg first.

Done.

---

### Post by dragos240 on 2009-09-20
How do I fix this?
```

Installing apt-key to /root/apt-0.7.21ubuntu1/bin
Installing apt-mark to /root/apt-0.7.21ubuntu1/bin
Installing apt-report-mirror-failure to /root/apt-0.7.21ubuntu1/bin
Generating C format header file for translation.
Wrote apt-auth-failure.note.h
Compiling apt-ftparchive.cc to /root/apt-0.7.21ubuntu1/obj/ftparchive/apt-ftparchive.o
Compiling cachedb.cc to /root/apt-0.7.21ubuntu1/obj/ftparchive/cachedb.o
cachedb.cc: In member function ‘bool CacheDB::GetFileInfo(std::string, bool, bool, bool, bool, bool, bool)’:
cachedb.cc:186: warning: suggest parentheses around ‘&&’ within ‘||’
cachedb.cc:187: warning: suggest parentheses around ‘&&’ within ‘||’
cachedb.cc:188: warning: suggest parentheses around ‘&&’ within ‘||’
cachedb.cc:189: warning: suggest parentheses around ‘&&’ within ‘||’
Compiling writer.cc to /root/apt-0.7.21ubuntu1/obj/ftparchive/writer.o
Compiling contents.cc to /root/apt-0.7.21ubuntu1/obj/ftparchive/contents.o
Compiling override.cc to /root/apt-0.7.21ubuntu1/obj/ftparchive/override.o
Compiling multicompress.cc to /root/apt-0.7.21ubuntu1/obj/ftparchive/multicompress.o
Building program /root/apt-0.7.21ubuntu1/bin/apt-ftparchive
Installing desc.apt to /root/apt-0.7.21ubuntu1/scripts/dselect
Installing install to /root/apt-0.7.21ubuntu1/scripts/dselect
Installing names to /root/apt-0.7.21ubuntu1/scripts/dselect
Installing setup to /root/apt-0.7.21ubuntu1/scripts/dselect
Installing update to /root/apt-0.7.21ubuntu1/scripts/dselect
Installing examples/apt.conf to /root/apt-0.7.21ubuntu1/docs/examples
Installing examples/sources.list to /root/apt-0.7.21ubuntu1/docs/examples
Installing examples/configure-index to /root/apt-0.7.21ubuntu1/docs/examples
Installing examples/apt-https-method-example.conf to /root/apt-0.7.21ubuntu1/docs/examples
Installing man page apt_preferences.pt_BR.5 to /root/apt-0.7.21ubuntu1/docs
Installing man page apt-cache.es.8 to /root/apt-0.7.21ubuntu1/docs
Installing man page apt-get.es.8 to /root/apt-0.7.21ubuntu1/docs
Installing man page apt-cdrom.es.8 to /root/apt-0.7.21ubuntu1/docs
Installing man page apt.conf.es.5 to /root/apt-0.7.21ubuntu1/docs
Installing man page sources.list.es.5 to /root/apt-0.7.21ubuntu1/docs
Installing man page apt-config.es.8 to /root/apt-0.7.21ubuntu1/docs
Installing man page apt_preferences.es.5 to /root/apt-0.7.21ubuntu1/docs
Generating POT file /root/apt-0.7.21ubuntu1/po/apt.pot Generating POT file /root/apt-0.7.21ubuntu1/po/libapt-inst1.1.pot Generating POT file /root/apt-0.7.21ubuntu1/po/libapt-pkg4.7.pot Generating /root/apt-0.7.21ubuntu1/po/domains/apt/ar.po ........................... done.
Generating /root/apt-0.7.21ubuntu1/locale/ar/LC_MESSAGES/apt.mo: 157 translated messages, 10 fuzzy translations, 73 untranslated messages.
Generating /root/apt-0.7.21ubuntu1/po/domains/apt/bg.po ........................... done.
Generating /root/apt-0.7.21ubuntu1/locale/bg/LC_MESSAGES/apt.mo: 233 translated messages, 2 fuzzy translations, 5 untranslated messages.
Generating /root/apt-0.7.21ubuntu1/po/domains/apt/bs.po ........................... done.
Generating /root/apt-0.7.21ubuntu1/locale/bs/LC_MESSAGES/apt.mo: 54 translated messages, 9 fuzzy translations, 177 untranslated messages.
Generating /root/apt-0.7.21ubuntu1/po/domains/apt/ca.po ........................... done.
Generating /root/apt-0.7.21ubuntu1/locale/ca/LC_MESSAGES/apt.mo: 234 translated messages, 2 fuzzy translations, 4 untranslated messages.
Generating /root/apt-0.7.21ubuntu1/po/domains/apt/cs.po ........................... done.
Generating /root/apt-0.7.21ubuntu1/locale/cs/LC_MESSAGES/apt.mo: 233 translated messages, 2 fuzzy translations, 5 untranslated messages.
Generating /root/apt-0.7.21ubuntu1/po/domains/apt/cy.po ........................... done.
Generating /root/apt-0.7.21ubuntu1/locale/cy/LC_MESSAGES/apt.mo: 160 translated messages, 63 fuzzy translations, 17 untranslated messages.
Generating /root/apt-0.7.21ubuntu1/po/domains/apt/da.po ........................... done.
Generating /root/apt-0.7.21ubuntu1/locale/da/LC_MESSAGES/apt.mo: 227 translated messages, 7 fuzzy translations, 6 untranslated messages.
Generating /root/apt-0.7.21ubuntu1/po/domains/apt/de.po ........................... done.
Generating /root/apt-0.7.21ubuntu1/locale/de/LC_MESSAGES/apt.mo: 233 translated messages, 2 fuzzy translations, 5 untranslated messages.
Generating /root/apt-0.7.21ubuntu1/po/domains/apt/dz.po ........................... done.
Generating /root/apt-0.7.21ubuntu1/locale/dz/LC_MESSAGES/apt.mo: 219 translated messages, 12 fuzzy translations, 9 untranslated messages.
Generating /root/apt-0.7.21ubuntu1/po/domains/apt/el.po ........................... done.
Generating /root/apt-0.7.21ubuntu1/locale/el/LC_MESSAGES/apt.mo: 232 translated messages, 3 fuzzy translations, 5 untranslated messages.
Generating /root/apt-0.7.21ubuntu1/po/domains/apt/en_GB.po ........................... done.
Generating /root/apt-0.7.21ubuntu1/locale/en_GB/LC_MESSAGES/apt.mo: 233 translated messages, 2 fuzzy translations, 5 untranslated messages.
Generating /root/apt-0.7.21ubuntu1/po/domains/apt/es.po ........................... done.
Generating /root/apt-0.7.21ubuntu1/locale/es/LC_MESSAGES/apt.mo: 233 translated messages, 2 fuzzy translations, 5 untranslated messages.
Generating /root/apt-0.7.21ubuntu1/po/domains/apt/eu.po ........................... done.
Generating /root/apt-0.7.21ubuntu1/locale/eu/LC_MESSAGES/apt.mo: 233 translated messages, 2 fuzzy translations, 5 untranslated messages.
Generating /root/apt-0.7.21ubuntu1/po/domains/apt/fi.po ........................... done.
Generating /root/apt-0.7.21ubuntu1/locale/fi/LC_MESSAGES/apt.mo: 233 translated messages, 2 fuzzy translations, 5 untranslated messages.
Generating /root/apt-0.7.21ubuntu1/po/domains/apt/fr.po ........................... done.
Generating /root/apt-0.7.21ubuntu1/locale/fr/LC_MESSAGES/apt.mo: 234 translated messages, 2 fuzzy translations, 4 untranslated messages.
Generating /root/apt-0.7.21ubuntu1/po/domains/apt/gl.po ........................... done.
Generating /root/apt-0.7.21ubuntu1/locale/gl/LC_MESSAGES/apt.mo: 233 translated messages, 2 fuzzy translations, 5 untranslated messages.
Generating /root/apt-0.7.21ubuntu1/po/domains/apt/he.po .......................... done.
Generating /root/apt-0.7.21ubuntu1/locale/he/LC_MESSAGES/apt.mo: 78 translated messages, 11 fuzzy translations, 151 untranslated messages.
Generating /root/apt-0.7.21ubuntu1/po/domains/apt/hu.po ........................... done.
Generating /root/apt-0.7.21ubuntu1/locale/hu/LC_MESSAGES/apt.mo: 232 translated messages, 3 fuzzy translations, 5 untranslated messages.
Generating /root/apt-0.7.21ubuntu1/po/domains/apt/it.po ........................... done.
Generating /root/apt-0.7.21ubuntu1/locale/it/LC_MESSAGES/apt.mo: 234 translated messages, 2 fuzzy translations, 4 untranslated messages.
Generating /root/apt-0.7.21ubuntu1/po/domains/apt/ja.po ........................... done.
Generating /root/apt-0.7.21ubuntu1/locale/ja/LC_MESSAGES/apt.mo: 233 translated messages, 2 fuzzy translations, 5 untranslated messages.
Generating /root/apt-0.7.21ubuntu1/po/domains/apt/km.po ........................... done.
Generating /root/apt-0.7.21ubuntu1/locale/km/LC_MESSAGES/apt.mo: 219 translated messages, 12 fuzzy translations, 9 untranslated messages.
Generating /root/apt-0.7.21ubuntu1/po/domains/apt/ko.po ........................... done.
Generating /root/apt-0.7.21ubuntu1/locale/ko/LC_MESSAGES/apt.mo: 233 translated messages, 2 fuzzy translations, 5 untranslated messages.
Generating /root/apt-0.7.21ubuntu1/po/domains/apt/ku.po ........................... done.
Generating /root/apt-0.7.21ubuntu1/locale/ku/LC_MESSAGES/apt.mo: 92 translated messages, 7 fuzzy translations, 141 untranslated messages.
Generating /root/apt-0.7.21ubuntu1/po/domains/apt/mr.po ........................... done.
Generating /root/apt-0.7.21ubuntu1/locale/mr/LC_MESSAGES/apt.mo: 233 translated messages, 2 fuzzy translations, 5 untranslated messages.
Generating /root/apt-0.7.21ubuntu1/po/domains/apt/nb.po ........................... done.
Generating /root/apt-0.7.21ubuntu1/locale/nb/LC_MESSAGES/apt.mo: 233 translated messages, 2 fuzzy translations, 5 untranslated messages.
Generating /root/apt-0.7.21ubuntu1/po/domains/apt/ne.po ........................... done.
Generating /root/apt-0.7.21ubuntu1/locale/ne/LC_MESSAGES/apt.mo: 216 translated messages, 14 fuzzy translations, 10 untranslated messages.
Generating /root/apt-0.7.21ubuntu1/po/domains/apt/nl.po ........................... done.
Generating /root/apt-0.7.21ubuntu1/locale/nl/LC_MESSAGES/apt.mo: 232 translated messages, 3 fuzzy translations, 5 untranslated messages.
Generating /root/apt-0.7.21ubuntu1/po/domains/apt/nn.po ........................... done.
Generating /root/apt-0.7.21ubuntu1/locale/nn/LC_MESSAGES/apt.mo: 202 translated messages, 22 fuzzy translations, 16 untranslated messages.
Generating /root/apt-0.7.21ubuntu1/po/domains/apt/pl.po ........................... done.
Generating /root/apt-0.7.21ubuntu1/locale/pl/LC_MESSAGES/apt.mo: 233 translated messages, 2 fuzzy translations, 5 untranslated messages.
Generating /root/apt-0.7.21ubuntu1/po/domains/apt/pt.po ........................... done.
Generating /root/apt-0.7.21ubuntu1/locale/pt/LC_MESSAGES/apt.mo: 233 translated messages, 2 fuzzy translations, 5 untranslated messages.
Generating /root/apt-0.7.21ubuntu1/po/domains/apt/pt_BR.po ........................... done.
Generating /root/apt-0.7.21ubuntu1/locale/pt_BR/LC_MESSAGES/apt.mo: 233 translated messages, 2 fuzzy translations, 5 untranslated messages.
Generating /root/apt-0.7.21ubuntu1/po/domains/apt/ro.po ........................... done.
Generating /root/apt-0.7.21ubuntu1/locale/ro/LC_MESSAGES/apt.mo: 233 translated messages, 2 fuzzy translations, 5 untranslated messages.
Generating /root/apt-0.7.21ubuntu1/po/domains/apt/ru.po ........................... done.
Generating /root/apt-0.7.21ubuntu1/locale/ru/LC_MESSAGES/apt.mo: 234 translated messages, 2 fuzzy translations, 4 untranslated messages.
Generating /root/apt-0.7.21ubuntu1/po/domains/apt/sk.po ........................... done.
Generating /root/apt-0.7.21ubuntu1/locale/sk/LC_MESSAGES/apt.mo: 235 translated messages, 1 fuzzy translation, 4 untranslated messages.
Generating /root/apt-0.7.21ubuntu1/po/domains/apt/sl.po ........................... done.
Generating /root/apt-0.7.21ubuntu1/locale/sl/LC_MESSAGES/apt.mo: 202 translated messages, 22 fuzzy translations, 16 untranslated messages.
Generating /root/apt-0.7.21ubuntu1/po/domains/apt/sv.po ........................... done.
Generating /root/apt-0.7.21ubuntu1/locale/sv/LC_MESSAGES/apt.mo: 233 translated messages, 2 fuzzy translations, 5 untranslated messages.
Generating /root/apt-0.7.21ubuntu1/po/domains/apt/th.po ........................... done.
Generating /root/apt-0.7.21ubuntu1/locale/th/LC_MESSAGES/apt.mo: 232 translated messages, 3 fuzzy translations, 5 untranslated messages.
Generating /root/apt-0.7.21ubuntu1/po/domains/apt/tl.po .......................... done.
Generating /root/apt-0.7.21ubuntu1/locale/tl/LC_MESSAGES/apt.mo: 219 translated messages, 12 fuzzy translations, 9 untranslated messages.
Generating /root/apt-0.7.21ubuntu1/po/domains/apt/uk.po ........................... done.
Generating /root/apt-0.7.21ubuntu1/locale/uk/LC_MESSAGES/apt.mo: 220 translated messages, 12 fuzzy translations, 8 untranslated messages.
Generating /root/apt-0.7.21ubuntu1/po/domains/apt/vi.po ........................... done.
Generating /root/apt-0.7.21ubuntu1/locale/vi/LC_MESSAGES/apt.mo: 233 translated messages, 2 fuzzy translations, 5 untranslated messages.
Generating /root/apt-0.7.21ubuntu1/po/domains/apt/zh_CN.po ........................... done.
Generating /root/apt-0.7.21ubuntu1/locale/zh_CN/LC_MESSAGES/apt.mo: 233 translated messages, 2 fuzzy translations, 5 untranslated messages.
Generating /root/apt-0.7.21ubuntu1/po/domains/apt/zh_TW.po ........................... done.
Generating /root/apt-0.7.21ubuntu1/locale/zh_TW/LC_MESSAGES/apt.mo: 233 translated messages, 2 fuzzy translations, 5 untranslated messages.
Generating /root/apt-0.7.21ubuntu1/po/domains/libapt-inst1.1/ar.po ....... done.
Generating /root/apt-0.7.21ubuntu1/locale/ar/LC_MESSAGES/libapt-inst1.1.mo: 26 translated messages, 32 untranslated messages.
Generating /root/apt-0.7.21ubuntu1/po/domains/libapt-inst1.1/bg.po ....... done.
Generating /root/apt-0.7.21ubuntu1/locale/bg/LC_MESSAGES/libapt-inst1.1.mo: 58 translated messages.
Generating /root/apt-0.7.21ubuntu1/po/domains/libapt-inst1.1/bs.po ....... done.
Generating /root/apt-0.7.21ubuntu1/locale/bs/LC_MESSAGES/libapt-inst1.1.mo: 10 translated messages, 1 fuzzy translation, 47 untranslated messages.
Generating /root/apt-0.7.21ubuntu1/po/domains/libapt-inst1.1/ca.po ....... done.
Generating /root/apt-0.7.21ubuntu1/locale/ca/LC_MESSAGES/libapt-inst1.1.mo: 58 translated messages.
Generating /root/apt-0.7.21ubuntu1/po/domains/libapt-inst1.1/cs.po ....... done.
Generating /root/apt-0.7.21ubuntu1/locale/cs/LC_MESSAGES/libapt-inst1.1.mo: 58 translated messages.
Generating /root/apt-0.7.21ubuntu1/po/domains/libapt-inst1.1/cy.po ....... done.
Generating /root/apt-0.7.21ubuntu1/locale/cy/LC_MESSAGES/libapt-inst1.1.mo: 45 translated messages, 13 fuzzy translations.
Generating /root/apt-0.7.21ubuntu1/po/domains/libapt-inst1.1/da.po ....... done.
Generating /root/apt-0.7.21ubuntu1/locale/da/LC_MESSAGES/libapt-inst1.1.mo: 57 translated messages, 1 fuzzy translation.
Generating /root/apt-0.7.21ubuntu1/po/domains/libapt-inst1.1/de.po ....... done.
Generating /root/apt-0.7.21ubuntu1/locale/de/LC_MESSAGES/libapt-inst1.1.mo: 58 translated messages.
Generating /root/apt-0.7.21ubuntu1/po/domains/libapt-inst1.1/dz.po ....... done.
Generating /root/apt-0.7.21ubuntu1/locale/dz/LC_MESSAGES/libapt-inst1.1.mo: 57 translated messages, 1 fuzzy translation.
Generating /root/apt-0.7.21ubuntu1/po/domains/libapt-inst1.1/el.po ....... done.
Generating /root/apt-0.7.21ubuntu1/locale/el/LC_MESSAGES/libapt-inst1.1.mo: 58 translated messages.
Generating /root/apt-0.7.21ubuntu1/po/domains/libapt-inst1.1/en_GB.po ...... done.
Generating /root/apt-0.7.21ubuntu1/locale/en_GB/LC_MESSAGES/libapt-inst1.1.mo: 58 translated messages.
Generating /root/apt-0.7.21ubuntu1/po/domains/libapt-inst1.1/es.po ....... done.
Generating /root/apt-0.7.21ubuntu1/locale/es/LC_MESSAGES/libapt-inst1.1.mo: 58 translated messages.
Generating /root/apt-0.7.21ubuntu1/po/domains/libapt-inst1.1/eu.po ....... done.
Generating /root/apt-0.7.21ubuntu1/locale/eu/LC_MESSAGES/libapt-inst1.1.mo: 58 translated messages.
Generating /root/apt-0.7.21ubuntu1/po/domains/libapt-inst1.1/fi.po ....... done.
Generating /root/apt-0.7.21ubuntu1/locale/fi/LC_MESSAGES/libapt-inst1.1.mo: 58 translated messages.
Generating /root/apt-0.7.21ubuntu1/po/domains/libapt-inst1.1/fr.po ....... done.
Generating /root/apt-0.7.21ubuntu1/locale/fr/LC_MESSAGES/libapt-inst1.1.mo: 58 translated messages.
Generating /root/apt-0.7.21ubuntu1/po/domains/libapt-inst1.1/gl.po ....... done.
Generating /root/apt-0.7.21ubuntu1/locale/gl/LC_MESSAGES/libapt-inst1.1.mo: 58 translated messages.
Generating /root/apt-0.7.21ubuntu1/po/domains/libapt-inst1.1/he.po ....... done.
Generating /root/apt-0.7.21ubuntu1/locale/he/LC_MESSAGES/libapt-inst1.1.mo: 1 translated message, 1 fuzzy translation, 56 untranslated messages.
Generating /root/apt-0.7.21ubuntu1/po/domains/libapt-inst1.1/hu.po ....... done.
Generating /root/apt-0.7.21ubuntu1/locale/hu/LC_MESSAGES/libapt-inst1.1.mo: 58 translated messages.
Generating /root/apt-0.7.21ubuntu1/po/domains/libapt-inst1.1/it.po ...... done.
Generating /root/apt-0.7.21ubuntu1/locale/it/LC_MESSAGES/libapt-inst1.1.mo: 58 translated messages.
Generating /root/apt-0.7.21ubuntu1/po/domains/libapt-inst1.1/ja.po ....... done.
Generating /root/apt-0.7.21ubuntu1/locale/ja/LC_MESSAGES/libapt-inst1.1.mo: 58 translated messages.
Generating /root/apt-0.7.21ubuntu1/po/domains/libapt-inst1.1/km.po ....... done.
Generating /root/apt-0.7.21ubuntu1/locale/km/LC_MESSAGES/libapt-inst1.1.mo: 57 translated messages, 1 fuzzy translation.
Generating /root/apt-0.7.21ubuntu1/po/domains/libapt-inst1.1/ko.po ....... done.
Generating /root/apt-0.7.21ubuntu1/locale/ko/LC_MESSAGES/libapt-inst1.1.mo: 58 translated messages.
Generating /root/apt-0.7.21ubuntu1/po/domains/libapt-inst1.1/ku.po ....... done.
Generating /root/apt-0.7.21ubuntu1/locale/ku/LC_MESSAGES/libapt-inst1.1.mo: 11 translated messages, 5 fuzzy translations, 42 untranslated messages.
Generating /root/apt-0.7.21ubuntu1/po/domains/libapt-inst1.1/mr.po ....... done.
Generating /root/apt-0.7.21ubuntu1/locale/mr/LC_MESSAGES/libapt-inst1.1.mo: 58 translated messages.
Generating /root/apt-0.7.21ubuntu1/po/domains/libapt-inst1.1/nb.po ....... done.
Generating /root/apt-0.7.21ubuntu1/locale/nb/LC_MESSAGES/libapt-inst1.1.mo: 58 translated messages.
Generating /root/apt-0.7.21ubuntu1/po/domains/libapt-inst1.1/ne.po ....... done.
Generating /root/apt-0.7.21ubuntu1/locale/ne/LC_MESSAGES/libapt-inst1.1.mo: 57 translated messages, 1 fuzzy translation.
Generating /root/apt-0.7.21ubuntu1/po/domains/libapt-inst1.1/nl.po ....... done.
Generating /root/apt-0.7.21ubuntu1/locale/nl/LC_MESSAGES/libapt-inst1.1.mo: 58 translated messages.
Generating /root/apt-0.7.21ubuntu1/po/domains/libapt-inst1.1/nn.po ....... done.
Generating /root/apt-0.7.21ubuntu1/locale/nn/LC_MESSAGES/libapt-inst1.1.mo: 56 translated messages, 2 fuzzy translations.
Generating /root/apt-0.7.21ubuntu1/po/domains/libapt-inst1.1/pl.po ....... done.
Generating /root/apt-0.7.21ubuntu1/locale/pl/LC_MESSAGES/libapt-inst1.1.mo: 58 translated messages.
Generating /root/apt-0.7.21ubuntu1/po/domains/libapt-inst1.1/pt.po ....... done.
Generating /root/apt-0.7.21ubuntu1/locale/pt/LC_MESSAGES/libapt-inst1.1.mo: 58 translated messages.
Generating /root/apt-0.7.21ubuntu1/po/domains/libapt-inst1.1/pt_BR.po ....... done.
Generating /root/apt-0.7.21ubuntu1/locale/pt_BR/LC_MESSAGES/libapt-inst1.1.mo: 58 translated messages.
Generating /root/apt-0.7.21ubuntu1/po/domains/libapt-inst1.1/ro.po ....... done.
Generating /root/apt-0.7.21ubuntu1/locale/ro/LC_MESSAGES/libapt-inst1.1.mo: 58 translated messages.
Generating /root/apt-0.7.21ubuntu1/po/domains/libapt-inst1.1/ru.po ....... done.
Generating /root/apt-0.7.21ubuntu1/locale/ru/LC_MESSAGES/libapt-inst1.1.mo: 58 translated messages.
Generating /root/apt-0.7.21ubuntu1/po/domains/libapt-inst1.1/sk.po ....... done.
Generating /root/apt-0.7.21ubuntu1/locale/sk/LC_MESSAGES/libapt-inst1.1.mo: 58 translated messages.
Generating /root/apt-0.7.21ubuntu1/po/domains/libapt-inst1.1/sl.po ....... done.
Generating /root/apt-0.7.21ubuntu1/locale/sl/LC_MESSAGES/libapt-inst1.1.mo: 56 translated messages, 2 fuzzy translations.
Generating /root/apt-0.7.21ubuntu1/po/domains/libapt-inst1.1/sv.po ....... done.
Generating /root/apt-0.7.21ubuntu1/locale/sv/LC_MESSAGES/libapt-inst1.1.mo: 58 translated messages.
Generating /root/apt-0.7.21ubuntu1/po/domains/libapt-inst1.1/th.po ....... done.
Generating /root/apt-0.7.21ubuntu1/locale/th/LC_MESSAGES/libapt-inst1.1.mo: 58 translated messages.
Generating /root/apt-0.7.21ubuntu1/po/domains/libapt-inst1.1/tl.po ....... done.
Generating /root/apt-0.7.21ubuntu1/locale/tl/LC_MESSAGES/libapt-inst1.1.mo: 57 translated messages, 1 fuzzy translation.
Generating /root/apt-0.7.21ubuntu1/po/domains/libapt-inst1.1/uk.po ....... done.
Generating /root/apt-0.7.21ubuntu1/locale/uk/LC_MESSAGES/libapt-inst1.1.mo: 39 translated messages, 19 fuzzy translations.
Generating /root/apt-0.7.21ubuntu1/po/domains/libapt-inst1.1/vi.po ....... done.
Generating /root/apt-0.7.21ubuntu1/locale/vi/LC_MESSAGES/libapt-inst1.1.mo: 58 translated messages.
Generating /root/apt-0.7.21ubuntu1/po/domains/libapt-inst1.1/zh_CN.po ....... done.
Generating /root/apt-0.7.21ubuntu1/locale/zh_CN/LC_MESSAGES/libapt-inst1.1.mo: 58 translated messages.
Generating /root/apt-0.7.21ubuntu1/po/domains/libapt-inst1.1/zh_TW.po ....... done.
Generating /root/apt-0.7.21ubuntu1/locale/zh_TW/LC_MESSAGES/libapt-inst1.1.mo: 58 translated messages.
Generating /root/apt-0.7.21ubuntu1/po/domains/libapt-pkg4.7/ar.po ............................ done.
Generating /root/apt-0.7.21ubuntu1/locale/ar/LC_MESSAGES/libapt-pkg4.7.mo: 111 translated messages, 13 fuzzy translations, 150 untranslated messages.
Generating /root/apt-0.7.21ubuntu1/po/domains/libapt-pkg4.7/bg.po ............................. done.
Generating /root/apt-0.7.21ubuntu1/locale/bg/LC_MESSAGES/libapt-pkg4.7.mo: 254 translated messages, 3 fuzzy translations, 17 untranslated messages.
Generating /root/apt-0.7.21ubuntu1/po/domains/libapt-pkg4.7/bs.po ............................. done.
Generating /root/apt-0.7.21ubuntu1/locale/bs/LC_MESSAGES/libapt-pkg4.7.mo: 31 translated messages, 22 fuzzy translations, 221 untranslated messages.
Generating /root/apt-0.7.21ubuntu1/po/domains/libapt-pkg4.7/ca.po ............................. done.
Generating /root/apt-0.7.21ubuntu1/locale/ca/LC_MESSAGES/libapt-pkg4.7.mo: 262 translated messages, 2 fuzzy translations, 10 untranslated messages.
Generating /root/apt-0.7.21ubuntu1/po/domains/libapt-pkg4.7/cs.po ............................. done.
Generating /root/apt-0.7.21ubuntu1/locale/cs/LC_MESSAGES/libapt-pkg4.7.mo: 254 translated messages, 3 fuzzy translations, 17 untranslated messages.
Generating /root/apt-0.7.21ubuntu1/po/domains/libapt-pkg4.7/cy.po ............................. done.
Generating /root/apt-0.7.21ubuntu1/locale/cy/LC_MESSAGES/libapt-pkg4.7.mo: 166 translated messages, 63 fuzzy translations, 45 untranslated messages.
Generating /root/apt-0.7.21ubuntu1/po/domains/libapt-pkg4.7/da.po ............................ done.
Generating /root/apt-0.7.21ubuntu1/locale/da/LC_MESSAGES/libapt-pkg4.7.mo: 246 translated messages, 9 fuzzy translations, 19 untranslated messages.
Generating /root/apt-0.7.21ubuntu1/po/domains/libapt-pkg4.7/de.po ............................ done.
Generating /root/apt-0.7.21ubuntu1/locale/de/LC_MESSAGES/libapt-pkg4.7.mo: 254 translated messages, 3 fuzzy translations, 17 untranslated messages.
Generating /root/apt-0.7.21ubuntu1/po/domains/libapt-pkg4.7/dz.po ............................ done.
Generating /root/apt-0.7.21ubuntu1/locale/dz/LC_MESSAGES/libapt-pkg4.7.mo: 236 translated messages, 18 fuzzy translations, 20 untranslated messages.
Generating /root/apt-0.7.21ubuntu1/po/domains/libapt-pkg4.7/el.po ............................. done.
Generating /root/apt-0.7.21ubuntu1/locale/el/LC_MESSAGES/libapt-pkg4.7.mo: 253 translated messages, 4 fuzzy translations, 17 untranslated messages.
Generating /root/apt-0.7.21ubuntu1/po/domains/libapt-pkg4.7/en_GB.po ............................. done.
Generating /root/apt-0.7.21ubuntu1/locale/en_GB/LC_MESSAGES/libapt-pkg4.7.mo: 254 translated messages, 3 fuzzy translations, 17 untranslated messages.
Generating /root/apt-0.7.21ubuntu1/po/domains/libapt-pkg4.7/es.po ............................. done.
Generating /root/apt-0.7.21ubuntu1/locale/es/LC_MESSAGES/libapt-pkg4.7.mo: 254 translated messages, 3 fuzzy translations, 17 untranslated messages.
Generating /root/apt-0.7.21ubuntu1/po/domains/libapt-pkg4.7/eu.po ............................. done.
Generating /root/apt-0.7.21ubuntu1/locale/eu/LC_MESSAGES/libapt-pkg4.7.mo: 255 translated messages, 3 fuzzy translations, 16 untranslated messages.
Generating /root/apt-0.7.21ubuntu1/po/domains/libapt-pkg4.7/fi.po ............................. done.
Generating /root/apt-0.7.21ubuntu1/locale/fi/LC_MESSAGES/libapt-pkg4.7.mo: 254 translated messages, 3 fuzzy translations, 17 untranslated messages.
Generating /root/apt-0.7.21ubuntu1/po/domains/libapt-pkg4.7/fr.po ............................. done.
Generating /root/apt-0.7.21ubuntu1/locale/fr/LC_MESSAGES/libapt-pkg4.7.mo: 260 translated messages, 3 fuzzy translations, 11 untranslated messages.
Generating /root/apt-0.7.21ubuntu1/po/domains/libapt-pkg4.7/gl.po ............................. done.
Generating /root/apt-0.7.21ubuntu1/locale/gl/LC_MESSAGES/libapt-pkg4.7.mo: 254 translated messages, 3 fuzzy translations, 17 untranslated messages.
Generating /root/apt-0.7.21ubuntu1/po/domains/libapt-pkg4.7/he.po ............................. done.
Generating /root/apt-0.7.21ubuntu1/locale/he/LC_MESSAGES/libapt-pkg4.7.mo: 3 translated messages, 10 fuzzy translations, 261 untranslated messages.
Generating /root/apt-0.7.21ubuntu1/po/domains/libapt-pkg4.7/hu.po ............................. done.
Generating /root/apt-0.7.21ubuntu1/locale/hu/LC_MESSAGES/libapt-pkg4.7.mo: 251 translated messages, 5 fuzzy translations, 18 untranslated messages.
Generating /root/apt-0.7.21ubuntu1/po/domains/libapt-pkg4.7/it.po ............................. done.
Generating /root/apt-0.7.21ubuntu1/locale/it/LC_MESSAGES/libapt-pkg4.7.mo: 260 translated messages, 3 fuzzy translations, 11 untranslated messages.
Generating /root/apt-0.7.21ubuntu1/po/domains/libapt-pkg4.7/ja.po ............................ done.
Generating /root/apt-0.7.21ubuntu1/locale/ja/LC_MESSAGES/libapt-pkg4.7.mo: 254 translated messages, 3 fuzzy translations, 17 untranslated messages.
Generating /root/apt-0.7.21ubuntu1/po/domains/libapt-pkg4.7/km.po ............................. done.
Generating /root/apt-0.7.21ubuntu1/locale/km/LC_MESSAGES/libapt-pkg4.7.mo: 236 translated messages, 18 fuzzy translations, 20 untranslated messages.
Generating /root/apt-0.7.21ubuntu1/po/domains/libapt-pkg4.7/ko.po ............................. done.
Generating /root/apt-0.7.21ubuntu1/locale/ko/LC_MESSAGES/libapt-pkg4.7.mo: 254 translated messages, 3 fuzzy translations, 17 untranslated messages.
Generating /root/apt-0.7.21ubuntu1/po/domains/libapt-pkg4.7/ku.po ............................. done.
Generating /root/apt-0.7.21ubuntu1/locale/ku/LC_MESSAGES/libapt-pkg4.7.mo: 69 translated messages, 18 fuzzy translations, 187 untranslated messages.
Generating /root/apt-0.7.21ubuntu1/po/domains/libapt-pkg4.7/mr.po ............................. done.
Generating /root/apt-0.7.21ubuntu1/locale/mr/LC_MESSAGES/libapt-pkg4.7.mo: 254 translated messages, 3 fuzzy translations, 17 untranslated messages.
Generating /root/apt-0.7.21ubuntu1/po/domains/libapt-pkg4.7/nb.po ............................. done.
Generating /root/apt-0.7.21ubuntu1/locale/nb/LC_MESSAGES/libapt-pkg4.7.mo: 255 translated messages, 3 fuzzy translations, 16 untranslated messages.
Generating /root/apt-0.7.21ubuntu1/po/domains/libapt-pkg4.7/ne.po ............................. done.
Generating /root/apt-0.7.21ubuntu1/locale/ne/LC_MESSAGES/libapt-pkg4.7.mo: 236 translated messages, 18 fuzzy translations, 20 untranslated messages.
Generating /root/apt-0.7.21ubuntu1/po/domains/libapt-pkg4.7/nl.po ............................. done.
Generating /root/apt-0.7.21ubuntu1/locale/nl/LC_MESSAGES/libapt-pkg4.7.mo: 251 translated messages, 5 fuzzy translations, 18 untranslated messages.
Generating /root/apt-0.7.21ubuntu1/po/domains/libapt-pkg4.7/nn.po ............................. done.
Generating /root/apt-0.7.21ubuntu1/locale/nn/LC_MESSAGES/libapt-pkg4.7.mo: 212 translated messages, 33 fuzzy translations, 29 untranslated messages.
Generating /root/apt-0.7.21ubuntu1/po/domains/libapt-pkg4.7/pl.po ............................. done.
Generating /root/apt-0.7.21ubuntu1/locale/pl/LC_MESSAGES/libapt-pkg4.7.mo: 254 translated messages, 3 fuzzy translations, 17 untranslated messages.
Generating /root/apt-0.7.21ubuntu1/po/domains/libapt-pkg4.7/pt.po ............................. done.
Generating /root/apt-0.7.21ubuntu1/locale/pt/LC_MESSAGES/libapt-pkg4.7.mo: 254 translated messages, 3 fuzzy translations, 17 untranslated messages.
Generating /root/apt-0.7.21ubuntu1/po/domains/libapt-pkg4.7/pt_BR.po ............................. done.
Generating /root/apt-0.7.21ubuntu1/locale/pt_BR/LC_MESSAGES/libapt-pkg4.7.mo: 254 translated messages, 3 fuzzy translations, 17 untranslated messages.
Generating /root/apt-0.7.21ubuntu1/po/domains/libapt-pkg4.7/ro.po ............................. done.
Generating /root/apt-0.7.21ubuntu1/locale/ro/LC_MESSAGES/libapt-pkg4.7.mo: 254 translated messages, 3 fuzzy translations, 17 untranslated messages.
Generating /root/apt-0.7.21ubuntu1/po/domains/libapt-pkg4.7/ru.po ............................. done.
Generating /root/apt-0.7.21ubuntu1/locale/ru/LC_MESSAGES/libapt-pkg4.7.mo: 260 translated messages, 3 fuzzy translations, 11 untranslated messages.
Generating /root/apt-0.7.21ubuntu1/po/domains/libapt-pkg4.7/sk.po ............................. done.
Generating /root/apt-0.7.21ubuntu1/locale/sk/LC_MESSAGES/libapt-pkg4.7.mo: 260 translated messages, 3 fuzzy translations, 11 untranslated messages.
Generating /root/apt-0.7.21ubuntu1/po/domains/libapt-pkg4.7/sl.po ............................. done.
Generating /root/apt-0.7.21ubuntu1/locale/sl/LC_MESSAGES/libapt-pkg4.7.mo: 212 translated messages, 33 fuzzy translations, 29 untranslated messages.
Generating /root/apt-0.7.21ubuntu1/po/domains/libapt-pkg4.7/sv.po ............................. done.
Generating /root/apt-0.7.21ubuntu1/locale/sv/LC_MESSAGES/libapt-pkg4.7.mo: 255 translated messages, 3 fuzzy translations, 16 untranslated messages.
Generating /root/apt-0.7.21ubuntu1/po/domains/libapt-pkg4.7/th.po ............................. done.
Generating /root/apt-0.7.21ubuntu1/locale/th/LC_MESSAGES/libapt-pkg4.7.mo: 254 translated messages, 3 fuzzy translations, 17 untranslated messages.
Generating /root/apt-0.7.21ubuntu1/po/domains/libapt-pkg4.7/tl.po ............................. done.
Generating /root/apt-0.7.21ubuntu1/locale/tl/LC_MESSAGES/libapt-pkg4.7.mo: 237 translated messages, 17 fuzzy translations, 20 untranslated messages.
Generating /root/apt-0.7.21ubuntu1/po/domains/libapt-pkg4.7/uk.po ............................. done.
Generating /root/apt-0.7.21ubuntu1/locale/uk/LC_MESSAGES/libapt-pkg4.7.mo: 226 translated messages, 28 fuzzy translations, 20 untranslated messages.
Generating /root/apt-0.7.21ubuntu1/po/domains/libapt-pkg4.7/vi.po ............................. done.
Generating /root/apt-0.7.21ubuntu1/locale/vi/LC_MESSAGES/libapt-pkg4.7.mo: 254 translated messages, 3 fuzzy translations, 17 untranslated messages.
Generating /root/apt-0.7.21ubuntu1/po/domains/libapt-pkg4.7/zh_CN.po ............................. done.
Generating /root/apt-0.7.21ubuntu1/locale/zh_CN/LC_MESSAGES/libapt-pkg4.7.mo: 255 translated messages, 3 fuzzy translations, 16 untranslated messages.
Generating /root/apt-0.7.21ubuntu1/po/domains/libapt-pkg4.7/zh_TW.po ............................. done.
Generating /root/apt-0.7.21ubuntu1/locale/zh_TW/LC_MESSAGES/libapt-pkg4.7.mo: 258 translated messages, 1 fuzzy translation, 15 untranslated messages.


```

---

### Post by Bachstelze on 2009-09-20
> **dragos240 said:**
> Done.

And it still says "dpkg-architecture: command not found"? Well, worst-case scenario, it's in your dpkg source dir, under script/ Just copy it over to /usr/local/bin if make install didn't install it.

---

### Post by Bachstelze on 2009-09-20
> **dragos240 said:**
> How do I fix this?

Fix what? No problem here.

---

### Post by dragos240 on 2009-09-20
> **Bachstelze said:**
> And it still says "dpkg-architecture: command not found"? Well, worst-case scenario, it's in your dpkg source dir, under script/ Just copy it over to /usr/local/bin if make install didn't install it.

No it displayed a different message.

---

### Post by Bachstelze on 2009-09-20
> **dragos240 said:**
> No it displayed a different message.

What message? There is no error in what you pasted before.

---

### Post by v8YKxgHe on 2009-09-20
Why not use the AUR for Arch, where there are thousands of software for you to install? Installing DPKG and Apt on Arch isn't the way to do it.

---

