---
title: "PHPMyAdmin setup script password"
date: 2009-04-15
forum: Server Platforms
---

### Post by papexus on 2009-04-15
Hello,

I have installed PhpMyadmin on Ubuntu 8.10. When I try to run the setup scripts located in phpmyadmin/scripts, I get a login window asking for a user name and password. I tried all my root and user name/passwords including the Mysql root/password but none would work.
What am I missing ?

thank you

Julia

---

### Post by tturrisi on 2009-04-16
Mysql root/password is what you need.  Try resetting the mysql root pw and try again.

[http://www.ducea.com/2008/01/31/mysql-tips-howto-change-the-mysql-root-password/](http://www.ducea.com/2008/01/31/mysql-tips-howto-change-the-mysql-root-password/)

---

### Post by steve_c on 2009-06-01
I'm running into this same problem.

I've installed phpMyAdmin via the repositories on an Ubuntu 8.04.2 LTS Server platform with the LAMP stack installed via the repositories.

I can log into phpMyAdmin as root with the MySQL root password just fine. However I'm wanting to configure it to manage multiple servers. Ideally I'd like to use the setup script in phpmyadmin/scripts/setup.php to make any changes/modifications, or at least to know that I *can* use the setup script.

Unfortunately when I open a browser to [http://server/phpmyadmin/scripts/setup.php](http://server/phpmyadmin/scripts/setup.php) it a login box pops up asking me for a username and password again, even if I already authenticated to [http://server/phpmyadmin](http://server/phpmyadmin) . If I try to log in with the root MySQL credentials it gives me a 401: Authorization Required error screen.

I tried resetting the MySQL root password as the user above suggested but that hasn't fixed it.

Thanks for any help.

---

### Post by steve_c on 2009-06-02
I've discovered the problem is with this section of the /etc/phpmyadmin/apache.conf file:
```

        # Authorize for setup
        <Files setup.php>
            # For Apache 1.3 and 2.0
            <IfModule mod_auth.c>
                AuthType Basic
                AuthName "phpMyAdmin Setup"
                AuthUserFile /etc/phpmyadmin/htpasswd.setup
            </IfModule>
            # For Apache 2.2
            <IfModule mod_authn_file.c>
                AuthType Basic
                AuthName "phpMyAdmin Setup"
                AuthUserFile /etc/phpmyadmin/htpasswd.setup
            </IfModule>
            Require valid-user
        </Files>
 
```

Commenting out "Require valid-user" allows you to access the script. Obviously this is less than ideal.

How can I my Apache to make sure that the necessary module (mod_authn_file.c) is installed and being used? I see "authn_file.load" in my mods-enabled. Is that the same thing?

Thanks for any help.

---

### Post by steve_c on 2009-06-03
Figured this out finally, thanks to this site:
[http://http://wiki.jumpbox.com/doc/runtime/faq/install_phpmyadmin]("http://http://wiki.jumpbox.com/doc/runtime/faq/install_phpmyadmin")

What I needed to do was this:
```
sudo htpasswd /etc/phpmyadmin/htpasswd.setup admin
```

For the life of me I could not find that anywhere in the documentation or in any forums. Hopefully this will help someone else.

---

### Post by dpilgrim on 2010-07-04
Thank you, steve_c! I was on Day Two of trying to figure out phpmyadmin setup on a proto-typing box on my home network, and your tip did the trick. I don't know why this isn't better documented.

---

### Post by dootzky on 2011-12-31
OMG! thanks man! :) I couldn't find this as well, it was driving me NUTS, and I'm all like "omg, I'm a senior web developer, who can't even install phpmyadmin to login from config.. wtfff" :D

thanks bro, really! :)

---

