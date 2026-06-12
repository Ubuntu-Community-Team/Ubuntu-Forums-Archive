---
title: "Adding multiple websites to my vhost"
date: 2010-07-15
forum: Server Platforms
---

### Post by Emascu on 2010-07-15
Hello

I'm setting up a server on Ubuntu 10.04 for development. It all seems to work nicely, I just have one thing that's bugging me.
I have a project in /var/www/portfolio, which is as you may guess my portfolio. Instead of the link [http://localhost/portfolio](http://localhost/portfolio) I'd like to use [http://portfolio.nl](http://portfolio.nl). So I set up a file 'portfolio.nl' under sites-available and a symlink on sites-enabled containing this:

[PHP]<VirtualHost 192.168.1.3>
    ServerName portfolio.nl
    ServerAlias *.portfolio.nl
    ServerAdmin myemail@gmail.com
    DocumentRoot /var/www/portfolio
</VirtualHost>[/PHP]To get this to work on my local machine I set up this in /etc/hosts:

[PHP]#127.0.0.1    localhost
#127.0.1.1    lars-desktop

127.0.0.1    localhost
127.0.1.1    lars-desktop

192.168.1.3    portfolio.nl

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts[/PHP]This works, but I have more websites I'd like to have in my vhost. I'd like to have 'junes.com' in my vhost and a lot of others as well. I set up a virtual host file under sites-avaliable and enabled just like I did with my portfolio and added the line '192.168.1.3    junes.com' to my vhost. But when I restart apache, it gives this output. I understand why it gives the error, but I don't know how to solve it.


 * Restarting web server apache2                                                    [Thu Jul 15 21:24:32 2010] [warn] VirtualHost 192.168.1.3:0 overlaps with VirtualHost 192.168.1.3:0, the first has precedence, perhaps you need a NameVirtualHost directive
 ... waiting [Thu Jul 15 21:24:34 2010] [warn] VirtualHost 192.168.1.3:0 overlaps with VirtualHost 192.168.1.3:0, the first has precedence, perhaps you need a NameVirtualHost directive

Does anyone know how to solve this? Can anyone help me?

---

### Post by Ryan Dwyer on 2010-07-15
Change this:
<VirtualHost 192.168.1.3>

To this:
<VirtualHost *:80>

---

### Post by Emascu on 2010-07-15
Simple solutions- I love it. I was close though!

Thanks a lot! :D

---

