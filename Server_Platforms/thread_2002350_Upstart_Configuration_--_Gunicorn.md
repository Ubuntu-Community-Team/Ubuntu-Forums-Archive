---
title: "Upstart Configuration -- Gunicorn"
date: 2012-06-12
forum: Server Platforms
---

### Post by iguard06 on 2012-06-12
So I'm trying to setup Gunicorn as a service.  Here is my current file:

Location: ln -s /lib/init/webapp.conf /etc/init.d/webapp

```

description "upstart configuration for gunicorn webapp"

start on net-device-up
stop on shutdown
env VENV ="/home/user/webapp"
respawn

exec $VENV/bin/gunicorn_django -u www-data -c -preload -w 2 --log-level debug --log-file $VENV/gunicorn.log -p
```

However, when I run:
```
service webapp start
```

I get a return of Unrecognized Service.

I'm not sure if I'm doing this right from an Upstart perspective. 

Any thoughts? Ps I'm running Ubuntu 10.04 LTS 64 BIT server

Thanks.

---

### Post by nsnidanko on 2012-06-14
[PHP]description "upstart configuration for gunicorn webapp" 
env VENV ="/home/user/webapp" 
expect fork

script
exec $VENV/bin/gunicorn_django -u www-data -c -preload -w 2 --log-level debug --log-file $VENV/gunicorn.log -p
end script
[/PHP]Try this and issue **webapp start** and see if it works. I am not expert on upstart but you can find good documentation here:

[http://upstart.ubuntu.com/cookbook/](http://upstart.ubuntu.com/cookbook/)

---

