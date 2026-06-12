---
title: "signatures were invalid"
date: 2010-10-29
forum: Ubuntuzilla
---

### Post by the.phantom on 2010-10-29
been using ubuntuzilla for a long time and since day one on this 10.04lts build

well just checked for updates and got this message?

> W: GPG error: [http://downloads.sourceforge.net](http://downloads.sourceforge.net) all Release: The following signatures were invalid: BADSIG CCC158AFC1289A29 Daniel Folkinshteyn (Ubuntuzilla signing key) <nanotube@users.sourceforge.net>


just checked a 10.10 and no trouble?
and a 10.4 backup system and NO error
any suggestions ( maybe re install the file)

just tried a different server ( main) and same error on this computer

just re installed the key with your instructions and got this 

> dennis@dennis-desktop:~$ sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com C1289A29
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --recv-keys --keyserver keyserver.ubuntu.com C1289A29
gpg: requesting key C1289A29 from hkp server keyserver.ubuntu.com
gpg: key C1289A29: "Daniel Folkinshteyn (Ubuntuzilla signing key) <nanotube@users.sourceforge.net>" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1
dennis@dennis-desktop:~$ 



still error

tried a specific usa server and it worked ( i think)
it had only been 1 hr so did not see the full check of net activity, just a quick burst

but no error this time
maybe server trouble?

---

### Post by nanotube on 2010-10-30
Hi
It happens sometimes after a fresh package upload, as the signatures have to propagate through the sourceforge.net file release system network.
Just do 'sudo apt-get update' again in a few minutes, and the error should disappear.

---

### Post by the.phantom on 2010-10-31
yep i did that a day later and all is well in "senior citizen land" again

just confused me as only one computer

thanks

---

