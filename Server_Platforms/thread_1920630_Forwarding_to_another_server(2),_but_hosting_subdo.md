---
title: "Forwarding to another server(2), but hosting subdomain on this server(1)"
date: 2012-02-05
forum: Server Platforms
---

### Post by siXor on 2012-02-05
Hi!

I've recently made forwarding everything with my domainname example.com to my secondary server 192.168.0.2. Now I have enabled a subdomain for example.com that is files.example.com that I want server 1 (192.168.0.1) to handle. But now, the problem being, is that all traffic with example.com seems to redirect to 192.168.0.2

This is the guide I followed: [http://www.sematopia.com/2007/09/apache-forwarding-requests-to-another-server/](http://www.sematopia.com/2007/09/apache-forwarding-requests-to-another-server/)

So here are my settings:
Virtual host **example.com**: 
```
<VirtualHost *>
   ServerName www.example.com
   # RewriteLog "/var/log/apache2/rewrite.log"
   # RewriteLogLevel 9
   RewriteEngine     On
   RewriteRule       ^(.*)$        http://example.com$1  [P]
   ServerAlias example.com
</VirtualHost>
```

Virtual host **files.example.com**:
```
<VirtualHost *>
   ServerName www.files.example.com
   DocumentRoot /var/www/owncloud/
   ServerAlias files.example.com
</VirtualHost>
```

My hosts file
```
127.0.0.1       localhost
192.168.0.2     example.com
192.168.0.2     www.example.com
127.0.0.1       files.example.com
127.0.0.1       www.files.example.com
```

Just to clarify. example.com is on server2(192.168.0.2) and **files.example.com** on server1(192.168.0.1). The problem is that when I connect to **files.example.com** I get redirected to server2 which should only be for example.com. How can I make this going the way I want?
Thanks in advanced :)

---

### Post by volkswagner on 2012-02-05
> **siXor said:**
> Hi!

I've recently made forwarding everything with my domainname example.com to my secondary server 192.168.0.2. Now I have enabled a subdomain for example.com that is files.example.com that I want server 1 (192.168.0.1) to handle. But now, the problem being, is that all traffic with example.com seems to redirect to 192.168.0.2

This is the guide I followed: [http://www.sematopia.com/2007/09/apache-forwarding-requests-to-another-server/](http://www.sematopia.com/2007/09/apache-forwarding-requests-to-another-server/)

So here are my settings:
Virtual host **example.com**: 
```
<VirtualHost *>
   ServerName www.example.com
   # RewriteLog "/var/log/apache2/rewrite.log"
   # RewriteLogLevel 9
   RewriteEngine     On
   RewriteRule       ^(.*)$        http://example.com$1  [P]
   ServerAlias example.com
</VirtualHost>
```

Virtual host **files.example.com**:
```
<VirtualHost *>
   ServerName www.files.example.com
   DocumentRoot /var/www/owncloud/
   ServerAlias files.example.com
</VirtualHost>
```

My hosts file
```
127.0.0.1       localhost
192.168.0.2     example.com
192.168.0.2     www.example.com
127.0.0.1       files.example.com
127.0.0.1       www.files.example.com
```




You don't want to use rewrite here.  You need to setup mod_proxy.

> **siXor said:**
> 

Just to clarify. example.com is on server2(192.168.0.2) and **files.example.com** on server1(192.168.0.1). The problem is that when I connect to **files.example.com** I get redirected to server2 which should only be for example.com. How can I make this going the way I want?
Thanks in advanced :)


This is because rewrite is not appropriate.

Is either server open to the world?  Have you opened port 80 on your router to server1 or server2?  This will determine which server will be your reverse_proxy machine.

---

### Post by volkswagner on 2012-02-05
I just created a small [how-to]("http://ubuntuforums.org/showthread.php?t=1920715")...

I hope it works well for you.

---

### Post by siXor on 2012-02-05
> **volkswagner said:**
> I just created a small [how-to]("http://ubuntuforums.org/showthread.php?t=1920715")...

I hope it works well for you.
Sorry for not telling before, but I allready have. If I wouldn't have set up mod_proxy then I wouldn't have been directed to 192.168.0.2 in the first place. Sorry for not letting you know. 
This is my proxy.conf file:
```
<IfModule mod_proxy.c>
        #turning ProxyRequests on and allowing proxying from all may allow
        #spammers to use your proxy to send email.

        ProxyRequests Off

        <Proxy *>
                AddDefaultCharset off
                Order deny,allow
                Deny from all
                #Allow from .example.com
        </Proxy>

        <Proxy http://example.com>
                Order deny,allow
                Deny from all
                Allow from all
        </Proxy>

        <Proxy https://example.com>
                Order deny,allow
                Deny from all
                Allow from all
        </Proxy>

        # Enable/disable the handling of HTTP/1.1 "Via:" headers.
        # ("Full" adds the server version; "Block" removes all outgoing Via: headers)
        # Set to one of: Off | On | Full | Block

        ProxyVia On
</IfModule>
```

