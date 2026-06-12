---
title: "Help with Nagios"
date: 2010-08-04
forum: Server Platforms
---

### Post by cvandal on 2010-08-04
Hello,

I installed Nagios on my Ubuntu 10.04 server using apt-get and when I accessed the web console, everything was OK. I made some changes to apache (creating some new virtual sites) and since then Nagios gives me a warning message for HTTP with the message, HTTP WARNING: HTTP/1.1 404 Not Found.

The sites that I created are working perfectly.

I noticed that the attemps are 4/4. Does this need to be reset or does Nagios automatically reset that once it detects the issue is resolved?

---

### Post by pipemartinm on 2010-08-04
When you say nagios is giving you a 404 do you mean the 
1) webserver is giving you a 404 saying you can't get to nagios. 
2) You can get to nagios however not all the information is shown (eg left bar is showing but main window shows 404)
3) A service on Nagios relating to the local http service is showing an error?
4) Something else entirely?
Can you give a (sanatised) version of your httpd.conf and nagios webconf (/etc/apache2/conf.d/nagios.conf)? I'm guessing the virtualhost you setup for nagios isn't quite right. Also a screenshot of the error would be nice. 
 
My virtualhost config for nagios is as follows if that helps (ignore the AD auth stuff)
httpd.conf
```

<VirtualHost *:443>
ServerAdmin [EMAIL="me@my.domain"]me@my.domain[/EMAIL]
ServerName nagios.my.domain
DocumentRoot /usr/local/nagios/share
ScriptAlias /cgi-bin "/usr/local/nagios/sbin"
</VirtualHost>
<VirtualHost *:80>
ServerAdmin [EMAIL="me@my.domain"]me@my.domain[/EMAIL]
ServerName nagios.my.domain
DocumentRoot /usr/local/nagios/share
ScriptAlias /cgi-bin "/usr/local/nagios/sbin
</VirtualHost>

```
 
/etc/apache2/conf.d/nagios.conf
```

ScriptAlias /nagios/cgi-bin "/usr/local/nagios/sbin"
<Directory "/usr/local/nagios/sbin">
   SSLRequireSSL
   Options ExecCGI
   AllowOverride None
   Order allow,deny
   Allow from all
   AuthName "Active Directory"
   AuthType Basic
   AuthBasicProvider ldap
   AuthLDAPUrl  "[ldap://myadserver.my.domain:389/ou=myou,dc=my,dc=domin?sAMAccountName?sub?(objectclass](ldap://myadserver.my.domain:389/ou=myou,dc=my,dc=domin?sAMAccountName?sub?(objectclass)=*)"
   AuthLDAPBindDN "[EMAIL="ldapuser@my.domain"]ldapuser@my.domain[/EMAIL]"
   AuthLDAPBindPassword 'mypassword'
   Require valid-user
</Directory>
Alias /nagios "/usr/local/nagios/share"
<Directory "/usr/local/nagios/share">
   SSLRequireSSL
   Options None
   AllowOverride None
   Order allow,deny
   Allow from all
   AuthName "Active Directory"
   AuthType Basic
   AuthBasicProvider ldap
   AuthLDAPUrl  "[ldap://myadserver.my.domain:389/ou=myou,dc=my,dc=domin?sAMAccountName?sub?(objectclass](ldap://myadserver.my.domain:389/ou=myou,dc=my,dc=domin?sAMAccountName?sub?(objectclass)=*)"
   AuthLDAPBindDN "[EMAIL="ldapuser@my.domain"]ldapuser@my.domain[/EMAIL]"
   AuthLDAPBindPassword 'mypassword'
   Require valid-user
</Directory>

```

---

