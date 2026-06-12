---
title: "SSI does not work with CGI script"
date: 2015-10-15
forum: Server Platforms
---

### Post by micahpage on 2015-10-15
I have SSI enabled and used thought in my server. However cgi scripts do not include my menu bar. 

the script is 
[http://python-gaming.com/cgi-bin/portingguide.py](http://python-gaming.com/cgi-bin/portingguide.py)

and the header is show here
[http://python-gaming.com](http://python-gaming.com)

/etc/apache2/conf-enabled/serve-cgi-bin.conf
```
    <IfDefine ENABLE_USR_LIB_CGI_BIN>

        ScriptAlias /cgi-bin/ /var/www/html/cgi-bin/
        <Directory "/var/www/html/cgi-bin">
            AllowOverride None
            Options +ExecCGI +MultiViews +SymLinksIfOwnerMatch +Includes +FollowSymLinks
            AddHandler cgi-script .py
            AddOutputFilter INCLUDES .shtml
            Require all granted
        </Directory>



```

if i make a scirpt alias in /etc/apache2/apache2.conf i get this error when restarting apache. 

```
metulburr /var/www/html $ sudo service apache2 restart        
                                            
 * Restarting web server apache2
[Thu Oct 15 12:26:47.861675 2015] [alias:warn] [pid 23995] AH00671: The ScriptAlias directive in /etc/apache2/conf-enabled/serve-cgi-bin.conf at line 11 will probably never match because it overlaps an earlier ScriptAlias.
   ...done.



```
I wouldnt think that is the problem though due to the fact of the cgi script working in general.

What can i do to make my cgi scripts allow virtual includes?

---

### Post by micahpage on 2015-10-16
I found out that, that is pretty much not possible. Or you have to do a lot of tinkering if it is. 

The easy solution i found (slap on forehead) is to utilize the scripting language of CGI to just open the file, get contents, and insert itself into the html before outputting. So simple i cant believe i didnt think that. I was so focused on getting the include visual line to work...

---

