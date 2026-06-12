---
title: "samba domain controller almost working!"
date: 2010-11-09
forum: Server Platforms
---

### Post by HBE66 on 2010-11-09
im setting up a windows domain controller on ubuntu server 10.10

i got as faar as joining the first client to the the domain
but after authentication it fails

im assuming that my user is in the wrong group and therefore has no priviledges
ive set windows group "Domain Admins" for unix group "admin"
and the SID is correct

can someone tell me if this group is correct, or if i will need another one?
and how/where can i check the priviledges and which user belongs to which group?

thank you!

---

### Post by s1nch4n on 2010-11-10
> **HBE66 said:**
> im setting up a windows domain controller on ubuntu server 10.10

i got as faar as joining the first client to the the domain
but after authentication it fails

im assuming that my user is in the wrong group and therefore has no priviledges
ive set windows group "Domain Admins" for unix group "admin"
and the SID is correct

can someone tell me if this group is correct, or if i will need another one?
and how/where can i check the priviledges and which user belongs to which group?

thank you!did you mean you can't joining client with PDC?

use root account to joining client with samba PDC

---

### Post by HBE66 on 2010-11-10
yep, i tried using the primary user i used to configure everything
i dont really have the root pw, using the same pw as for the primary user wont work

the return code i get is 534 if thats any help...

in the meantime im even ready to pay someone to get my pdc working! =)
need it desperately...

---

### Post by HBE66 on 2010-11-10
i dont want to have to install windows again :-?

---

### Post by HBE66 on 2010-11-10
ok, in half an hour its too late. ill finish work an get to setup windows again :cry:

---

### Post by luvshines on 2010-11-10
> **HBE66 said:**
> ok, in half an hour its too late. ill finish work an get to setup windows again :cry:

If you don't mind interruption, what exactly is the error/issue ?

---

