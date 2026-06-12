---
title: "apache and cgi-bin folder"
date: 2005-06-20
forum: Server Platforms
---

### Post by casualtie on 2005-06-20
I've installed apache webserver with Synaptic.
It all works just fine, but I can't access my [http://localhost/cgi-bin/](http://localhost/cgi-bin/) folder, it's forbidden.
So I want to locate the folder so I can chmod it.

But the folder aint located in my htdocs folder. My question to you is then: Where is my /cgi-bin folder located? :)

---

### Post by intangible on 2005-06-20
The default location for cgi-bin on deb systems is **/usr/lib/cgi-bin**

You can move it though, edit **/etc/apache/httpd.conf** and look for something like this, change it to fit your system:

```

<IfModule mod_alias.c>                                                      
    ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/                                
                                                                             
# "/usr/lib/cgi-bin" could be changed to whatever your ScriptAliased          
# CGI directory exists, if you have that configured.                        
                                                                             
    <Directory /usr/lib/cgi-bin/>
        AllowOverride None                                                 
        Options ExecCGI -MultiViews +SymLinksIfOwnerMatch                    
        Order allow,deny                                                    
        Allow from all                                                       
    </Directory>                                                            
</IfModule>

```

---

### Post by casualtie on 2005-06-20
Thank you for your input.
But actually my /etc/apache2/httpd.conf only contains this text:
> # This is here for backwards compatability reasons and to support
#  installing 3rd party modules directly via apxs2, rather than
#  through the /etc/apache2/mods-{available,enabled} mechanism.
#
#LoadModule mod_placeholder /usr/lib/apache2/modules/mod_placeholder.so
I guess my config file is /etc/apache2/apache2.conf.

I tried to add your piece of code into it, but with no succseed (restartet the webserver).
Actually I first tried to search my apache2.conf for the text /usr/lib/cgi-bin, with no results :/
There is no line in my apache2.conf which tells apache to locate /cgi-bin/ to /usr/lib/cgi-bin.

But it does, since I've added files to my /usr/lib/cgi-bin folder, which I now can access using [http://localhost/cgi-bin/](http://localhost/cgi-bin/)

---

### Post by intangible on 2005-06-20
Oops, sorry about that, I have apache 1.3, the config files are a bit different.

You should be able to search the config file for "cgi-bin" and the settings should be pretty obvious.

---

### Post by casualtie on 2005-06-20
Thats weird.
I've now searched the entire apache2.conf file for the string "cgi-bin", and I got 2 results, both commented (#). There is no settings for my cgi-bin folder there...

I can paste my config here if you want.
-Thx

---

### Post by intangible on 2005-06-20
Here ya go, this guy had the same problem: [http://www.linuxquestions.org/questions/history/331174](http://www.linuxquestions.org/questions/history/331174)

Apparently the setting you want is in /etc/apache2/sites-enabled

Good Hunting!

---

### Post by casualtie on 2005-06-20
Thank you so much :D
Problem solved.

---

