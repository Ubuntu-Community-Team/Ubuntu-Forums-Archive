---
title: "Seamonky - how do I fix many broken dependencies?"
date: 2010-11-03
forum: Ubuntuzilla
---

### Post by conmat on 2010-11-03
Ubuntu 9.10 64-bit
Lenovo T400
2GB ram

I did an update and now Seamonkey (among other things) won't run.

Here is some output:


foobar@foobar:~/software/linux/seamonkey$ seamonkey
/opt/seamonkey/seamonkey-bin: error while loading shared libraries: libgtk-x11-2.0.so.0: cannot open shared object file: No such file or directory


foobar@foobar:~/software/linux/seamonkey$ ldd /opt/seamonkey/seamonkey-bin
    linux-gate.so.1 =>  (0xf777a000)
    libpthread.so.0 => /lib32/libpthread.so.0 (0xf7746000)
    libmozjs.so => not found
    libxpcom.so => not found
    libxpcom_core.so => not found
    libplds4.so => not found
    libplc4.so => not found
    libnspr4.so => not found
    libdl.so.2 => /lib32/libdl.so.2 (0xf7740000)
    libgtk-x11-2.0.so.0 => not found
    libatk-1.0.so.0 => not found
    libgdk-x11-2.0.so.0 => not found
    libgdk_pixbuf-2.0.so.0 => not found
    libpangocairo-1.0.so.0 => not found
    libpango-1.0.so.0 => not found
    libcairo.so.2 => not found
    libgobject-2.0.so.0 => not found
    libgmodule-2.0.so.0 => not found
    libglib-2.0.so.0 => not found
    libX11.so.6 => not found
    libdbus-glib-1.so.2 => not found
    libdbus-1.so.3 => not found
    libm.so.6 => /lib32/libm.so.6 (0xf7718000)
    libsmime3.so => not found
    libssl3.so => not found
    libnss3.so => not found
    libnssutil3.so => not found
    libsoftokn3.so => not found
    libldap60.so => not found
    libprldap60.so => not found
    libldif60.so => not found
    libXrender.so.1 => not found
    libfreetype.so.6 => not found
    libfontconfig.so.1 => not found
    libXt.so.6 => not found
    libgthread-2.0.so.0 => not found
    libpangoft2-1.0.so.0 => not found
    libsqlite3.so => not found
    libasound.so.2 => not found
    libstdc++.so.6 => not found
    libgcc_s.so.1 => not found
    libc.so.6 => /lib32/libc.so.6 (0xf75cf000)
    /lib/ld-linux.so.2 (0xf777b000)

