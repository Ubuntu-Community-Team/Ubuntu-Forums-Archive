---
title: "Problem with Subdomains"
date: 2008-04-13
forum: Server Platforms
---

### Post by yodomino6 on 2008-04-13
Using Webmin:

From what I understand, it's really easy to create a subdomain. Correct me if I'm wrong, but all you need to do is create a new virtual host with the subdomain address in the Servername and the directory of it in the Document Root?

I did all that, then I went to the address and all it came back with was Server Not Found. So it couldn't even see my server, let alone the website.
Thanks for help!

---

### Post by zooper on 2008-04-13
I suppose you are takling about Apache?
Have you restarted apache after you added the virtual host?
/etc/init.d/apache restart

This is how a "host" could look like in the config file:

<VirtualHost *:80>
    DocumentRoot /home/www/webmail
    ServerName webmail.linuxburken.se
    ErrorLog /home/logs/webmail_error.log
    CustomLog /home/logs/webmail_access.log common
</VirtualHost>

---

