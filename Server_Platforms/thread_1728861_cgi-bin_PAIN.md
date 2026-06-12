---
title: "cgi-bin PAIN"
date: 2011-04-14
forum: Server Platforms
---

### Post by tjbradford on 2011-04-14
for the love of god someone help me ! 

I have spent most of the day trying and FAILING to get cgi-bin working

ubuntu 10 

apt-get install apache2 
apt-get install php5

noticed it never created a cgi-bin folder so created it under /var/www/cgi-bin

looked at many online guides as to why this doesn't work but no joy, checked chmod +x 

i note that apache2 has changed ALOT since i last configured it, whats with the config file pointing to other config files, why can't it all just sit under one roof! 

is anybody able to help me thought this / point me to a good guide that is for a complete dimbo (me) 

?

---

### Post by Doug S on 2011-04-14
I am not an expert, but I can try to help you.
By default the cgi files should be placed in /usr/lib/cgi-bin
And that default location is defined in /etc/apache2/sites-available/default. Look for this segment in that file:
```
 
        ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
        <Directory "/usr/lib/cgi-bin">
                AllowOverride None
                Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
                Order allow,deny
                Allow from all
        </Directory>


```
Yes, Apache config has changed a lot since I had last configured it also. However, I do not know why. Moslty I use all default settings and put files where apache expects to find them.
I hope this helps.

---

