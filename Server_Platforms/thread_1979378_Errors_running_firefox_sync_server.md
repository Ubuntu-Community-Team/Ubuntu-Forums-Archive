---
title: "Errors running firefox sync server"
date: 2012-05-13
forum: Server Platforms
---

### Post by radcom on 2012-05-13
I have tried to set up a firefox sync server according to these instructions [http://sathya.de/blog/how-tos/setup-your-own-firefox-sync-server-on-debian-with-apache2-and-mysql/]("http://sathya.de/blog/how-tos/setup-your-own-firefox-sync-server-on-debian-with-apache2-and-mysql/")

only I have replaced "weave" with "firesync" in the usernames, databasenames, foldernames, etc. from what I can gather it compiles ok but every time I have firefox sync connect to it I get this error:

```
[Sun May 13 14:37:39 2012] [error] [client 78.105.162.246] mod_wsgi (pid=20279): Target WSGI script '/opt/firesync/sync.wsgi' cannot be loaded as Python module.
[Sun May 13 14:37:39 2012] [error] [client 78.105.162.246] mod_wsgi (pid=20279): Exception occurred processing WSGI script '/opt/firesync/sync.wsgi'.
[Sun May 13 14:37:39 2012] [error] [client 78.105.162.246] Traceback (most recent call last):
[Sun May 13 14:37:39 2012] [error] [client 78.105.162.246]   File "/opt/firesync/sync.wsgi", line 74, in <module>
[Sun May 13 14:37:39 2012] [error] [client 78.105.162.246]     application = loadapp('config:%s'% ini_file)
[Sun May 13 14:37:39 2012] [error] [client 78.105.162.246]   File "/opt/firesync/lib/python2.6/site-packages/paste/deploy/loadwsgi.py", line 203, in loadapp
[Sun May 13 14:37:39 2012] [error] [client 78.105.162.246]     return loadobj(APP, uri, name=name, **kw)
[Sun May 13 14:37:39 2012] [error] [client 78.105.162.246]   File "/opt/firesync/lib/python2.6/site-packages/paste/deploy/loadwsgi.py", line 224, in loadobj
[Sun May 13 14:37:39 2012] [error] [client 78.105.162.246]     return context.create()
[Sun May 13 14:37:39 2012] [error] [client 78.105.162.246]   File "/opt/firesync/lib/python2.6/site-packages/paste/deploy/loadwsgi.py", line 617, in create
[Sun May 13 14:37:39 2012] [error] [client 78.105.162.246]     return self.object_type.invoke(self)
[Sun May 13 14:37:39 2012] [error] [client 78.105.162.246]   File "/opt/firesync/lib/python2.6/site-packages/paste/deploy/loadwsgi.py", line 109, in invoke
[Sun May 13 14:37:39 2012] [error] [client 78.105.162.246]     return fix_call(context.object, context.global_conf, **context.local_conf)
[Sun May 13 14:37:39 2012] [error] [client 78.105.162.246]   File "/opt/firesync/lib/python2.6/site-packages/paste/deploy/util/fixtypeerror.py", line 57, in fix_call
[Sun May 13 14:37:39 2012] [error] [client 78.105.162.246]     val = callable(*args, **kw)
[Sun May 13 14:37:39 2012] [error] [client 78.105.162.246]   File "/opt/firesync/deps/server-core/services/baseapp.py", line 368, in make_app
[Sun May 13 14:37:39 2012] [error] [client 78.105.162.246]     app = klass(urls, controllers, params, auth_class)
[Sun May 13 14:37:39 2012] [error] [client 78.105.162.246]   File "/opt/firesync/deps/server-storage/syncstorage/wsgiapp.py", line 106, in __init__
[Sun May 13 14:37:39 2012] [error] [client 78.105.162.246]     self.storages = {'default': get_storage(config)}
[Sun May 13 14:37:39 2012] [error] [client 78.105.162.246]   File "/opt/firesync/deps/server-storage/syncstorage/storage/__init__.py", line 395, in get_storage
[Sun May 13 14:37:39 2012] [error] [client 78.105.162.246]     return SyncStorage.get_from_config(config, 'storage')
[Sun May 13 14:37:39 2012] [error] [client 78.105.162.246]   File "/opt/firesync/deps/server-core/services/pluginreg.py", line 153, in get_from_config
[Sun May 13 14:37:39 2012] [error] [client 78.105.162.246]     return cls.get(backend_name, **config)
[Sun May 13 14:37:39 2012] [error] [client 78.105.162.246]   File "/opt/firesync/deps/server-core/services/pluginreg.py", line 159, in get
[Sun May 13 14:37:39 2012] [error] [client 78.105.162.246]     return klass(**params)
[Sun May 13 14:37:39 2012] [error] [client 78.105.162.246]   File "/opt/firesync/deps/server-storage/syncstorage/storage/sql.py", line 234, in __init__
[Sun May 13 14:37:39 2012] [error] [client 78.105.162.246]     self._engine = create_engine(sqluri, **sqlkw)
[Sun May 13 14:37:39 2012] [error] [client 78.105.162.246]   File "/opt/firesync/lib/python2.6/site-packages/sqlalchemy/engine/__init__.py", line 263, in create_engine
[Sun May 13 14:37:39 2012] [error] [client 78.105.162.246]     return strategy.create(*args, **kwargs)
[Sun May 13 14:37:39 2012] [error] [client 78.105.162.246]   File "/opt/firesync/lib/python2.6/site-packages/sqlalchemy/engine/strategies.py", line 50, in create
[Sun May 13 14:37:39 2012] [error] [client 78.105.162.246]     u = url.make_url(name_or_url)
[Sun May 13 14:37:39 2012] [error] [client 78.105.162.246]   File "/opt/firesync/lib/python2.6/site-packages/sqlalchemy/engine/url.py", line 170, in make_url
[Sun May 13 14:37:39 2012] [error] [client 78.105.162.246]     return _parse_rfc1738_args(name_or_url)
[Sun May 13 14:37:39 2012] [error] [client 78.105.162.246]   File "/opt/firesync/lib/python2.6/site-packages/sqlalchemy/engine/url.py", line 211, in _parse_rfc1738_args
[Sun May 13 14:37:39 2012] [error] [client 78.105.162.246]     "Could not parse rfc1738 URL from string '%s'" % name)
[Sun May 13 14:37:39 2012] [error] [client 78.105.162.246] ArgumentError: Could not parse rfc1738 URL from string 'sqluri = mysql://firesync:password@localhost/firesync'


```

The content of my apache2 site config file is:
```

<VirtualHost *:80>
        ServerName firesync.mydomain.org
        Redirect / https://firesync.mydomain.org
</VirtualHost>
<VirtualHost *:443>
        ServerName firesync.mydomain.org
        DocumentRoot /opt/firesync

        WSGIProcessGroup sync
        WSGIDaemonProcess sync user=www-data group=www-data processes=2 threads=25
        WSGIPassAuthorization On
        WSGIScriptAlias / /opt/firesync/sync.wsgi

        SSLEngine On
        SSLCertificateFile    /etc/apache2/ssl/ssl.crt
        SSLCertificateKeyFile /etc/apache2/ssl/ssl.key

        CustomLog /var/log/apache2/access_sync.log combined
        ErrorLog /var/log/apache2/error_sync.log
        LogLevel warn
</VirtualHost>
<Directory /opt/firesync>
        Order deny,allow
        Allow from all
</Directory>

```

and the content of my sync.conf file is:
```
[global]
clean_shutdown = false

[captcha]
use = false
public_key = 6Le8OLwSAAAAAK-wkjNPBtHD4Iv50moNFANIalJL
private_key = 6Le8OLwSAAAAAEKoqfc-DmoF4HNswD7RNdGwxRij
use_ssl = false

[storage]
backend = syncstorage.storage.sql.SQLStorage
sqluri = sqluri = mysql://firesync:password@localhost/firesync
standard_collections = false
use_quota = true
quota_size = 5120
pool_size = 100
pool_recycle = 3600
reset_on_return = true
display_config = true
create_tables = true

[auth]
backend = services.user.sql.SQLUser
sqluri =  mysql://firesync:password@localhost/firesync
pool_size = 100
pool_recycle = 3600
create_tables = true

[nodes]
fallback_node = https://firesync.mydomain.org

[smtp]
host = localhost
port = 25
sender = weave@mozilla.com

[cef]
use = true
file = syslog
vendor = mozilla
version = 0
device_version = 1.3
product = weave

```
I'm running python 2.6.5 (r265:79063, Apr 16 2010, 13:09:56)
[GCC 4.4.3]

ubuntu 10.04

is there anyone here that can help me make it work?

---

### Post by radcom on 2012-05-13
it was my own stupidity the sqluri line was wrong like it said seems now to be working

---

