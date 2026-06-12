---
title: "ultra 10 + Edgy + Atheros"
date: 2007-11-21
forum: Sun Sparc Users
---

### Post by TehCamel on 2007-11-21
I have an ultra 10, that i've got an Atheros card of some description in it.
(I added it myself after purchase, and I think it's a Dlink G-520 or similar. 108mbps anyway.

It doesn't appear in the OBP, but if I do an LSPCI i can see it.

Is there any way I could utilise this ?

---

### Post by netztier on 2007-11-21
> **TehCamel said:**
> I have an ultra 10, that i've got an Atheros card of some description in it. (I added it myself after purchase, and I think it's a Dlink G-520 or similar. 108mbps anyway.

It doesn't appear in the OBP, but if I do an LSPCI i can see it.

Is there any way I could utilise this ?

I doubt that the atheros driver that comes as part of linux-restricted-modules for i386 and x64 architectures is also available for SPARC. I believe there once was a free implementation of the atheros HAL ([http://lwn.net/Articles/209587/](http://lwn.net/Articles/209587/)), so this might be portable to SPARC. 

Of course, all the WiFi-related tools would need to bee made available for SPARC also, so yes, it might be possible to get this card running. With a lot of work, though.

best regards

Marc

---

### Post by TehCamel on 2007-11-21
the wifi tools are definitely there for sparc, iwconfig etc.

---

### Post by TehCamel on 2007-12-07
So, i'm currently building MadWifi-0.9.3.3 for my Ultra 10.

I came across an error:
> root@hecate:/home/andrew/madwifi-0.9.3.3# make
Checking requirements... ok.
Checking kernel configuration... ok.
make -C /lib/modules/2.6.17-10-sparc64/build SUBDIRS=/home/andrew/madwifi-0.9.3.3 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.17-10-sparc64'
  CC [M]  /home/andrew/madwifi-0.9.3.3/net80211/ieee80211_linux.o
cc1: warnings being treated as errors
/home/andrew/madwifi-0.9.3.3/net80211/ieee80211_linux.c: In function 'ieee80211_notify_sta_stats':
/home/andrew/madwifi-0.9.3.3/net80211/ieee80211_linux.c:256: warning: format '%llu' expects type 'long long unsigned int', but argument 7 has type 'u_int64_t'
/home/andrew/madwifi-0.9.3.3/net80211/ieee80211_linux.c:256: warning: format '%llu' expects type 'long long unsigned int', but argument 9 has type 'u_int64_t'
/home/andrew/madwifi-0.9.3.3/net80211/ieee80211_linux.c:256: warning: format '%llu' expects type 'long long unsigned int', but argument 7 has type 'u_int64_t'
/home/andrew/madwifi-0.9.3.3/net80211/ieee80211_linux.c:256: warning: format '%llu' expects type 'long long unsigned int', but argument 9 has type 'u_int64_t'
make[3]: *** [/home/andrew/madwifi-0.9.3.3/net80211/ieee80211_linux.o] Error 1
make[2]: *** [/home/andrew/madwifi-0.9.3.3/net80211] Error 2
make[1]: *** [_module_/home/andrew/madwifi-0.9.3.3] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.17-10-sparc64'
make: *** [modules] Error 2
root@hecate:/home/andrew/madwifi-0.9.3.3#

And a bit of JFGI found me some notes on madwifi about the cc1: warnings being treated as errors part, and to disable this.

So i went into the makefile.inc file and found -Werrors, and commented out the line, and it's managed to compile past where it was going before. 

Hopefully, I'll be able to provide some more feedback later on whether i've actually been able to make it work..

---

### Post by TehCamel on 2007-12-07
nope.

> 
root@hecate:/etc# modprobe ath_pci
Killed
root@hecate:/etc#



more work to do

---

