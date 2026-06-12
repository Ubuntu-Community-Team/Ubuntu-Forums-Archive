---
title: "Bind9 deletes is /var/run/named"
date: 2007-04-02
forum: Server Platforms
---

### Post by prodsacnetworking on 2007-04-02
hi,

I have 3 ubuntu 6.06 servers running Bind9 (packages).

When I need to reboot the server, the bind9 gives error.
He seems to delete is /var/run/named folder where he put his named.pid.. 

So I need to create and chmod the folder.. 


any ideas to get rid of this?

thanks

---

### Post by shufla on 2007-04-24
Hello,

Which version of bind9 do you have installed? Mine is 9.3.2-2ubuntu1.2 and there is no folder /var/run/named, but /var/run/bind.

Bye,
Shufla

---

