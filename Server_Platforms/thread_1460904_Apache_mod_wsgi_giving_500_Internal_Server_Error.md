---
title: "Apache mod_wsgi giving 500 Internal Server Error"
date: 2010-04-23
forum: Server Platforms
---

### Post by the real omni on 2010-04-23
Hi,

I'm trying to install mod_wsgi for apache/2.2.12 on ubuntu 9.10

It appears the official package is broken, as a simple apt-get install libapache2-mod-wsgi doesn't do the trick.

So far I have done the following, as per instructions on [http://serverfault.com/questions/91468/how-to-set-up-mod-wsgi-for-python-on-ubuntu/134696#134696]("http://serverfault.com/questions/91468/how-to-set-up-mod-wsgi-for-python-on-ubuntu/134696#134696"):

```
# apt-get install libapache2-mod-wsgi
```

I've created the wsgi.load file with the following contents:

```
LoadModule wsgi_module /usr/lib/apache2/modules/mod_wsgi.so
```

I've ensured that /usr/lib/apache2/modules/mod_wsgi.so does in fact exist.

I've created symlinks:

```
# ln -s /etc/apache2/mods-available/wsgi.load /etc/apache2/mods-enabled/wsgi.load
# ln -s /etc/apache2/mods-available/wsgi.conf /etc/apache2/mods-enabled/wsgi.conf
```

I've restarted apache:

```
# /etc/init.d/apache2 restart
```

I've ensured mod_wsgi is loaded:

```
# apache2ctl -t -D DUMP_MODULES
Loaded Modules:
 core_module (static)
 log_config_module (static)
 logio_module (static)
 mpm_prefork_module (static)
 http_module (static)
 so_module (static)
 alias_module (shared)
 auth_basic_module (shared)
 authn_file_module (shared)
 authz_default_module (shared)
 authz_groupfile_module (shared)
 authz_host_module (shared)
 authz_user_module (shared)
 autoindex_module (shared)
 cgi_module (shared)
 deflate_module (shared)
 dir_module (shared)
 env_module (shared)
 mime_module (shared)
 negotiation_module (shared)
 php5_module (shared)
 rewrite_module (shared)
 setenvif_module (shared)
 status_module (shared)
 wsgi_module (shared)
Syntax OK
```

At this point, according to the thread listed above, I should be able to load up a test.wsgi document with the following contents:

```
def application(evinron, start_response): status = '200 OK' output = 'Hello World!'
response_headers = [('Content-type', 'text/plain'),
                    ('Content-Length', str(len(output)))]
start_response(status, response_headers)
return [output]
```

But instead of displaying 'Hello World!' I get a 500 Internal Server Error:

```
The server encountered an internal error or misconfiguration and was unable to complete your request.
```

The apache2 error log has this to say:

```
[Fri Apr 23 16:56:33 2010] [error] [client 154.5.37.221] mod_wsgi (pid=31027): Target WSGI script '/path/to/myapp.wsgi' cannot be loaded as Python module.
[Fri Apr 23 16:56:33 2010] [error] [client 154.5.37.221] mod_wsgi (pid=31027): Exception occurred processing WSGI script '/path/to/myapp.wsgi'.
[Fri Apr 23 16:56:33 2010] [error] [client 154.5.37.221] Traceback (most recent call last):
[Fri Apr 23 16:56:33 2010] [error] [client 154.5.37.221]   File "/path/to/myapp.wsgi", line 8, in <module>
[Fri Apr 23 16:56:33 2010] [error] [client 154.5.37.221]     import django.core.handlers.wsgi
[Fri Apr 23 16:56:33 2010] [error] [client 154.5.37.221] ImportError: No module named django.core.handlers.wsgi
```

Can anyone tell me what I'm missing? I've scoured the web and the only thread I can find where someone is able to get mod_wsgi working, the solution was to pave ubuntu and use debian instead.. There must be a proper solution to get mod_wsgi working in ubuntu!

---

### Post by coolesting on 2011-06-29
I got the same problem, anyone help ..:p

---

