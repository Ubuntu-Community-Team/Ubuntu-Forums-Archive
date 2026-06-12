---
title: "crypttab does not appear to run on boot"
date: 2013-12-07
forum: Security
---

### Post by helloworld1215 on 2013-12-07
The cryptdisks service is set to run levels 0 and 6. 

However, I don't know if this is a correct setting because perhaps crypttab is made to run in some other fashion. 

In either case, this is a default 12.04.3 install. I have added:

cryptswap1 /dev/sda8 /dev/urandom swap,cipher=aes-cbc-essiv:sha256

but at boot it is specifying that the /dev/mapper/cryptswap1 disk is not available and to either wait, resolve manually or skip.

---

