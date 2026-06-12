---
title: "apache load balancing to directories"
date: 2013-03-12
forum: Server Platforms
---

### Post by Rpgglitchy on 2013-03-12
Hello!

I have a setup that exists out of an apache2 load balancer that balances to two webservers.
The following is my balancer setup:

<Proxy balancer://cluster>
    Allow from all
     # cluster member 1
      BalancerMember [http://172.16.100.190:80](http://172.16.100.190:80) route=1


      # cluster member 2
      BalancerMember [http://172.16.100.191:80](http://172.16.100.191:80) route=2
</Proxy>
ProxyPass /balancer-manager !
ProxyPass / balancer://cluster/ stickysession=ROUTEID

This works for my site in /var/www/
But I have multiple directories inside my /var/www  -> /var/www/site1  /var/www/site2 , ...
And I cannot figure out how to load balance to those directories.
I tried reverse proxy to the sites:

ProxyPassReverse / [http://172.16.100.190/site1](http://172.16.100.190/site1)
ProxyPassReverse / [http://172.16.100.191/site1](http://172.16.100.191/site1)

That did not work. nor did, using the servername from the site work

ProxyPassReverse / [http://site1/](http://site1/)


Is there a kind soul out there that knows the solution to this problem?

---

### Post by Rpgglitchy on 2013-03-13
bump for glory

---

### Post by Rpgglitchy on 2013-03-13
Solved it by adding:
 RewriteEngine On
        RewriteCond %{DOCUMENT_ROOT}/%{REQUEST_FILENAME} !-f
        RewriteRule ^/(.*)$ balancer://stage%{REQUEST_URI} [P,QSA,L]

still thx for trying ^^

---

