---
title: "Apache2, Virtual Hosts, internet access vs intranet access"
date: 2005-11-01
forum: Server Platforms
---

### Post by Metz on 2005-11-01
I'm currently running a name based virtual host setup at home. I have three seperate domains all pointing to my (dynamic and managed by ddclient) ip address, with each site in it's own document root. 

This all works great. :)

Now,  I've recently install phpMyAdmin on the same server. It is placed in a directory of it's own off the wwwroot. Which has created a problem. If someone external used my IP address to reach me, no virtual host exists to catch the call.....and it resolves to the myPHPAdmin page !!!! 

:mad: :mad: :mad: 

Can't have that !!! I only want the myphpadmin site accessible from within my intranet....not from outside  !!!

Any ideas folks ?

---

### Post by souki on 2005-11-01
my guess is that phpmyadmin's configuration conflict with the default server (take a look at the error logs)

you should restrict its access to local network or put a password.
unless the vhost is set to run on the local interface, everybody can see it (you just need to know the ServerAlias)

---

### Post by LordHunter317 on 2005-11-01
Here's what you should do, the correct option depends on your exact configuration:[list][*]Move the phpmyadmin configuration (it's probably a <Directory> entry or an Alias) to a different VirtualHost, one that's accessible only by the intranet[*]Add a dummy page for your default VirtualHost.  Your default vhost is whatever host is listed first in the Apache configuration.  Normally, this would be in the file 000-default.  Then, configure the phpmyadmin directory to have access to it denied by any IP address except those on your Intranet[/list]

---

### Post by Metz on 2005-11-02
[QUOTE=LordHunter317]Then, configure the phpmyadmin directory to have access to it denied by any IP address except those on your Intranet[/list][/QUOTE]


Bingo. Thanks for that. That's the bit I was missing....the allow/deny stuff needed 'Allow' set to 192.168.1 ....I beleive that should work :)

Thanks again. :)

---

