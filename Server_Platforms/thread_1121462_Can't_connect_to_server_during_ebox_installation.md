---
title: "Can't connect to server during ebox installation"
date: 2009-04-10
forum: Server Platforms
---

### Post by pinko on 2009-04-10
I was installing ebox via ssh and suddenly I lost connection to the server on any port. And I can't even ping it.

I followed a guide for ebox here [https://help.ubuntu.com/community/eBox]("https://help.ubuntu.com/community/eBox")

And this is the last thing I saw:
```
Setting up libcarp-clan-perl (5.9-2) ...
Setting up libbit-vector-perl (6.4-6) ...
Setting up libdate-calc-perl (5.4-5) ...
Setting up ebox-ca (0.11.99-0ubuntu2) ...

Setting up ebox-objects (0.11.99-0ubuntu1) ...

Setting up jnettop (0.12.0-4) ...

Setting up libnet-arp-perl (1.0.1-1) ...
Setting up librrd2 (1.2.19-1ubuntu1) ...

Setting up librrds-perl (1.2.19-1ubuntu1) ...
Setting up rrdtool (1.2.19-1ubuntu1) ...
Setting up vlan (1.9-3) ...
Setting up ebox-network (0.11.99-0ubuntu1) ...
```

I was wondering if anyone has come across this problem

---

### Post by foolano on 2009-04-10
Hi,

It seems that there was a bug on that version and the network configuration importing.

I guess you are using hardy or intrepid and you are installing directly from the Ubuntu repositories.  

0.11.99 is a pretty old version. We have released a few other versions since then. You can install them using our repos. Take a look at: [http://ebox-platform.com/community/installation-guide/](http://ebox-platform.com/community/installation-guide/)

Thanks

---

### Post by pinko on 2009-04-10
you wouldn't happen to know how I could connect to it do you?

---

