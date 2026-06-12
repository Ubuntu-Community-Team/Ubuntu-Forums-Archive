---
title: "Trying to setup a forum using SMF"
date: 2010-06-24
forum: Server Platforms
---

### Post by JohnElway on 2010-06-24
I'm trying to setup an SMF forum on a server running Ubuntu Hardy. The problem is that the website on the server was built using Django. So considering that Django uses Python and SMF uses PHP, would it be possible for both of these to coexist on the same server? If so, how?  If this can't be done, I'm more than willing to rebuild the website in PHP. If I were to do this, then what do I need to do to reconfigure Apache? As of right now it's using mod_wsgi, but I'm assuming I would need mod_php. How would I set this up?

---

### Post by cdenley on 2010-06-24
> **JohnElway said:**
> I'm trying to setup an SMF forum on a server running Ubuntu Hardy. The problem is that the website on the server was built using Django. So considering that Django uses Python and SMF uses PHP, would it be possible for both of these to coexist on the same server? If so, how?  If this can't be done, I'm more than willing to rebuild the website in PHP. If I were to do this, then what do I need to do to reconfigure Apache? As of right now it's using mod_wsgi, but I'm assuming I would need mod_php. How would I set this up?

I never tried, but you should be able to run both the wsgi and php5 modules.
```

sudo apt-get install libapache2-mod-php5 libapache2-mod-wsgi
sudo a2enmod php5
sudo a2enmod mod-wsgi
sudo /etc/init.d/apache2 restart

```

---

### Post by JohnElway on 2010-06-24
I entered all the commands with no errors, but when I go to the website I get a "Unable to connect" message.

---

### Post by cdenley on 2010-06-24
> **JohnElway said:**
> I entered all the commands with no errors, but when I go to the website I get a "Unable to connect" message.

What kind of "unable to connect" message? Are you getting a response from the server? How are you attempting to connect? What domain or IP are you using?

---

### Post by JohnElway on 2010-06-24
I'm just trying to visit the website through a web browser. The url is [www.royaltechnique.com](www.royaltechnique.com).

---

### Post by cdenley on 2010-06-24
Is apache running and listening on port 80?
```

sudo netstat -tlnp

```

Do you have any firewall rules?
```

sudo iptables -L -n

```

Does the domain resolve to the correct IP address?
```

getent hosts www.royaltechnique.com
wget -q -O - http://whatismyip.org/ && echo

```

Is there a router or hardware firewall between your server and the internet? If so, is it configured to forward or allow traffic on TCP/80 to our server?

Can you connect using the server's LAN address or local loopback address?
```

nc -z -v -w 4 127.0.0.1 80

```

---

### Post by JohnElway on 2010-06-24
The code is looking weird when I try to copy-paste here in the forum so I just attached a pdf which displays the output I got for some of the commands. I tried the getent command which did return the correct ip address. I was a little confused by what url I'm supposed to enter for the wget command. If I actually enter my ip address plus a '.org' then it returns some random HTML source. If I enter my ip address plus a '.com' or I enter 'www.royaltechnique.com', then nothing is returned.

---

### Post by cdenley on 2010-06-25
You don't have apache or anything listening on port 80? Did you install apache? If you didn't have it installed already, it should have been installed as a dependency when you installed the apache modules. Did it fail to start?
```

sudo /etc/init.d/apache2 restart

```

Also, when posting output, you should use "CODE" tags.
[NOPARSE]
```

output goes here

```
[/NOPARSE]

---

### Post by JohnElway on 2010-06-25
I know that I have apache installed. When I first tried to restart I got the following message:  ```
 httpd (no pid file) not running 
```  But when I tried it again it worked. Now when I go to [www.royaltechnique.com](www.royaltechnique.com), I get a 500 internal server error message.

---

### Post by cdenley on 2010-06-25
```

tail /var/log/apache2/error.log

```

---

### Post by JohnElway on 2010-06-25
Sorry the code is looking weird even if I use the code tags.

---

### Post by cdenley on 2010-06-25
Run the command immediately after you get a 500 error. Otherwise, we can't the message related to your 500 error, since that command only lists the last 10 lines in the log.

---

### Post by JohnElway on 2010-06-25
Ok here it is.

---

