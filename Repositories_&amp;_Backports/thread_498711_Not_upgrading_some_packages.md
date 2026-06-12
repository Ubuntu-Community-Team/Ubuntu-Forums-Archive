---
title: "Not upgrading some packages"
date: 2007-07-11
forum: Repositories &amp; Backports
---

### Post by dumbbeatnix on 2007-07-11
Hello Ubuntu Users

I have a problem upgrading three packages, as a result the upgrade program will not upgrade my other packages until this issue is fixed.  I run the upgrade program and it comes up with the following errors:

W: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/o/openoffice.org/python-uno_2.2.0-1ubuntu4_i386.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/o/openoffice.org/python-uno_2.2.0-1ubuntu4_i386.deb)
  404 Not Found


W: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/o/openoffice.org/ttf-opensymbol_2.2.0-1ubuntu4_all.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/o/openoffice.org/ttf-opensymbol_2.2.0-1ubuntu4_all.deb)
  404 Not Found


W: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org_2.2.0-1ubuntu4_i386.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org_2.2.0-1ubuntu4_i386.deb)
  404 Not Found


It appears as though there are problems with python-uno, ttf-opensymbol and openoffice itself.

Before some of you step in and say "try the packages again, they maybe corrupt", I tried yesterday and now this morning.

I enjoy Ubuntu, so in no way am I knocking it.  I am sure that people will work out what is going on here.:KS

I also want to know, could this error be caused because I haven't upgraded from fiesty to something else?

Cheers
dumbbeatnix

---

### Post by solar george on 2007-07-11
Open your sources.list file and change your mirrors to archive.ubuntu.com instead of au.archive.ubuntu.com - au.archive appears to be incomplete.

EDIT: Do an apt-get update and then aptitude dist-upgrade after editing your sources.list file.

---

### Post by dumbbeatnix on 2007-07-18
Thank you solar george, but I managed to correct the problem myself.

The problem occurred after I changed a few settings and created a dun file.  I then changed my rc.local file, all in the need to get a mobile started with some foreign package.

What I have is a bluetooth phone and I am trying to connect it serially, without any success at all.  Thinking now of getting the dongle with the antenna to talk to the phone.  Got ripped off on ebay!  Say no more.

Well all I did was change everything back in the rc.local file and it went smoothly.

P.S.  Nothing like the message "Your system is up to date"  :guitar:

Cheers
dumbbeatnix

---

### Post by solar george on 2007-07-18
It's always good when someone works things out for themselves.

---

