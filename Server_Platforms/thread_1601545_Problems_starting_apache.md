---
title: "Problems starting apache"
date: 2010-10-20
forum: Server Platforms
---

### Post by greengunboat on 2010-10-20
I am trying to install Zend Server, and that went well. Apache and all the other items were installed.

But when I go to start Apache, I get this error:

> 
root@laptop:~# /etc/init.d/apache2 restart
* Restarting web server apache2 Syntax error on line 6 of /etc/apache2/sites-enabled/zendserver_gui.conf:
Invalid command 'php_admin_flag', perhaps misspelled or defined by a module not included in the server configuration
[fail]


And on line 6: php_admin_flag tidy.clean_output off
The rest of the file is below:

> 
# Warning: Modifying this file will break the Zend Server Administration Interface
Listen 127.0.0.1:10083
NameVirtualHost 127.0.0.1:10083
# do not allow override of this value for the UI's Vhost as it should always be off when generating non-html content such as dynamic images
<VirtualHost 127.0.0.1:10083>
        php_admin_flag tidy.clean_output off
        php_admin_flag session.auto_start off
        Alias /ZendServer "/usr/local/zend/gui/UserServer"
	DocumentRoot /usr/local/zend/gui/UserServer
        ErrorLog /usr/local/zend/var/log/gui_vhost_error.log
        CustomLog /usr/local/zend/var/log/gui_vhost_access.log combined
	<Directory /usr/local/zend/gui/UserServer>
		Options Indexes FollowSymLinks MultiViews
		AllowOverride None
		Order deny,allow
		deny from all
                allow from 127.0.0.1/8
	</Directory>

	ServerSignature On

</VirtualHost>



Can anyone tell me why apache refuses to start?

---

### Post by SeijiSensei on 2010-10-20
The [page for php_admin_flag]("http://php.net/manual/en/configuration.changes.php") at php.net says it cannot be used in .htaccess files.  Perhaps that extends to <VirtualHost> containers as well?  You'll notice that the example given there applies globally, not within a particular virtual host.

I usually change settings with ini_set() in the script itself.

According to [this](http://www.php.net/manual/en/ini.list.php), both session.auto_start and tidy.clean_output default to off.  Try commenting those lines out and see if everything works as expected.

---

