---
title: "Unable to start my Startup Script"
date: 2018-07-04
forum: Server Platforms
---

### Post by SpecialNeeds on 2018-07-04
Hello 
I'm deploying a django app with daphne and nginx in a Ubuntu Server
I follow this two tutorial, mainly the first:
[LIST=1]
[*][Tutorial 1]("http://masnun.rocks/2016/11/02/deploying-django-channels-using-daphne/")
[*][Tutorial 2]("https://ponytech.net/blog/django-deployement-ubuntu-upstart-nginx-gunicorn-and-virtualenvwrapper")
[/LIST]


Before all, I get working everything in dev mode and expose it through an open port 8000.

```

python manage.py runserver 0.0.0.0:8000
#or
daphne -b 0.0.0.0 -p 8000 myapp.asgi:application

```

Then in my first step I installed redis-server
```

sudo apt-get install redis-server

```


I created my startup script (following the second tutorial).
My cnf in: *[COLOR=#444444][FONT=Georgia]/etc/init/[/FONT][/COLOR]*[COLOR=#444444][FONT=Georgia]

[/FONT][/COLOR][INDENT][I][COLOR=#444444][FONT=Georgia]sudo nano [/FONT][/COLOR][COLOR=#444444][FONT=Georgia]/etc/init/myapp.cnf[/FONT][/COLOR][COLOR=#444444][FONT=Georgia]
[/FONT][/COLOR][/I][/INDENT]
[COLOR=#444444][FONT=Georgia]
[/FONT][/COLOR]```
[COLOR=#444444][FONT=Georgia]

[/FONT][/COLOR]start on runlevel [2345]
stop on runlevel [016]

respawn

script
    cd /home/mypath/myapp
    export DJANGO_SETTINGS_MODULE="myapp.settings"
    exec daphne -b 0.0.0.0 -p 8000 myapp.asgi:application
end script

```

[COLOR=#444444][FONT=Georgia]The symbolic link
[/FONT][/COLOR]```
ln -fs /lib/init/upstart-job /etc/init/myapp
```

But here it throw me the following error:[COLOR=#444444][FONT=Georgia]
[/FONT][/COLOR]```
update-rc.d ferreyrostimecontrol defaults
```
**update-rc.d: error: unable to read /etc/init.d/myapp**

Then I decide to delete the previously symbolic link created and create my conf in init.d.
[COLOR=#444444][FONT=Georgia]
[/FONT][/COLOR][INDENT][I][COLOR=#444444][FONT=Georgia]sudo nano [/FONT][/COLOR][COLOR=#444444][FONT=Georgia]/etc/init.d/myapp.cnf[/FONT][/COLOR][COLOR=#444444][FONT=Georgia]
[/FONT][/COLOR][/I][/INDENT]
[COLOR=#444444][FONT=Georgia]
[/FONT][/COLOR]```
[COLOR=#444444][FONT=Georgia]
[/FONT][/COLOR]start on runlevel [2345]
stop on runlevel [016]

respawn

script
    cd /home/mypath/myapp
    export DJANGO_SETTINGS_MODULE="myapp.settings"
    exec daphne -b 0.0.0.0 -p 8000 myapp.asgi:application
end script


```
[COLOR=#444444][FONT=Georgia]
[/FONT][/COLOR]Again the symbolic link[COLOR=#444444][FONT=Georgia]
[/FONT][/COLOR]```
ln -fs /lib/init/upstart-job /etc/init.d/myapp
```

But also fails
```
update-rc.d ferreyrostimecontrol defaults
```
[B][COLOR=#ff0000]update-rc.d: error: unable to read /etc/init.d/myapp[/COLOR]


[/B]Where is the problem?

---

### Post by TheFu on 2018-07-04
Can't tell.  The way thing start is different depending on the release used.  There are no more "runlevels" since before 16.04, so that doesn't  make sense.

Inside your scripts, always use the full path to every program, never trust the PATH environment variable.

When I setup Redis, there was more configuration needed than you are showing, but I don't do python.

---

