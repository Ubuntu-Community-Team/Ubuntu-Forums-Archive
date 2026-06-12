---
title: "Firefox 3 on Ubuntu 6.06 (Dapper Drake)"
date: 2008-07-02
forum: Ubuntuzilla
---

### Post by nanotube on 2008-07-02
This thread is created to be the working hub of getting ff3 to run on Ubuntu 6.06 (dapper). 

The problem is that ff3 requires gtk 2.10 or later, but Dapper only has gtk 2.8.

So far we've tried using a pre-compiled gtk2.10 library (from feisty repos) and pointing ff3 to it, but it doesn't work. (see discussion thread here: 
[http://ubuntuforums.org/showthread.php?t=832407](http://ubuntuforums.org/showthread.php?t=832407)

The next thing to do is to try compiling gtk2.10 from source on dapper, to see if that gets the desired result. (instructions here: [http://www.captain.at/howto-run-firefox-3-debian-etch.php](http://www.captain.at/howto-run-firefox-3-debian-etch.php))

Anyone with input on getting this working (or anyone with a dapper box to try this on and report results) is welcome to post to this thread.

---

### Post by wkitty42 on 2008-07-03
ok, nanotube... i've read thru the thread where you and stig were working on getting this going... rather than following exactly the path you guys have already traversed, i've jumped ahead of that thread a bit and downloaded gtk+2.10.14 as indicated [*[COLOR="Blue"]here[/COLOR]*]("http://www.captain.at/howto-run-firefox-3-debian-etch.php") per your instructions...

i am keeping a log of the steps i am taking and what will need to be done so that when it is all over, i can post something similar to what i did in the other thread... i've already gathered the other instructions and will be working them into the steps as we get things compiled and working... well, if we can, that is :lol:

back to working with gtk+2.10.14... when running ./configure on the gtk+2.10.14 code, i'm getting a base_dependencies error stating that two packages i have are not new enough versions... here's the last lines where it is erroring out...

> checking for BASE_DEPENDENCIES... configure: error: Package requirements (glib-2.0 >= 2.12.0    atk >= 1.9.0    pango >= 1.12.0    cairo >= 1.2.0) were not met:

Requested 'glib-2.0 >= 2.12.0' but version of GLib is 2.10.3
Requested 'cairo >= 1.2.0' but version of cairo is 1.0.4

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables BASE_DEPENDENCIES_CFLAGS
and BASE_DEPENDENCIES_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.
seems easy enough to understand... however, i don't know which way to go, at this time, to get these and where to put them so they can be used and ***not*** screw up my existing Dapper installation...

your turn, maestro ;)

---

### Post by 0chiehchen on 2008-07-03
I am getting almost the same output here after I tried to compile gtk+2.10.14 under Dapper:

> checking for BASE_DEPENDENCIES... configure: error: Package requirements (glib-2.0 >= 2.12.0    atk >= 1.9.0    pango >= 1.12.0    cairo >= 1.2.0) were not met:
No package 'glib-2.0' found
No package 'atk' found
No package 'pango' found
No package 'cairo' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables BASE_DEPENDENCIES_CFLAGS
and BASE_DEPENDENCIES_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

---

### Post by nanotube on 2008-07-03
thanks for trying, wkitty42, 0chienchen.

ok, next try, try this: 

first, use ubuntuzilla to install ff3, then move your existing firefox profile out of the way, and then

run this script:
```
#!/bin/bash

########
# add-on script for ubuntuzilla, to make firefox3 run on Ubuntu 6.06 (Dapper).
# since ff3 requires gtk 2.10, but dapper comes with gtk 2.8, we need to 
# get gtk 2.10 and supporting libraries, and point firefox to it. 

#libglib
wget -c --tries=5 --read-timeout=20 --waitretry=10 http://mirror.mcs.anl.gov/pub/ubuntu/pool/main/g/glib2.0/libglib2.0-0_2.16.3-1_i386.deb -O /tmp/libglib2.0-0_2.16.3-1_i386.deb
sudo dpkg-deb -x /tmp/libglib2.0-0_2.16.3-1_i386.deb /opt/libglib

#libatk
wget -c --tries=5 --read-timeout=20 --waitretry=10 http://mirror.mcs.anl.gov/pub/ubuntu/pool/main/a/atk1.0/libatk1.0-0_1.22.0-0ubuntu1_i386.deb -O /tmp/libatk1.0-0_1.22.0-0ubuntu1_i386.deb
sudo dpkg-deb -x /tmp/libatk1.0-0_1.22.0-0ubuntu1_i386.deb /opt/libatk

#libpango
wget -c --tries=5 --read-timeout=20 --waitretry=10 http://mirror.mcs.anl.gov/pub/ubuntu/pool/main/p/pango1.0/libpango1.0-0_1.20.1-1_i386.deb -O /tmp/libpango1.0-0_1.20.1-1_i386.deb
sudo dpkg-deb -x /tmp/libpango1.0-0_1.20.1-1_i386.deb /opt/libpango

#libcairo
wget -c --tries=5 --read-timeout=20 --waitretry=10 http://mirror.mcs.anl.gov/pub/ubuntu/pool/main/c/cairo/libcairo2_1.6.0-0ubuntu1_i386.deb -O /tmp/libcairo2_1.6.0-0ubuntu1_i386.deb
sudo dpkg-deb -x /tmp/libcairo2_1.6.0-0ubuntu1_i386.deb /opt/libcairo

#libgtk
wget -c --tries=5 --read-timeout=20 --waitretry=10 http://mirror.mcs.anl.gov/pub/ubuntu/pool/main/g/gtk+2.0/libgtk2.0-0_2.12.9-3ubuntu2_i386.deb -O /tmp/libgtk2.0-0_2.12.9-3ubuntu2_i386.deb
sudo dpkg-deb -x /tmp/libgtk2.0-0_2.12.9-3ubuntu2_i386.deb /opt/libgtk

(
cat <<'EOF'
#!/bin/bash
export LD_LIBRARY_PATH="/opt/libglib/usr/lib:/opt/libatk/usr/lib:/opt/libpango/usr/lib:/opt/libcairo/usr/lib:/opt/libgtk/usr/lib"
/opt/firefox/firefox $*
EOF
) > /tmp/startfirefox.sh
sudo mv /tmp/startfirefox.sh /opt/firefox/
sudo chmod 755 /opt/firefox/startfirefox.sh
sudo chown root:root /opt/firefox/startfirefox.sh

# and finally, link /usr/bin/firefox to our startfirefox.sh script
sudo ln -s -f /opt/firefox/startfirefox.sh /usr/bin/firefox

```

try starting firefox by using command
```
/usr/bin/firefox
```

if any error messages are printed, please copy them all and post here. (hopefully, it will just work :) ). 

(by the way - it's certainly possible to restore back to ff2 afterwards... but it might be easier/safer to play with this using a livecd.)

would appreciate your feedback!

---

### Post by wkitty42 on 2008-07-03
ok... i've got the script and have moved my profile and existing ff2 install out of the way... will be back shortly to report on the results... hopefully i'll be coming in in FF3 ;)

FWIW: livecd is much much too slow on this old PII 450 :?

---

### Post by wkitty42 on 2008-07-03
> **wkitty42 said:**
> ok... i've got the script and have moved my profile and existing ff2 install out of the way... will be back shortly to report on the results... hopefully i'll be coming in in FF3 ;)

FWIW: livecd is much much too slow on this old PII 450 :?

well... luckily there still exists the /usr/bin/firefox.ubuntu link to the old FF1.5.0.12eol and i don't have to dance too much to get back in here to make my report...

here's the error message...

> /usr/bin/firefox
/opt/firefox/firefox-bin: error while loading shared libraries: libpixman-1.so.0: cannot open shared object file: No such file or directory
:(

gimme the couple of lines to add to my ff3-fixer script and i'll shoot it again ;)

**[EDIT]**
belay that... actually, i created the following lines based on the existing ones in the script and then fixed up the LD_LIBRARY_PATH export line to include the pixman stuff and now i get a different set of errors...  here's what i added...

```
#libpixman
wget -c --tries=5 --read-timeout=20 --waitretry=10 http://mirror.mcs.anl.gov/pub/ubuntu/pool/main/p/pixman/libpixman-1-0_0.10.0-0ubuntu1_i386.deb -O /tmp/libpixman-1-0_0.10.0-0ubuntu1_i386.deb
sudo dpkg-deb -x /tmp/libpixman-1-0_0.10.0-0ubuntu1_i386.deb /opt/libpixman
```

and the updated LD_LIBRARY_PATH line...

```
export LD_LIBRARY_PATH="/opt/libpixman/usr/lib:/opt/libglib/usr/lib:/opt/libatk/usr/lib:/opt/libpango/usr/lib:/opt/libcairo/usr/lib:/opt/libgtk/usr/lib"
```

and finally, the new errors...

> /usr/bin/firefox
/opt/firefox/firefox-bin: /lib/tls/i686/cmov/libc.so.6: version `GLIBC_2.4' not found (required by /opt/libgtk/usr/lib/libgtk-x11-2.0.so.0)
/opt/firefox/firefox-bin: /lib/tls/i686/cmov/libc.so.6: version `GLIBC_2.4' not found (required by /opt/libgtk/usr/lib/libgdk-x11-2.0.so.0)
/opt/firefox/firefox-bin: /lib/tls/i686/cmov/libc.so.6: version `GLIBC_2.4' not found (required by /opt/libgtk/usr/lib/libgdk_pixbuf-2.0.so.0)
/opt/firefox/firefox-bin: /lib/tls/i686/cmov/libc.so.6: version `GLIBC_2.4' not found (required by /opt/libpango/usr/lib/libpango-1.0.so.0)
/opt/firefox/firefox-bin: /lib/tls/i686/cmov/libc.so.6: version `GLIBC_2.4' not found (required by /opt/libcairo/usr/lib/libcairo.so.2)
/opt/firefox/firefox-bin: /lib/tls/i686/cmov/libc.so.6: version `GLIBC_2.4' not found (required by /opt/libglib/usr/lib/libgobject-2.0.so.0)
/opt/firefox/firefox-bin: /lib/tls/i686/cmov/libc.so.6: version `GLIBC_2.4' not found (required by /opt/libglib/usr/lib/libglib-2.0.so.0)
/opt/firefox/firefox-bin: /lib/tls/i686/cmov/libc.so.6: version `GLIBC_2.4' not found (required by /opt/libglib/usr/lib/libgthread-2.0.so.0)
/opt/firefox/firefox-bin: /lib/tls/i686/cmov/libc.so.6: version `GLIBC_2.4' not found (required by /opt/libpixman/usr/lib/libpixman-1.so.0)

looks like we need this tls stuff??? :(
**[/EDIT]**

FWIW: we should also try to get in sync for being on here at the same time while working on this... we're both on east coast time... in fact, i was just in your area no more than a month or two ago! :lolflag:
PM me with the best time(s) for you and i'll be here ;)

---

### Post by vob on 2008-07-04
Obviously we need a newer glibc version, since dapper comes with 2.3.6 (check this with 'dpkg -l |grep libc6', this will also list you the libc6 versions that are installed on your machine). I suspect that the above procedure of downloading the library, installing it to a custom place and updating the LD_LIBRARY_PATH accordingly should work as before. Could you try that and post the results? Thanks.

---

### Post by nanotube on 2008-07-04
> **wkitty42 said:**
> well... luckily there still exists the /usr/bin/firefox.ubuntu link to the old FF1.5.0.12eol and i don't have to dance too much to get back in here to make my report...
 

indeed :)

> 
looks like we need this tls stuff??? :(


yea, that's the libc6 library, which is pretty central to the whole system... but what the heck, let's give it a shot. i added the libc6 to the script, give it another try. (note also that i decided to install all "local" libraries to /opt/lib/libname, rather than just to /opt/libname, so that when we are all done, if we want to undo, all you need to do is delete /opt/lib, rather than deleting a bunch of different dirs.

anyway, here's the latest script:
```
#!/bin/bash

########
# add-on script for ubuntuzilla, to make firefox3 run on Ubuntu 6.06 (Dapper).
# since ff3 requires gtk 2.10, but dapper comes with gtk 2.8, we need to 
# get gtk 2.10 and supporting libraries, and point firefox to it. 

#libglib
wget -c --tries=5 --read-timeout=20 --waitretry=10 http://mirror.mcs.anl.gov/pub/ubuntu/pool/main/g/glib2.0/libglib2.0-0_2.16.3-1_i386.deb -O /tmp/libglib2.0-0_2.16.3-1_i386.deb
sudo dpkg-deb -x /tmp/libglib2.0-0_2.16.3-1_i386.deb /opt/lib/libglib

#libatk
wget -c --tries=5 --read-timeout=20 --waitretry=10 http://mirror.mcs.anl.gov/pub/ubuntu/pool/main/a/atk1.0/libatk1.0-0_1.22.0-0ubuntu1_i386.deb -O /tmp/libatk1.0-0_1.22.0-0ubuntu1_i386.deb
sudo dpkg-deb -x /tmp/libatk1.0-0_1.22.0-0ubuntu1_i386.deb /opt/lib/libatk

#libpango
wget -c --tries=5 --read-timeout=20 --waitretry=10 http://mirror.mcs.anl.gov/pub/ubuntu/pool/main/p/pango1.0/libpango1.0-0_1.20.1-1_i386.deb -O /tmp/libpango1.0-0_1.20.1-1_i386.deb
sudo dpkg-deb -x /tmp/libpango1.0-0_1.20.1-1_i386.deb /opt/lib/libpango

#libcairo
wget -c --tries=5 --read-timeout=20 --waitretry=10 http://mirror.mcs.anl.gov/pub/ubuntu/pool/main/c/cairo/libcairo2_1.6.0-0ubuntu1_i386.deb -O /tmp/libcairo2_1.6.0-0ubuntu1_i386.deb
sudo dpkg-deb -x /tmp/libcairo2_1.6.0-0ubuntu1_i386.deb /opt/lib/libcairo

#libgtk
wget -c --tries=5 --read-timeout=20 --waitretry=10 http://mirror.mcs.anl.gov/pub/ubuntu/pool/main/g/gtk+2.0/libgtk2.0-0_2.12.9-3ubuntu2_i386.deb -O /tmp/libgtk2.0-0_2.12.9-3ubuntu2_i386.deb
sudo dpkg-deb -x /tmp/libgtk2.0-0_2.12.9-3ubuntu2_i386.deb /opt/lib/libgtk

#libpixman
wget -c --tries=5 --read-timeout=20 --waitretry=10 http://mirror.mcs.anl.gov/pub/ubuntu/pool/main/p/pixman/libpixman-1-0_0.10.0-0ubuntu1_i386.deb -O /tmp/libpixman-1-0_0.10.0-0ubuntu1_i386.deb
sudo dpkg-deb -x /tmp/libpixman-1-0_0.10.0-0ubuntu1_i386.deb /opt/lib/libpixman

#libc6
wget -c --tries=5 --read-timeout=20 --waitretry=10 http://mirror.mcs.anl.gov/pub/ubuntu/pool/main/g/glibc/libc6_2.7-10ubuntu3_i386.deb -O /tmp/libc6_2.7-10ubuntu3_i386.deb
sudo dpkg-deb -x /tmp/libc6_2.7-10ubuntu3_i386.deb /opt/lib/libc6

http://mirror.mcs.anl.gov/pub/ubuntu/pool/main/g/glibc/libc6_2.7-10ubuntu3_i386.deb
(
cat <<'EOF'
#!/bin/bash
export LD_LIBRARY_PATH="/opt/lib/libglib/usr/lib:/opt/lib/libatk/usr/lib:/opt/lib/libpango/usr/lib:/opt/lib/libcairo/usr/lib:/opt/lib/libgtk/usr/lib:/opt/lib/libpixman/usr/lib:/opt/lib/libc6/lib/tls/i686/cmov"
/opt/firefox/firefox $*
EOF
) > /tmp/startfirefox.sh
sudo mv /tmp/startfirefox.sh /opt/firefox/
sudo chmod 755 /opt/firefox/startfirefox.sh
sudo chown root:root /opt/firefox/startfirefox.sh

# and finally, link /usr/bin/firefox to our startfirefox.sh script
sudo ln -s -f /opt/firefox/startfirefox.sh /usr/bin/firefox
```

give it a whirl, and then see what ```
/usr/bin/firefox
``` does. :)

> 
FWIW: we should also try to get in sync for being on here at the same time while working on this... we're both on east coast time... in fact, i was just in your area no more than a month or two ago! :lolflag:
PM me with the best time(s) for you and i'll be here ;)

an excellent idea - but unfortunately i don't really have a set time when i work on this - whenever i get a break from doing "<officespace>real, actual, work </officespace>". :)

but if we'll see...

somehow, i suspect that putting in libc6 is not going to make a lot of other stuff happy... there is a whole tree of libc6 dependents out there. but let's hope. :)

---

### Post by wkitty42 on 2008-07-05
> **vob said:**
> Obviously we need a newer glibc version, since dapper comes with 2.3.6 (check this with 'dpkg -l |grep libc6', this will also list you the libc6 versions that are installed on your machine).

> **dpkg -l | grep libc6]```
ii  libc6                                  2.3.6-0ubuntu20.5                                   GNU C Library: Shared libraries and Timezone
ii  libc6-dev                              2.3.6-0ubuntu20.5                                   GNU C Library: Development Libraries and Hea
ii  libc6-i686                             2.3.6-0ubuntu20.5                                   GNU C Library: Shared libraries [i686 optimi
```[/quote]

[QUOTE=vob said:**
> I suspect that the above procedure of downloading the library, installing it to a custom place and updating the LD_LIBRARY_PATH accordingly should work as before. Could you try that and post the results? Thanks.
i suspect you may be correct ;)

---

### Post by wkitty42 on 2008-07-05
> **nanotube said:**
> indeed :)
yeah, and i've also tried to work this out so that i can have all three available and operational... but i'm not so sure about how to handle the ~/.mozilla folder or how to get each one to look at it's own (ie: ~/.mozilla for ff1, ~/.mozilla.ff2 for ff2, and ~/.mozilla.ff3 for ff3) so i've been juggling the ~/.mozilla folder by copying back and forth depending on which version i'm trying to work with at the moment...

> **nanotube said:**
> yea, that's the libc6 library, which is pretty central to the whole system... but what the heck, let's give it a shot. i added the libc6 to the script, give it another try. (note also that i decided to install all "local" libraries to /opt/lib/libname, rather than just to /opt/libname, so that when we are all done, if we want to undo, all you need to do is delete /opt/lib, rather than deleting a bunch of different dirs.
and we don't have to do anything with dpkg to remove anything from the database, eh?

> **nanotube said:**
> anyway, here's the latest script:
got it and tried it... while it seems to work, we've still got a problem... two, actually... the first is an errant line in the script...

> **nanotube said:**
> ```
sudo dpkg-deb -x /tmp/libc6_2.7-10ubuntu3_i386.deb /opt/lib/libc6

http://mirror.mcs.anl.gov/pub/ubuntu/pool/main/g/glibc/libc6_2.7-10ubuntu3_i386.deb
(
cat <<'EOF'

```
that **http://** line appears to be in the way... i removed it in my copy and the script ran on to completion...

> **nanotube said:**
> somehow, i suspect that putting in libc6 is not going to make a lot of other stuff happy... there is a whole tree of libc6 dependents out there. but let's hope. :)
well, seems that the libc6 library doesn't contain everything needed or the libraries we've stuffed into /opt/lib are hardcoded to look in a specific place for the tls stuff...

> /usr/bin/firefox
/opt/firefox/firefox-bin: /lib/tls/i686/cmov/libc.so.6: version `GLIBC_2.4' not found (required by /opt/lib/libgtk/usr/lib/libgtk-x11-2.0.so.0)
/opt/firefox/firefox-bin: /lib/tls/i686/cmov/libc.so.6: version `GLIBC_2.4' not found (required by /opt/lib/libgtk/usr/lib/libgdk-x11-2.0.so.0)
/opt/firefox/firefox-bin: /lib/tls/i686/cmov/libc.so.6: version `GLIBC_2.4' not found (required by /opt/lib/libgtk/usr/lib/libgdk_pixbuf-2.0.so.0)
/opt/firefox/firefox-bin: /lib/tls/i686/cmov/libc.so.6: version `GLIBC_2.4' not found (required by /opt/lib/libpango/usr/lib/libpango-1.0.so.0)
/opt/firefox/firefox-bin: /lib/tls/i686/cmov/libc.so.6: version `GLIBC_2.4' not found (required by /opt/lib/libcairo/usr/lib/libcairo.so.2)
/opt/firefox/firefox-bin: /lib/tls/i686/cmov/libc.so.6: version `GLIBC_2.4' not found (required by /opt/lib/libglib/usr/lib/libgobject-2.0.so.0)
/opt/firefox/firefox-bin: /lib/tls/i686/cmov/libc.so.6: version `GLIBC_2.4' not found (required by /opt/lib/libglib/usr/lib/libglib-2.0.so.0)
/opt/firefox/firefox-bin: /lib/tls/i686/cmov/libc.so.6: version `GLIBC_2.4' not found (required by /opt/lib/libglib/usr/lib/libgthread-2.0.so.0)
/opt/firefox/firefox-bin: /lib/tls/i686/cmov/libc.so.6: version `GLIBC_2.4' not found (required by /opt/lib/libpixman/usr/lib/libpixman-1.so.0)
yeah... it is the same error as before... so i peeked into /opt/lib/libc6 to compare what was in there with the LD_LIBRARY_PATH line addition and there's no tls stuff in there at all... so i'm wondering if we should have the tls portion listed on that line... maybe just a pointer to the /opt/lib/libc6/lib?

i'll give that a try and see what happens... be back in a short since i gotta juggle the ~/.mozilla directory between ff2 and ff3...

---

### Post by wkitty42 on 2008-07-05
> **wkitty42 said:**
> yeah... it is the same error as before... so i peeked into /opt/lib/libc6 to compare what was in there with the LD_LIBRARY_PATH line addition and there's no tls stuff in there at all... so i'm wondering if we should have the tls portion listed on that line... maybe just a pointer to the /opt/lib/libc6/lib?

i'll give that a try and see what happens... be back in a short since i gotta juggle the ~/.mozilla directory between ff2 and ff3...
well, changing the LD_LIBRARY_PATH didn't work at all...

we started with this...
```
export LD_LIBRARY_PATH="/opt/lib/libglib/usr/lib:/opt/lib/libatk/usr/lib:/opt/lib/libpango/usr/lib:/opt/lib/libcairo/usr/lib:/opt/lib/libgtk/usr/lib:/opt/lib/libpixman/usr/lib:/opt/lib/libc6/lib/tls/i686/cmov"
```
and i knocked it down to this [see end of the line]...
```
export LD_LIBRARY_PATH="/opt/lib/libglib/usr/lib:/opt/lib/libatk/usr/lib:/opt/lib/libpango/usr/lib:/opt/lib/libcairo/usr/lib:/opt/lib/libgtk/usr/lib:/opt/lib/libpixman/usr/lib:/opt/lib/libc6/lib"
```
and got this in return...
> /usr/bin/firefox
/usr/bin/firefox: line 3: 13961 Segmentation fault      /opt/firefox/firefox $*
so, i trimmed it down a tad more [see end of the line again]...
```
export LD_LIBRARY_PATH="/opt/lib/libglib/usr/lib:/opt/lib/libatk/usr/lib:/opt/lib/libpango/usr/lib:/opt/lib/libcairo/usr/lib:/opt/lib/libgtk/usr/lib:/opt/lib/libpixman/usr/lib:/opt/lib/libc6"
```
as well as editing /opt/firefox/firefox to turn on debugging and i got this...
> /usr/bin/firefox
+ moz_libdir=/usr/local/lib/firefox-3.0
+ found=0
+ progname=/opt/firefox/firefox
++ dirname /opt/firefox/firefox
+ curdir=/opt/firefox
++ basename /opt/firefox/firefox
+ progbase=firefox
+ run_moz=/opt/firefox/run-mozilla.sh
+ test -x /opt/firefox/run-mozilla.sh
+ dist_bin=/opt/firefox
+ found=1
+ '[' 1 = 0 ']'
+ script_args=
+ debugging=0
+ MOZILLA_BIN=firefox-bin
+ '[' linux-gnu = beos ']'
+ pass_arg_count=0
+ '[' 0 -gt 0 ']'
+ '[' 0 = 1 ']'
+ /opt/firefox/run-mozilla.sh /opt/firefox/firefox-bin
/opt/firefox/firefox-bin: /lib/tls/i686/cmov/libc.so.6: version `GLIBC_2.4' not found (required by /opt/lib/libgtk/usr/lib/libgtk-x11-2.0.so.0)
/opt/firefox/firefox-bin: /lib/tls/i686/cmov/libc.so.6: version `GLIBC_2.4' not found (required by /opt/lib/libgtk/usr/lib/libgdk-x11-2.0.so.0)
/opt/firefox/firefox-bin: /lib/tls/i686/cmov/libc.so.6: version `GLIBC_2.4' not found (required by /opt/lib/libgtk/usr/lib/libgdk_pixbuf-2.0.so.0)
/opt/firefox/firefox-bin: /lib/tls/i686/cmov/libc.so.6: version `GLIBC_2.4' not found (required by /opt/lib/libpango/usr/lib/libpango-1.0.so.0)
/opt/firefox/firefox-bin: /lib/tls/i686/cmov/libc.so.6: version `GLIBC_2.4' not found (required by /opt/lib/libcairo/usr/lib/libcairo.so.2)
/opt/firefox/firefox-bin: /lib/tls/i686/cmov/libc.so.6: version `GLIBC_2.4' not found (required by /opt/lib/libglib/usr/lib/libgobject-2.0.so.0)
/opt/firefox/firefox-bin: /lib/tls/i686/cmov/libc.so.6: version `GLIBC_2.4' not found (required by /opt/lib/libglib/usr/lib/libglib-2.0.so.0)
/opt/firefox/firefox-bin: /lib/tls/i686/cmov/libc.so.6: version `GLIBC_2.4' not found (required by /opt/lib/libglib/usr/lib/libgthread-2.0.so.0)
/opt/firefox/firefox-bin: /lib/tls/i686/cmov/libc.so.6: version `GLIBC_2.4' not found (required by /opt/lib/libpixman/usr/lib/libpixman-1.so.0)
+ exitcode=1
+ exit 1
so we're still in the same boat unless/until we can figure out what's going on with the tls stuff :?

alternatively, it would appear that we might be approaching the land of compiling ff3 from sources on Dapper if we really want to run ff3...

---

### Post by nanotube on 2008-07-06
hm, ok, try running with debug again, but use the last bit of ld_library_path as "/opt/lib/libc6/lib", and see what it spits out. 

but yes, if that doesn't point us to anywhere useful, seems like the best bet would be to compile ff3 into a static binary (so that rather than depending on a bunch of shared libs, everything is linked into the binary), and see if that runs.

---

### Post by nanotube on 2008-07-06
ok well, if the previous bit doesn't do it, try a static compile of firefox. 

i made a static compile of ff3 source on my feisty box, posted the package. 
give it a try:
[http://ubuntuzilla.sourceforge.net/firefox-3.0.en-US.linux-i686.static.tar.bz2](http://ubuntuzilla.sourceforge.net/firefox-3.0.en-US.linux-i686.static.tar.bz2)

all the libraries are statically linked (or should be, at any rate :) ), so it should run on "anything".

edit: another thing to try would be to try compiling gtk2.10 from source on dapper, and then pointing ff3 to it. that would have the benefit of not having to recompile firefox every time there's a firefox update, you only have to compile gtk2.10 once. there are some instructions here: [http://www.captain.at/howto-run-firefox-3-debian-etch.php](http://www.captain.at/howto-run-firefox-3-debian-etch.php)

---

### Post by wkitty42 on 2008-07-09
> **nanotube said:**
> hm, ok, try running with debug again, but use the last bit of ld_library_path as "/opt/lib/libc6/lib", and see what it spits out. 
ahh... yeah, i didn't do that...

> **nanotube said:**
> but yes, if that doesn't point us to anywhere useful, seems like the best bet would be to compile ff3 into a static binary (so that rather than depending on a bunch of shared libs, everything is linked into the binary), and see if that runs.
yeah... i think that's the best way to go... that way dapper doesn't get "polluted" with all those other, newer libraries and stuff ;)

---

### Post by wkitty42 on 2008-07-09
> **nanotube said:**
> ok well, if the previous bit doesn't do it, try a static compile of firefox. 

i made a static compile of ff3 source on my feisty box, posted the package. 
give it a try:
[http://ubuntuzilla.sourceforge.net/firefox-3.0.en-US.linux-i686.static.tar.bz2](http://ubuntuzilla.sourceforge.net/firefox-3.0.en-US.linux-i686.static.tar.bz2)

all the libraries are statically linked (or should be, at any rate :) ), so it should run on "anything".
cool... i'll pull it down later and give it a try... dunno how to install it, though :?

[edit]
after a quick peek inside the archive (from my windows side of the world), i'm guessing that the standard ```
sudo tar -zxvf filename -C /opt
```command would be appropriate?
[/edit]

> **nanotube said:**
> edit: another thing to try would be to try compiling gtk2.10 from source on dapper, and then pointing ff3 to it. that would have the benefit of not having to recompile firefox every time there's a firefox update, you only have to compile gtk2.10 once. there are some instructions here: [http://www.captain.at/howto-run-firefox-3-debian-etch.php](http://www.captain.at/howto-run-firefox-3-debian-etch.php)
hummm... i actually did drop by the mozilla site thinking that i might grab the sources and give the compile a try but their requirements are a bit more than this machine can handle... plus there's those libraries they require... i think i'll give your static version a try first before attempting the compile thingee ;)

---

### Post by nanotube on 2008-07-09
Hi,
yea, the compiled tar.bz2 just has to be extracted to somewhere. note that its a tar.bz2, not tar.gz, so the tar flags have to be -xjf, not -xzf.

also, for just in case, delete the previous stuff in /opt/firefox, before you extract the new archive into it. so:
```
sudo rm -rf /opt/firefox
sudo tar -xjf firefox-3.0.en-US.linux-i686.static.tar.bz2 -C /opt
```

then, try 
```
/opt/firefox/firefox
```
and see what happens. :)

---

### Post by Nitemare14 on 2008-07-12
The static binary doesn't work for me.

```

/opt/firefox/firefox-bin: /lib/tls/i686/cmov/libc.so.6: version `GLIBC_2.4' not found (required by /opt/firefox/firefox-bin)
/opt/firefox/firefox-bin: /lib/tls/i686/cmov/libc.so.6: version `GLIBC_2.4' not found (required by /opt/firefox/libjemalloc.so)
/opt/firefox/firefox-bin: /lib/tls/i686/cmov/libc.so.6: version `GLIBC_2.4' not found (required by /opt/firefox/libmozjs.so)
/opt/firefox/firefox-bin: /lib/tls/i686/cmov/libc.so.6: version `GLIBC_2.4' not found (required by /opt/firefox/libxpcom_core.so)
/opt/firefox/firefox-bin: /lib/tls/i686/cmov/libc.so.6: version `GLIBC_2.4' not found (required by /opt/firefox/libnspr4.so)
/opt/firefox/firefox-bin: /lib/tls/i686/cmov/libc.so.6: version `GLIBC_2.4' not found (required by /opt/firefox/libsmime3.so)
/opt/firefox/firefox-bin: /lib/tls/i686/cmov/libc.so.6: version `GLIBC_2.4' not found (required by /opt/firefox/libssl3.so)
/opt/firefox/firefox-bin: /lib/tls/i686/cmov/libc.so.6: version `GLIBC_2.4' not found (required by /opt/firefox/libnss3.so)
/opt/firefox/firefox-bin: /lib/tls/i686/cmov/libc.so.6: version `GLIBC_2.4' not found (required by /opt/firefox/libnssutil3.so)
/opt/firefox/firefox-bin: /lib/tls/i686/cmov/libc.so.6: version `GLIBC_2.4' not found (required by /opt/firefox/libsoftokn3.so)
/opt/firefox/firefox-bin: /lib/tls/i686/cmov/libc.so.6: version `GLIBC_2.4' not found (required by /opt/firefox/libsqlite3.so)

```

---

### Post by nanotube on 2008-07-12
> **Nitemare14 said:**
> The static binary doesn't work for me.

```

/opt/firefox/firefox-bin: /lib/tls/i686/cmov/libc.so.6: version `GLIBC_2.4' not found (required by /opt/firefox/firefox-bin)
/opt/firefox/firefox-bin: /lib/tls/i686/cmov/libc.so.6: version `GLIBC_2.4' not found (required by /opt/firefox/libjemalloc.so)
/opt/firefox/firefox-bin: /lib/tls/i686/cmov/libc.so.6: version `GLIBC_2.4' not found (required by /opt/firefox/libmozjs.so)
/opt/firefox/firefox-bin: /lib/tls/i686/cmov/libc.so.6: version `GLIBC_2.4' not found (required by /opt/firefox/libxpcom_core.so)
/opt/firefox/firefox-bin: /lib/tls/i686/cmov/libc.so.6: version `GLIBC_2.4' not found (required by /opt/firefox/libnspr4.so)
/opt/firefox/firefox-bin: /lib/tls/i686/cmov/libc.so.6: version `GLIBC_2.4' not found (required by /opt/firefox/libsmime3.so)
/opt/firefox/firefox-bin: /lib/tls/i686/cmov/libc.so.6: version `GLIBC_2.4' not found (required by /opt/firefox/libssl3.so)
/opt/firefox/firefox-bin: /lib/tls/i686/cmov/libc.so.6: version `GLIBC_2.4' not found (required by /opt/firefox/libnss3.so)
/opt/firefox/firefox-bin: /lib/tls/i686/cmov/libc.so.6: version `GLIBC_2.4' not found (required by /opt/firefox/libnssutil3.so)
/opt/firefox/firefox-bin: /lib/tls/i686/cmov/libc.so.6: version `GLIBC_2.4' not found (required by /opt/firefox/libsoftokn3.so)
/opt/firefox/firefox-bin: /lib/tls/i686/cmov/libc.so.6: version `GLIBC_2.4' not found (required by /opt/firefox/libsqlite3.so)

```

aha, so it appears that glibc did not get statically linked for some reason. try adding it in separately, using this script:

```
#!/bin/bash

#libc6
wget -c --tries=5 --read-timeout=20 --waitretry=10 http://mirror.mcs.anl.gov/pub/ubuntu/pool/main/g/glibc/libc6_2.5-0ubuntu14_i386.deb -O /tmp/libc6_2.5-0ubuntu14_i386.deb
sudo dpkg-deb -x /tmp/libc6_2.5-0ubuntu14_i386.deb /opt/lib/libc6

(
cat <<'EOF'
#!/bin/bash
export LD_LIBRARY_PATH="/opt/lib/libc6/lib"
/opt/firefox/firefox $*
EOF
) > /tmp/startfirefox.sh
sudo mv /tmp/startfirefox.sh /opt/firefox/
sudo chmod 755 /opt/firefox/startfirefox.sh
sudo chown root:root /opt/firefox/startfirefox.sh

```

then try running firefox with
```
/opt/firefox/startfirefox.sh
```

i think we're getting close... :)

---

### Post by nanotube on 2008-07-22
well, i just tried this on my dapper livecd, and the static build gives a segfault when trying to point it to a "new" libc6. 

so, unless someone else figures out how to statically-compile firefox, including the static linking of libc6 (which "usual" static compile appears not to do), or finds some other workaround, it seems that dapper users will have to stick with firefox 2.

---

### Post by Buddha443556 on 2008-08-20
Any update on this? This ever going to work on Dapper?

---

### Post by wkitty42 on 2008-08-20
> **Buddha443556 said:**
> Any update on this?
to be honest, i don't know...

> **Buddha443556 said:**
> This ever going to work on Dapper?
that remains to be seen...

sadly, i've not had time to revisit the project... R.L. situations have risen their heads which keep me from having been able to get back to this to carry on with my testings :(

the most extreme of these R.L. situations is that my mother has landed herself in the hospital with what appears to be [[COLOR="Red"]_pancreatic cancer_[/COLOR]]("http://en.wikipedia.org/wiki/Pancreatic_cancer") :(  the current prognosis is 6 to 9 months before termination (of life) :( :( :(

please, if anyone wishes to give condolences or otherwise express their emotions, take this to PM/email... alternatively, visit [[COLOR="Red"]_her caringbridge site_[/COLOR]]("http://www.caringbridge.org/visit/donnalewis") with the password of "marciasmom" (sans quotes)...

thank you in advance for your consideration and cooperation...

---

### Post by Buddha443556 on 2008-10-06
I found something that works.

[How to Run Firefox 3 on Ubuntu Edgy, Feisty or Dapper](http://techieblurbs.blogspot.com/2008/09/how-to-run-firefox3-on-ubuntu-edgy.html) [LINK]

It works. Here's the versions of the libraries I used (in the correct order):

glib-2.18.1
pixman-0.12.0 (May screws up the environmental varables ... not sure)
cairo-1.8.0
pango-1.20.5
atk-1.22.0
gtk+-2.12.12 (2.14.3 would not build)

Pixman and GTK+ gave me some problems. 

```
mkdir -p ~/firefox/src
export LD_LIBRARY_PATH=~/firefox/lib
export LDFLAGS=-L${HOME}/firefox/lib
export CPPFLAGS=-I${HOME}/firefox/include
export PKG_CONFIG_PATH=${HOME}/firefox/lib/pkgconfig/
export CFLAGS=-I${HOME}/firefox/include
cd ~/firefox
tar xvjf ~/firefox-3.0.3.tar.bz2
cd ~/firefox/src

cd (package dir)
./configure --prefix=$HOME/firefox
make
make install

LD_LIBRARY_PATH=~/firefox/lib ~/firefox/firefox/firefox
```

Flash worked with no problems, Java may have needed updating. Anyway I wasn't impressed enough to move up to FF3 but now I can at least check it out from time to time.

Sorry to hear about your mother wkitty42, my own mother died recently after a long hospital stay. Best advice I can give you, 80% of family members with relatives in ICU develop a Post Traumatic Stress Reaction and up to as high as 30% of those will actually develop PTSD or Traumatic Grief so get counseling. PTSD, TG and Severe MD all suck ... yes that's a personal statement from someone that knows.

UPDATE:

Adding gtk-qt-engine (version 0.7) helps the look a lot!

---

### Post by Schugy on 2008-12-07
I've made a f[ew deb-packages for Dapper]("http://www.schugy.de/Linux/firefox3libs4dapper/firefox3libs4dapper.tar.bz2") to make things easier. Just download an offcial FF3 build and install it to /usr/local/firefox. That works system wide with every user.

---

### Post by jhorv on 2009-01-29
Great job guys.

For me, however, it still doesn't work. :(

In installed the deb packages (dpkg -i [file].deb), worked like a charm. :p

I checked Synaptic and everything was listed there as installed. However, when I installed FireFox to /usr/local/firefox and tried to run it (/usr/local/firefox/firefox), I got the same message as before that I only had GTK+ 2.8 installed and that I needed 2.10 or newer, yet the version that was installed was 2.12 so it should have worked.

Anyone have any ideas?

---

### Post by Schugy on 2009-01-29
I've edited /usr/local/firefox/firefox startup script.

```
#!/bin/sh
#
# ***** BEGIN LICENSE BLOCK *****
# Version: MPL 1.1/GPL 2.0/LGPL 2.1
#
# The contents of this file are subject to the Mozilla Public License Version
# 1.1 (the "License"); you may not use this file except in compliance with
# the License. You may obtain a copy of the License at
# http://www.mozilla.org/MPL/
#
# Software distributed under the License is distributed on an "AS IS" basis,
# WITHOUT WARRANTY OF ANY KIND, either express or implied. See the License
# for the specific language governing rights and limitations under the
# License.
#
# The Original Code is mozilla.org Code.
#
# The Initial Developer of the Original Code is
# Netscape Communications Corporation.
# Portions created by the Initial Developer are Copyright (C) 1998
# the Initial Developer. All Rights Reserved.
#
# Contributor(s):
#
# Alternatively, the contents of this file may be used under the terms of
# either the GNU General Public License Version 2 or later (the "GPL"), or
# the GNU Lesser General Public License Version 2.1 or later (the "LGPL"),
# in which case the provisions of the GPL or the LGPL are applicable instead
# of those above. If you wish to allow use of your version of this file only
# under the terms of either the GPL or the LGPL, and not to allow others to
# use your version of this file under the terms of the MPL, indicate your
# decision by deleting the provisions above and replace them with the notice
# and other provisions required by the GPL or the LGPL. If you do not delete
# the provisions above, a recipient may use your version of this file under
# the terms of any one of the MPL, the GPL or the LGPL.
#
# ***** END LICENSE BLOCK *****

## $Id: mozilla.in,v 1.16 2007/10/05 07:29:26 reed%reedloden.com Exp $
## 
## Usage:
##
## $ mozilla [args]
##
## This script is meant to run the mozilla-bin binary from either 
## mozilla/xpfe/bootstrap or mozilla/dist/bin.
##
## The script will setup all the environment voodoo needed to make
## the mozilla-bin binary to work.
##
export LD_LIBRARY_PATH=/usr/local/ff3compatlibs/lib
#uncomment for debugging
#set -x
```

Just paste this export LD_LIBRARY_PATH=/usr/local/ff3compatlibs/lib into the file. For me it is in line 51.

---

### Post by jhorv on 2009-01-29
Thanks Schugy. Unfortunately it still doesn't work.

At first I tried creating a Launcher on my desktop with the following:
[INDENT]*LD_LIBRARY_PATH=/usr/local/ff3compatlibs/lib /usr/local/firefox/firefox*[/INDENT]
but it didn't work. The error I got was that it couldn't find the file or directory /usr/local/ff3compatlibs/lib even though it's there.

I then thought the solution might be with the firefox startup script, so I changed the line
[INDENT]*moz_libdir=/usr/local/lib/firefox-3.0.5*[/INDENT] to [INDENT]*moz_libdir=/usr/local/ff3compatlibs/lib*[/INDENT]
Needless to say that didn't work. I got the same message as before that I have the wrong version of GTK+.

I then tried your suggestion 
[INDENT]*export LD_LIBRARY_PATH=/usr/local/ff3compatlibs/lib*[/INDENT]
but nothing happened. I didn't get an error message either. Simply nothing happened.

What I can't understand is that when I got the wrong version error message why does firefox say I have version 2.8? In Synaptic I see only 2.12; there isn't a GTK+2.8 anywhere.:confused:

---

### Post by drepa on 2009-05-21
> **Schugy said:**
> I've made a f[ew deb-packages for Dapper]("http://www.schugy.de/Linux/firefox3libs4dapper/firefox3libs4dapper.tar.bz2") to make things easier. Just download an offcial FF3 build and install it to /usr/local/firefox. That works system wide with every user.

Your debs worked great.  I installed them in this order glib, pixman, cairo, pango, atk, gtk+, as suggested by [http://techieblurbs.blogspot.com/2008/09/how-to-run-firefox3-on-ubuntu-edgy.html](http://techieblurbs.blogspot.com/2008/09/how-to-run-firefox3-on-ubuntu-edgy.html) .

I also needed to install libxcomposite1.

Question - is there an easy way to get Flash Player 10 working now with this little FF3 hack?

Thanks for the debs!!

---

### Post by Schugy on 2009-05-22
I'd suggest to type it in xterm first before using a launcher. Maybe it just need the hole thing in "".

Reinstall the original firefox-script. Note, it will be overwritten on some automatic updates. Just repaste that line into the skript.

Good luck.

I will test the flash plyer for you soon but I usually hate and boycott that stupid flash pages.

---

### Post by drepa on 2009-05-22
> **Schugy said:**
> 

I will test the flash plyer for you soon but I usually hate and boycott that stupid flash pages.

I'm with you on that.  The work was for my folks computer.  I don't give them a hard time about the flash, I am just happy to see them use something Linux based. Thank goodness for ssh and vnc, as I did the fix(well more like a hack) from 5,000km away.

---

### Post by Bunny Boy on 2009-06-01
> **nanotube said:**
> thanks for trying, wkitty42, 0chienchen.

ok, next try, try this: 

first, use ubuntuzilla to install ff3, then move your existing firefox profile out of the way, and then

run this script:
```
#!/bin/bash

########
# add-on script for ubuntuzilla, to make firefox3 run on Ubuntu 6.06 (Dapper).
# since ff3 requires gtk 2.10, but dapper comes with gtk 2.8, we need to 
# get gtk 2.10 and supporting libraries, and point firefox to it. 

#libglib
wget -c --tries=5 --read-timeout=20 --waitretry=10 http://mirror.mcs.anl.gov/pub/ubuntu/pool/main/g/glib2.0/libglib2.0-0_2.16.3-1_i386.deb -O /tmp/libglib2.0-0_2.16.3-1_i386.deb
sudo dpkg-deb -x /tmp/libglib2.0-0_2.16.3-1_i386.deb /opt/libglib

#libatk
wget -c --tries=5 --read-timeout=20 --waitretry=10 http://mirror.mcs.anl.gov/pub/ubuntu/pool/main/a/atk1.0/libatk1.0-0_1.22.0-0ubuntu1_i386.deb -O /tmp/libatk1.0-0_1.22.0-0ubuntu1_i386.deb
sudo dpkg-deb -x /tmp/libatk1.0-0_1.22.0-0ubuntu1_i386.deb /opt/libatk

#libpango
wget -c --tries=5 --read-timeout=20 --waitretry=10 http://mirror.mcs.anl.gov/pub/ubuntu/pool/main/p/pango1.0/libpango1.0-0_1.20.1-1_i386.deb -O /tmp/libpango1.0-0_1.20.1-1_i386.deb
sudo dpkg-deb -x /tmp/libpango1.0-0_1.20.1-1_i386.deb /opt/libpango

#libcairo
wget -c --tries=5 --read-timeout=20 --waitretry=10 http://mirror.mcs.anl.gov/pub/ubuntu/pool/main/c/cairo/libcairo2_1.6.0-0ubuntu1_i386.deb -O /tmp/libcairo2_1.6.0-0ubuntu1_i386.deb
sudo dpkg-deb -x /tmp/libcairo2_1.6.0-0ubuntu1_i386.deb /opt/libcairo

#libgtk
wget -c --tries=5 --read-timeout=20 --waitretry=10 http://mirror.mcs.anl.gov/pub/ubuntu/pool/main/g/gtk+2.0/libgtk2.0-0_2.12.9-3ubuntu2_i386.deb -O /tmp/libgtk2.0-0_2.12.9-3ubuntu2_i386.deb
sudo dpkg-deb -x /tmp/libgtk2.0-0_2.12.9-3ubuntu2_i386.deb /opt/libgtk

(
cat <<'EOF'
#!/bin/bash
export LD_LIBRARY_PATH="/opt/libglib/usr/lib:/opt/libatk/usr/lib:/opt/libpango/usr/lib:/opt/libcairo/usr/lib:/opt/libgtk/usr/lib"
/opt/firefox/firefox $*
EOF
) > /tmp/startfirefox.sh
sudo mv /tmp/startfirefox.sh /opt/firefox/
sudo chmod 755 /opt/firefox/startfirefox.sh
sudo chown root:root /opt/firefox/startfirefox.sh

# and finally, link /usr/bin/firefox to our startfirefox.sh script
sudo ln -s -f /opt/firefox/startfirefox.sh /usr/bin/firefox

```

try starting firefox by using command
```
/usr/bin/firefox
```

if any error messages are printed, please copy them all and post here. (hopefully, it will just work :) ). 

(by the way - it's certainly possible to restore back to ff2 afterwards... but it might be easier/safer to play with this using a livecd.)

would appreciate your feedback!


I tried running your script, and it went fine up until the part where it writes the startfirefox.sh file.  The script just seemed to stop after downloading gtk+2.0.  Is there a bug in it?

I tried doing the steps manually, but I get this error message when I try to run firefox:

[B][I]member@ubuntu20061223:~$ /usr/bin/firefox
/opt/firefox/firefox-bin: error while loading shared libraries: libXcomposite.so.1: cannot open shared object file: No such file or directory[/I][/B]

---

### Post by nanotube on 2009-06-02
Hi Bunny Boy
that approach was tried and it failed... so read on further in the thread for the approach that seems to have worked...

---

### Post by Schugy on 2009-07-05
I have firefox3libs4dapper.tar.bz2 overwritten on my server. It now contains
a new dbus and a new alsa-lib against openvideo crashes.
The startup script (as initially released V3.5 [might be changed in 3.5.1, e.g.]) is also included.
For later firefox automagic hotfixes check the script for the line
export LD_LIBRARY_PATH=/usr/local/ff3compatlibs/lib
if it is still there or add it again.
Performance of new FF 3.5 is great. Don't miss this update!
I'm happy that I can still use KUbuntu / Ubuntu 6.06 Dapper Drake with Firefox 3.5 !

---

### Post by nanotube on 2009-07-05
Schugy, thanks for the update. :)

---

### Post by Schugy on 2009-12-14
Thunderbird 3.0 just works the same way with ```
export LD_LIBRARY_PATH=/usr/local/ff3compatlibs/lib
``` in Kubuntu or Ubuntu Dapper Drake 6.06
Enjoy! :D

---

### Post by Schugy on 2010-01-26
I have Firefox 3.6 and Thunderbird 3.0.1 running. Don´t forget to change the Java6 plugin (use latest version) to the new plugin interface libnpjp2.so

---

### Post by priyasuri on 2010-06-28
> **drepa said:**
> Your debs worked great.  I installed them in this order glib, pixman, cairo, pango, atk, gtk+, as suggested by [http://techieblurbs.blogspot.com/2008/09/how-to-run-firefox3-on-ubuntu-edgy.html](http://techieblurbs.blogspot.com/2008/09/how-to-run-firefox3-on-ubuntu-edgy.html) .

I also needed to install libxcomposite1.

Question - is there an easy way to get Flash Player 10 working now with this little FF3 hack?

Thanks for the debs!!
Hi Drepa,
I was able to install firefox3.6.4 on Dapper successfully. I used Schugy's deb installers and installed firefox3.6.4 on /usr/local/firefox directory.   
I encountered the below error as well
[B][I]error while loading shared libraries:  libXcomposite.so.1: cannot open shared object file: No such file or  directory

[/I][/B]But I realized my instance of Dapper had libxcomposite1 library already installed. So I adapted Schugy's suggestion and edited line 51 to the following 
LD_LIBRARY_PATH=/usr/local/ff3compatlibs/lib:/usr/local/lib

The above solved my problem. 

My thanks to Nanotube for the suggestions and Schugy for the deb installers for all the libs and the firefox startup correction.

Regards,
Priya

---

### Post by SanityCzech on 2011-07-09
> **nanotube said:**
> This thread is created to be the working hub of getting ff3 to run on Ubuntu 6.06 (dapper). 

The problem is that ff3 requires gtk 2.10 or later, but Dapper only has gtk 2.8.

So far we've tried using a pre-compiled gtk2.10 library (from feisty repos) and pointing ff3 to it, but it doesn't work. (see discussion thread here: 
[http://ubuntuforums.org/showthread.php?t=832407](http://ubuntuforums.org/showthread.php?t=832407)

The next thing to do is to try compiling gtk2.10 from source on dapper, to see if that gets the desired result. (instructions here: [http://www.captain.at/howto-run-firefox-3-debian-etch.php](http://www.captain.at/howto-run-firefox-3-debian-etch.php))

Anyone with input on getting this working (or anyone with a dapper box to try this on and report results) is welcome to post to this thread.


Not to be overly ambitious, but your overthinking this. Just install 3.6 and up alongside 1.5, although, there is a fair bit of terminal use... (e.g. mkdir ~/.mozilla/plugins, lots of 'mv's, etc, also, change the repositories, if you havent already) only problem is i dont know how i got it working, and it was NOT out of the box, it took some doing, 3 years or so (without vigour)

---

### Post by Sef on 2011-07-10
Locked. Necromancing and Dapper no longer gets any updates.

---

