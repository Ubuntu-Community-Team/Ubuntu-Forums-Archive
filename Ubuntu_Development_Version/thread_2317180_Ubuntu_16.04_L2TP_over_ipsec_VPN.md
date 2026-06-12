---
title: "Ubuntu 16.04 L2TP over ipsec VPN"
date: 2016-03-14
forum: Ubuntu Development Version
---

### Post by stefano-incontri on 2016-03-14
Hello all,
there's no more an option to connect to an L2TP over ipsec VPN, how to do it in Ubuntu 16.04?

Thanks

---

### Post by QDR06VV9 on 2016-03-14
Have you installed the L2TP Ipsec VPN Manager yet?

---

### Post by stefano-incontri on 2016-03-15
Can't find such package in the 16.04 repositories.
I see it was available until 14.04 together with OpenSwan (now 16.04 ships StrongSwan), but the custom repository i have found fails the installation.
So i'm trying to build the L2TP ipsec VPN manager from sources, as specified here: [http://wiki.l2tpipsecvpn.tuxfamily.org/wiki/index.php?title=Main_Page#From_Source](http://wiki.l2tpipsecvpn.tuxfamily.org/wiki/index.php?title=Main_Page#From_Source)

It builds and install successfully but when attempting a connection i get the error:
```

[COLOR=#000000]mar 15 17:03:15.942 /usr/sbin/ipsec: unknown IPsec command `setup' (`ipsec --help' for list)[/COLOR]
[COLOR=#ff0000]mar 15 17:03:15.942 [ERROR    2]   Command 'ipsec setup start' failed and exited with given error code[/COLOR]

```

I'm right now investigating on it and will be back reporting.

---

### Post by QDR06VV9 on 2016-03-15
I did not know they discontinued the L2TP Ipsec VPN Manager.
Is this the PPA that failed on installing StrongSwan:[ ppa:strongswan/strongswan-daily]("https://launchpad.net/~strongswan/+archive/ubuntu/strongswan-daily")
If it is might be worth filing a bug report

---

