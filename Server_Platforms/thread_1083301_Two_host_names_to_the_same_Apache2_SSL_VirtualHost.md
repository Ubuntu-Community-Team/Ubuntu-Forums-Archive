---
title: "Two host names to the same Apache2 SSL VirtualHost"
date: 2009-02-28
forum: Server Platforms
---

### Post by MikeBenza on 2009-02-28
Hello,

I've taken over a machine that has a number of aliases.  Two such aliases are [www.xyz.someuni.edu]("http://www.xyz.someuni.edu") and xyz.someuni.edu.  There is also a Subversion repository on the machine that about 30-40 people use.  Some people use [https://www.xyz.someuni.edu/svn/](https://www.xyz.someuni.edu/svn/) and some use [https://xyz.someuni.edu/svn/](https://xyz.someuni.edu/svn/).  Both are equivalent.  Both use the same expired, self-signed certificate.  I got shiny, new, CA signed certificates for both [www.xyz.someuni.edu]("http://www.xyz.someuni.edu") and xyz.someuni.edu.

I want to set up the machine so that [https://www.xyz.someuni.edu/svn/](https://www.xyz.someuni.edu/svn/) and [https://xyz.someuni.edu/svn/](https://xyz.someuni.edu/svn/) both point to the same to the same repository, without any certificate warnings for the clients.

Apache2 doesn't allow virtual host based SSL because the Host header (which selects virtual hosts) isn't read until after the connection has been made, and apache2 needs to know which certificate to use while setting up the connection.

So, how do I make both virtual hosts point to the same place?  I found something about [mod_gnutls]("http://www.g-loaded.eu/2007/08/10/ssl-enabled-name-based-apache-virtual-hosts-with-mod_gnutls/"), but I can't find it in Ubuntu, and I'd prefer to stay with easy-to-upgrade packages.

I can do DNS tricks if I have to, but I don't know if there are any tricks that might work.  I *can* get a second IP for the second host name and forward it to the correct one, but that's really a last resort.

- Mike Benza

---

### Post by martien on 2009-03-01
> **MikeBenza said:**
> Hello,

I've taken over a machine that has a number of aliases.  Two such aliases are [www.xyz.someuni.edu]("http://www.xyz.someuni.edu") and xyz.someuni.edu.  There is also a Subversion repository on the machine that about 30-40 people use.  Some people use [https://www.xyz.someuni.edu/svn/](https://www.xyz.someuni.edu/svn/) and some use [https://xyz.someuni.edu/svn/](https://xyz.someuni.edu/svn/).  Both are equivalent.  Both use the same expired, self-signed certificate.  I got shiny, new, CA signed certificates for both [www.xyz.someuni.edu]("http://www.xyz.someuni.edu") and xyz.someuni.edu.

I want to set up the machine so that [https://www.xyz.someuni.edu/svn/](https://www.xyz.someuni.edu/svn/) and [https://xyz.someuni.edu/svn/](https://xyz.someuni.edu/svn/) both point to the same to the same repository, without any certificate warnings for the clients.

Apache2 doesn't allow virtual host based SSL because the Host header (which selects virtual hosts) isn't read until after the connection has been made, and apache2 needs to know which certificate to use while setting up the connection.

So, how do I make both virtual hosts point to the same place?  I found something about [mod_gnutls]("http://www.g-loaded.eu/2007/08/10/ssl-enabled-name-based-apache-virtual-hosts-with-mod_gnutls/"), but I can't find it in Ubuntu, and I'd prefer to stay with easy-to-upgrade packages.

I can do DNS tricks if I have to, but I don't know if there are any tricks that might work.  I *can* get a second IP for the second host name and forward it to the correct one, but that's really a last resort.

- Mike Benza
In the xyz.someuni.edu's virtualhost (this with the ssl) simply add ServerAlias [www.xyz.someuni.edu](www.xyz.someuni.edu). It will look something like this:
...
ServerName xyz.someuni.edu
ServerAlias [www.xyz.someuni.edu](www.xyz.someuni.edu)
...

---

### Post by MikeBenza on 2009-03-03
But if I do that, won't I get warnings that the certificate name doesn't match the host name?

---

