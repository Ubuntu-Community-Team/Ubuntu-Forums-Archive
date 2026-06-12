---
title: "Graphite under apache2 turn it to HTTPS + authentication"
date: 2015-07-25
forum: Server Platforms
---

### Post by tbaror on 2015-07-25
Hello  All,

I have Ubuntu 14.04.02 server with Apache2 installed with graphite , i need to secure a bit the server by turning it into https and get some basic authentication  for main Graphite graph page
I did generated  ssl key all other virtual  host on the web are turned to be https , only the graphite web not its config is as shown below ,so if someone could help how to turn this web into https and include some basic   authentication  to it will be appreciated
please advice
Thanks 
```
<VirtualHost *:80>

    WSGIDaemonProcess _graphite processes=5 threads=5 display-name='%{GROUP}' inactivity-timeout=120 user=_graphite group=_graphite
    WSGIProcessGroup _graphite
    WSGIImportScript /usr/share/graphite-web/graphite.wsgi process-group=_graphite application-group=%{GLOBAL}
    WSGIScriptAlias / /usr/share/graphite-web/graphite.wsgi

    Alias /content/ /usr/share/graphite-web/static/
    <Location "/content/">
        SetHandler None
    </Location>

    ErrorLog ${APACHE_LOG_DIR}/graphite-web_error.log

    # Possible values include: debug, info, notice, warn, error, crit,
    # alert, emerg.
    LogLevel warn

    CustomLog ${APACHE_LOG_DIR}/graphite-web_access.log combined

</VirtualHost>


```

---

