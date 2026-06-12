---
title: "lsb-core &amp; Google Earth?"
date: 2015-12-11
forum: Ubuntu Development Version
---

### Post by Smask on 2015-12-11
Use latest version of GE (7.1.7.2600) as these hackery steps are no longer needed.


Lsb-core has been dropped from the repository for Xenial. Found that when trying to install Google Earth, which depends on it. That means more deb-file hackery than usual (Qt4 libraries provided by Google needs to be replaced). 

Deb hackery and Google Earth 64-bit installation:
Install [http://packages.ubuntu.com/wily/lsb-core](http://packages.ubuntu.com/wily/lsb-core) using "dpkg --force-depends -i" method, then add [Google Earth (Qt4 fixed, 64-bit only)]("https://drive.google.com/file/d/0Bx0YZ3Xi3rgTLXotTnRndVVkOTA/view") the same way. 
Now edit /var/lib/dpkg/status so that lsb-core doesn't depend on anything. And while editing the status file, add libfreeimage3 to the depends line at google-earth-stable. Alchemist251 (a [Google Maps and Earth product forums]("https://productforums.google.com/forum/#!topicsearchin/maps/category$3A%28google-earth$20AND$20linux%29") user) forgot to add the libfreeimage3 to the depends section when he built the modified GE package.
This way you get the needed lsb-core without installing all that 32-bit cruft.
The deb file install script in the Google Earth deb package adds the Google deb file  repository. Since it adds this with an old certificate (2007 SHA1), Ubuntu will complain next time you reloads/refreshes the repositories.  Just remove it from the repositories.




If you run Yakkety you might need some extra packages to run Google Earth, as gstreamer 0.10 has been dropped from Yakkety:

[URL="http://packages.ubuntu.com/xenial/libgstreamer0.10-0"]http://packages.ubuntu.com/xenial/libgstreamer0.10-0
[/URL] and [http://packages.ubuntu.com/xenial/libgstreamer-plugins-base0.10-0](http://packages.ubuntu.com/xenial/libgstreamer-plugins-base0.10-0)

Install those and add libgstreamer0.10-0 and libgstreamer-plugins-base0.10-0 to the depends line at "Package: google-earth-stable" in /var/lib/dpkg/status.

---

### Post by ronacc on 2015-12-11
I just bumped into the same thing . I wonder what brought that on . it was there earlier , I installed google earth when I first installed Xerus  and it was there at that time . it has also disappeared from my /var/cache/apt/archives even though I have it set to keep all packages even if they are no longer available .

---

### Post by Smask on 2015-12-11
Looks like they dropped it upstream...

---

### Post by ronacc on 2015-12-11
just wonderful

---

### Post by ronacc on 2015-12-11
lsb-core (4.1) is available in debian stable ( jesse )   link    [https://packages.debian.org/jessie/lsb-core](https://packages.debian.org/jessie/lsb-core)    you will also need lsb-security from there other depends are in the xenial repos . I installed lsb-secruity first then lsb-core then google-earth and all was well .

---

### Post by valereguerin on 2015-12-16
it works ! just this in the terminal :

```
freeman@Sniper-one:~$ google-earth
[1216/212053:ERROR:net_util.cc(2195)] Not implemented reached in bool net::HaveOnlyLoopbackAddresses()
[1216/212053:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[1216/212053:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[1216/212053:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[1216/212053:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[1216/212053:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[1216/212053:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[1216/212053:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[1216/212053:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[1216/212053:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[1216/212053:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[1216/212053:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[1216/212053:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[1216/212053:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[1216/212053:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[1216/212053:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[1216/212053:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[1216/212054:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[1216/212054:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[1216/212054:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[1216/212054:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[1216/212054:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[1216/212054:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[1216/212054:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[1216/212054:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[1216/212054:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[1216/212054:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[1216/212054:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[1216/212054:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[1216/212054:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[1216/212054:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[1216/212054:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[1216/212054:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[1216/212054:WARNING:backend_impl.cc(1875)] Destroying invalid entry.
[1216/212054:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[1216/212054:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[1216/212054:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[1216/212054:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[1216/212054:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[1216/212054:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[1216/212054:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[1216/212054:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[1216/212054:WARNING:backend_impl.cc(1875)] Destroying invalid entry.
[1216/212054:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[1216/212054:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[1216/212054:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[1216/212054:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[1216/212054:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[1216/212054:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[1216/212054:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[1216/212054:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[1216/202054:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[1216/202054:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[1216/202054:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[1216/202054:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[1216/202054:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[1216/202054:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[1216/202054:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[1216/202054:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[1216/202054:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[1216/202054:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[1216/202054:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[1216/202054:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[1216/202054:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[1216/202054:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[1216/202054:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[1216/202054:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[1216/202055:WARNING:backend_impl.cc(1875)] Destroying invalid entry.
[1216/202055:WARNING:backend_impl.cc(1875)] Destroying invalid entry.
[1216/202055:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[1216/202055:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[1216/202055:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[1216/202055:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[1216/202055:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[1216/202055:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[1216/202055:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[1216/202055:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[1216/202055:WARNING:backend_impl.cc(1875)] Destroying invalid entry.
[1216/202055:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[1216/202055:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[1216/202055:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[1216/202055:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[1216/202055:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[1216/202055:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[1216/202055:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[1216/202055:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[1216/202055:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[1216/202055:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[1216/202055:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[1216/202055:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[1216/202055:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[1216/202055:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[1216/202055:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[1216/202055:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[1216/202055:WARNING:backend_impl.cc(1875)] Destroying invalid entry.
[1216/202055:WARNING:backend_impl.cc(1875)] Destroying invalid entry.
[1216/202055:WARNING:backend_impl.cc(1875)] Destroying invalid entry.
[1216/202055:WARNING:backend_impl.cc(1875)] Destroying invalid entry.
[1216/202055:WARNING:backend_impl.cc(1875)] Destroying invalid entry.
[1216/202055:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[1216/202055:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[1216/202055:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[1216/202055:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[1216/202055:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[1216/202055:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[1216/202055:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[1216/202055:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[1216/202056:WARNING:backend_impl.cc(1875)] Destroying invalid entry.
[1216/202056:WARNING:backend_impl.cc(1875)] Destroying invalid entry.
[1216/202056:WARNING:backend_impl.cc(1875)] Destroying invalid entry.
```

i install 64 bits version without error

---

### Post by Smask on 2016-05-11
Updated my first post regarding to Google Earth on Xenial/Yakkety

Mods: Can you change the title to "lsb-core and Google Earth"?

---

### Post by DaBzzz on 2016-06-04
Doesn't really work (anymore) for a current Xenial installation. The fixed GE package starts up, the 3D earth shows for a split second, then crashes, saying totally useful things like

```
Major Version 7
Minor Version 1
Build Number 0004
Build Date Mar 30 2015
Build Time 22:42:31
OS Type 3
OS Major Version 4
OS Minor Version 4
OS Build Version 0
OS Patch Version 0
Crash Signal 11
Crash Time 1465073968
Up Time 2,88531

Stacktrace from glibc:
./libgoogleearth_free.so(+0x23924c)[0x7f4a9f54224c]
./libgoogleearth_free.so(+0x2394ad)[0x7f4a9f5424ad]
/lib/x86_64-linux-gnu/libpthread.so.0(+0x113d0)[0x7f4aa02173d0]

```

in the crash log. Anyone knows what to do? Install more of the old lsb package dependencies? Any workaround or newer "fixed" deb package?

btw:

> **Smask said:**
> Now edit /usr/lib/dpkg/status so that lsb-core doesn't depend on anything. And while editing the status file, add libfreeimage3 to the depends line at google-earth-stable.

Must be **/var**/lib/dpkg/status

---

### Post by Smask on 2016-06-05
I dunno if Alchemist251 have rebuilt the package. If he done so, that would have generated a new URL for the files, right?

---

### Post by Smask on 2016-09-13
I upgraded GE to the latest version 7.1.7.2600 on both Xenial and Yakkety and the only thing I had to do was adding "export LC_NUMERIC=en_US.UTF-8" to /opt/google/earth/free/googleearth as I'm an non-English user.

I do know that libgstreamer0.10 isn't needed any more (unless you use DraftSight), and libpng12 is no longer needed. Panoramio photos works, so no more use of AmirPli's Qt libraries (and the need of libfreeimage3). Some Debian users have search problems (thanks to openssl 1.0.0),  but search works here at my end.

---

