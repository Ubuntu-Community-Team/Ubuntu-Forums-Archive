---
title: "A Problem with my LAMP setup"
date: 2009-10-22
forum: Server Platforms
---

### Post by j7%&lt;RmUg on 2009-10-22
Ok, so i have 9.04 with apache2, php5, mysql and phpmyadmin installed, if i point my browser to localhost on my machine(the LAMP setup is on my main computer not a dedicated server.) i get my index.html file in /var/www. Iv also managed to get php working fine also.

Now my issue is with phpmyadmin, i have it installed and it works fine, but when i include /etc/phpmyadmin/apache.conf in /etc/apache2/apache2.conf to get phpmyadmin to show up, i can no longer get any changes to show up at localhost if i modify /var/www/index.html. If i remove that include and restart apache then it all goes back to normal, except then i dont have phpmyadmin.

There is not really information about this particular problem on the net(yes i googled for 4 hours thismorning.) iv tried everything i can think of and everything that iv found on the net.

It is not vital that i get this working but i do want to start mucking around with mysql so it would be awesome if this annoying problem could be fixed. I have not modified anything from its defaults since installing LAMP.

Thanks in advance.

---

### Post by OpenGuard on 2009-10-22
What does error log have to say about this issue ?

---

### Post by j7%&lt;RmUg on 2009-10-22
/var/log/apache2/error.log says:

File does not exist: /var/www/phpmyadmin

it appears to have logged that error every time i try to access phpmyadmin when i have the include for phpmyadmin commented out.

That log says nothing else about phpmyadmin.

---

### Post by j7%&lt;RmUg on 2009-10-23
BUMP, still havent resolved this issue.

---

### Post by masux594 on 2009-10-23
At home i've had a problem like that.. Now i'm out, but, try to create a new folder in /var/www named phpmyadmin.. and see if it works.. I actually don't remember what i've done for get it work, but, maybe this evening i'll check at home..

Sysc, A

P.s. Obvoisly, if doesen't work erase the folder that i say before ..

---

### Post by OpenGuard on 2009-10-23
Please attach your [COLOR=DimGray]/etc/phpmyadmin/apache.conf[/COLOR] file.

---

### Post by j7%&lt;RmUg on 2009-10-23
Thanks, adding a directory does nothing, as i said phpmyadmin works, but i then cant edit my site so i have to disable it.

---

### Post by masux594 on 2009-10-23
Ok, i've understand that i don't understand your problem.. What do y mean whan u say "cant edit my site"?

Sysc, A

---

### Post by j7%&lt;RmUg on 2009-10-23
Heres my /etc/phpmyadmin/apache.conf file:

```
# phpMyAdmin default Apache configuration



<Directory /usr/share/phpmyadmin>
	Options Indexes FollowSymLinks
	DirectoryIndex index.php

	<IfModule mod_php5.c>
		AddType application/x-httpd-php .php

		php_flag magic_quotes_gpc Off
		php_flag track_vars On
		php_flag register_globals Off
		php_value include_path .
	</IfModule>

</Directory>

# Authorize for setup
<Directory /usr/share/phpmyadmin/setup>
    <IfModule mod_authn_file.c>
    AuthType Basic
    AuthName "phpMyAdmin Setup"
    AuthUserFile /etc/phpmyadmin/htpasswd.setup
    </IfModule>
    Require valid-user
</Directory>

# Disallow web access to directories that don't need it
<Directory /usr/share/phpmyadmin/libraries>
    Order Deny,Allow
    Deny from All
</Directory>
<Directory /usr/share/phpmyadmin/setup/lib>
    Order Deny,Allow
    Deny from All
</Directory>

```

By not being able to edit my site i mean:

If i have phpmyadmin enabled and i edit my index.html file in /var/www then that works and i save it. if i then go to localhost (which is where my website is located on my network) it doesnt show any of the changes iv just made.

---

### Post by masux594 on 2009-10-23
Correct me if i'm wrong.. Then.. u have phpmyadmin "enabled" on your web server.. If u modify your index.html, and then open file, everything is fine, but, if u go in "localhost/" all the changes y've done doesen't shows up.. But, if u disable phpmyadmin [ and restart apache] and do the same steps, even in "localhost/" u can see your changes..

Am i right?

Sysc, A

---

### Post by j7%&lt;RmUg on 2009-10-23
Thats exactly it.

and by disable phpmyadmin i mean commenting out the Include from /etc/apache2/apache2.conf

---

### Post by masux594 on 2009-10-23
Oki, i'll think about it..

how did u installed all the lamp server? Have u used some command in the terminal?? if yes, post it [if y found it]..

Sysc, A

---

### Post by j7%&lt;RmUg on 2009-10-23
I used the usual repo packages:

apache2
php5
libapache2-mod-php5
mysql
phpmyadmin

Plus i would have install all required dependencies for those packages.

---

### Post by j7%&lt;RmUg on 2009-10-28
Also i just found out that if i just type in my servers name or ip address it comes up with the old index.html, but if i specifically type <servername/ipaddressofserver>/index.html then it displays the edited version.

I still have no idea what is going on with this so if anyone has any ideas id still like to hear them, otherwise ill wait for karmic and use the newer apache version.

---

### Post by masux594 on 2009-10-28
... ... I've thought about it and there's no reason that the web server doesen't display your edited version of "index.html" .. I have a LAMP server like your, no settings configured, no changed configuration and all works from the beginning! So, what i can tell you is, backup your data, uninstall all the LAMP the pakages and then install LAMP server form the taskList.. What do you think about it?

Sysc, A

P.s. - TaskSel, not TaskList.. oops..

---

### Post by j7%&lt;RmUg on 2009-10-28
Im not sure what you mean by install from the tasklist...

---

### Post by masux594 on 2009-10-28
well, a simple command..```
sudo tasksel install lamp-server
```

.. The steps are:
_BackUp files-databases [if you create something that u want to keep]
_ uninstall all the packages that u tells before
_ run that command

Sysc, A..

---

### Post by j7%&lt;RmUg on 2009-10-28
Ah yes, ok iv tried three times now, it seems it leaves all my config files behind, tried removing them and the problem is still there.

Thanks for helping out but i think ill just wait for karmic, ill be downloading it tomorrow anyway.

---

### Post by masux594 on 2009-10-28
Sure, I'm going to upgrade too, but i think that the problem won't solved with it.. Hope..

Sysc, A

---

