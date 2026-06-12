---
title: "2 websites behind the same router"
date: 2009-11-02
forum: Server Platforms
---

### Post by any.linux12 on 2009-11-02
Hey guys!

How can I have 2 websites behind the same router if my router only allows me to configure one http service related to the NAT? Because I need the website and it would be nice to have the email web access.

Thanks

---

### Post by mbeach on 2009-11-02
What you are looking for is offered by Apache and is called Virtual Hosts.

One apache service will respond on the same IP to various server name requests.

Official documentation:
[http://httpd.apache.org/docs/2.2/vhosts/](http://httpd.apache.org/docs/2.2/vhosts/)

Search these forums for 'virtual hosts'
outside links would also yield something like:
[http://www.debuntu.org/2006/02/22/7-virtual-hosting-using-apache-2](http://www.debuntu.org/2006/02/22/7-virtual-hosting-using-apache-2)

If you prefer a gui, I believe rapache ([https://launchpad.net/rapache](https://launchpad.net/rapache)) can handle virtual host setup.

Also, some good documentation at:
/usr/share/doc/apache2.2-common/

---

### Post by any.linux12 on 2009-11-03
is there any other way?

---

### Post by volkswagner on 2009-11-03
You could add the second site inside a directory of your fist site.

If you are using the default location /var/www for your current site add a directory such as /var/www/mail.  

If you install your webmail site inside /var/www/mail, you will be able to navigate to [http://www.example.com/mail](http://www.example.com/mail).


EDIT:  I must say creating virtual hosts is the preferred way, and is an excellent tool to know.  It becomes easier to manage if you have multiple sites, and is the only way I know to use multiple domains.

---

