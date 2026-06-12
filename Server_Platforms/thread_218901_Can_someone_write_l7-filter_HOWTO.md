---
title: "Can someone write l7-filter HOWTO?"
date: 2006-07-19
forum: Server Platforms
---

### Post by dixon on 2006-07-19
I can't install l7-filter, because I can't find some of the features in menuconfig

    * EXPERIMENTAL (Code maturity level options &#8594; Prompt for development and/or incomplete code/drivers) FOUND

    * Netfilter (Device Drivers &#8594; Networking support &#8594; Networking Options &#8594; Network packet filtering) FOUND in Networking --> Networking options --> Network packet filtering (replaces ipchains) -->

    * Connection tracking (Network packet filtering &#8594; IP: Netfilter Configuration &#8594; Connection tracking) FOUND
    * "Connection tracking flow accounting" and "IP tables support" (on the same screen) DIDN'T FIND
    * And finally, "Layer 7 match support" DIDN'T FIND :((
    * Optional: Lots of other Netfilter options, notably "FTP support" and other matches. If you don't know what you're doing, go ahead and enable all of them.

---

### Post by dixon on 2006-07-26
OK, so I've compiled the patched kernel and iptables.

But when I try e.g.
```

sudo iptables -I INPUT -m layer7 --l7proto http -j DROP

```
it ends with error

iptables: Unknown error 4294967295 :(((((

---

### Post by Mithrilhall on 2006-12-20
dixon...did you ever get this worked out?

---

### Post by dixon on 2007-03-20
Yep, I've got it working - it turned up that whole my problem was damaged memory(RAM)...

---