foobar@foobar:/opt/seamonkey$ ls -la
total 18084
drwxr-xr-x 15 root root     4096 2010-11-03 11:38 .
drwxr-xr-x  8 root root     4096 2010-02-28 16:20 ..
-rw-r--r--  1 root root     2123 2010-02-06 03:13 application.ini
-rw-r--r--  1 root root        0 2010-02-06 03:13 .autoreg
-rw-r--r--  1 root root     1426 2010-02-06 03:13 blocklist.xml
drwxr-xr-x  3 root root     4096 2010-02-06 03:13 chrome
drwxr-xr-x  2 root root     4096 2010-02-06 03:13 components
-rwxr-xr-x  1 root root    45912 2010-02-06 03:13 crashreporter
-rw-r--r--  1 root root     3801 2010-02-06 03:13 crashreporter.ini
drwxr-xr-x  6 root root     4096 2010-02-06 03:13 defaults
lrwxrwxrwx  1 root root       24 2010-02-19 20:08 dictionaries -> /usr/share/myspell/dicts
drwxr-xr-x  2 root root     4096 2009-12-06 18:20 dictionaries_2010-01-01T17:15:05-0500
lrwxrwxrwx  1 root root       24 2010-01-01 23:15 dictionaries_2010-01-16T18:09:52-0500 -> /usr/share/myspell/dicts
lrwxrwxrwx  1 root root       24 2010-01-17 00:09 dictionaries_2010-02-19T20:08:41+0100 -> /usr/share/myspell/dicts
drwxr-xr-x  7 root root     4096 2010-02-06 03:13 extensions
drwxr-xr-x  2 root root     4096 2010-02-06 03:13 greprefs
drwxr-xr-x  2 root root     4096 2010-02-06 03:13 icons
drwxr-xr-x  2 root root     4096 2010-02-06 03:13 isp
-rw-r--r--  1 root root      478 2010-02-06 03:13 libfreebl3.chk
-rwxr-xr-x  1 root root   321140 2010-02-06 03:13 libfreebl3.so
-rwxr-xr-x  1 root root   188752 2010-02-06 03:13 libldap60.so
-rwxr-xr-x  1 root root     8076 2010-02-06 03:13 libldif60.so
-rwxr-xr-x  1 root root   839944 2010-02-06 03:13 libmozjs.so
-rwxr-xr-x  1 root root   200736 2010-02-06 03:13 libnspr4.so
-rwxr-xr-x  1 root root   863000 2010-02-06 03:13 libnss3.so
-rwxr-xr-x  1 root root   364684 2010-02-06 03:13 libnssckbi.so
-rw-r--r--  1 root root      478 2010-02-06 03:13 libnssdbm3.chk
-rwxr-xr-x  1 root root   122908 2010-02-06 03:13 libnssdbm3.so
-rwxr-xr-x  1 root root    78800 2010-02-06 03:13 libnssutil3.so
-rwxr-xr-x  1 root root    13180 2010-02-06 03:13 libplc4.so
-rwxr-xr-x  1 root root     8748 2010-02-06 03:13 libplds4.so
-rwxr-xr-x  1 root root    16688 2010-02-06 03:13 libprldap60.so
-rwxr-xr-x  1 root root   125644 2010-02-06 03:13 libsmime3.so
-rw-r--r--  1 root root      478 2010-02-06 03:13 libsoftokn3.chk
-rwxr-xr-x  1 root root   194128 2010-02-06 03:13 libsoftokn3.so
-rwxr-xr-x  1 root root   447000 2010-02-06 03:13 libsqlite3.so
-rwxr-xr-x  1 root root   160140 2010-02-06 03:13 libssl3.so
-rwxr-xr-x  1 root root   551036 2010-02-06 03:13 libxpcom_core.so
-rwxr-xr-x  1 root root    12192 2010-02-06 03:13 libxpcom.so
-rwxr-xr-x  1 root root    30826 2010-02-06 03:13 license.txt
drwxr-xr-x  3 root root     4096 2010-02-06 03:13 modules
-rwxr-xr-x  1 root root    10560 2010-02-06 03:13 mozilla-xremote-client
-rw-r--r--  1 root root      136 2010-02-06 03:13 platform.ini
lrwxrwxrwx  1 root root       24 2010-02-19 20:08 plugins -> /usr/lib/mozilla/plugins
drwxr-xr-x  2 root root     4096 2009-12-06 18:20 plugins_2010-01-01T17:15:05-0500
lrwxrwxrwx  1 root root       24 2010-01-01 23:15 plugins_2010-01-16T18:09:44-0500 -> /usr/lib/mozilla/plugins
lrwxrwxrwx  1 root root       24 2010-01-17 00:09 plugins_2010-02-19T20:08:41+0100 -> /usr/lib/mozilla/plugins
-rw-r--r--  1 root root     4823 2010-02-06 03:13 README
-rw-r--r--  1 root root     5169 2010-02-06 03:13 removed-files
drwxr-xr-x  6 root root     4096 2010-02-06 03:13 res
-rwxr-xr-x  1 root root    10450 2010-02-06 03:13 run-mozilla.sh
-rwxr-xr-x  1 root root     3887 2010-02-06 03:13 seamonkey
-rwxr-xr-x  1 root root 13649044 2010-02-06 03:13 seamonkey-bin
drwxr-xr-x  2 root root     4096 2010-02-06 03:13 searchplugins
-rw-r--r--  1 root root      825 2010-02-06 03:13 Throbber-small.gif
-rw-r--r--  1 root root        6 2010-02-06 03:13 update.locale
-rwxr-xr-x  1 root root    67348 2010-02-06 03:13 updater
-rw-r--r--  1 root root      147 2010-02-06 03:13 updater.ini
drwxr-xr-x  3 root root     4096 2010-01-03 22:21 updates


