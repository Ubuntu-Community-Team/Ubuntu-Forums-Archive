---
title: "Apache2 configuration for HTML::Mason"
date: 2010-09-02
forum: Server Platforms
---

### Post by Davidslv on 2010-09-02
Hi everyone,

I have a VM with Ubuntu Server 10.04 and i'm having problems configuring HTML::Mason to deal with files

I don't touch in perl for about.... 6months ago...

So i wanted to install and have some time programming with HTML::Mason, but i can't figure why i'm not being successfull.

i have the website folder in /var/www/mason2010

so: 
/var/www/mason2010
/var/www/mason2010/docs (in this one i have index.html)
/var/www/mason2010/mason-data 

in my apache2 i tried the documentation in masonbook.com (chapter 7)

<VirtualHost mason2010:80>
   ServerName  mason2010
   DocumentRoot  /var/www/mason2010/docs/

   PerlSetVar  MasonCompRoot  /var/www/mason2010/docs
   PerlSetVar  MasonDataDir   /var/www/mason2010/mason-data[INDENT]<LocationMatch "\.html$">[INDENT]SetHandler   perl-script
PerlHandler  HTML::Mason::ApacheHandler
[/INDENT]</LocationMatch>
[/INDENT]</VirtualHost>
But no sucess... i'm becomming desesperate about this....
You can see it by going to:
[http://213.22.166.109/mason2010/](http://213.22.166.109/mason2010/)

this is my index.html
[http://213.22.166.109/mason2010/docs/index.html](http://213.22.166.109/mason2010/docs/index.html)

Why isn't HTML::Mason taking care of the files?

the resolution of this big problem is :

```

PerlModule HTML::Mason::ApacheHandler

<Directory /var/www/mason2010>
        PerlSetVar MasonDataDir "/var/www/mason2010/mason-data"
        PerlSetVar MasonCompRoot "/var/www/mason2010/docs"

        <FilesMatch "\.html$">
                SetHandler perl-script
                PerlHandler HTML::Mason::ApacheHandler
        </FilesMatch>
</Directory>
```

---

