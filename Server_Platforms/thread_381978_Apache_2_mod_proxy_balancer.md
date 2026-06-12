---
title: "Apache 2 mod_proxy_balancer"
date: 2007-03-11
forum: Server Platforms
---

### Post by rundeks on 2007-03-11
Hi All,

I am trying to configure Apache 2 with the mod_proxy_balancer module. I installed Apache 2 via the System Package Manager GUI. It included many other mods, but I don't see the mod_proxy_balancer. How do I get and download this module. It is a normal Apache 2 module. Am I at the point I need to switch from the Apache Package and install the Apache source?

Thanks,
Kevin

---

### Post by Nikron on 2007-03-11
If you  have apache2, check /etc/apache2/mods-enabled/ to see if it 's has

mod_proxy_balancer.load

If it isn't there, there should be a module called that in /etc/apache2/mods-available which you can move to enabled.  There is a command that automatically does it for you, but I can't think of it off the top of my head.

---

### Post by rundeks on 2007-03-11
You hit the problem right no the head. mod_proxy_balancer does not exist in mod-available nor does the mod_proxy_balancer.so file exist in /usr/lib/apache2/modules. According to everything I have read it is a normal module of Apache 2 and should be there.

Thanks,
Kevin

---

### Post by Nikron on 2007-03-11
Yeah, you'll have to get a newer version of apache2..  My version is 2.0.55, and I assume you downloaded apache of either the edgy repos or the dapper ones, so it should be the same or lower since I'm on Edgy.  The module page for mod_proxy_balancer says you need 2.1.  Have fun compiling =P

---

### Post by rundeks on 2007-03-11
Thanks for the information. I will download the src and build it my self. By complaining I assume you mean the people behind the package repository. This sucks I liked how the apache install was setup.

Thanks,
Kevin

---

### Post by rundeks on 2007-03-12
It works! In case someone has the same problems as I did here is whats up.

As stated above the Apache available via package manager is 2.0. Apache is upto 2.2.4 as of right now. I had to uninstall apache completely (also Subversion too).

Then I followed the instructions on this page:
[http://davidwinter.me.uk/articles/2006/10/17/building-apache-22-from-source-for-ubuntu-dapper/]("http://davidwinter.me.uk/articles/2006/10/17/building-apache-22-from-source-for-ubuntu-dapper/")
NOTE I uses apache 2.2.4 instead of 2.2.3. Also I added -enable-ssl to the configure line.

Then to get Subversion back (plus be on the latest version) I followed the instructions on this page: (same site, same guy)
[http://davidwinter.me.uk/articles/2006/10/17/subversion-140-from-source-over-apache-22-on-ubuntu-dapper/]("http://davidwinter.me.uk/articles/2006/10/17/subversion-140-from-source-over-apache-22-on-ubuntu-dapper/")
NOTE again I found out the most recent version of subversion and used that.

Thanks,
Kevin

---

