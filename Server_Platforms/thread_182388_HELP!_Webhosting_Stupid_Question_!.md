---
title: "HELP! Webhosting Stupid Question !"
date: 2006-05-26
forum: Server Platforms
---

### Post by Socratez on 2006-05-26
Ok I have setup a local apache2 machine at home that is working great but I can not figure out how to change the default page loaded. When i put the IP into my browser I get the Apache2 defualt place holder page. I would like to set it up to go to my TWiki site I am working on by default ... Is there an easy way to do this ???

---

### Post by henriquemaia on 2006-05-26
[quote=Socratez]Ok I have setup a local apache2 machine at home that is working great but I can not figure out how to change the default page loaded. When i put the IP into my browser I get the Apache2 defualt place holder page. I would like to set it up to go to my TWiki site I am working on by default ... Is there an easy way to do this ???[/quote] 
Yes there is.

Two ways of doing it.


[B] 1. Change the DocumentRoot
[/B][LIST]
[*] Open a terminal.[/LIST][INDENT] Type:

```
sudo gedit /etc/apache2/sudo gedit /etc/apache2/sites-enabled/000-default

``` 
Edit the entry DocumentRoot. Put there the path to the folder where you have the TWiki.
[/INDENT][LIST]
[*] save file[/LIST][LIST]
[*] restart apache[/LIST][INDENT]
```
sudo /etc/init.d/apache2 restart
``` 

[/INDENT][LIST]
[*]access your address as normally (e.g. [http://localhost]("http://localhost")[/LIST][B] 2. Enable user public_html folder
[/B][LIST]
[*] Open a terminal.[/LIST][INDENT]Type
```
sudo a2enmod
``` 
You'll get:

Which module would you like to enable?
Your choices are: actions asis auth_anon auth_dbm auth_digest auth_ldap cache cern_meta cgid cgi dav_fs dav deflate disk_cache expires ext_filter file_cache headers imap include info ldap mem_cache mime_magic php5 proxy_connect proxy_ftp proxy_http proxy rewrite speling ssl suexec unique_id userdir usertrack vhost_alias
Module name? [B]userdir

[/B]answer **userdir** (as stated) after the question mark.
[/INDENT][LIST]
[*] restart apache[/LIST][INDENT]```
sudo /etc/init.d/apache2 restart
``` 
[/INDENT][LIST]
[*] Put the TWiki folder in the folder ~/public_html[/LIST][LIST]
[*] Access it by typing your address followed by ~your_username (e.g. [http://localhost/~henriquemaia]("http://localhost/%7Ehenriquemaia"))[/LIST]

---

### Post by Socratez on 2006-05-30
Ok so now when i put in the server Ip it shows me 2 directories.

apache2-default/ 
twiki/

If i click on the apache it brings up default Apache homepage. If i click on the TWiki it brings me to pub/. Then from there I can see the folders but the Twiki does not start. I have this list of directories I found when installing the twiki which i think is the key but I am not sure how to make it work so I can just have [http://www.mydomina.com/twiki/](http://www.mydomina.com/twiki/) 

Folder List ... 


Default TWiki directory                                                

/home/httpd/twiki/bin                                             
/home/httpd/twiki/pub                                             
/home/httpd/twiki/templates                                
/home/httpd/twiki/data                                                
/home/httpd/twiki/lib/TWiki                                    


Debian directory   
/usr/lib/cgi-bin/twiki  
/var/www/twiki/pub3
/var/lib/twiki/templates  
/var/lib/twiki/data
/usr/share/perl5/TWiki 
/var/log/twiki

---

