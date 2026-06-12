---
title: "Lucid 10.04, broadcom tg3 drivers and bonding"
date: 2013-11-29
forum: Server Platforms
---

### Post by kevpatts2 on 2013-11-29
Okay, I need to install 10.04 server on a brand new Dell Poweredge server.

10.04.4 doesn't recognise the NICs, so on Dells advise I've installed  withour networking, copied on the build-essential debs, installed, built  the Broadcom tg3 driver ([http://www.broadcom.com/support/license.php?file=570x/linux-3.133d.zip](http://www.broadcom.com/support/license.php?file=570x/linux-3.133d.zip)) and got it running fine on a single NIC.

The problem is, when I try to bond it the eth0 and eth1 interfaces won't  join the bond, even though the docs say that the tg3 drivers support  bonding.

I'm using the same /etc/network/interfaces as I am on another identical  (older hardware so didn't have this problem) and the other box has  always worked without problem.

any ideas (module loading order / something I haven't thought of)?

Thanks in advance,
Kev

---

### Post by Bucky Ball on 2013-11-29
Why don't you try the next current LTS server and that is 12.04. Five years support from April last year.

---

### Post by kevpatts2 on 2013-11-29
Can't due to issues in OpenSSL 1.0 and above. Must temporarily stay on OpenSSL 0.9.8(insert random letter here) until workarounds are found.

I could build old openssl and mod_ssl for the newer dist but trieing to avoid this as I've done this before and it's a hassle, and you don't get security updates. 10.04 still getting security updates until April next year.

---

### Post by Bucky Ball on 2013-11-29
That's what I mean, 12.04 LTS is supported until April 2017. Might be worth building it. ;)

I guess upgrading the current installed LTS to 12.04 LTS (you can leapfrog from LTS to LTS) would break the openssl setup ...

---

### Post by kevpatts2 on 2013-11-29
Hey man, looking to get back to the core issue. Can't upgrade to 12.04 for the time being for business reasons.

---

### Post by kevpatts2 on 2013-12-02
Any other iseas about this one?

---

