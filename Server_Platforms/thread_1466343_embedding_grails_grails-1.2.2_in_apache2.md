---
title: "embedding grails grails-1.2.2 in apache2"
date: 2010-04-30
forum: Server Platforms
---

### Post by tapas_mishra on 2010-04-30
I downloaded grails [http://grails.org](http://grails.org) and installed it.
Created a sample application hello world. It was running successfully.
In browser [http://localhost:8080/helloworld](http://localhost:8080/helloworld)
I was able to see grails running.
Now comes the problem.


To be able to always start the grails application running after boot
  I wrote a script in  /etc/init.d/software_grails

its contents are
```

#! /bin/sh
echo "Starting script grails for software"
cd /root/helloworld/
grails run-app

```then update-rc.d software_grails default
so it create the scripts
now I reboot it the application could not be opened in browser

[http://localhost:8080/helloworld]("http://172.21.100.193:8080/helloworld")

I have to open command prompt and go to /root/helloworld
and then execute
grails run-app

you dont have to write the name of application to run it.
  logging of boot messages is enabled
/etc/default/bootlogd
BOOTLOGD_ENABLE=Yes

then I opened
/var/log/boot.
```

Fri Apr 30 06:10:14 2010: Starting script grails for software
Fri Apr 30 06:10:14 2010: /etc/rc2.d/S20software_grails: line 4:
grails: command not found

```where as in .bashrc
```

export GRAILS_HOME=/root/grails
export PATH="$PATH:$GRAILS_HOME/bin"

```and in /etc/profile
[/code]
PATH="$JAVA_HOME/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin"
[/code]

If I am not wrong then above method will work only when some one Logs in not on boot time.
Is there a way where I can embed grails in apache2
they [http://www.grails.org/Deployment/](http://www.grails.org/Deployment/) have not mentioned any thing about apache2.

---

