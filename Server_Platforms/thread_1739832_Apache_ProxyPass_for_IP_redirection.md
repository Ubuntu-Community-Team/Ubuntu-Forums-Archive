---
title: "Apache ProxyPass for IP redirection"
date: 2011-04-26
forum: Server Platforms
---

### Post by majorpay on 2011-04-26
So I am brand new to the Ubuntu Server realm and Linux in general (15 years MS development utilizing MS Servers), and so far have been able to tackle some of the most pain in the butt installs and configs ever (VMWare Server being the worst and least stable, but running good now). I have done the site search thing to find out if there were similar issues surrounding Apache and if the answers were found within those posts.
 
The issue that I am having is in utilizing Apache as a proxy server for redirecting web traffic on one external IP to multiple internal IP addresses. I have multiple virtual servers and I need apache to act as a pass through / redirection proxy for web traffic. So far, it worked for a bit, then it becomes flaky and starts failing randomly while clicking through some of my sites. The worst offender being my SharePoint site.
 
I rebooted the linux server, and when I try to access one of my pass-through sites, all I received was an error message about server difficulties and possibly too much traffic. After some time had passed, and few refreshes later, I finally received the authentication prompt from my windows web server, but this whole configuration is still unreliable. I sometimes get the password prompt several times where it does not allow me to login with my proper credentails, etc, and other times it just fails to display the page full stop. This is an externally facing SharePoint site.
 
So there's the Windows side. I also have a WordPress site that has similar issues. With WordPress it's even more odd as I have set the WP site settings to not include the directory /wordpress/ and setup my Proxy to point to the [http://xxx.xxx.xxx.xxx/wordpress/](http://xxx.xxx.xxx.xxx/wordpress/) landing. Yet on some actions (i.e. browsing themes) it decides to throw in the wordpress directory causing it to 404, and in other sections it doesn't. This actually sounds more likely a WordPress bug than a Apache bug. 
 
file: Default (from available sites):
 
```

<VirtualHost *:80>
        ServerAdmin webmaster@localhost
        <Location "/">
                Allow from all
                Order allow,deny
        </Location>
</VirtualHost>
<VirtualHost *:80>
        ServerName something.com
        ProxyPreserveHost on
        ProxyPass / [http://192.168.101.15/](http://192.168.101.15/)
        ProxyPassReverse / [http://192.168.101.15/](http://192.168.101.15/)
</VirtualHost>
<VirtualHost *:80>
        ServerName [www.something.com]("http://www.something.com")
        ProxyPreserveHost on
        ProxyPass / [http://192.168.101.15/](http://192.168.101.15/)
        ProxyPassReverse / [http://192.168.101.15/](http://192.168.101.15/)
</VirtualHost>
<VirtualHost *:80>
        ServerName dba.something.com
        ProxyPreserveHost on
        ProxyPass / [http://192.168.101.15/](http://192.168.101.15/)
        ProxyPassReverse / [http://192.168.101.15/](http://192.168.101.15/)
</VirtualHost>
<VirtualHost *:80>
        ServerName [www.somethingelse.com]("http://www.somethingelse.com")
        ProxyPreserveHost on
        ProxyPass / [http://192.168.101.156/wordpress/](http://192.168.101.156/wordpress/)
        ProxyPassReverse / [http://192.168.101.156/wordpress/](http://192.168.101.156/wordpress/)
</VirtualHost>

```
 
 
Ubuntu Server 10.10
Apache 2.2
 
Am I doing something wrong here? Is Apache even the right tool for the job, or is there a better, specialized tool for this?

---

### Post by majorpay on 2011-04-26
Here is the latest error coming from Ubuntu (the target per the proxy definition is supposed to be a Suse server):
 
```

The server is temporarily unable to service your request due to maintenance downtime or capacity problems. Please try again later.
 
Apache/2.2.16 (Ubuntu) 

```

---

### Post by majorpay on 2011-04-26
I think I've got this one under control.  For anyone with similar issues, here was my "final" fix:
 
```

<VirtualHost *:80>
        ServerAdmin [EMAIL="webmaster@localhost"]webmaster@localhost[/EMAIL]
        ProxyRequests Off 
        <Proxy *> 
          Order deny,allow 
          Allow from all 
        </Proxy> 
        <Location /> 
          Order allow,deny 
          Allow from all 
        </Location> 
</VirtualHost>
<VirtualHost *:80>
        ServerName something.com
        ProxyRequests Off 
        <Proxy *> 
          Order deny,allow 
          Allow from all 
        </Proxy> 
        <Location /> 
          Order allow,deny 
          Allow from all 
        </Location> 
        ProxyPreserveHost on
        ProxyPass / [http://192.168.101.15/](http://192.168.101.15/)
        ProxyPassReverse / [http://192.168.101.15/](http://192.168.101.15/)
</VirtualHost>
<VirtualHost *:80>
        ServerName [www.something.com]("http://www.something.com")
        ProxyRequests Off 
        <Proxy *> 
          Order deny,allow 
          Allow from all 
        </Proxy> 
        <Location /> 
          Order allow,deny 
          Allow from all 
        </Location> 
        ProxyPreserveHost on
        ProxyPass / [http://192.168.101.15/](http://192.168.101.15/)
        ProxyPassReverse / [http://192.168.101.15/](http://192.168.101.15/)
</VirtualHost>
<VirtualHost *:80>
        ServerName dba.something.com
        ProxyRequests Off 
        <Proxy *> 
          Order deny,allow 
          Allow from all 
        </Proxy> 
        <Location /> 
          Order allow,deny 
          Allow from all 
        </Location> 
        ProxyPreserveHost on
        ProxyPass / [http://192.168.101.15/](http://192.168.101.15/)
        ProxyPassReverse / [http://192.168.101.15/](http://192.168.101.15/)
</VirtualHost>
<VirtualHost *:80>
        ServerName [www.somethingelse.com]("http://www.somethingelse.com")
        ProxyRequests Off 
        <Proxy *> 
          Order deny,allow 
          Allow from all 
        </Proxy> 
        <Location /> 
          Order allow,deny 
          Allow from all 
        </Location> 
        ProxyPreserveHost on
        ProxyPass / [http://192.168.101.156/wordpress/](http://192.168.101.156/wordpress/)
        ProxyPassReverse / [http://192.168.101.156/wordpress/](http://192.168.101.156/wordpress/)
</VirtualHost>
```

---

