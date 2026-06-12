---
title: "Getting vHosts to work with multiple sites"
date: 2010-07-13
forum: Server Platforms
---

### Post by nic.matthew on 2010-07-13
Hi! I'm somewhat new to webservers and such, but have managed to get a single site going in /var/www. What I want to do now is make nicmatthew.co.cc point to /var/www/nicmatthew/html and make rielworld.co.cc point to /var/www/jimriel/html. I have created the apache vHosts nicmatthew.co.cc and rielworld.co.cc containing this:

```
<VirtualHost 67.23.224.90:80>
ServerName nicmatthew.co.cc
ServerAlias nicmatthew.co.cc
ServerAdmin nmatthew@nicmatthew.co.cc
DocumentRoot /var/www/nicmatthew/html
</VirtualHost>
```and:

```
<VirtualHost 67.23.224.90:80>
ServerName rielworld.co.cc
ServerAlias [www.rielworld.co.cc]("http://www.rielworld.co.cc")
ServerAdmin [EMAIL="jriel@rielworld.co.cc"]jriel@rielworld.co.cc[/EMAIL]
DocumentRoot /var/www/jimriel/html
</VirtualHost>
```

So now I would like to know how to make rielworld.co.cc and nicmatthew.co.cc point to the correct places. Do I somehow set up nameservers? Do I make an A record? 

Any help would be greatly appreciated!

---

### Post by nic.matthew on 2010-07-13
I got it! I set the A record of my co.cc domain to my ip address and it worked! I also had to restart apache and make sure that the specified directory was already made.

---

