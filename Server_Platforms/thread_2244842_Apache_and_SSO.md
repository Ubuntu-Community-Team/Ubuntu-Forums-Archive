---
title: "Apache and SSO"
date: 2014-09-19
forum: Server Platforms
---

### Post by Fredrik_Persson_ on 2014-09-19
Hi! This is my first post here. I hope I have put this in the right place. I have a problem and I was hoping that someone maybe can help me in the right direction. I will try to explain my scenario. 

I have a Joomla 1.7 site (yes I know it is old but the site is not done by me) running on Ubuntu LAMP server. I have downloded a plugin called JMapMyLDAP - HTTP SSO Plugin that allows me to use LDAP and SSO to Joomla. I can now access the site by using my AD login. However I just do not get the sso to work. This is not a joomla problem but more of a general apache/linux problem. I have setup kerberos, I have checked that kerberos is working with the kinit command. and the ktutil to verify. I have created the keytab files on my dc and the linux server. I have put the following in my apache conf file. 

<Directory /var/www/joomla/>
AuthType Kerberos
AuthName whitehelp
KrbAuthRealms WHITE.LOCAL
KrbServiceName HTTP
Krb5Keytab /etc/kerberos_hostname.keytab
require valid-user
KrbMethodNegotiate On
KrbMethodK5Passwd On
</Directory>

I want to get the value REMOTE_USER in my PHP Info so I can use this to get my username. This works when the above lines are in apache. However I just get a pop up window in my browser asking me for username and password. This is the problem. I want to be signed in via SSO. Maybe I have missed something here. I am not an expert at all regarding apache. Plaese can someone point me in the right direction.

---

### Post by cariboo on 2014-09-20
Seeing as this is a server problem, moved to Server Platforms.

---

