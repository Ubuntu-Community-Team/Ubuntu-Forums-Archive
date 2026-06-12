---
title: "Apache2 LTS 8.04 LoadModule Section."
date: 2008-10-03
forum: Server Platforms
---

### Post by nitecon on 2008-10-03
Hey folks, this might be a really dumb question....

I'm doing virtual hosts with ProxyPass / ProxyPassReverse,  that is all fine and dandy, the only problem is I can't find the LoadModule section in any of the conf files contained in /etc/apache2/

I assume doing a sudo apt-get install libapache2-mod-proxy-html is enough since I can't grep for anything else but that module.

Where to add the LoadModule though?

Thanks in advance :)

Nite.

---

### Post by windependence on 2008-10-04
Enable the module:
```

a2enmod proxy
```

Then, restart Apache:

/etc/init.d/apache2 restart


-Tim

---

