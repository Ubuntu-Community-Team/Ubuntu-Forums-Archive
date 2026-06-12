---
title: "php5-ldap wont download"
date: 2012-08-15
forum: Server Platforms
---

### Post by Psycholiquid71 on 2012-08-15
I am trying to setup a webpage to use LDAP in my internal LAN. I have tried installing the php5-ldap module but when I run:

sudo apt-get install php5-ldap

I get the following:

srvadmin@dcvgasv40013:/etc/apache2$ sudo apt-get install php5-ldap
Reading package lists... Done
Building dependency tree
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  php5-ldap: Depends: phpapi-20090626
E: Broken packages

Any help would be appreciated.

---

### Post by sandyd on 2012-08-15
> **Psycholiquid71 said:**
> I am trying to setup a webpage to use LDAP in my internal LAN. I have tried installing the php5-ldap module but when I run:

sudo apt-get install php5-ldap

I get the following:

srvadmin@dcvgasv40013:/etc/apache2$ sudo apt-get install php5-ldap
Reading package lists... Done
Building dependency tree
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  php5-ldap: Depends: phpapi-20090626
E: Broken packages

Any help would be appreciated.
What are you using for php?
mod_php? php-fpm? php-cgi?

---

### Post by Psycholiquid71 on 2012-08-15
PHP Version 5.3.2-1ubuntu4.14

Loaded Modules:

core mod_log_config mod_logio prefork http_core mod_so mod_alias mod_auth_basic mod_authn_file mod_authz_default mod_authz_groupfile mod_authz_host mod_authz_user mod_autoindex mod_cgi mod_deflate mod_dir mod_env mod_mime mod_negotiation mod_php5 mod_reqtimeout mod_setenvif mod_status 


php-fpm?

Unsure of what you are asking for there.

php-cgi?

Unsure of what you are asking for there.

---

### Post by Psycholiquid71 on 2012-08-15
> **sandyd said:**
> What are you using for php?
mod_php? php-fpm? php-cgi?
Was a bad PPA that was causing it. I did the following to remove:


/etc/apt/source.list

sudo nano /etc/apt/source.list

"Removed the offending PPS in my case was": 

deb [http://php53.dotdeb.org](http://php53.dotdeb.org) stable all


Saved, Exited.

Reran:

sudo apt-get update

sudo apt-get install php5-ldap


Worked like a champ.

---

