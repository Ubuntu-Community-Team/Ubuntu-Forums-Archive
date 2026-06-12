---
title: "phpmyadmin not working after installation"
date: 2013-01-12
forum: Server Platforms
---

### Post by Extol11 on 2013-01-12
I installed phpmyadmin on my lubuntu 12.04 installation and after finishing with the installation, when I go to [http://midna/phpmyadmin](http://midna/phpmyadmin) I get a 404 page. I have everything necessary installed, apache, mysql and every dependency that synaptic asked for. Do I still need to configure something else before using the service?

---

### Post by chrisguk on 2013-01-12
Are you using this in a desktop environment or server?

If your are using the Gnome (GUI) environment it is very easy to install phpmyadmin in this order.  Essentially it works out of the box:

Follow this great guide:

[http://www.unixmen.com/install-lamp-with-1-command-in-ubuntu-1010-maverick-meerkat/]("http://www.unixmen.com/install-lamp-with-1-command-in-ubuntu-1010-maverick-meerkat/")

---

### Post by Extol11 on 2013-01-12
I'm using Lubuntu which brings the LXDE gui. I'll check that out and see if it talks more about the setup process. I installed this following the official documentation and there's nothing else it says I should do.

---

### Post by cariboo on 2013-01-13
There should be a file in /etc/phpmyadmin called apache.conf, you need to copy this file to /etc/apache2/sites-enabled, then run a2ensite:

```
sudo cp /etc/phpmyadmin/apache.conf /etc/apaches2/sites-enabled/phpmyadmin.conf
```

Then enable the site:

```
sudo a2ensite /etc/apache2/sites-enabled/phpmyadmin.conf
```

After restarting apache:

```
sudo service apache2 restart
```

you should be able to access phpmyadmin.

---

