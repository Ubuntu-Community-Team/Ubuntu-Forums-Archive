---
title: "mod_python with apache2, (Re)importing module error"
date: 2009-03-31
forum: Server Platforms
---

### Post by tworking on 2009-03-31
Hi, we've moved a number of our static and php based sites to a dedicated server running ubuntu. I'm trying to get mod_python to work with apache2 but not having any success.

I've followed a few tutorials for getting mod_python working but I can't see what I'm doing wrong. 

When I visit http://site.example.com/cgi-bin/test.py I actually get my 404 page! (whereas I get a 403 Forbidden if the file really doesn't exist)

Here's my setup:

In /etc/apache2/sites-enabled/ there are configuration files named after each of my domains. In [the site.example.com file]("http://dpaste.com/hold/21618/") I've added this to the user directives section:

```
# Begin user directives <--          
<Directory /home/default/site.example.com/user/htdocs/cgi-bin/>
                  Options Indexes FollowSymLinks MultiViews
                  AllowOverride AuthConfig
                  Order allow,deny
                  allow from all
                  AddHandler mod_python .py
                  PythonHandler mod_python.publisher
                  PythonDebug On
          </Directory>
  # --> End user directives
  
  #(full file _[here]("http://dpaste.com/hold/21618/")_)
```I've apt-getted mod_python, and I have "LoadModule python_module /usr/lib/apache2/modules/mod_python.so" in /etc/apache2/mods-available/mod_python.load. I've confirmed mod_python.so exists. And I can do "import mod_python" in a python shell but haven't done anymore than that.

/etc/apache2/apache2.conf contains a [load of settings]("http://dpaste.com/hold/21663/") but I haven't changed any of them.

I don't think it's a permissions problem, I've tried a few different  chmods on cgi-bin and test.py, but it could be. And yes my script works when I do python test.py on the command line.

When I use cgi-bin in the directory line above I get this in error.log:

```
[Tue Mar 31 15:27:11 2009] [notice] mod_python: (Re)importing module 'mod_python.publisher'
[Tue Mar 31 15:27:11 2009] [notice] mod_python: (Re)importing module 'test' with path set to '['/home/default/site.example.com/user/htdocs/cgi-bin']'
```But when I use ...htdocs/python/ I get no error logged.

Any help is greatly appreciated :-)

---

