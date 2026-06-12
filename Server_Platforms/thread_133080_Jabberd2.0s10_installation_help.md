---
title: "Jabberd2.0s10 installation help"
date: 2006-02-19
forum: Server Platforms
---

### Post by dodolz on 2006-02-19
I have just installed Ubuntu 5.10 as server.
Then I'm trying to install jabberd2.0s10 on my machine. 
But when i run configure like :
**./configure --enable-mysql --enable-debug --enable-ssl -enable-idn**
thereis an error said "cannot find openssl >= 0.9.6b".
When I check the version of openssl on my machine, its higher than 0.9.6b
Why it can't find openssl on my machine ?


Thanks,
sory if my english is bad :mrgreen:

---

### Post by Burke on 2006-02-20
maybe if you just install it from the apt repository? 

sudo apt-get install jabberd2

you may need this: [http://easylinux.info/wiki/Ubuntu#How_to_add_extra_repositories](http://easylinux.info/wiki/Ubuntu#How_to_add_extra_repositories)

---

