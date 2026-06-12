---
title: "vhosts query"
date: 2011-09-10
forum: Server Platforms
---

### Post by spiffed on 2011-09-10
Hi

Recently installed Jira server on ubuntu running on port 9090 over at Amazon EC2 on an Ubuntu instance. Installed the apache2 server and it works fine.

Then I pointed the domain name trinedev.com to the IP address of Amazon EC2 using A records.

Now what I need is when my users enter jira.trinedev.com it should open up my Jira page running at [www.trinedev.com:9090](www.trinedev.com:9090)

I looked around on Jira forums and couldnt find much support.

What I did so far is :
ports.conf :
NameVirtualHost *:80
Listen 80

trinedev.com in sites-enabled :
LoadModule proxy_module /usr/lib/apache2/modules/mod_proxy.so
LoadModule proxy_http_module /usr/lib/apache2/modules/mod_proxy_http.so


<VirtualHost *:80>
    ServerName wiki.trinedev.com
     ProxyPass / [http://wiki.trinedev.com:9080/](http://wiki.trinedev.com:9080/)
    ProxyPassReverse / [http://wiki.trinedev.com:9080/](http://wiki.trinedev.com:9080/)

</VirtualHost>
<VirtualHost *:80>
    ServerName jira.trinedev.com
    ProxyPass / [http://jira.trinedev.com:9090/](http://jira.trinedev.com:9090/)
    ProxyPassReverse / [http://jira.trinedev.com:9090/](http://jira.trinedev.com:9090/)

</VirtualHost>


Am I missing a step here ? Do I need to add anymore A/CNAME records ?

---

### Post by spiffed on 2011-09-10
Help!

---

### Post by volkswagner on 2011-09-10
I am not understanding what you are asking.

Please ask a direct question.

It appears your proxy pass is working for wiki but not jira subdomain.

Is your goal to get the url rewritten?  

Do you have plans to host sites on Apache2?

Do you plan to use [www.trinedev.com:80](www.trinedev.com:80) and [www.trinedev.com:9090](www.trinedev.com:9090) as different content sites?  Apache2 on port 80 and jira on 9090?

Instead of:
```
ProxyPass / http://wiki.trinedev.com:9080/
ProxyPassReverse / http://wiki.trinedev.com:9080/

```


You can use:
```
ProxyPass / http://127.0.0.1:9080/
ProxyPassReverse / http://127.0.0.1:9080/

```

If you are not ready to host sites on apache and want all traffic to go to [http://jira.trinedev.com:9090/](http://jira.trinedev.com:9090/)

Then change the servername in host file to your www, and add aliases as follows:

```
</VirtualHost>
<VirtualHost *:80>
ServerName trinedev.com
ServerAlias www.trinedev.com jira.trinedev.com
ProxyPass / http://127.0.0.1:9090/
ProxyPassReverse / http://127.0.0.1:9090/

</VirtualHost>
```

---

