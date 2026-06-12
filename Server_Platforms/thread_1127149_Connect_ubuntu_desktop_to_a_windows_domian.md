---
title: "Connect ubuntu desktop to a windows domian"
date: 2009-04-16
forum: Server Platforms
---

### Post by acid_burns on 2009-04-16
I would like to use Ubuntu at work for administrating my network ect we are using windows server2003 so how do connect it to my domian?

---

### Post by glauco.b on 2009-04-16
It depends on what you want to do.

If you want to just authenticate using Active Directory, you can use the likewise tool [here]("http://www.likewise.com/products/likewise_open/") and also available in the ubuntu apt repo

If you need to join ubuntu as a member server to the Active Directory, here is a very well made how to
[http://ubuntuforums.org/showthread.php?t=280305]("http://ubuntuforums.org/showthread.php?t=280305")

If you want ubuntu to ac as a domain controller, it's a little more complicated: [http://www.howtoforge.com/openldap-samba-domain-controller-ubuntu7.10]("http://www.howtoforge.com/openldap-samba-domain-controller-ubuntu7.10") (it's for the 7.10 but works for almost any ubuntu version

You can event wait for samba4 to be released (I tried the Alpha7 and works very well as domain controller).

---

