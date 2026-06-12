---
title: "How install krb5(Kerberos?) headers and libs?"
date: 2017-10-04
forum: Ubuntu Application Development
---

### Post by borucki-andrzej on 2017-10-04
I am trying compile HBase native client, is yet OK but is problem with krb5.h from folder krb5 or mit-krb5.
Also, compiler wants #include <et/com_err.h>. So far , I have copied folder mit-krb5 from Docker environment and commented <et/com_err.h>.
But I need library (what is her name? libkrb5.a?) which has krb5_init_context,krb5_cc_default or krb5_cc_get_principal.
sudo apt-get install krb5-kdc krb5-admin-server - not helps
sudo apt-get install krb5-user libcomerr2 - nothing install because above command already it install
ANSWER: sudo apt-get install libkrb5-dev

---