### Post by cdenley on 2010-06-25
I still don't see anything related to your 500 error, and I'm pretty sure something would get logged there whenever apache gives a 500 response. Are you sure your are visiting your server, and the vhost is using that error log?
```

echo -e "GET / HTTP/1.0\nHost: www.royaltechnique.com\n"|nc 127.0.0.1 80
tail /var/log/apache2/access.log
tail /var/log/apache2/error.log

```

---

### Post by JohnElway on 2010-06-26
echo -e "GET / HTTP/1.0\nHost: www.royaltechnique.com\n"|nc 127.0.0.1 80

```
HTTP/1.1 500 Internal Server Error
Date: Sat, 26 Jun 2010 13:27:38 GMT
Server: Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.10 with Suhosin-Patch mod_wsgi/1.3 Python/2.5.2
Content-Length: 702
Connection: close
Content-Type: text/html; charset=iso-8859-1
X-Pad: avoid browser bug

<!DOCTYPE HTML PUBLIC "-//IETF//DTD HTML 2.0//EN">
<html><head>
<title>500 Internal Server Error</title>
</head><body>
<h1>Internal Server Error</h1>
<p>The server encountered an internal error or
misconfiguration and was unable to complete
your request.</p>
<p>Please contact the server administrator,
 webmaster@royaltechnique.com and inform them of the time the error occurred,
and anything you might have done that may have
caused the error.</p>
<p>More information about this error may be available
in the server error log.</p>
<hr>
<address>Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.10 with Suhosin-Patch mod_wsgi/1.3 Python/2.5.2 Server at www.royaltechnique.com Port 80</address>
</body></html>

```


sudo tail /var/log/apache2/error.log

```
[Fri Jun 25 23:29:51 2010] [error] [client 75.126.3.242] client sent HTTP/1.1 request without hostname (see RFC2616 section 14.23): /w00tw00t.at.ISC.SANS.test0:)
[Sat Jun 26 00:53:26 2010] [error] [client 187.45.224.218] client sent HTTP/1.1 request without hostname (see RFC2616 section 14.23): /w00tw00t.at.ISC.SANS.DFind:)
[Sat Jun 26 03:05:34 2010] [error] [client 187.45.224.218] client sent HTTP/1.1 request without hostname (see RFC2616 section 14.23): /w00tw00t.at.ISC.SANS.DFind:)
[Sat Jun 26 05:14:27 2010] [error] [client 187.45.224.218] client sent HTTP/1.1 request without hostname (see RFC2616 section 14.23): /w00tw00t.at.ISC.SANS.DFind:)
[Sat Jun 26 05:52:13 2010] [error] [client 75.126.3.242] client sent HTTP/1.1 request without hostname (see RFC2616 section 14.23): /w00tw00t.at.ISC.SANS.test0:)
[Sat Jun 26 07:22:03 2010] [error] [client 187.45.224.218] client sent HTTP/1.1 request without hostname (see RFC2616 section 14.23): /w00tw00t.at.ISC.SANS.DFind:)
[Sat Jun 26 09:32:59 2010] [error] [client 187.45.224.218] client sent HTTP/1.1 request without hostname (see RFC2616 section 14.23): /w00tw00t.at.ISC.SANS.DFind:)
[Sat Jun 26 10:42:17 2010] [error] [client 74.63.218.250] client sent HTTP/1.1 request without hostname (see RFC2616 section 14.23): /w00tw00t.at.ISC.SANS.DFind:)
[Sat Jun 26 11:39:39 2010] [error] [client 187.45.224.218] client sent HTTP/1.1 request without hostname (see RFC2616 section 14.23): /w00tw00t.at.ISC.SANS.DFind:)
[Sat Jun 26 11:58:22 2010] [error] [client 75.126.3.242] client sent HTTP/1.1 request without hostname (see RFC2616 section 14.23): /w00tw00t.at.ISC.SANS.test0:)

```

I didn't get any output for access.log.

---

### Post by cdenley on 2010-06-26
You must not be using the default vhost configuration for the hostname you are using. Where did you configure it to log?
```

sudo cat /etc/apache2/sites-enabled/*

```

---

### Post by JohnElway on 2010-06-26
Not sure if I'm using the default logging setup.

