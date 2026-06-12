---
title: "Setup GoDaddy SSL Cert"
date: 2011-05-12
forum: Server Platforms
---

### Post by rainleader on 2011-05-12
I use Webmin to manage an Ubuntu 10.10 server and have a VirtualHost setup (and working) for [http://mydomain.com]("http://mydomain.com/").  If I want to install an SSL certificate from a CA like GoDaddy (already  generated a CSR), how do I set it up in Webmin? Would I just create  another Vhost with the same document root but have it listen on *:443?
  Are there any special directives I'd need to add to the configuration or would Webmin set that up for me (for SSL)?
  I used the guide here: [https://help.ubuntu.com/10.10/serverguide/C/certificates-and-security.html](https://help.ubuntu.com/10.10/serverguide/C/certificates-and-security.html)

---

