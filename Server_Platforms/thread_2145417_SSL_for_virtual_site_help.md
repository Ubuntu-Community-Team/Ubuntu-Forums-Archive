---
title: "SSL for virtual site help"
date: 2013-05-15
forum: Server Platforms
---

### Post by mcraul on 2013-05-15
I"m running  ubuntu 10.01.4 with apache 2 version 2.2.14. The site is up and running fine but I'm having a problem installing a ssl cert for the site.
Does it matter where the cert is installed it? 

In the sites-available conf file for the site do I reference port 443 along with port 80 and the location of the cert path in one file?

This is what I have now

> <virtualhost *:80>                                                         
ServerAdmin [email]xxxxx@comcast.net[/email]       
ServerName xxxx.com           ServerAlias [www.xxxx.com](www.xxxx.com)                   
DirectoryIndex index.cfm                
DocumentRoot "/var/www/xxx"        

<VirtualHost *:443>
 ServerName [www.yoursite.com](www.yoursite.com)
 DocumentRoot /var/www/site
 SSLEngine on
 SSLCertificateFile /path/to/www_yoursite_com.crt
 SSLCertificateKeyFile /path/to/www_yoursite_com.key
 SSLCertificateChainFile /path/to/DigiCertCA.crt
</Virtual Host>                                                                                                                                                        
</virtualhost>   


Is that right or do I have to make two separate vhost files one for port 80 and one for port 443?
Also do I have to change anything in the httpd.conf file as well?

I tested this config and it didn't work so i'm missing something.

THanks!

---

### Post by sandyd on 2013-05-15
**moved to server platforms**

try
```

<VirtualHost *:80>
ServerAdmin xxxxx@comcast.net
ServerName xxxx.com ServerAlias www.xxxx.com
DirectoryIndex index.cfm
DocumentRoot "/var/www/xxx"
</VirtualHost>

<VirtualHost *:443>
ServerName www.yoursite.com
DocumentRoot /var/www/site
SSLEngine on
SSLCertificateFile /path/to/www_yoursite_com.crt
SSLCertificateKeyFile /path/to/www_yoursite_com.key
SSLCertificateChainFile /path/to/DigiCertCA.crt
</VirtualHost>
 
```

---

### Post by mcraul on 2013-05-15
Ok i see what i did wrong there. 

I didnt close out the reference to port 80.

Also does it matter were I put that cert file at? as long as i have the correct path right?

Do I need to change anything in the apache2.conf or the httpd.conf?

I also noticed there was two files in /etc/sites-available  called 

default
default-ssl

would I have to mess with those as well ?

Thanks again!

---

### Post by sandyd on 2013-05-15
> **mcraul said:**
> Ok i see what i did wrong there. 

I didnt close out the reference to port 80.

Also does it matter were I put that cert file at? as long as i have the correct path right?

Do I need to change anything in the apache2.conf or the httpd.conf?

I also noticed there was two files in /etc/sites-available  called 

default
default-ssl

would I have to mess with those as well ?

Thanks again!
The path of the cert file doesnt matter - as long as its readable by apache, its fine

the files in /etc/sites-avaliable are just examples - you can remove them if you want

---

### Post by mcraul on 2013-05-15
So the path to the cert files just need to be in the domain conf under etc/sites-available? or do I have to put the path to the cert in another conf as well?

Thanks for the help!

---

### Post by mcraul on 2013-05-15
One more question, do I have to make a new private key for each virtual host or?

Thanks

---

### Post by SeijiSensei on 2013-05-15
> **mcraul said:**
> So the path to the cert files just need to be in the domain conf under etc/sites-available? or do I have to put the path to the cert in another conf as well?

The only place you need to reference the certificate files in is the server definition for the SSL host.

> **mcraul said:**
> One more question, do I have to make a new private key for each virtual host?

This is a much more complicated issue.  Usually every SSL host needs to be assigned to a separate IP address.  So if you wanted to have three different SSL hosts with different hostnames, you'd need three IPs.  However there are [ways to support multiple hostnames]("http://wiki.apache.org/httpd/NameBasedSSLVHosts") within a single domain using a wildcard certficate.

---

### Post by mcraul on 2013-05-15
So I installed the SSL and now I"m getting this error

> nvalid command 'SSLCertificate', perhaps misspelled or defined by a module not included in the server configuration 

Any way to overcome this?

Thanks!

---

### Post by mcraul on 2013-05-15
This is my config now thats giving me that error 

> <virtualhost *:80>                                                                                                                                                                             
                                                                                                                                                                                               
ServerAdmin [email]xxxx@comcast.net[/email]                                                                                                                                                                                                                                                                                                                                                    
ServerName xxxx.com                                                                                                                                                                  
ServerAlias [www.xxxx.com](www.xxxx.com)                                                                                                                                                             
                                                                                                                                                                                               
                                                                                                                                                                                       
DirectoryIndex index.cfm                                                                                                                                                                       
DocumentRoot "/var/www/nearby"                                                                                                                                                                 
</virtualhost>                                                                                                                                                                                 
                                                                                                                                                                                               
<virtualHost 23.xx.xx.xxx:443>                                                                                                                                                                 
ServerName xxxx.com                                                                                                                                                                  
DocumentRoot "/var/www/nearby"                                                                                                                                                                 
                                                                                                                                                                                               
SSLEngine on                                                                                                                                                                                   
SSLCertificate /etc/ssl/certs/xxxx.com.crt                                                                                                                                           
SSLCertificateKeyFile /root/www_xxxx_com.key                                                                                                                                         
SSLCertificateChainFile /etc/ssl/gd_bundle.crt         

---

### Post by mcraul on 2013-05-15
Do I have to make some change in

/etc/apache2/sites-available/ssl

as well?

---

### Post by mcraul on 2013-05-15
actually the whole error is 

Syntax error on line 25 of /etc/apache2/sites-enabled/xxxxxxx.com:                                                                                                                      
Invalid command 'SSLCertificate', perhaps misspelled or defined by a module not included in the server configuration

---

### Post by mcraul on 2013-05-15
Actually the full error is

> Syntax error on line 25 of /etc/apache2/sites-enabled/xxxx.com:                                                                                                                      
Invalid command 'SSLCertificate', perhaps misspelled or defined by a module not included in the server configuration

opps double post

---

