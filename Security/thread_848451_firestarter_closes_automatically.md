---
title: "firestarter closes automatically??"
date: 2008-07-03
forum: Security
---

### Post by AnthonyArde2 on 2008-07-03
Hi all,

I think i have a serious problem, i am using firestarter to protect against a 2dn network and that networks internet connection which i share to my other network. i have set the outbound policy to restrictive by default and only opened a few common ports, however when i scan my secondary network interface i see that some ports are being opened, and every five minutes or so my firestarter application closes by itself??? i know you dont have to have the fontend open in order for firestarter to be running but the frontend closes and i`m not sure if this is only the frontend or the actual firestarter program, is there a way for me to check all processes running om my system? i have looked at the system monitor app and that doesnt say that firestarter is open even when it is. is there a more reliable way to test this. or a better firewall? something to make my network go on lock down  except for a few ports.

Thanks

Anthony.

---

### Post by HermanAB on 2008-07-03
Firestarter is just a (Bad-ish) wizard for iptables, which is a front-end for netfilter, which is a kernel module and once loaded is always working.

So, don't worry about it.  

If you *still* want to worry about it, install the Shorewall wizard instead of Firestarter.  You can manage Shorewall with Webmin.

Cheers,

Herman

---

