---
title: "Apache2 unknown host error - baffled."
date: 2010-07-08
forum: Server Platforms
---

### Post by ssalter2010 on 2010-07-08
hi,

just installed ubuntu and apache2/php/mysql

changed default apache2 site to /home/ssalter/www
edited /etc/apache2/sites-available/www to look like this:

<VirtualHost *:80>

    ServerName ssub01.psych.indiana.edu
    ServerAlias [www.ssub01.psych.indiana.edu]("http://www.ssub01.psych.indiana.edu")
    ServerAdmin [EMAIL="ssalter@indiana.edu"]ssalter@indiana.edu[/EMAIL]

    DocumentRoot /home/ssalter/www/
    <Directory />
        Options FollowSymLinks
        AllowOverride None
    </Directory>
    <Directory /home/ssalter/www/>
        Options Indexes FollowSymLinks MultiViews
        AllowOverride None
        Order allow,deny
        allow from all
    </Directory>
......
and so on.

All is fine on the server, IP or name.

But, when I try to access the site from another machine only the IP will get me there, I get an "unknown host" when I ping the machine name and browsers can't find [http://ssub01.psych.indiana.edu](http://ssub01.psych.indiana.edu) but will access the proper apache2 webroot with IP.

What am I missing?  I've restarted Apache and restarted machine.

thanks,
Steve

---

### Post by dapperdanny77 on 2010-07-08
your client host is unable to resolve your webservers hostname.
usually a client asks a DNS server for the ip of a given server name.

if it's a private setup, you can put this ip/hostname in /etc/hosts on client side (linux), or lmhosts ?? (win)

---

### Post by ssalter2010 on 2010-07-08
> **dapperdanny77 said:**
> your client host is unable to resolve your webservers hostname.
usually a client asks a DNS server for the ip of a given server name.

if it's a private setup, you can put this ip/hostname in /etc/hosts on client side (linux), or lmhosts ?? (win)


I only had 
127.0.0.1    localhost 
127.0.0.1    ssub01.psych.indiana.edu   ssub01

so I added the following and restarted:

129.79.193.131    ssub01.psych.indiana.edu   ssub01

no change.
:(

---

### Post by dapperdanny77 on 2010-07-08
> **ssalter2010 said:**
> I only had 
127.0.0.1    localhost 
127.0.0.1    ssub01.psych.indiana.edu   ssub01

so I added the following and restarted:

129.79.193.131    ssub01.psych.indiana.edu   ssub01

no change.
:(

where did you put that - on your client (browser) or on the web server?
this has to be put on the client machine

---

### Post by ssalter2010 on 2010-07-08
> **dapperdanny77 said:**
> where did you put that - on your client (browser) or on the web server?
this has to be put on the client machine

I have a static ip on the server machine. I want it's web content to be public (more or less). Maybe I'm not understanding you.  If my server is set up properly, I should be able to type in [http://ssub01.psych.indiana.edu](http://ssub01.psych.indiana.edu) from any client machine and get to the webserver.

---

### Post by dapperdanny77 on 2010-07-08
ok - if a client from the internet should be able to reach your server via   [http://ssub01.psych.indiana.edu]("http://ssub01.psych.indiana.edu/") you need your server registered at a DNS server.

any client on the internet can reach your server only via your IP address - usually the clients get this IP by asking a DNS server. for private testing you can put this ip in /etc/hosts on the client machine - then your browser is able to get the IP from there.

you can register your server ip at dyndns.org - it's a free service - but you can't have a server name with indiana.edu domain. if this is mandatory you have to find the DNS admin of the indiana.edu domain and ask her/him to register you server. you should be able to reach this person via email [email]hostmaster@indiana.edu[/email].
before putting effort in this issue you should do the local testing

---

### Post by ssalter2010 on 2010-07-08
Oh gosh, how embarrassing. I know all that. lol...I blindsided myself with other details. It has been a couple of years since I have worked with Linux or Apache and I got totally enmeshed in "what am I doing wrong in the unix world?"....

what is worse is that it worked briefly yesterday and then I changed the machine name. hehe...*smacks self*

I'll contact our DNS people and have em adjust the records.

Thank you!
Steve

---