It looks like (most of) the library's are there.

Any suggestions on how to fix this are appreciated.

TIA

---

### Post by nanotube on 2010-11-03
Well, if 'other things' also won't run, it's probably not a seamonkey problem

What kind of an 'update' did you do, exactly?

---

### Post by TSJason on 2010-11-03
conmat,

 "ldd" isn't really a good diagnostic for this problem since it won't know to look in the seamonkey directory (based on the config in /etc/ld.so.conf).

I notice that seamonkey is installed to /opt which is non-standard for ubuntu packages. Normally this would be installed in /usr/lib/seamonkey-[version]/seamonkey-2.0/

I'm guessing that you may have manually installed the 32-bit binary version on a 64-bit system?

---

### Post by conmat on 2010-11-03
O.K., this is a little ugly.

I burned a Ubuntu 10.4 alternate CD.  I ran it and selected install.  I just wanted to run the live CD but not install 10.4.  It didn't give an option for installing a live version so I quit the installation.

While the CD was in the drive I tried to do an update.  Somehow the packages from the CD were added to my repository list.

After the "update" my system would not start gnome desktop, gdm was no longer installed.  I could boot to 9.10  in recovery mode no problem.  I reinstalled gdm (and some other packages that seemed to be needed for the desktop) and now the desktop is mostly O.K.  Some applets that worked before no longer work.  Annoying but no big deal.

However, Seamonkey won't run.  For me this is a very big deal.  If you can give me any suggestions I would be very grateful. 

TIA

---

### Post by conmat on 2010-11-03
> **TSJason said:**
> conmat,

 "ldd" isn't really a good diagnostic for this problem since it won't know to look in the seamonkey directory (based on the config in /etc/ld.so.conf).

I notice that seamonkey is installed to /opt which is non-standard for ubuntu packages. Normally this would be installed in /usr/lib/seamonkey-[version]/seamonkey-2.0/

I'm guessing that you may have manually installed the 32-bit binary version on a 64-bit system?


Hi,  Thanks very much for your reply.

You are correct that I am (was) running the 32-bit version of Seamonkey.  I installed it from Ubuntuzilla with their install script.  If there was a 64-bit version I would use it! :-)

I am happy to install Seamonkey anywhere!  I have looked around and there doesn't  seem to be complete agreement on where to install additional programs.  A lot of sources say to install additional programs in /opt so I tried it.

Any suggestions to get things working again would be very much appreciated.  I am hoping that all my profile information is intact so I suppose I could just reinstall Seamonkey and import all my old data.  If you think this is the best solution please let me know.

I really like Seamonkey so I hope I can get it working again.

TIA

---

### Post by nanotube on 2010-11-04
wow, that /is/ really ugly.

anyway, yes, your seamonkey profile info is in your ~/.mozilla directory, so you should be able to safely uninstall/reinstall seamonkey, and see if that'll help.

(never hurts to make a backup first!)

that said... if you borked up a bunch of your packages with incompatible ones due to your funky update, it may not help, and your best option may be to do a clean install of the OS. ...

---

### Post by linux18 on 2010-11-04
sudo aptitude -f install

---

### Post by conmat on 2010-11-04
Hi,

I really want to thank everyone who replied!!!

I did a bunch of googling and I found the problem was I was missing all the ia32 libraries.  I just installed them with Synaptic and now Seamonkey is running again.

It was only because Linux users replied to other posts that I was able to find the solution to my problem.

Thanks again

---

### Post by conmat on 2010-11-04
> **nanotube said:**
> wow, that /is/ really ugly.

anyway, yes, your seamonkey profile info is in your ~/.mozilla directory, so you should be able to safely uninstall/reinstall seamonkey, and see if that'll help.

(never hurts to make a backup first!)

that said... if you borked up a bunch of your packages with incompatible ones due to your funky update, it may not help, and your best option may be to do a clean install of the OS. ...

I think this is what I will do.  10.4 is out so this is a good reason to do a clean install.  Thanks for your suggestions.

---

