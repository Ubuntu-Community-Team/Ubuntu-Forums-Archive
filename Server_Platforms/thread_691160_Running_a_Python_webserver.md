---
title: "Running a Python webserver?"
date: 2008-02-08
forum: Server Platforms
---

### Post by baggus on 2008-02-08
Hi community!

First thread ever for me :)

I've been succesfully running an Ubuntu Server for a while after using the tutorial on [http://www.howtoforge.com/perfect_server_ubuntu7.10]("http://www.howtoforge.com/perfect_server_ubuntu7.10").

Everything worked fine until i got this school project where i had to set up a Python based wiki.

After looking at [http://en.wikipedia.org/wiki/Comparison_of_wiki_software]("http://en.wikipedia.org/wiki/Comparison_of_wiki_software") i decided that it was going to be either Sycamore or MoinMoin.

Problem is that nomatter how i change the config files or what packages i install, it just wont parse Python.

Now i have actually done some research and there are some people saying that it can't work under ISPconfig, then again this is apache and you can give apache directives in ISPconfig. No succes whatsoever.

Ofcourse there's the alternative of just virtualizing another server to work with a Python compatible apache. Tried this, but i can't find any good tutorial on how to get an Ubuntu server installed with apache python.

If this can't work in ISPconfig maybe someone can help me find a good tutorial on how to set up an Apache with Python support.

All and any help would be much appreciated :)

Many thanks in advance!

---

### Post by [2]BoxingFiend on 2008-02-08
try sudo apt-get install llibapache2-mod-python

---

### Post by baggus on 2008-02-08
> **'[2]BoxingFiend said:**
> try sudo apt-get install llibapache2-mod-python

i have infact installed that package

i checked and it is in the mod available and mod activated folders

---

### Post by KCPokes on 2008-02-08
Have you verified that mod_python is in fact being loaded in the Apache configuration?  We tend to rely on the packages making the necessary changes when we install them, but a quick check of the config can verify.

---

### Post by baggus on 2008-02-08
> **KCPokes said:**
> Have you verified that mod_python is in fact being loaded in the Apache configuration?  We tend to rely on the packages making the necessary changes when we install them, but a quick check of the config can verify.

what config files do you want me to check?

in the sites available default it says:
```
        <Directory /var/www/>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride None
                Order allow,deny
                allow from all

                AddHandler mod_python .py
                PythonHandler mod_python.publisher
                PythonDebug On

                # This directive allows us to have apache2's default start page
                # in /apache2-default/, but still have / go to the right place
                #RedirectMatch ^/$ /apache2-default/
        </Directory>

```

---

### Post by keeb on 2008-02-08
Also make sure that you have restarted Apache.

---

### Post by KCPokes on 2008-02-08
Ensuring there is a handler is important, but you also need to make sure there is a Load directive for mod_python, otherwise the handler does nothing.  

Look for something along the lines of...
```

LoadModule python_module libexec/mod_python.so

```

---

### Post by baggus on 2008-02-09
> **KCPokes said:**
> Ensuring there is a handler is important, but you also need to make sure there is a Load directive for mod_python, otherwise the handler does nothing.  

Look for something along the lines of...
```

LoadModule python_module libexec/mod_python.so

```

It's all there and it still won't work, really starting to think that a seperate server in VMware is the best solution. I am no noob to VMware, but i can't find a good tutorial on how to set up an Ubuntu webserver that will run python :(

Maybe someone can help me on that? :)

ps. yes i did restart apache after ever change

---

### Post by macdet on 2008-03-06
i have had the same probs. see my notes 

[http://wiki.mobbing-gegner.de/Linux/ServerConfig/Hetzner/Apache_Konfig/WebDjango](http://wiki.mobbing-gegner.de/Linux/ServerConfig/Hetzner/Apache_Konfig/WebDjango)

and search my wiki. :popcorn: If you have more questions feel free to mail me. ok!

[http://wiki.mobbing-gegner.de/Linux/ServerConfig/Hetzner/Apache_Konfig/WebDjango?highlight=%28apache%29](http://wiki.mobbing-gegner.de/Linux/ServerConfig/Hetzner/Apache_Konfig/WebDjango?highlight=%28apache%29)

---

