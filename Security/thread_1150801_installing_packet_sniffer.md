---
title: "installing packet sniffer"
date: 2009-05-06
forum: Security
---

### Post by javedd.ali on 2009-05-06
i am having a problem installing packet sniffer can anyone help plzzz
this is the response on running make install

Making install in src
make[1]: Entering directory `/home/javed/aps-0.18/src'
Making install in include
make[2]: Entering directory `/home/javed/aps-0.18/src/include'
make[3]: Entering directory `/home/javed/aps-0.18/src/include'
make[3]: Nothing to be done for `install-exec-am'.
make[3]: Nothing to be done for `install-data-am'.
make[3]: Leaving directory `/home/javed/aps-0.18/src/include'
make[2]: Leaving directory `/home/javed/aps-0.18/src/include'
make[2]: Entering directory `/home/javed/aps-0.18/src'
make[3]: Entering directory `/home/javed/aps-0.18/src'
/bin/sh ../mkinstalldirs /usr/local/bin
  /usr/bin/install -c  aps /usr/local/bin/aps
  /usr/bin/install -c  xaps /usr/local/bin/xaps
make[3]: Nothing to be done for `install-data-am'.
make[3]: Leaving directory `/home/javed/aps-0.18/src'
make[2]: Leaving directory `/home/javed/aps-0.18/src'
make[1]: Leaving directory `/home/javed/aps-0.18/src'
make[1]: Entering directory `/home/javed/aps-0.18'
make[2]: Entering directory `/home/javed/aps-0.18'
make[2]: Nothing to be done for `install-exec-am'.
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/home/javed/aps-0.18'
make[1]: Leaving directory `/home/javed/aps-0.18'
mkdir -p /usr/local/include/aps
if [ -f src/include/portlist.aps ]; then\
    cp -f src/include/portlist.aps /usr/local/include/aps;fi
/bin/sh: Syntax error: "fi" unexpected (expecting "then")
make: *** [install] Error 2

---

### Post by cdenley on 2009-05-06
Why not use tcpdump or wireshark?

---

### Post by The Cog on 2009-05-06
tcpdump is (I think) installed by default. Much easier to understand is wireshark, which you can install with this command:
**sudo aptitude install wireshark**

As a general rule, you should use the repositories (System->Administration->Synaptic Package Manager) as your first place to look, and use internet searches for software as your last resort.

---

