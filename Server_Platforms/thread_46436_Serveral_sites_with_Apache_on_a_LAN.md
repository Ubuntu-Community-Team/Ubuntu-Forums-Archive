---
title: "Serveral sites with Apache on a LAN"
date: 2005-07-04
forum: Server Platforms
---

### Post by DrQuincy on 2005-07-04
Hi

I want to be able to run several websites on my home LAN on a single machine with Ubuntu on; I am using Apache as the web server.

I was going to run the sites through different ports like:

[http://192.168.1.101:8000/](http://192.168.1.101:8000/)  would be [http://site1/](http://site1/)
[http://192.168.1.101:8001/](http://192.168.1.101:8001/)  would be [http://site2/](http://site2/)
[http://192.168.1.101:8002/](http://192.168.1.101:8002/)  would be [http://site3/](http://site3/)

This works if I specify the port number and the IP address on any machine in the LAN if I do something like this in the httd.conf file:

Listen 8000

NameVirtualHost 192.168.1.101:8000
NameVirtualHost 127.0.0.1:8000

 <VirtualHost 192.168.1.101:8000>
  ServerName site1
 DocumentRoot /var/www/site1
  </VirtualHost>

 <VirtualHost 127.0.0.1:8000>
  ServerName site1
 DocumentRoot /var/www/site1
  </VirtualHost>

... for each of the sites I want to host locally.

I cannot get them to run by their respective server names though (so on any machine on the network [http://192.168.1.101:8000/](http://192.168.1.101:8000/) will work but [http://site1/](http://site1/) won't).  I tried mapping the names in the /etc/hosts file; I am VERY new to this and I read that host files cannot handle port numbers other than the default (80 in this case).  So my question is, is there a workaround for this?  I would much rather that on my LAN I can use names rather than IP addresses and port numbers.

Many thanks.

---

### Post by LordHunter317 on 2005-07-05
You can't use seperate ports and not have to specify the port everytime.

HTTP runs over port 80.  If you don't specify a port, port 80 is assumed. 

You want to do name-based virtualhosting, which is where the client sends the name of the site they want to talk to with the connection.  This allows Apache to redirect to the correct site.

To make this work, you will need working DNS with entries for each site on your LAN, accessible by both the servers and clients.

---

### Post by mcaibad2 on 2005-07-05
Hi,

I had the same question myself. You need DNS server like BIND9. I can't understand how to set this up though... Try editing /etc/hosts to check apache configuration by adding the following:

192.168.1.101 site1
127.0.0.1 site2

If you try [www.site1](www.site1) and [www.site2](www.site2) on your machine everything should work. I repeat this should work only on your machine for testing purposes.

---

### Post by LordHunter317 on 2005-07-05
Actually, just site1 and site2 would work.

---

### Post by DrQuincy on 2005-07-05
Thanks for your replies.


How come on the Apache site it says:

> You have multiple domains going to the same IP and also want to serve multiple ports. By defining the ports in the "NameVirtualHost" tag, you can allow this to work. If you try using <VirtualHost name:port> without the NameVirtualHost name:port or you try to use the Listen directive, your configuration will not work.

Server configuration
Listen 80
Listen 8080

NameVirtualHost 172.20.30.40:80
NameVirtualHost 172.20.30.40:8080

<VirtualHost 172.20.30.40:80>

ServerName [www.example1.com](www.example1.com)
DocumentRoot /www/domain-80

</VirtualHost>

<VirtualHost 172.20.30.40:8080>

ServerName [www.example1.com](www.example1.com)
DocumentRoot /www/domain-8080

</VirtualHost>

<VirtualHost 172.20.30.40:80>

ServerName [www.example2.org](www.example2.org)
DocumentRoot /www/otherdomain-80

</VirtualHost>

<VirtualHost 172.20.30.40:8080>

ServerName [www.example2.org](www.example2.org)
DocumentRoot /www/otherdomain-8080

</VirtualHost>  

What exactly does this do? It seems to suggest you can use a single IP address and put each site through a different port.

I think I know what do now; I should send each site through port 80 and to the same IP address in httd.conf and then send each site to the IP address in each client's hosts file send them to the IP address and let Apache do the rest.  Anyway, I willl try it tonigt when I get home.

Thanks.

---

### Post by LordHunter317 on 2005-07-05
> **DrQuincy]What exactly does this do? It seems to suggest you can use a single IP address and put each site through a different port.[/quote]You can.

You can run Apache on any port you want.  And you can do name-based virtual hosting on as many ports and IP addresses as you want.

However, here's the thing.  By standard, it's assumed that a HTTP server runs on port 80.  Not 8080, not 10000, not anything but 80.

So, if you put in 'www.example.com' into your browser, it will connect to the site hosting [www.example.com](www.example.com) on port 80.  And the **only** way to override this is to have the client explictly specify the port: 'www.example.com:8080'.  There's nothing you can do on your server to change this behavior, it's just how the Internet works.

Just because Apache lets you do it doesn't mean it'll help you.

[quote]I think I know what do now said:**
> Correct.

[quote] and then send each site to the IP address in each client's hosts file send them to the IP address and let Apache do the rest.Not sure what you mean here.  If you mean provide a host entry for each site in your clients' host files, then yes, this will work.  However, you'd likely be better off setting up DNS.

---