```
<VirtualHost *:80>
    ServerAdmin webmaster@localhost
    
    DocumentRoot /var/www/
    <Directory />
        Options FollowSymLinks
        AllowOverride None
    </Directory>
    <Directory /var/www/>
        Options Indexes FollowSymLinks MultiViews
        AllowOverride None
        Order allow,deny
        allow from all
    </Directory>

    ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
    <Directory "/usr/lib/cgi-bin">
        AllowOverride None
        Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
        Order allow,deny
        Allow from all
    </Directory>

    ErrorLog /var/log/apache2/error.log

    # Possible values include: debug, info, notice, warn, error, crit,
    # alert, emerg.
    LogLevel warn

    CustomLog /var/log/apache2/access.log combined
    ServerSignature On

    Alias /doc/ "/usr/share/doc/"
    <Directory "/usr/share/doc/">
        Options Indexes MultiViews FollowSymLinks
        AllowOverride None
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>

</VirtualHost>
# Place any notes or comments you have here
# It will make any customisation easier to understand in the weeks to come

# domain: royaltechnique.com
# public: /home/admin/public_html/royaltechnique.com/

<VirtualHost *:80>

  # Admin email, Server Name (domain name) and any aliases
  ServerAdmin webmaster@royaltechnique.com
  ServerName  www.royaltechnique.com
  WSGIScriptAlias / /home/admin/public_html/royaltechnique.com/royalTechnique.wsgi
  


  # Index file and Document Root (where the public files are located)
  DirectoryIndex index.html
  DocumentRoot /home/admin/public_html/royaltechnique.com/public


  # Custom log file locations
  LogLevel warn
  ErrorLog  /home/admin/public_html/royaltechnique.com/log/error.log
  CustomLog /home/admin/public_html/royaltechnique.com/log/access.log combined

</VirtualHost>

<VirtualHost *:80>
  ServerName royaltechnique.com
  Redirect permanent / http://www.royaltechnique.com/
</VirtualHost>

```

---

### Post by cdenley on 2010-06-26
```

echo -e "GET / HTTP/1.0\nHost: www.royaltechnique.com\n"|nc 127.0.0.1 80
sudo tail /home/admin/public_html/royaltechnique.com/log/access.log
sudo tail /home/admin/public_html/royaltechnique.com/log/error.log

```

---

### Post by JohnElway on 2010-06-26
echo -e "GET / HTTP/1.0\nHost: www.royaltechnique.com\n"|nc 127.0.0.1 80
```
HTTP/1.1 500 Internal Server Error
Date: Sun, 27 Jun 2010 03:00:38 GMT
Server: Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.10 with Suhosin-Patch mod_wsgi/1.3 Python/2.5.2
Content-Length: 702
Connection: close
Content-Type: text/html; charset=iso-8859-1
X-Pad: avoid browser bug

<!DOCTYPE HTML PUBLIC "-//IETF//DTD HTML 2.0//EN">
<html><head>
<title>500 Internal Server Error</title>
</head><body>
<h1>Internal Server Error</h1>
<p>The server encountered an internal error or
misconfiguration and was unable to complete
your request.</p>
<p>Please contact the server administrator,
 webmaster@royaltechnique.com and inform them of the time the error occurred,
and anything you might have done that may have
caused the error.</p>
<p>More information about this error may be available
in the server error log.</p>
<hr>
<address>Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.10 with Suhosin-Patch mod_wsgi/1.3 Python/2.5.2 Server at www.royaltechnique.com Port 80</address>
</body></html>

```

