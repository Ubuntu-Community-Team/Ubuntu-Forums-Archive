---
title: "Postfix install freezes"
date: 2007-09-11
forum: Server Platforms
---

### Post by fowie on 2007-09-11
Using Ubuntu 6.06 on an HP Netserver LH4r.  I did an original install with postfix and dovecot, then changed my mind and removed dovecot to install courier. Still couldn't get the installation to work properly so I apt-get --purge remove'd all of the postfix and courier files.  Now when I try to install postfix again the apt-get setup freezes.  I get the two screens about postfix configuration where I specify "Internet Site" and the mail name, then it just sits there forever using 50% of my processor time for dpkg-preconfigure and 20% for postfix.config.  The only warning I get is: 
> Warning: Newline present in parameters passed to debconf.                                                                    
This will probably cause strange things to happen!


I can ctr-c out of it, but the install never finishes.

--UPDATE--
I've found that the installation will **not** freeze _if_ I do not select "Internet Site" in the postfix config.  Does anyone know why this would happen?

---

