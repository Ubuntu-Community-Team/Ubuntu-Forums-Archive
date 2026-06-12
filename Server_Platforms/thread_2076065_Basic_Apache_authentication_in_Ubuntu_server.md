---
title: "Basic Apache authentication in Ubuntu server"
date: 2012-10-25
forum: Server Platforms
---

### Post by lads on 2012-10-25
Dear all,

I'm trying to set up basic authentication in Apache on Ubuntu Server 12.10. I'm following the [Apache manual]("http://httpd.apache.org/docs/2.2/howto/auth.html"), but there are several things in Ubuntu that differ from that document. One of the options would be to edit the *httpd.conf* file, but in my installation it is void. Hence I followed the route of creating a *.htaccess* file in the web directory.

I created a password file with *htpasswd* and a group file in */etc/apache2/passwd*. Again this location differs from the manual, is it a proper place to have these assets?

Then I created an *.htaccess* file with the following contents:

```
AuthType Basic
AuthName "Test application"
# (Following line optional)
AuthBasicProvider file
AuthUserFile /etc/apache2/passwd/passwords
AuthGroupFile /usr/local/apache/passwd/groups
Require group MyGroup

```

After this I restarted Apache but no authentication is required to access the web page.

Are the required modules ([mod_authn_core]("http://httpd.apache.org/docs/2.2/mod/mod_authn_core.html") and [mod_authz_core]("http://httpd.apache.org/docs/2.2/mod/mod_authz_core.html")) installed with the Apache package? How can I verify that they are installed? As I write this the Apache manual pages for these modules seem to unavailable.

Thank you reading.

---

### Post by Lars Noodén on 2012-10-25
Rather than putting those options in a .htaccess file, put them in  the configuration for the appropriate directory inside the Apache virtual host configuration.  There should be <Directory /var/www/foo> or something like that.  .htaccess is only for when you yourself don't actually have write access to the web server's configuration files.

---

### Post by lads on 2012-10-29
Thanks Lars, once I found out this would have to be set up in *apache2.conf* it was an easy task.

---

### Post by Lars Noodén on 2012-10-29
apache2.conf is more the glue to hold together the different configuration files, so it is seldom that any changes go there.  Since basic authentication applies to a specific virtual host, it is best to put it in that vhost's configuration file.  That keeps like things together in one file.  If you haven't changed anything there should be the default vhost configuration file in  /etc/apache2/sites-available/default.  That's where to put the basic authentication configurations for the main vhost.

Apache2 configuration is a little more complicated than 1.3.x but is intended to scale up better to  handling many sites on the same server.

---

