---
title: "How to get the latest stable SeaMonkey for x86-64?"
date: 2011-09-09
forum: Ubuntuzilla
---

### Post by Frettchen II on 2011-09-09
I'm running 64-bit Ubuntu 10.04 and would like to install the latest stable release of SeaMonkey.  I could compile everything myself but would prefer something prepackaged if possible.

Does anyone know if any Ubuntu packages exist?

The closest thing I found was mention on the [Ubuntuzilla wiki]("http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page#64bit_users") that "The best alternative for Thunderbird and Seamonkey is probably using the latest trunk builds from the [Ubuntu Mozilla Daily PPA]("https://launchpad.net/%7Eubuntu-mozilla-daily/+archive/ppa"), which includes 64 bit builds."  However, this is for daily builds, and besides which, despite what the wiki claims, there don't seem to be any SeaMonkey builds on that page.

---

### Post by nanotube on 2011-09-13
ubuntuzilla doesn't (yet) have any 64bit builds. so your best bet may be to just grab the distribution from the seamonkey project site.

---

### Post by kernel2korn on 2011-10-04
[Frettchen II]("http://ubuntuforums.org/member.php?u=1373904"):  What did you end up doing?

I too, want the latest Seamonkey, so I was able to run 2.4.1 build from /opt/ but can not get SeaMonkey to pick up my Flash (or any) plug-in settings.  I tried moving it over the top over 2.0.11 build that 10.04 installs from apt, but it breaks the plug-ins.  I was wondering if you had any success.

---

### Post by Frettchen II on 2011-10-04
[kernel2korn]("http://ubuntuforums.org/member.php?u=1404141"), I just did as [nanotube]("http://ubuntuforums.org/member.php?u=66474") suggested and [downloaded the source from ftp.mozilla.org]("ftp://ftp.mozilla.org/pub/mozilla.org/") and compiled it from source using the [Simple SeaMonkey build instructions]("https://developer.mozilla.org/en/Simple_SeaMonkey_build").  My .mozconfig file is as follows; you may need to adjust the value of the -j flag to suit your number of processors:
```
ac_add_options --enable-application=suite
mk_add_options MOZ_OBJDIR=@TOPSRCDIR@/objdir-sm-release
mk_add_options MOZ_MAKE_FLAGS="-j6"
ac_add_options --libdir=/usr/local/lib64
ac_add_options --disable-libjpeg-turbo
ac_add_options --disable-necko-wifi
```I used /usr/local/lib64 because that's where openSUSE puts its 64-bit binaries; I'm not sure what the convention is on Ubuntu.  Anyway, then I just compiled and installed it as follows:
```
$ make -f client.mk
$ sudo make -f client.mk install
```SeaMonkey installed to /usr/local/lib64/seamonkey-2.4 with a link to the binary from /usr/local/bin, and when I run that I still have all my plugins and extensions.  I didn't uninstall the old SeaMonkey from the Ubuntu repositories, so maybe that has something to do with it.

---

### Post by Frettchen II on 2011-10-04
I've just noticed that there's [an unofficial 64-bit build available on the official SeaMonkey Download & Releases site]("http://www.seamonkey-project.org/releases/#contrib").  I haven't tried it myself.

---

### Post by nanotube on 2012-01-13
FYI, ubuntuzilla now includes 64bit seamonkey builds (and firefox and thunderbird too, of course).

---

