---
title: "Showing full path in virtual hosts"
date: 2009-06-10
forum: Server Platforms
---

### Post by Goddard on 2009-06-10
I am having a problem with my virtual hosts showing to much information.

I have several virtual hosts setup and they give full system path information example /var/ww/user/httdocs when all I want it to do is display the httdocs as root so / would be all that is show.  I am new to apache so any help would be great.

---

### Post by el.otro on 2009-06-12
Did you use the *DocumentRoot* and *ServerName* directive*?  *You probably need to give a little more info as to what you HAVE done, so that your problem becomes clear, it's generally a little mistake on the configuration files. 

It generally follows a pattern like this (in this case a IP-based vHost):

> <VirtualHost 10.1.2.3>
               ServerAdmin [EMAIL="webmaster@host.example.com"]webmaster@host.example.com[/EMAIL]
        DocumentRoot /www/docs/host.example.com
        ServerName host.example.com
        ErrorLog logs/host.example.com-error_log
        TransferLog logs/host.example.com-access_log
             </VirtualHost>        
I took that from the documentation, you might wanna take a look at it.

[http://httpd.apache.org/docs/2.2/en/mod/core.html#virtualhost](http://httpd.apache.org/docs/2.2/en/mod/core.html#virtualhost)

I'm not sure what your problem is, but I hope I helped, what I said up there is more likely to happen if you manually set the vhost...but well.

Good Luck

---

