---
title: "LDAP auth for apache and viewvc"
date: 2016-11-07
forum: Server Platforms
---

### Post by houch80 on 2016-11-07
[COLOR=#111111][FONT=Ubuntu]I am newer to Ubuntu and Apache. I know I have a config that works, if I put the directory /var/www/html and go to that directory I get prompted for creds and they work. What I can not figure out is how to make this work for the viewvc site. I have tried numerous directories including root of www and /usr/lib/cgi-bin I can not seem to get it to prompt for username when I go to /cgi-bin/viewvc.cgi[/FONT][/COLOR]

---

### Post by SeijiSensei on 2016-11-07
Are you using an .htaccess file?  Those don't work with the default Apache configuration.  It's best to put the authorization directives inside the <Directory> stanza for appropriate directory in the configuration file for the virtual host.  If you must use an .htaccess file, you'll need to add "[AllowOverride All]("http://httpd.apache.org/docs/2.4/mod/core.html#allowoverride")" to the default configuration.

Read this: [https://httpd.apache.org/docs/2.4/howto/auth.html](https://httpd.apache.org/docs/2.4/howto/auth.html)

---

### Post by houch80 on 2016-11-08
Thank you for your reply, I am using the 000-default.config file. I have it set right if I use different directory/location, I just cant figure out the path or how to make it work with the viewvnc site.

---

### Post by SeijiSensei on 2016-11-08
You might try adding an [Alias]("https://httpd.apache.org/docs/current/mod/mod_alias.html") directive to the 000-default file:
```

Alias /viewvnc /path/to/the/viewvnc/directory
<Directory "/path/to/the/viewvnc/directory">
    relevant options that would otherwise be in .htaccess
</Directory>

```
Then if you navigate to [http://server_name/viewvnc](http://server_name/viewvnc) you should end up in the correct directory.

---