---

### Post by volkswagner on 2012-02-05
I am not versed enough in rewrite rules/conditions and your method of proxy.

I does seem to me that you have over complicated your setup.

With the method of  proxy I have shown, there is no need for rewrite rules.  If you want rewrite, they can be done on the server hosting the site.

I just don't see how your proxy rule works.... Sorry.

Perhaps someone more experienced can chime in.

---

### Post by siXor on 2012-02-06
> **volkswagner said:**
> I am not versed enough in rewrite rules/conditions and your method of proxy.

I does seem to me that you have over complicated your setup.

With the method of  proxy I have shown, there is no need for rewrite rules.  If you want rewrite, they can be done on the server hosting the site.

I just don't see how your proxy rule works.... Sorry.

Perhaps someone more experienced can chime in.
Sorry, but this won't work at all.
> [SIZE="4"]**Forbidden**[/SIZE]

You don't have permission to access / on this server.

Apache/2.2.14 (Ubuntu) Server at files.2advanced.nu Port 80

*These are my configurations at the moment:*

The following should be forwarded to Server2 but it doesn't seem to work:
```
<VirtualHost *>
        ServerName www.example.com
        ServerAlias     example.com
        ServerAdmin     webmaster@example.com
        ProxyPass / http://192.168.0.2/
        ProxyPassReverse / http://192.168.0.2/
</VirtualHost>
```

The following is the VirtualHost for OwnCloud on server1 (same error message):
```
<VirtualHost *>
        ServerName www.files.example.com
        ServerAlias     files.example.com
        ServerAdmin     webmaster@2example.com
        DocumentRoot    /var/www/owncloud/
</VirtualHost>
```

And finally this is my proxy.conf file:
```
<IfModule mod_proxy.c>
        #turning ProxyRequests on and allowing proxying from all may allow
        #spammers to use your proxy to send email.

        ProxyRequests Off

        <Proxy *>
                AddDefaultCharset off
                Order deny,allow
                Deny from all
        </Proxy>
        # Enable/disable the handling of HTTP/1.1 "Via:" headers.
        # ("Full" adds the server version; "Block" removes all outgoing Via: he$
        # Set to one of: Off | On | Full | Block

        ProxyVia On
</IfModule>
```

What am I doing wrong?

Edit: Ooh, there must be something wrong with the proxy settings. When I dissabled example.com, then OwnCloud worked just fine on files.example.com **and** on example.com. Why would it work on example.com when I specified the servername and alias? Is this because I've set the virtualhost as "<VirtualHost *>" ?
Althought, when changing this to "<VirtualHost files.example.com:80>" I get the error message Not Found on server: "The requested URL / was not found on this server.". This is complicated, and frustrating. Why the h*ll won't it work? I feel like I'm the only one having these strange problems.
Thanks in advanced for solving my problem :)

---

### Post by volkswagner on 2012-02-06
The reason for the forbidden error..

```
<VirtualHost *>
        ServerName www.example.com
        ServerAlias     example.com
        ServerAdmin     webmaster@example.com
        ProxyPass / http://192.168.0.2/
        ProxyPassReverse / http://192.168.0.2/
</VirtualHost>
```


You are missing <location> allow from directive:

Should be.

```
 
<VirtualHost *>
        ServerName www.example.com
        ServerAlias     example.com
        ServerAdmin     webmaster@example.com
<location />
          allow from all
    </location>
ProxyPass / http://192.168.0.2/
        ProxyPassReverse / http://192.168.0.2/

```

Of course you can restrict the allow to just your network or whatever you like.

---

### Post by siXor on 2012-02-07
> **volkswagner said:**
> The reason for the forbidden error..

```
<VirtualHost *>
        ServerName www.example.com
        ServerAlias     example.com
        ServerAdmin     webmaster@example.com
        ProxyPass / http://192.168.0.2/
        ProxyPassReverse / http://192.168.0.2/
</VirtualHost>
```


You are missing <location> allow from directive:

Should be.

```
 
<VirtualHost *>
        ServerName www.example.com
        ServerAlias     example.com
        ServerAdmin     webmaster@example.com
<location />
          allow from all
    </location>
ProxyPass / http://192.168.0.2/
        ProxyPassReverse / http://192.168.0.2/

```

Of course you can restrict the allow to just your network or whatever you like.

Awsome, a thousands thank you for this solution. Everything works as it should now. Can't thank you enough :) :) :) :)

Mod can close this thread.

---

### Post by volkswagner on 2012-02-07
Glad it worked.

Mods don't really close threads.  It is best if you could mark it as solved using the thread tools at the top of your thread,

---

