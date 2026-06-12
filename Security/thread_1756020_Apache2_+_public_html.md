---
title: "Apache2 + public_html"
date: 2011-05-11
forum: Security
---

### Post by rainleader on 2011-05-11
I have a fresh installation of Ubuntu 10.10 Server w/ LAMP. I've created a new user account and added a public_html folder in their home directory. I installed and used Webmin to create a new VirtualHost and modified that host's DocumentRoot to /userfolder/public_html. In addition, I've properly symlinked the config file for that Vhost from sites-available to sites-enabled.

As of right now, I'm the only user on the server. If I want to add others (new user account, separate public_html directory), do I just repeat the process above? Or, are their security considerations?  What permissions do these directories need (chown useraccount, chgrp www-data, chmod 755)? Can I apply umask 022 automatically to all new files/folders?

Thanks in advance for any help.

---

### Post by Lars Noodén on 2011-05-12
You probably want to wind back to the defaults you had before and use the directive [Userdir](http://httpd.apache.org/docs/2.2/mod/mod_userdir.html#userdir) instead.  **Userdir** automatically points the web server to a folder in the user's home directory.  That's a lot simpler than creating a new virtual host for each user.

---

### Post by Lars Noodén on 2011-05-12
> **rainleader said:**
>   What permissions do these directories need (chown useraccount, chgrp www-data, chmod 755)? Can I apply umask 022 automatically to all new files/folders?


The directories should be world-readable (555 or 755 or 775).  Make sure they are *not* in the group **www-data** that's for the web server. Making a directory writable by the web server introduces some serious concerns regarding security.  Make a new group, such as **webmasters** and use that.  

You can set the sticky bit for the group (chmod g+s) if you want every file in that directory to be in the same group as the directory is.

---

### Post by rainleader on 2011-05-12
Thanks, great information.

With regard to setting the Userdir, doesn't that mean URLs will be in the form of domain.com/~user? How can I associate many domains to many different users on the same server with one IP address (I'm using named based virtual hosts now).

---

### Post by Lars Noodén on 2011-05-12
> **rainleader said:**
> Thanks, great information.

With regard to setting the Userdir, doesn't that mean URLs will be in the form of domain.com/~user? 

Yes.  You might be able to figure out something else using [AliasMatch](http://httpd.apache.org/docs/2.2/mod/mod_alias.html#aliasmatch) but that's just a guess.  

> **rainleader said:**
> How can I associate many domains to many different users on the same server with one IP address (I'm using named based virtual hosts now).

That's the way to do it.  One virtual host per domain.  Apache 2 lets you split each one into a separate file.  So it is theoretically possible to grant access to individual users for their virtual host.

---

### Post by MarkoCro on 2011-07-24
To use web server you have two ways. First using virtual hosts like I've wrote here:

[http://www.techytalk.info/ubuntu-netbeans-lamp-with-xdebug-nonroot/]("http://www.techytalk.info/ubuntu-netbeans-lamp-with-xdebug-nonroot/")

And second using userdir apache module like this:

[URL="http://www.techytalk.info/enable-userdir-apache-module-ubuntu-debian-based-linux-distributions/"]
http://www.techytalk.info/enable-userdir-apache-module-ubuntu-debian-based-linux-distributions/[/URL]

As for virtual hosts I think you would have access to user directories from every domain, not sure about this.

---

