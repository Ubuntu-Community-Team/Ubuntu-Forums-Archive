---
title: "Hosting two domains on broadband modem pls help"
date: 2007-02-21
forum: Server Platforms
---

### Post by digitalhav0c on 2007-02-21
Well hopefully this makes sense. Well i have two domains i want to host  on one pc i setup with ubuntu server 6.10. I have lamp server installed i want to host them on a dynamic ip address using dynamic dns some how and vitual hosts. I would really appreciate it if some one could point me in the right direction on were i could get maybe a howto or more information regarding both. 

Thank you

---

### Post by digitalhav0c on 2007-02-22
Listen 8080

        NameVirtualHost *:8080



        <VirtualHost *:8080>
        DocumentRoot /www/docs/tafadzwa.info
        ServerName [www.tafadzwa.info](www.tafadzwa.info)
        ServerAlias tafadzwa
        </VirtualHost>



        <VirtualHost *:8080>
        DocumentRoot /www/docs/daclan.info
        ServerName [www.daclan.info](www.daclan.info)
        ServerAlias daclan
        </VirtualHost>



        #<VirtualHost 192.168.1.1>
        #ServerName name3.mydomain.com
        #DocumentRoot /usr/local/apache/name3docs
        #ServerAlias name3
        #</VirtualHost>



---------------------------------------------------------------------------------------------------------

What am i doing wrong? 
Im getting this error 

* Starting apache 2.0 web server...                                                                                                                                             apache2: Could not determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
[Thu Feb 22 00:27:00 2007] [error] VirtualHost *:8080 -- mixing * ports and non-* ports with a NameVirtualHost address is not supported, proceeding with undefined results
[Thu Feb 22 00:27:00 2007] [error] VirtualHost *:8080 -- mixing * ports and non-* ports with a NameVirtualHost address is not supported, proceeding with undefined results
[Thu Feb 22 00:27:00 2007] [warn] NameVirtualHost *:8080 has no VirtualHosts



_______________________________________________________________________

I edited to this now 

# This is here for backwards compatability reasons and to support
#  installing 3rd party modules directly via apxs2, rather than
#  through the /etc/apache2/mods-{available,enabled} mechanism.
#
#LoadModule mod_placeholder /usr/lib/apache2/modules/mod_placeholder.so


        Listen 8080

        NameVirtualHost 65.190.254.48

        <VirtualHost 65.190.254.48>
        ServerName tafadzwa.tafadzwa.info
        DocumentRoot /www/docs/tafadzwa.info
        ServerAlias tafadzwa
        </VirtualHost>



        <VirtualHost 65.190.254.48>
        ServerName daclan.daclan.info
        DocumentRoot /www/docs/daclan.info
        ServerAlias daclan
        </VirtualHost>



        #<VirtualHost 192.168.1.1>
        #ServerName name3.mydomain.com
        #DocumentRoot /usr/local/apache/name3docs
        #ServerAlias name3
        #</VirtualHost>

and im getting this error 

 * Starting apache 2.0 web server...                                                                                                                                             apache2: Could not determine the server's fully qualified domain name, using 127.0.1.1 for ServerName

If anyone could lead me in the right direction it would be greatly aprreciated. 

thank you

---

