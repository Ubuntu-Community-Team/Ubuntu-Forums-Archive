---
title: "Apache 2 &amp; Webmin:10000"
date: 2008-06-18
forum: Server Platforms
---

### Post by Frobe82 on 2008-06-18
I would like to know where the configuration files for apache is.
Ive usually never had to use anything else then httpd.conf. In Ubuntu this is an empty file. I find similar conf files under /etc/apache2/sites-availible/default
But Where is the reference for localhost:10000
I cant find it anywhere. When i enter my adress on port 10000. What is telling the browser where to go?

Kind Regards
Fred

---

### Post by windependence on 2008-06-18
I'm not sure I understand. Port 10000 is usually where WebMin is located. Are you trying to configure the server with WebMin?

The configuration files are in /etc/apache2/apache2.conf

-Tim

---

### Post by Frobe82 on 2008-06-18
Hi!

I wanna know what configuration file is telling Apache that localhost:10000 is webmin.
Where is the reference that tells apache that localhost:10000 should send me to the webmin directory.

---

### Post by windependence on 2008-06-18
AFAIK WebMin does not use Apache, it has it's own webserver which I think is miniserv.pl.

The port it uses is set in the Webmin Configuration module.

[http://www.linuxjunkies.org/adminstration%20Howto/webminguide/x313.htm](http://www.linuxjunkies.org/adminstration%20Howto/webminguide/x313.htm)

-Tim

---

### Post by Frobe82 on 2008-06-18
I cant say that I fully understand why Webmin would run its own independent webserver outside of apache. I however thank you for pointing me in the direction of the miniserv configuration files.

If anyone care to explain how webmin can function as a webserver in this state it would be greatly appreciated.

Kind regards
Fred

---

