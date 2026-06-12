---
title: "Apache Virtual Hosts"
date: 2008-01-02
forum: Server Platforms
---

### Post by orgrimdoom on 2008-01-02
i have tried looking a few different guides in ubuntu forums and other sites but have run into a error I have not been able to find a explanation for.

Im trying to make 3 "virtual hosts" right now, a IP, a Domain, and a SubDomain.

first i have my IP which looks like this in /etc/apache2/site-available/myip.conf

> <VirtualHost *:80>
  ServerName XX.XXX.XX.XXX
  ServerAlias XX.XXX.XX.XXX
  DocumentRoot /var/www/
  CustomLog /var/log/apache2/XX.XXX.XX.XXX-access.log combined
  ErrorLog /var/log/apache2/XX.XXX.XX.XXX-error.log
</VirtualHost>

and the other 2 look identical except that they have different server alias's and names, and the document roots are in a different place.

my /etc/hosts looks like this

> 127.0.0.1 localhost 
127.0.1.1 jareth
XX.XXX.XX.XXX <website names>


when i boot up the server it gives me a 

>  * Restarting web server apache2                                                apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
[Wed Jan 02 21:32:45 2008] [warn] _default_ VirtualHost overlap on port 80, the first has precedence
[Wed Jan 02 21:32:45 2008] [warn] _default_ VirtualHost overlap on port 80, the first has precedence
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
[Wed Jan 02 21:32:55 2008] [warn] _default_ VirtualHost overlap on port 80, the first has precedence
[Wed Jan 02 21:32:55 2008] [warn] _default_ VirtualHost overlap on port 80, the first has precedence
                                                                         [ OK ]


and the server boots up fine, however it acts as if there are no virtualhosts and just goes to /var/www/ (b/c they cant bind on the port ><)

thanks for the help ^^

---

### Post by andol on 2008-01-03
Do you in any anywhere in your apache-conf have this line?

```
NameVirtualHost *:80
```

---

### Post by orgrimdoom on 2008-01-03
omg, i cant believe i forgot that ><

thanks ^^

---