sudo tail /home/admin/public_html/royaltechnique.com/log/access.log 
```
212.159.16.237 - - [26/Jun/2010:18:03:28 +0000] "GET / HTTP/1.1" 500 702 "-" "Mozilla/5.0 (X11; U; Linux i686; en-US) AppleWebKit/533.4 (KHTML, like Gecko) Chrome/5.0.375.70 Safari/533.4"
212.159.16.237 - - [26/Jun/2010:18:03:28 +0000] "GET /favicon.ico HTTP/1.1" 500 702 "-" "Mozilla/5.0 (X11; U; Linux i686; en-US) AppleWebKit/533.4 (KHTML, like Gecko) Chrome/5.0.375.70 Safari/533.4"
119.63.198.36 - - [26/Jun/2010:22:15:38 +0000] "GET /robots.txt HTTP/1.1" 500 702 "-" "Baiduspider+(+http://www.baidu.com/search/spider.htm)"
220.181.94.237 - - [27/Jun/2010:00:32:39 +0000] "GET /robots.txt HTTP/1.1" 500 702 "-" "-"
220.181.7.37 - - [27/Jun/2010:01:38:31 +0000] "GET /robots.txt HTTP/1.1" 500 702 "-" "Baiduspider+(+http://www.baidu.com/search/spider.htm)"
127.0.0.1 - - [27/Jun/2010:02:58:56 +0000] "GET / HTTP/1.0" 500 702 "-" "-"
76.168.142.57 - - [27/Jun/2010:03:00:30 +0000] "GET / HTTP/1.1" 500 702 "-" "Mozilla/5.0 (X11; U; Linux x86_64; en-US; rv:1.9.2.3) Gecko/20100423 Ubuntu/10.04 (lucid) Firefox/3.6.3"
76.168.142.57 - - [27/Jun/2010:03:00:31 +0000] "GET /favicon.ico HTTP/1.1" 500 702 "-" "Mozilla/5.0 (X11; U; Linux x86_64; en-US; rv:1.9.2.3) Gecko/20100423 Ubuntu/10.04 (lucid) Firefox/3.6.3"
76.168.142.57 - - [27/Jun/2010:03:00:34 +0000] "GET /favicon.ico HTTP/1.1" 500 702 "-" "Mozilla/5.0 (X11; U; Linux x86_64; en-US; rv:1.9.2.3) Gecko/20100423 Ubuntu/10.04 (lucid) Firefox/3.6.3"
127.0.0.1 - - [27/Jun/2010:03:00:38 +0000] "GET / HTTP/1.0" 500 702 "-" "-"

```

sudo tail /home/admin/public_html/royaltechnique.com/log/error.log 
```
[Sun Jun 27 03:00:38 2010] [error] [client 127.0.0.1]     set_script_prefix(base.get_script_name(environ))
[Sun Jun 27 03:00:38 2010] [error] [client 127.0.0.1]   File "/usr/lib/python2.5/site-packages/django/core/handlers/base.py", line 186, in get_script_name
[Sun Jun 27 03:00:38 2010] [error] [client 127.0.0.1]     if settings.FORCE_SCRIPT_NAME is not None:
[Sun Jun 27 03:00:38 2010] [error] [client 127.0.0.1]   File "/usr/lib/python2.5/site-packages/django/conf/__init__.py", line 28, in __getattr__
[Sun Jun 27 03:00:38 2010] [error] [client 127.0.0.1]     self._import_settings()
[Sun Jun 27 03:00:38 2010] [error] [client 127.0.0.1]   File "/usr/lib/python2.5/site-packages/django/conf/__init__.py", line 59, in _import_settings
[Sun Jun 27 03:00:38 2010] [error] [client 127.0.0.1]     self._target = Settings(settings_module)
[Sun Jun 27 03:00:38 2010] [error] [client 127.0.0.1]   File "/usr/lib/python2.5/site-packages/django/conf/__init__.py", line 94, in __init__
[Sun Jun 27 03:00:38 2010] [error] [client 127.0.0.1]     raise ImportError, "Could not import settings '%s' (Is it on sys.path? Does it have syntax errors?): %s" % (self.SETTINGS_MODULE, e)
[Sun Jun 27 03:00:38 2010] [error] [client 127.0.0.1] ImportError: Could not import settings 'royalTechnique.settings' (Is it on sys.path? Does it have syntax errors?): No module named royalTechnique.settings

```

In there error.log, it looks like there are some Django related problems which makes sense because I deleted my Django website files. However I still want it to be able to display a website written in PHP.

---

### Post by cdenley on 2010-06-27
With "WSGIScriptAlias" setting your root directory to royalTechnique.wsgi, how do you expect to access any php scripts with that vhost?

---

### Post by JohnElway on 2010-06-27
I have absolutely no idea. Can I reconfigure the vhost to use php or would it be easier to just make a new vhost?

---

### Post by cdenley on 2010-06-28
> **JohnElway said:**
> I have absolutely no idea. Can I reconfigure the vhost to use php or would it be easier to just make a new vhost?

Take out (or comment out) that line.

---

