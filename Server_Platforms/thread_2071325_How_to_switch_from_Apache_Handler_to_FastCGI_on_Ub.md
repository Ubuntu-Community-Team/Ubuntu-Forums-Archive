---
title: "How to switch from Apache Handler to FastCGI on Ubuntu Zend Server?"
date: 2012-10-15
forum: Server Platforms
---

### Post by amoooc on 2012-10-15
Hello
Installed fresh Ubuntu Server 12.04 and Zend Server Community Edition 5.6.0. Unfortunately I can't deploy my CMS Joomla 2.5.7 based websites due to file permissions error(CHOD 755)during Joomla installation/Joomla extensions installation (files unwriteable) so I'm assuming that's because cgi-fcgi is not shipped with Zend Server for Linux (only for Windows where it's working OK). 

Ref. [http://files.zend.com/help/previous-version/Zend-Server-4-Community-Edition/zend_server_ce_php_5.3_extensions.htm]("http://files.zend.com/help/previous-version/Zend-Server-4-Community-Edition/zend_server_ce_php_5.3_extensions.htm")) 

It's possible to install Joomla and extensions only with CHMOD 777 but of course I can't do that on live web server. Could you help me please resolve my problem? Maybe there is other solution than switching Zend Server Apache 2.0 Handler to CGI/FastCGI? 

PHP info on Ubuntu Server
Server API:	Apache 2.0 Handler
PHP Version 5.3.14
Zend Server Community Edition 5.6.0
Server Software	Apache/2.2.22 (Ubuntu)
Zend Framework 1.12.

Let me know if you need additional informations. Thank you for any help
Cheers

---

### Post by FrischInBigD on 2013-02-25
We have same issue with Joomla3 jumpboxes deploying with Apache2 handler but need to be using fast cgi/cgi per RocketTheme.com for their newest templates to be used that utilize LESS compile.

RocketTheme states it is a permissions problem with several directories and once Apache "owns" them joomla cannot write new changes to them, which is why they are saying to use fast cgi, instead.

Could we not do:

sudo chown -R admin:www-data /var/data/joomla3/xxx/xxx/xxx
and then...
sudo chmod -R 775 /var/data/joomla3/xxx/xxx/xxx

to change directory permissions?  Would this not remedy not being able to write to those previously unwriteable folders?

Thanks in advance.
):P

---

