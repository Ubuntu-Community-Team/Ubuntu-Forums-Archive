---
title: "we need help in setting up LXC"
date: 2011-03-07
forum: Virtualisation
---

### Post by grisswold on 2011-03-07
Has anybody followed this link in setting up the lxc in ubuntu 10.10?

[http://blog.bodhizazen.net/linux/lxc-configure-ubuntu-lucid-containers/](http://blog.bodhizazen.net/linux/lxc-configure-ubuntu-lucid-containers/)

The problem that we have right now is that when we do > lxc-console -n ubuntu, we get an error saying console denied.

Following the original instructions didn't get us to nowhere. So weve made some little changes and these are the changes that we have done:
-we set the > lxc.tty=1 in the config.ubuntu file.
-we did not mount a shared directory
-> lxc-create -f /lxc/conf.ubuntu -n ubuntu instead of using that we used lxc-create -f /lxc/config.ubuntu -n ubuntu

we get no error upon creating and starting the lxc but upon doin the lxc-console it gives us console denied error. We also tried using ssh but nothing happens. 

So could anybody site what weve done wrong or help us?
After

---

### Post by stlsaint on 2011-03-10
That is a fairly common error so i suggest joining the mailing list for accurate answers. The lxc devs also are on there and are good with answering issues: 
Lxc-users mailing list:
[email]Lxc-users@lists.sourceforge.net[/email]
[https://lists.sourceforge.net/lists/listinfo/lxc-users](https://lists.sourceforge.net/lists/listinfo/lxc-users)

---

