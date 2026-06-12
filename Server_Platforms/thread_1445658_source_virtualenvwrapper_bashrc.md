---
title: "source virtualenvwrapper_bashrc"
date: 2010-04-02
forum: Server Platforms
---

### Post by jwxie on 2010-04-02
I am reading this entry, and tried some of them. This did not work at all
[http://blog.adammiskiewicz.com/2009/11/08/setting-up-a-production-django-environment-on-ubuntu-karmic/](http://blog.adammiskiewicz.com/2009/11/08/setting-up-a-production-django-environment-on-ubuntu-karmic/)

[B]
source /usr/local/bin/virtualenvwrapper_bashrc[/B]

it gave
```
jwxie@jwxie-laptop:~$ source /usr/local/bin/virtualenvwrapper_bashrc
bash: /var/www/python/premkvirtualenv: Permission denied
chmod: cannot access `/var/www/python/premkvirtualenv': No such file or directory
bash: /var/www/python/postmkvirtualenv: Permission denied
chmod: cannot access `/var/www/python/postmkvirtualenv': No such file or directory
bash: /var/www/python/prermvirtualenv: Permission denied
chmod: cannot access `/var/www/python/prermvirtualenv': No such file or directory
bash: /var/www/python/postrmvirtualenv: Permission denied
chmod: cannot access `/var/www/python/postrmvirtualenv': No such file or directory
bash: /var/www/python/predeactivate: Permission denied
chmod: cannot access `/var/www/python/predeactivate': No such file or directory
bash: /var/www/python/postdeactivate: Permission denied
chmod: cannot access `/var/www/python/postdeactivate': No such file or directory
bash: /var/www/python/preactivate: Permission denied
chmod: cannot access `/var/www/python/preactivate': No such file or directory
bash: /var/www/python/postactivate: Permission denied
chmod: cannot access `/var/www/python/postactivate': No such file or directory
```

So what went wrong? Everything else was fine...

---

