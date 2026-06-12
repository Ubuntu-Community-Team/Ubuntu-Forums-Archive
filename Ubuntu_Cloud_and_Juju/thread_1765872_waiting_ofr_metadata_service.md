---
title: "waiting ofr metadata service"
date: 2011-05-23
forum: Ubuntu Cloud and Juju
---

### Post by madao-ansisup on 2011-05-23
i can ping my running intance but i can't ssh into. when i checked the console output i found no error at all, it just seems to hang at this message :
[80G  * Setting up console font and keymap...       
[80G  * Waiting for EC2 meta-data service       
[80G 

i found that's it's have to do with me using system mode instead of managed-novlan
please can you help, i searched everywhere and didn't find anything.

---

### Post by kim0 on 2011-05-25
Hi,
UEC is really only tested with managed-novlan mode as you mentioned. You will probably hit problems if you choose otherwise. If you cannot use managed-novlan, either install plain Eucalyptus or maybe look at OpenStack which is packaged for 11.04
Enjoy :)

---

