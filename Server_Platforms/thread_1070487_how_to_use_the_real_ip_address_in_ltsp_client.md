---
title: "how to use the real ip address in ltsp client?"
date: 2009-02-15
forum: Server Platforms
---

### Post by zyencomputer on 2009-02-15
hi group

i tried to use ltsp environment on my internet cafe. No problems in installation, it works like a charm. All clients succesfully boot via PXE, but then comes the problem.

For billing software i use [BiOS]("http://bios.googlecode.com"). It written in php, so i can watch remotely how many user in my internet cafe etc. The problem is BiOS use static IP address for client to be registered in billing server.  

I read some articles about to [use static IP with DHCP]("https://help.ubuntu.com/community/UbuntuLTSP/StaticIPsWithDHCP"), but when i tried to ifconfig on client, it all written that ip address are same with IP on billing.

Any suggestion ? or does any reference about billing software that use name/login, not IPs?

---

### Post by haddog on 2009-02-15
Zyen. Are you using two NIC cards?

---

### Post by djk_srs on 2009-04-12
have you try ccl ? It's suit for LTSP based :p

---

### Post by taktiktux on 2009-08-27
dear all,

I hope this thread could be continued.
i use ltsp5 in jaunty with 1 nic.
I though dhcp server will give a ltsp client an unique ip-address. But after i check by ifconfig, it shown ip-add of server.
Is there any idea to make ip address on client be unique and not same with server? 

thanks
ubuntu-makassar.org

---

