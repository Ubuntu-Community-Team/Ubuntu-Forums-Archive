---
title: "URL redirection problem in a reverse proxy apache2"
date: 2010-04-28
forum: Server Platforms
---

### Post by tapas_mishra on 2010-04-28
Hi,
 I have a webserver apache2 .


I want to have a few websites
[http://site1.myserver.com](http://site1.myserver.com)
[http://myserver.com](http://myserver.com)
and [http://myserver.com/site2](http://myserver.com/site2)

 I did set up a reverse proxy environment for doing this.
```

Dom0 LAN IP ----> 192.168.1.1 Gateway (where reverse proxy is set)
DomU1 LAN IP ----> 192.168.1.13 ( here myserver.com
                                   and site1.myserver.com
                                    both are hosted.)

Domu2  LAN IP ----> 192.168.1.17  myserver.com/site2 is here.
```




	Configuration on Dom0 of sites site1.myserver.com and myserver.com
 Virtual Host Configurations on Dom0
in /etc/apache2/sites-enabled/myserver.com (on gateway)
```

<VirtualHost *:80>
        ServerAdmin webmaster@localhost
        ServerName myserver.com

        ProxyRequests off
        <Proxy *>
        Order deny,allow
        Allow from all
        </Proxy>
        ProxyPass / http://192.168.1.13/
        ProxyPassReverse / http://192.168.1.13/
        ProxyPass /site2 http://192.168.1.17/
        ProxyPassReverse /site2 http://192.168.1.17/

       
</VirtualHost>

```

then /etc/apache2/sites-enabled/site1.myserver.com  (on gateway)
has
```

<VirtualHost *:80>
        ServerAdmin webmaster@localhost
        ServerName site1.myserver.com

        ProxyRequests off
        <Proxy *>
        Order deny,allow
        Allow from all
        </Proxy>
        ProxyPass / http://192.168.1.13/
        ProxyPassReverse / http://192.168.1.13/
       
       
</VirtualHost>

```



and following asci chart 

```

	On Dom0 
	sites-enabled
	  |
	  |--------------->myserver.com      (ProxyPass / to http://192.168.1.13/)      
	  |
	  |--------------->site1.myserver.com (ProxyPass / to http://192.168.1.13/)

```

and for myserver.com/site2
on Dom0 in same file I have following
```

ProxyPass /site2 192.168.1.17
ProxyPassReverse /site2 192.168.1.17

```



	On DomU (site1) 192.168.1.13 where site1.myserver.com and myserver.com are actually present.
```

	sites-enabled
	  |
	  |--------------->myserver.com      (DocumentRoot /var/www/myserver)      
	  |
	  |--------------->site1.myserver.com (DocumentRoot /var/www/site1)

```
Is this configuration wrong. 
What is happening is 
 if some one clicks on [http://myserver.com](http://myserver.com) or [http://site1.myserver.com](http://site1.myserver.com)  he sees [http://site1.myserver.com](http://site1.myserver.com)  

Which should not happen.



	Scene 2) 
	
	 If you open
	 [http://myserver.com/site2](http://myserver.com/site2)
	 Following comes 
```

	 Not Found
	  The requested URL /site2 was not found on this server.

```
	Configuration is 
```

	On Dom0 
	sites-enabled  in same file myserver.com
	  |
	  |--------------->myserver.com    (ProxyPass /site2 to http://192.168.1.17/)      
                                              (ProxyPassReverse /site2  http://192.168.1.17/)

```
	[http://myserver.com/site2](http://myserver.com/site2) is not opening.


On DomU that is 192.168.1.13  where site1.myserver.com and myserver.com are hosted 
I have 
 /etc/apache2/sites-enabled/site1.myserver.com (where it is hosted on LAN)


```

<VirtualHost *:80>
        ServerAdmin webmaster@localhost
        ServerName myserver.com
         DocumentRoot /var/www/mainsite/
        <Directory /var/www/ >
                Options FollowSymLinks
                AllowOverride None
        </Directory>
      
</VirtualHost>

```
and  /etc/apache2/sites-enabled/myserver.com  (where it is hosted on LAN)

```

<VirtualHost *:80>
        ServerAdmin webmaster@localhost
        ServerName site1.myserver.com
         DocumentRoot /var/www/site1/
        <Directory /var/www/ >
                Options FollowSymLinks
                AllowOverride None
        </Directory>
      
</VirtualHost>

```

and configuration of myserver.com/site2 on 192.168.1.17

```

<VirtualHost *:80>
        ServerAdmin webmaster@localhost
        ServerName myserver.com/site2
         DocumentRoot /var/www
        <Directory /var/www/ >
                Options FollowSymLinks
                AllowOverride None
        </Directory>
      
</VirtualHost>

```

So what should I check in?

---

### Post by cdenley on 2010-04-28
If you proxy a connection from dom0 to domu1 using [http://192.168.1.13/](http://192.168.1.13/), then you can't do name-based virtual hosting on domu1 since no hostname will be provided by dom0. Perhaps you can assign it surrogate hostnames, and create entries in /etc/hosts on dom0.

/etc/hosts
```

192.168.1.13 proxy1 proxy2

```
```

<VirtualHost *:80>
        ServerAdmin webmaster@localhost
        ServerName myserver.com

        ProxyRequests off
        <Proxy *>
        Order deny,allow
        Allow from all
        </Proxy>
        ProxyPass / http://proxy1/
        ProxyPassReverse / http://proxy1/
        ProxyPass /site2 http://192.168.1.17/
        ProxyPassReverse /site2 http://192.168.1.17/

</VirtualHost>

```
```

<VirtualHost *:80>
        ServerAdmin webmaster@localhost
        ServerName site1.myserver.com

        ProxyRequests off
        <Proxy *>
        Order deny,allow
        Allow from all
        </Proxy>
        ProxyPass / http://proxy2/
        ProxyPassReverse / http://proxy2/
</VirtualHost>

```

Then create vhosts on domu1, replacing "myserver.com" with "proxy1" and "site1.myserver.com" with "proxy2".

---

### Post by tapas_mishra on 2010-04-28
> **cdenley said:**
> Perhaps you can assign it surrogate hostnames, and create entries in /etc/hosts on dom0.

/etc/hosts
```

192.168.1.13 proxy1 proxy2


```
It exits.
> **cdenley said:**
> 
```

<VirtualHost *:80>
        ServerAdmin webmaster@localhost
        ServerName myserver.com

        ProxyRequests off
        <Proxy *>
        Order deny,allow
        Allow from all
        </Proxy>
        ProxyPass / http://proxy1/
        ProxyPassReverse / http://proxy1/
        ProxyPass /site2 http://192.168.1.17/
        ProxyPassReverse /site2 http://192.168.1.17/

</VirtualHost>

```
```

<VirtualHost *:80>
        ServerAdmin webmaster@localhost
        ServerName site1.myserver.com

        ProxyRequests off
        <Proxy *>
        Order deny,allow
        Allow from all
        </Proxy>
        ProxyPass / http://proxy2/
        ProxyPassReverse / http://proxy2/
</VirtualHost>

```

Then create vhosts on domu1, replacing "myserver.com" with "proxy1" and "site1.myserver.com" with "proxy2".

I will try and post it here.

---

### Post by cdenley on 2010-04-28
> **tapas_mishra said:**
> It exits.


I will try and post it here.

What?

---

### Post by tapas_mishra on 2010-04-29
I have found some thing which may help
apache2 when has 2 vhosts on same IP serves them in alphabetical order
that is why installation of apache2 has 000-default as a vhost
[http://articles.slicehost.com/2009/5/27/debian-lenny-apache-virtual-hosts-1](http://articles.slicehost.com/2009/5/27/debian-lenny-apache-virtual-hosts-1)


On apache2 documentation last example Using the ServerPath  directive
on following link
[http://httpd.apache.org/docs/2.0/vhosts/examples.html#page-header](http://httpd.apache.org/docs/2.0/vhosts/examples.html#page-header)

says ```
"To provide as much backward compatibility as possible we create
a primary vhost which returns a single page containing links with an
URL prefix to the name-based virtual hosts."

```

so I infer we should have one more file on DomU site1 which
separates myserver.com and site1.myserver.com vhosts although right
now there are 2 files but I think there should be one more file
since in url myserver.com and site1.myserver.com
alphabetically myserver.com is coming first and so it is being served always.
Since the gatway is forwarding both the requests to internal machine whose IP is 192.168.1.13
and when it is giving response it is by default serving the page which alphabetically is coming first so I am seeing both the websites as same pages.

Since to the gateway is forwarding both  request 
(site1.myserver.com and myserver.com )
to IP 192.168.1.13 
and apache2 on 192.168.1.13 is serving vhost requests in alphabetical order.

As an idea if I configure on internal domu1 myserver.com on a different port then it may work but I do not want to do that.
In case you feel my observation is right let me know.

---

### Post by cdenley on 2010-04-29
I already told you what your problem is! Yes, it searches for a matching vhost ServerName alphabetically by the site configuration filename, starting with 000-default. If there is no match, it serves the first (000-default). This is irrelevant since you will never have a match. As I explained earlier, when your gateway sends the request to 192.168.1.13 for the proxied connection, it doesn't provide any hostname since you're proxying to [http://192.168.1.13/](http://192.168.1.13/), so it can never match any site configuration. Proxying to [http://192.168.1.13/](http://192.168.1.13/) will give the same results as entering that URL in your browser, regardless of what hostname you use to access the proxy.

---

### Post by tapas_mishra on 2010-04-29
On Dom0 in /etc/hosts
I did
```

192.168.1.13 proxy1 proxy2

```

and Dom0 /etc/apache2/sites-enabled/myserver.com 
```

   <VirtualHost *:80>
           ServerAdmin webmaster@myserver.com
           ServerName  myserver.com
           ProxyPreserveHost On
           ProxyPass / http://proxy1
           ProxyPassReverse / http://proxy1
   </VirtualHost>


```
and
/etc/apache2/sites-enabled/site1.myserver.com 
```

   <VirtualHost *:80>
           ServerAdmin webmaster@myserver.com
           ServerName  site1.myserver.com
           ProxyPreserveHost On
           ProxyPass / http://proxy2
           ProxyPassReverse / http://proxy2
   </VirtualHost>


```
Given that proxy1 and proxy2 are same IP
and are in /etc/hosts also
```

192.168.1.13 proxy1 proxy2
``` still the pages I am getting are same they are not from different vhosts.

---

### Post by cdenley on 2010-04-29
> **tapas_mishra said:**
> still the pages I am getting are same they are not from different vhosts.

Did you configure the vhosts on 192.168.1.13 with "ServerName proxy1" and "ServerName proxy2" so 192.168.1.13 knows which vhost to serve for which hostname?

---

### Post by tapas_mishra on 2010-04-30
Finally I got every thing working.
Thanks for your help and support.

I am posting the findings of all what it made work.

The solution for above error came by adding
ServerName directive on DomU1 also adding the corresponding thing to /etc/hosts on Dom0
and in the sites-enabled where ProxyPass and ProxyPassReverse is mentioned
 
<VirtualHost *:80>    
# do not mention IP read the note below
ProxyPass              /          [http://servername](http://servername) where redirected 
ProxyPassReverse   /          [http://servername](http://servername) where redirected

</VirtualHost>


Read this note it is important
     Do not use the IP here if more than one site is on the DomU

    What happens is when you put up the IP address in Dom0 as above then the server which will recieve request will server you a vhost which is present alphabeticaly first in its sites-enabled directory.
    
     To get rid of this you need to have on your gateway or Dom0 
a DNS if you do not have then use /etc/hosts to map internal servers by name.

```

    /etc/hosts/

    192.168.1.13   abc1 abc2 
    192.168.1.17 abc3
    192.168.1.18 abc4

```    Now your Dom0 or Gateway  is aware of abc1 abc2 abc3 and abc4 are which IP internally     mapped to.Do not thing that putting abc1 and abc2 above is a mistake .

    I redirected two pages from main site to ip 192.168.1.13 internally
     the scenario is your main site itself is  on an internal machine which is accessible by a     gateway redirecting the requests to it.

    Now you have to do some home work on Dom1 at 192.168.1.13 where your sites are     hosted in the vhost configuration file write 
    ```

    ServerName abc1
    
```    and in another host write
    ```

    ServerName abc2
    
```    ServerName directive will serve the vhost request based on the servers name.
Otherwise vhosts will be served in alphabetical order.
Thanks for your help.

---

