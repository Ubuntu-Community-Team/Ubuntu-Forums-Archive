---
title: "Password protect Apache dir"
date: 2014-07-10
forum: Server Platforms
---

### Post by damien10 on 2014-07-10
I've looked around but what I've tried so far hasn't worked. I want to password protect a subdir of a web site using a <directory> directive instead of .htaccess. How do I do that? I either get a message that Apache doesn't know what to do with the credentials or that Apache is incorrectly configured.

---

### Post by Lars Noodén on 2014-07-10
Which directions have you tried following?

There are two parts for Basic authentication.  

1) One is the configuration of the Apache2 configuration file.  Use <Directory> or <Location> for that.  

For example, if I have a sub-directory called 'test'

```

  <Directory /var/www/html/test>
    AuthType Basic
    AuthName "Authentication Required"
    AuthUserFile "/var/www/htpasswd/test"
    Require valid-user

    Order allow,deny
    Allow from all
  </Directory>

```

Then I also need a matching htpasswd file, the one designated by **AuthUserFile**.  After changes to the configuration, Apache2 needs to reload.

2) The second part is to make the matching password file.  In the the example above it would be /var/www/htpasswd/test

```

sudo htpasswd -c /var/www/htpasswd/test damien10

```

That creates a user 'damien10' and prompts for the password.  Remember that unless you are exclusively using HTTPS for those directories, the username and password will be transmitted in the clear every time a page or an object on a page is loaded.  

Be sure to read the options for [htpasswd](http://manpages.ubuntu.com/manpages/trusty/en/man1/htpasswd.1.html)

In debugging it is helpful to have the error log open and track it live.

```

tail -f /var/log/apache2/error.log

```

---

### Post by damien10 on 2014-07-10
Thanks, Lars! I've followed steps similar to those. When I've followed those other steps, and when I've followed your advice, I get the following:

**Unauthorized**

 This server could not verify that you are authorized to access the document requested.  Either you supplied the wrong credentials (e.g., bad password), or your browser doesn't understand how to supply the credentials required.

The credentials I supplied are correct. I don't think it's the browser's problem because this happens regardless of which browser I'm using. What am I missing?

Just to make sure we're talking about the same file, I'm editing /etc/apache2/apache2.conf.

---

### Post by SeijiSensei on 2014-07-10
You shouldn't be editing apache2.conf.  You should either modify the file /etc/apache2/sites-available/000-default.conf which defines the default virtual host, or create a new virtual host file in that directory and "enable" it with the a2ensite command.

I suggest you read the section on Apache in the [Ubuntu Server Guide]("https://help.ubuntu.com/14.04/serverguide/httpd.html") to understand the layout of files in the Debian/Ubuntu implementation of Apache.

If you modify the default file, I'd first create a backup copy with an extension other than .conf.  Next open 000-default.conf and revise it to appear like this:
```

<VirtualHost *:80>
        #ServerName www.example.com

        ServerAdmin webmaster@localhost
        DocumentRoot /var/www/html

        ErrorLog ${APACHE_LOG_DIR}/error.log
        CustomLog ${APACHE_LOG_DIR}/access.log combined

   <Directory /var/www/html/test>
    AuthType Basic
    AuthName "Authentication Required"
    AuthUserFile "/var/www/htpasswd/test"
    Require valid-user

    Order allow,deny
    Allow from all
  </Directory>

</VirtualHost>

```
using Lars's code from above.  Then restart Apache with "sudo service apache2 restart".

---

### Post by damien10 on 2014-07-10
Thanks for the reply. I already have a site set up. I need to password protect a subdir of that site. So I edited the vhost in sites-enabled like so:

```

<VirtualHost *:80>
    ServerAdmin (email)
    ServerName (domain)
    ServerAlias www.(domain)
    DocumentRoot /var/www/(location)
    ErrorLog ${APACHE_LOG_DIR}/error.log
    CustomLog ${APACHE_LOG_DIR}/access.log combined
<Directory /var/www/(location)/(subdir)>
        AuthType Basic
        AuthName "Authentication Required"
        AuthUserFile "/etc/apache2/(auth_file)"
        Require valid-user
        Order allow,deny
        Allow from all
</Directory>
</VirtualHost>

```

I ran htpasswd -c /etc/apache2/(auth_file) (username). After restarting Apache, I still get the Unauthorized error I mentioned above. (Also, I took the directive out of apache2.conf before I restarted Apache.)

---

### Post by SeijiSensei on 2014-07-10
What do you see in /var/log/apache2/error.log?  Is the password file readable by the www-data user that owns the Apache2 process?

---

### Post by damien10 on 2014-07-10
I just did a chown www-data on the auth file, but I still get the same error. There's nothing about this in /var/log/apache2/error.log. I even did tail -f /var/log/apache2/error.log while accessing the subdir and nothing about it appeared.

---

