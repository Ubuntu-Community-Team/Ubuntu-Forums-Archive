---
title: "LDAP auth for PHP, without creating a domain controler"
date: 2009-04-27
forum: Server Platforms
---

### Post by eDRoaCH on 2009-04-27
Hi all. I am trying to integrate Mediawiki with our internal W2k3 AD. 

What I need to do, is to import the server's certificate so that the authentication can go through. However, I have no /etc/ldap.conf or /etc/openldap/ldap.conf. I do however have /etc/ldap/ldap.conf. 

All the tutorials, troubleshooting, etc I seem to dig up want to use slapd to turn the Ubuntu into a domain controller, which I do not wish to do. I tried to install the package and see how I could configure it, but in the wizard it seems to want a domain admin account in case root changes password. I am actually not the admin for the domain so I do not have this.

The creator of the LDAP authentication plugin has a tutorial here [http://ryandlane.com/wprdl/2009/03/23/using-the-ldap-authentication-plugin-for-mediawiki-the-basics-part-1/](http://ryandlane.com/wprdl/2009/03/23/using-the-ldap-authentication-plugin-for-mediawiki-the-basics-part-1/) which I have been following, including how I got the certificate.

Can anyone give me some info on this? Once again I just want PHP to be able to do ldaps:// I want the actual server logins to stay local.

Ubuntu 8.04 LTS with all updates. LAMP & PHP-ldap is installed. Help appreciated!

---

### Post by terazen on 2009-04-27
There is a project called ADLDAP on sourceforge you should look into.  
[http://adldap.sourceforge.net/download.php]("http://adldap.sourceforge.net/download.php")

You don't necessarily need to use the files as is.  Just use them as a template.  For me I had to add "TLS_REQCERT never" to my /etc/ldap/ldap.conf file because of a certificate error, but other than that I think I just edited the ADLDAP.php file only.

---

### Post by eDRoaCH on 2009-04-27
so is /etc/ldap/ldap.conf the correct and only file to edit? I have tried adding TLS_REQCERT never to it with no success. The file does not seem to be otherwise set up at all, however mediawiki config does hold the settings for the AD servers, encryption type, etc so maybe it is not needed? 

I appreciate the help

---

### Post by terazen on 2009-04-27
PHP should be able to work for you with the right settings.  I believe it just relies on openldap/openssl.

You can try using ldapsearch (man ldapsearch for details) in debugging mode to see what kind of error you get from command line.  At least that will get you a better error than "bind failed" or whatever the error is that you are getting now.

---

### Post by eDRoaCH on 2009-04-27
I got it! Silly thing really. I guess I misread the documentation, i had it in the mediawiki config as mydomain\USER-NAME (USER-NAME) is a variable) however I left off the .local on the domain.

So I changed it to [email]USER-NAME@domain.local[/email] (it makes more sense reading it that way to me than domain.local/USER-NAME and it works!

Man I have been pulling my hair out over this (on an intermittent basis) for over a year. So happy to have it.

And thanks for that link, that is a very nice library. I will be adding it to my bag of tricks. (ldapsearch is so painful to figure out)

---

### Post by terazen on 2009-04-27
Oh congrats!  The domain\user is supposed to work for older windows os so you probably did read that in the docs. :)

---

