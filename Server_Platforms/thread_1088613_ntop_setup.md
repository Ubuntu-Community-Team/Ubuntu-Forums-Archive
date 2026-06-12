---
title: "ntop setup"
date: 2009-03-06
forum: Server Platforms
---

### Post by genset on 2009-03-06
hey guys

im trying to install ntop but i get this error about the gdbm package
please help me

found in /usr/local
checking for pcap_next_ex in -lpcap... yes
checking for gdbm...
checking gdbm.h usability... no
checking gdbm.h presence... no
checking for gdbm.h... no
checking for gdbm_open in -lgdbm... yes

*******************************************************************
*
* ERROR: gdbm header or library routines are missing
*           (yes means it was found, no means it was not found)
*
*              gdbm.h...no
*              gdbm_open() in -lgdbm...yes
*
*>>> No way to proceed.
*
*???     1. Install libgdbm
*???    and Rerun ./configure
*???  or 2. Use the --with-gdbm-xxxxx= options
*
*******************************************************************

configure: error: Unable to continue... aborting ./configure


what do i need to do?

---

### Post by terazen on 2009-03-06
I'm not completely sure what the error means except to make sure that you have all of your dependancies met.  My ntop server has these packages installed:

> libgdbm-dev                                     install
libgdbm3                                        install
python-gdbm                                     install


Possibly you are missing one of these?  Also the command I used was this:
```
dpkg --get-selections | grep gdbm
```

---

