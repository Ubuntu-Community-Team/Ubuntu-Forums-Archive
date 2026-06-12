---
title: "Cannot install Firestarter"
date: 2006-09-25
forum: Server Platforms
---

### Post by marianom on 2006-09-25
Hi,
pretty sure this is an easy one:
following the instructions @ [http://ubuntuguide.org/wiki/Dapper#How_to_install_Firewall_.28Firestarter.29](http://ubuntuguide.org/wiki/Dapper#How_to_install_Firewall_.28Firestarter.29)
I uncommented all repositories (and even add a few new ones) 
but when I do:

$ sudo apt-get install firestarter
it keeps telling me that the package could not been found.

Can you please guide me in order to find it?
Regards

---

### Post by Technophobia on 2006-09-26
try: sudo apt-get update

Might work

---

### Post by marianom on 2006-09-26
Thanks a lot. It worked.

---

