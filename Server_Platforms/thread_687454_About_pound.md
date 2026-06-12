---
title: "About pound"
date: 2008-02-04
forum: Server Platforms
---

### Post by satimis on 2008-02-04
Hi folks,


What will be the use of "pound"?

[http://www.apsis.ch/pound/](http://www.apsis.ch/pound/)


I don't have a clear picture of its application on reading its website.  Any example?  TIA


B.R.
satimis

---

### Post by popch on 2008-02-04
It says right on their homepage:

**WHAT POUND IS:**

  [LIST=1]
[*]  a reverse-proxy: it passes requests from client         browsers to one or more back-end servers.
[*]  a load balancer: it will distribute the requests from         the client browsers among several back-end servers,         while keeping session information.
[*]  an SSL wrapper: *Pound* will decrypt HTTPS requests         from client browsers and pass them as plain HTTP         to the back-end servers.
[*]  an HTTP/HTTPS sanitizer: *Pound* will verify requests         for correctness and accept only well-formed ones.
[*]  a fail over-server: should a back-end server fail,         *Pound* will take note of the fact and stop passing         requests to it until it recovers.
[*]  a request redirector: requests may be distributed         among servers according to the requested URL.[/LIST]Which part do you find hard to understand? If you do not understand those points, you will presumably not need this product.

---

### Post by satimis on 2008-02-05
> **popch said:**
> It says right on their homepage:

**WHAT POUND IS:**

  [LIST=1]
[*]  a reverse-proxy: it passes requests from client         browsers to one or more back-end servers.
[*]  a load balancer: it will distribute the requests from         the client browsers among several back-end servers,         while keeping session information.
[*]  an SSL wrapper: *Pound* will decrypt HTTPS requests         from client browsers and pass them as plain HTTP         to the back-end servers.
[*]  an HTTP/HTTPS sanitizer: *Pound* will verify requests         for correctness and accept only well-formed ones.
[*]  a fail over-server: should a back-end server fail,         *Pound* will take note of the fact and stop passing         requests to it until it recovers.
[*]  a request redirector: requests may be distributed         among servers according to the requested URL.[/LIST]Which part do you find hard to understand? If you do not understand those points, you will presumably not need this product.
Thanks for your advice.


I'm interested on points 3 and 4;```
3.   an SSL wrapper: Pound will decrypt HTTPS requests from client browsers and pass them as plain HTTP to the back-end servers.
4.   an HTTP/HTTPS sanitizer: Pound will verify requests for correctness and accept only well-formed ones.
```
The backside story leading to my discovery of "pound" on googling is as follows;

I'm doing a test on virturalization with following setup;
(This is a test NOT for production)


VMWare Server

Ubuntu 7.04 server amd64 (Host)
(Mail Server with SquirrelMail running)
Internal IP addr 192.168.0.10
Port forwarded 80, 443 (orginal setup on router)


CentOS 5 x56_64 (Guest)
(Web Server)
Internal IP addr 192.168.0.20
Port forwarded 8080 (orginal setup on router]


The Mail Server is running w/o problem.  The Web Server can be visited with;

[https://public_ip:8080](https://public_ip:8080)


I expect to exclude ":8080", therefore re-setup the router as follows;

Ports forward to Ubuntu - 80 and 8080
Port forward to CentOS - 443


On CentOS;
======

Edit /etc/httpd/conf/httpd.conf
Add "Listen 443" and comment out;
Listen 80
Listen 8080


# service httpd start```
Starting httpd: (98)Address already in use: make_sock: could not bind to address [::]:443
(98)Address already in use: make_sock: could not bind to address 0.0.0.0:443
no listening sockets available, shutting down
Unable to open logs
```
I fixed the problem as follow;

Edit /etc/httpd/conf.d/ssl.conf
comment out "Listen 443"```
....
#
# When we also provide SSL we have to listen to the
# the HTTPS port in addition.
#
#Listen 443
...
```
# service httpd start```
Starting httpd:                                            [  OK  ]
```
[https://public_ip](https://public_ip)
displays Apache default page on CentOS
(Remark - haven't setup homepage yet)


[http://public_ip](http://public_ip)
displays Apache default page on Ubuntu
(Remark - haven't setup homepage yet)


[http://public_ip/mail](http://public_ip/mail)
starts SquirrelMail on Ubuntu


Now my problem is ssl httpd needs listening to port 443.  I can't forward all www ports, 80, 8080 and 443 to CentOS.  Because SquirrelMail on Ubuntu needs web port to run.  It is a web base package.


Do you think "pound" can help me out?  Any suggestion?  TIA.


Furthermore;

I'm at lost what will be the use or advantage to go virtualization? I can't run mail and web server on Host/Guest separately. What shall I make use of the Guest ? Only for testing? I think virtualization will only be suitable for running multiple public IPs.


B.R.
satimis

---

### Post by ellis rowell on 2008-02-05
I may be completely wrong, but 1 & 2 suggests to me that it is server control program to share the load with other servers.

"If you do not understand those points, you will presumably not need this product.", I think that is right.

---

### Post by p_quarles on 2008-02-05
Moved to servers & security.

---

### Post by koenn on 2008-02-05
I think your problem is in the
```
Starting httpd: (98)Address already in use: make_sock: could not bind to address [::]:443
(98)Address already in use: make_sock: could not bind to address 0.0.0.0:443
```
0.0.0.0 means any or no specific address. You could probably solve that by telling apache on centos to listen on 192.168.0.20 and apache on ubuntu to listen on  192.168.0.10. There's a directive for that in apache conf , but I don't remember exactly what. 

It's a weird problem, your guest and host system seem to be aware of eachother's sockets. Could it be you did a lot of trial and error with the VM Networking and left a bit of a mess ? 

From your post it seems to me that you're doing virualization because you want both webmail and a website on port 80. In that case, you can probably set up apache to handle both. Apache can handle multiple sites, so you could just have both 
[www.anydomainname.xx](www.anydomainname.xx) --> website
webmail.anydomainname.xx --> webmail.
on the same server. Unless, of course, Squirell has its own web server and can't be made to work with apache. That, I don't know.

If all that doesn't offer a sollution, then probably a reverse proxy such as pound might help, cause it would allow you to direct traffic to 1 of both servers, eg based on protocol, requested url, etc. 
But that's only plan D.

---

### Post by satimis on 2008-02-05
Hi koenn,


Thanks for your advice.


> 
I think your problem is in the
```
Starting httpd: (98)Address already in use: make_sock: could not bind to address [::]:443
(98)Address already in use: make_sock: could not bind to address 0.0.0.0:443
```
0.0.0.0 means any or no specific address. You could probably solve that by telling apache on centos to listen on 192.168.0.20 and apache on ubuntu to listen on  192.168.0.10. There's a directive for that in apache conf , but I don't remember exactly what. 

On CentOS I'm NOT allowed changing;

Listen 443

to;
Listen 192.168.0.20


# /etc/init.d/httpd restart```

Stopping httpd:                                            [FAILED]
Starting httpd: Syntax error on line 137 of /etc/httpd/conf/httpd.conf:
Port must be specified

```


> 
It's a weird problem, your guest and host system seem to be aware of eachother's sockets. Could it be you did a lot of trial and error with the VM Networking and left a bit of a mess ? 

I have no idea.  I did lot of changes on this test.  Is there any way checking irregularities on VM Networking?


> 
From your post it seems to me that you're doing virualization because you want both webmail and a website on port 80. In that case, you can probably set up apache to handle both. Apache can handle multiple sites, so you could just have both 
[www.anydomainname.xx](www.anydomainname.xx) --> website
webmail.anydomainname.xx --> webmail.
on the same server. Unless, of course, Squirell has its own web server and can't be made to work with apache. That, I don't know.
Please explain in more detail how to make them?  TIA


On Ubuntu;

$ cat /etc/squirrelmail/apache.conf```

Alias /squirrelmail /usr/share/squirrelmail

<Directory /usr/share/squirrelmail>
  Options Indexes FollowSymLinks
  <IfModule mod_php4.c>
    php_flag register_globals off
  </IfModule>
  <IfModule mod_php5.c>
    php_flag register_globals off
  </IfModule>
  <IfModule mod_dir.c>
    DirectoryIndex index.php
  </IfModule>

  # access to configtest is limited by default to prevent information leak
  <Files configtest.php>
    order deny,allow
    deny from all
    allow from 127.0.0.1
  </Files>
</Directory>

# users will prefer a simple URL like http://webmail.example.com
#<VirtualHost 1.2.3.4>
#  DocumentRoot /usr/share/squirrelmail
#  ServerName webmail.example.com
#</VirtualHost>

# redirect to https when available (thanks omen@descolada.dartmouth.edu)
#
#  Note: There are multiple ways to do this, and which one is suitable for
#  your site's configuration depends. Consult the apache documentation if
#  you're unsure, as this example might not work everywhere.
#
#<IfModule mod_rewrite.c>
#  <IfModule mod_ssl.c>
#    <Location /squirrelmail>
#      RewriteEngine on
#      RewriteCond %{HTTPS} !^on$ [NC]
#      RewriteRule . https://%{HTTP_HOST}%{REQUEST_URI}  [L]
#    </Location>
#  </IfModule>
#</IfModule>

```


> 
If all that doesn't offer a sollution, then probably a reverse proxy such as pound might help, cause it would allow you to direct traffic to 1 of both servers, eg based on protocol, requested url, etc. 
But that's only plan D.
Will come back to pound later if w/o a solution found.


B.R.
satimis

---

### Post by koenn on 2008-02-05
I always have mixed feelings when I see someone setting up servers without really knowing what they're doing. Reminds me of the times when anyone with enough brains to click Next Next Next was setting up NT4 servers, which then got cracked, ann became the basis for todays spam problem
That, and I really don't know all that much about Apache or VM ware.

Anyway :
If you tell apache to listen on a given address, you still need to give a port as well. 
See here [http://httpd.apache.org/docs/2.0/bind.html](http://httpd.apache.org/docs/2.0/bind.html)

For 2 sites / urls / ... on 1 server : see Virtual Hosts
[http://httpd.apache.org/docs/1.3/vhosts/name-based.html](http://httpd.apache.org/docs/1.3/vhosts/name-based.html)

From the looks of that squirrel/apache.conf, squirrel can be set up as a virtual host on an apache. Try to get apache running, then use that squirrel file to create a 2nd (or 3th) site.


Re. the VMware networking : Try the virtualisation forum - I always set up bridged networking myself (looks like that is what you want too), but I've never had to troubleshoot it so I don't even know where the config files are. Probably somewhere in /etc/vmware ?

---

### Post by satimis on 2008-02-06
> **koenn said:**
> If you tell apache to listen on a given address, you still need to give a port as well. 
See here [http://httpd.apache.org/docs/2.0/bind.html](http://httpd.apache.org/docs/2.0/bind.html)

Performed following steps on CentOS:-

On /etc/httpd/conf.d/ssl.conf
uncomment
Listen 443


$ cat /etc/httpd/conf.d/ssl.conf```

....
#
# When we also provide SSL we have to listen to the
# the HTTPS port in addition.
#
Listen 443
....

```


On /etc/httpd/conf/httpd.conf
change;
Listen 443

to;
192.168.0.20:443


# /etc/init.d/httpd start```

Starting httpd:  ( 98 ) Address already in use: make_sock: could not bind to address
 [::]:443
 ( 98 ) Address already in use: make_sock: could not bind to address 0.0.0.0:443
no listening sockets available, shutting down
Unable to open logs
                                                           [FAILED]

```


The fix is still;
On /etc/httpd/conf.d/ssl.conf
comment out
#Listen 443


# /etc/init.d/httpd start```

Starting httpd:                         [  OK  ]

```


# /etc/init.d/sshd status```

sshd (pid 2596 2594 2250) is running...

```

Hoping that it is still checking all services.


> 
From the looks of that squirrel/apache.conf, squirrel can be set up as a virtual host on an apache. Try to get apache running, then use that squirrel file to create a 2nd (or 3th) site.

Could you please explain in more detail "then use that squirrel file to create a 2nd (or 3th) site".  TIA


Tried previously.  After forwarding all www ports, 80, 443 and 8080 to CentOS (Guest), on browser (on Ubuntu) running "domain.com/mail" can't start SquirrelMail.

Others noted with thanks


satimis

---

### Post by koenn on 2008-02-06
> Could you please explain in more detail "then use that squirrel file to create a 2nd (or 3th) site". TIA
on Debian/Ubuntu, the sites are created with text files in /etc/apache2/sites-available, 1 file per site ( - and enabled by linking to these files from /etc/apache2/sites-enabled).
A site in apache2/sites-... looks like this : 
```
<VirtualHost *>
ServerName www.example.com
ServerAlias example.com
DocumentRoot /home/www/html/example.com/html
CustomLog logs/www.example.com-access_log common
</VirtualHost>
```
Note the striking resemblance to the squirrel file you posted (and  look at /etc/apache2/sites-available/default for a real example)
My guess is you just copy that squirrel file to /etc/apache2/sites-available/ and create a link to it from ../enabled (or just copy it in to .../enabled . You may have to edit some small stuff here and their (paths) and maybe read the squirrel documentation, but basically, that should be it. I think. Never done it.

This might help : [http://www.debianhelp.co.uk/virtualhosts.htm](http://www.debianhelp.co.uk/virtualhosts.htm)

---

### Post by koenn on 2008-02-06
> On /etc/httpd/conf/httpd.conf
change;
Listen 443

to;
192.168.0.20:443

 ( 98 ) Address already in use: make_sock: could not bind to address 0.0.0.0:443


The fix is still;
On /etc/httpd/conf.d/ssl.conf
comment out
#Listen 443

I'm not familiar with how centOS organizes the apache config files, but it seems that you shouldn't have a "Listen" in both /etc/httpd/conf.d/ssl.conf and /etc/httpd/conf/httpd.conf (cause the both refer to the same apache. My guess would be that for ssl your best bet is to put Listen 192.168.0.20:443 in /etc/httpd/conf.d/ssl.conf

---

### Post by SuperMike on 2008-02-06
You can use Pound to create a cheap web farm without having to pay for proprietary and mega-expensive Cisco stuff. Great for starting a project.

---

### Post by satimis on 2008-02-06
> **koenn said:**
> I'm not familiar with how centOS organizes the apache config files, but it seems that you shouldn't have a "Listen" in both /etc/httpd/conf.d/ssl.conf and /etc/httpd/conf/httpd.conf (cause the both refer to the same apache. My guess would be that for ssl your best bet is to put Listen 192.168.0.20:443 in /etc/httpd/conf.d/ssl.conf
Thanks for your advice.


This is only a test.  My main interest is trying to discover the use of Guests on virtualization if w/o www and mail ports forwarded.


satimis

---

### Post by satimis on 2008-02-07
> **SuperMike said:**
> You can use Pound to create a cheap web farm without having to pay for proprietary and mega-expensive Cisco stuff. Great for starting a project.
Where can I find relevant document to start?  I have been googling a while on "pound tutorial/guide server farm virtualization networking" without discovery.  Any suggestion?


satimis

---

### Post by soulresin on 2008-02-07
> **koenn said:**
> I'm not familiar with how centOS organizes the apache config files, but it seems that you shouldn't have a "Listen" in both /etc/httpd/conf.d/ssl.conf and /etc/httpd/conf/httpd.conf (cause the both refer to the same apache. My guess would be that for ssl your best bet is to put Listen 192.168.0.20:443 in /etc/httpd/conf.d/ssl.conf

This person speaks the truth.

Essentially, /etc/httpd/conf/httpd.conf has an Include directive in it that includes everything in /etc/httpd/conf.d, so if you had a Listen 443 in both files you'd have 2 Listen 443 statements, which is blowing Apache up.  (Unfortunately, httpd -t isn't smart enough to catch that one.)

---

