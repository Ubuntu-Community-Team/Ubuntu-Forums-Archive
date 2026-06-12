---
title: "running Perl script in web host."
date: 2011-03-23
forum: Server Platforms
---

### Post by srijith_bhandary on 2011-03-23
Hi guys,
I am trying to run a perl script in a web host and I am really new to this. 

I dont know how to set-up a web host and how to run perl in a browser. 

I have installed LAMP in ubuntu (desktop edition) but I dont see a cgi-bin folder in there. 

Here is the link  which I wanted to do exactly [http://www.giantflyingsaucer.com/blog/?p=575](http://www.giantflyingsaucer.com/blog/?p=575) 
 
 Currently I have a ubuntu desktop with LAMP installed. I dont have a cgi-bin configured. 


Now how can I proceed ?

---

### Post by falko on 2011-03-23
Assuming that your document root is /var/www/web1/web/, create a cgi-bin folder above your document root (/var/www/web1/cgi-bin/) and make it owned by the user and group of your web site. Don't forget to make it executable:
chmod 755 /var/www/web1/cgi-bin/

Place your script in /var/www/web1/cgi-bin/, make it owned by the same user and group and make it executable as well.

To your Apache vhost configuration, add:
```
ScriptAlias  /cgi-bin/ /var/www/web1/cgi-bin/
AddHandler cgi-script .cgi
AddHandler cgi-script .pl
```
Restart Apache.
Afterwards, you can access the script like this: http://www.example.com/cgi-bin/name_of_script.cgi

---

### Post by Lars Noodén on 2011-03-24
Once you are up and running, you can get better performaance using [mod_perl](http://perl.apache.org/outstanding/).

---

### Post by srijith_bhandary on 2011-03-28
ok, I have done what you said.

But I am getting these errors when restarting apache


 * Restarting web server apache2                                                                                                                                                   Syntax error on line 3 of /etc/apache2/sites-enabled/example.com/example.com/example.cgi:
Invalid command 'use', perhaps misspelled or defined by a module not included in the server configuration


If comment this "use" statement" and restart apache I get the same above error, but "use" is replaced by "print" and the line number is changed.

---

