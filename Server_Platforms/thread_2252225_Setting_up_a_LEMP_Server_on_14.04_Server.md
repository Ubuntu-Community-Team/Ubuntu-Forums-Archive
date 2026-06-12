---
title: "Setting up a LEMP Server on 14.04 Server"
date: 2014-11-10
forum: Server Platforms
---

### Post by Enforcer83 on 2014-11-10
Hello all. I have been trying to setup a Linux Nginx (pronounced Engine-X) MySQL PHP (LEMP) server as a test platform in preparation of doing so in a production setup for my wife's home buisness. I have a machine with limited resources (I will post exact hardware specs later since I am at work right now); Dual core CPU, approx. 4GB RAM, but harddrive space is no issue >2TB. I am currently dual booting Windows/Ubuntu until I get this all setup. I had seen reviews that Nginx was better for resource limited applications.

I have been following a Guide on how to setup a LEMP stack for 12.04 from ARS Technica. I started by following the guide located at [http://arstechnica.com/gadgets/2012/11/how-to-set-up-a-safe-and-secure-web-server/](http://arstechnica.com/gadgets/2012/11/how-to-set-up-a-safe-and-secure-web-server/). Everything worked fine. I skipped the SSL/TLS guide, for now until I got a production server with its own domain name, and went right to the PHP guide located at [http://arstechnica.com/information-technology/2012/12/web-served-part-3-bolting-on-php-with-php-fpm/](http://arstechnica.com/information-technology/2012/12/web-served-part-3-bolting-on-php-with-php-fpm/). This is where everything breaks. PHP is running but Nginx is not. When I type the following commands I get a [[COLOR=#ff0000]fail[/COLOR]] message. FYI I noticed in the guide that there are inconsistencies in the use of "soc" and "sock" for the unix sockets. Everywhere "soc" is used, I used "sock".

```
sudo /etc/init.d/nginx restart
sudo /etc/init.d/nginx reload
```

I will provide all modified files in a seperate post when I get home as well.

Can anyone direct me on the correct configuration or provide correcting information to the guide such as improper syntax or spelling?

---

### Post by SeijiSensei on 2014-11-10
I don't use nginx, but I'll just observe that 4 GB of memory in no way constitutes a resource-limited server.  If you were running a machine in 512 MB, that's approaching memory starvation, but even then a swap file would make things work.  

I used to host web sites with Apache on a Pentium box in 512M.  Web hosting is a really low-demand service.  The only time I've encountered performance issues is when the application relied on a database with poor indexing.

---

### Post by irv on 2014-11-10
Why are you using Nginx. I think Apache is much better server and very easy to setup? 
[https://help.ubuntu.com/community/ApacheMySQLPHP]("https://help.ubuntu.com/community/ApacheMySQLPHP")

---

### Post by Enforcer83 on 2014-11-10
Previous stated reviews also pointed out Nginx serves files faster and to more concurrent requests than apache.

I had considered using apache until I found the reviews.

Apache is still a candidate if I can't get this to work with Nginx.

---

### Post by nerdtron on 2014-11-10
What is the error when you start/restart nginx? Soc problems I think is that it can't bind on the default port? do you have apache installed too?

Also have you looked into the logs of nginx when it fails to start? Maybe we can have clues in there.

Nginx is good for low resource servers, it's lightweight and has good response. But maybe a little harder to setup.

You can also try to use this **more updated and detailed guide**: [https://www.digitalocean.com/community/tutorials/how-to-install-linux-nginx-mysql-php-lemp-stack-on-ubuntu-14-04](https://www.digitalocean.com/community/tutorials/how-to-install-linux-nginx-mysql-php-lemp-stack-on-ubuntu-14-04)

---

### Post by Lars Noodén on 2014-11-10
I found this one for 14.04:

[https://www.digitalocean.com/community/tutorials/how-to-install-linux-nginx-mysql-php-lemp-stack-on-ubuntu-14-04](https://www.digitalocean.com/community/tutorials/how-to-install-linux-nginx-mysql-php-lemp-stack-on-ubuntu-14-04)

and to get nginx with php, all I needed to do was add nginx and php5-fpm and then adjust the nginx vhost's configuration file to allow processing. (Adjusting cgi.fix_pathinfo is probably a good idea too.)

Edit:  Oops.  Too slow!  :)

---

### Post by Enforcer83 on 2014-11-10
> **nerdtron said:**
> What is the error when you start/restart nginx? Soc problems I think is that it can't bind on the default port? do you have apache installed too?

Also have you looked into the logs of nginx when it fails to start? Maybe we can have clues in there.

found the problem.  never thought to look in the error log.  found the issue right there in the log. ](*,)  one of the # at the start was removed so it was seeing server { server {.

I am going to keep this thread open for a little while if I encounter any other issues.

Thanks everyone, so far, for the help.

---

