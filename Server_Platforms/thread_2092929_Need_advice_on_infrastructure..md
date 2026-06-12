---
title: "Need advice on infrastructure."
date: 2012-12-09
forum: Server Platforms
---

### Post by pepsifx357 on 2012-12-09
Hey everybody!


I've got a nice Rackable Systems server that I got from ebay.  I highly suggest anyone go find one and get it.  $400 got me 2, 2.33GHz quad core processors, 16GB of ram, and 4 500GB hard drives.


I first installed FreeNAS on the thing as a backup, but it really wasn't a backup, it was just my computer connected to NFS shares on the server.  I felt that FreeNAS was just wasting all those cores and ram.  So I installed Proxmox.


Here's where I ran into a PARADOX!!!!!!!!!!!!


I've been wondering this for a while by the way...


For some reason, Apache2 is not able link to another Apache2 server so that you can have somewhat of an apache cluster.  That way Apache 2 server A is the master and can "mount" Server B to address: ```
http://server-A/Server-B-Alias
```  I hope that makes sense.  I'm sure a LOT of people have been asked about this, if I am.


Anyway, since apache can't do this.  How in the hell, do datacenters run thousands of virtual machines behind a NAT and expect a billion users to hit only one apache2 server at their internet address?!!!


For instance...I have a "Turnkey Linux" openvz of OwnCloud.  I also have a separate openvz with my git repository on it.  I wan't users to be able to access the gitweb interface but since it's on another machine, there's nothing I can do.  To clarify, server A is 192.168.1.13. I want this address:

```
http://192.168.1.13/git
```

To reach server B, which is at 192.168.1.17


I could install git on the owncloud server, but now if the apache2 system crashes, so will git.

How can I solve this problem?  Assuming I only have one internet connection, one WAN IP address, and one domain.  How do you guys do it?

---

### Post by TheFu on 2012-12-09
> **pepsifx357 said:**
> How can I solve this problem?  Assuming I only have one internet connection and one WAN IP address.  How do you guys do it?

You want a load-balancer and/or reverse proxy.
These can be software on Linux or hardware based from Juniper, Cisco, F5 and many others.

**nginx**, **pound**, **ha-proxy** are examples used on Linux. There are many others for specific software stacks too - Perl has** plackup/starman**, Ruby has **thin **or** mongrel** ... you get the idea. There is probably an apache module for this too, but we don't run apache here - it is too bloated for our needs.

You can read more about reverse proxies and why you really want one for better security of your website here: **[http://blog.jdpfu.com/2011/08/18/readers-ask-about-reverse-proxy-servers](http://blog.jdpfu.com/2011/08/18/readers-ask-about-reverse-proxy-servers)**  I hope it helps.

It is much easier to manage complexity and security when all web traffic into a single reverse-proxy server for most companies. From there, the traffic can be spread out to the different back end web servers, while blocking many "bad requests" from the internet. For my company, it is an added layer of security - usually blocking any php requests from the internet - our security team will not allow any php websites to be accessed directly from the internet, as an example. This can be blocked at the proxy, regardless of what internal development teams try to do behind the scenes. Often developers don't know squat about security.  A program that works, doesn't mean it is secure, as we all know.

I know you didn't ask this, but I'd highly recommend that you **do not mix virtual machine infrastructure with your storage infrastructure on the same hardware.** There is a history of interoperability issues when these are run on the same hardware.  Storage probably should use dedicated hardware, without any virtualization on it.  Many people have been burned by mixing.  Having a VM go down isn't a big deal, but having a storage server go down is definitely a big deal.  KISS - [https://en.wikipedia.org/wiki/KISS_principle](https://en.wikipedia.org/wiki/KISS_principle)

---

### Post by pepsifx357 on 2012-12-09
Thank you for the quick response!

It looks like I'm gong to install a dedicated web server and play around with reverse proxies for a while.

> nginx, pound, ha-proxy are examples used on Linux. There are many others for specific software stacks too - Perl has plackup/starman, Ruby has thin or mongrel ... you get the idea. There is probably an apache module for this too, but we don't run apache here - it is too bloated for our needs.

I've noticed a lot of nginx sites lately, is that where everyone is going?

> I know you didn't ask this, but I'd highly recommend that you do not mix virtual machine infrastructure with your storage infrastructure on the same hardware. There is a history of interoperability issues when these are run on the same hardware. Storage probably should use dedicated hardware, without any virtualization on it. Many people have been burned by mixing. Having a VM go down isn't a big deal, but having a storage server go down is definitely a big deal. KISS - [https://en.wikipedia.org/wiki/KISS_principle](https://en.wikipedia.org/wiki/KISS_principle)

I was slightly aware of that and was looking at FreeNAS on another box to serve storage.  Proxmox was crap for storage, but I couldn't let those cores go to waste.  Right now, I'm using git and owncloud separately to sync what is on my computer so there are 3 copies of everything.  I'll just tread lightly for now.




Edit:

I might try this.  I'll try to post anything that works.

[https://help.ubuntu.com/community/Nginx/ReverseProxy]("https://help.ubuntu.com/community/Nginx/ReverseProxy")

---

### Post by TheFu on 2012-12-09
> **pepsifx357 said:**
> I was slightly aware of that and was looking at FreeNAS on another box to serve storage.  Proxmox was crap for storage, but I couldn't let those cores go to waste.  Right now, I'm using git and owncloud separately to sync what is on my computer so there are 2 copies of everything.  I'll just tread lightly for now.

The people burned by mixing VMs and storage weren't pushing anything too complex either. I truly hope it works out for you.

Running the reverse proxy inside a dedicated VM is a best practice. If you look at that prior link, there are other articles about those aspects of security and flexibility infrastructure design.

Having a good, solid, automatic backup solution is critical.  **rdiff-backup **is my tool of choice for this.  It has rsync-like command options, but most of the features needed by a real enterprise backup too.  Backups need to be like a code repository with the ability to restore specific versions from specific points in time.  BTW, I'm a huge virtualization user - even my main desktop runs in a VM in a private cloud accessible from anywhere in the world through a VPN.

For a cheap NAS server, I've used a $100 AMD E-350 APU box with a GigE NIC. Before HDDs are added, only 14W of power draw. With a few HDDs, under 25W needed.  Not good for enterprise needs, but definitely good enough for home use and learning about NFS, iSCSI and AoE block storage.

---

### Post by pepsifx357 on 2012-12-09
> **TheFu said:**
> The people burned by mixing VMs and storage weren't pushing anything too complex either. I truly hope it works out for you.

LMAO...It's a laboratory in here.  I've created a monster and at this point, if it does go down, it would be a good thing.

> Running the reverse proxy inside a dedicated VM is a best practice. If you look at that prior link, there are other articles about those aspects of security and flexibility infrastructure design.

Just tried an openvz with no luck, so I'll do that, but the configuration of the reverse proxy is complicated.  The tutorials give you good generic codes to modify, but they don't explain which host goes where or if I can substitute an ip address for the host name.  I have to admit I haven't messed around much with virtualhosts...at all, so it's kinda new to me.

I followed this:

[https://help.ubuntu.com/community/Nginx/ReverseProxy]("https://help.ubuntu.com/community/Nginx/ReverseProxy")

For example, on the nginx server, you create a file inside /etc/nginx/sites-enabled/ called "default," or whatever.  Mine is "default."

> server {
        listen   80;
        server_name  foo.bar.no foo.bar.yes foo.bar.ok;

        access_log  /var/log/nginx/access.log;


        location / {
                proxy_pass      [http://172.27.0.2/;](http://172.27.0.2/;)
                include         /etc/nginx/proxy.conf;
        }
}

My questions are:

1. What is listening on 80?  localhost?  My other apache2 server?
2. What am I supposed to replace foo.bar.no, foo.bar.yes, ect. with?  My apache server is owncloud.bencookemusic.local, put that there?
3. I assume proxy_pass is supposed to be the apache2, owncloud.bencookemusic.local.  I have no idea.

I also edit /etc/nginx/proxy_params to read:

> proxy_redirect          off;
proxy_set_header        Host            $host;
proxy_set_header        X-Real-IP       $remote_addr;
proxy_set_header        X-Forwarded-For $proxy_add_x_forwarded_for;
client_max_body_size    10m;
client_body_buffer_size 128k;
proxy_connect_timeout   90;
proxy_send_timeout      90;
proxy_read_timeout      90;
proxy_buffers           32 4k;

To setup the apache2 server to use nginx as a proxy, they just ask you to install "libapache2-mod-rpaf" and modify /etc/apache2/mods-available/rpaf.conf to read like this:

> <IfModule mod_rpaf.c>
RPAFenable On
RPAFsethostname On
RPAFproxy_ips 192.168.1.19
</IfModule>

192.168.1.19, being nginx.bencookemusic.local

---

### Post by pepsifx357 on 2012-12-09
I'm not going to lie.  This is a nightmare to figure out.  I'm not sure why I'm so stumped.  I just can't seem to wrap my head around the whole idea of virtualhosts and reverse proxy.  The configs that I set up, from the tutorial, on the nginx server dont seem point to my other server, just a dns name that probably doesn't work because my DNS server doesn't exist yet.

Here's where you might have to spoonfeed me a bit.  Just a little bit.

Server A is the nginx server.  It is what sees the internet @ [www.example.com](www.example.com) and is what I want to use as a reverse proxy.  It is a fully virtualized machine.  Its IP address is 192.168.1.139

Server B is the apache2 server that I want to be seen on the internet via something like "owncloud.example.com."  It is an openvz template with the IP address of 192.168.1.13.

On Server A I have the following in my configs:

/etc/nginx/proxy.conf
```
proxy_redirect          off;
proxy_set_header        Host            $host;
proxy_set_header        X-Real-IP       $remote_addr;
proxy_set_header        X-Forwarded-For $proxy_add_x_forwarded_for;
client_max_body_size    10m;
client_body_buffer_size 128k;
proxy_connect_timeout   90;
proxy_send_timeout      90;
proxy_read_timeout      90;
proxy_buffers           32 4k;
```

/etc/nginx/sites-enabled/default
```
server {
        listen   80;
        listen   [::]:80

        root /usr/share/nginx/www;
        index index.html index.htm;

        # Make site accessible from http://localhost/
        server_name localhost;

        location / {
                # First attempt to serve request as file, then
                # as directory, then fall back to index.html
                try_files $uri $uri/ /index.html;
                # Uncomment to enable naxsi on this location
                # include /etc/nginx/naxsi.rules
        }

        location /doc/ {
                alias /usr/share/doc/;
                autoindex on;
                allow 127.0.0.1;
                deny all;
        }


############################################

server {
        listen 8000;
        listen 192.168.1.13:8000;
        server_name owncloud.example.local owncloud owncloud.example.com$
        root /var/www/owncloud;
        index index.html index.htm index.php;

        location / {
                try_files $uri $uri/ /index.html;
        }
}
```

On Server B
/etc/apache2/sites-enabled/default
```
<VirtualHost *:8000>
        ServerAdmin webmaster@localhost

        DocumentRoot /var/www
        <Directory />
                Options FollowSymLinks
                AllowOverride ALL
        </Directory>
        <Directory /var/www/>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride None
                Order allow,deny
                allow from all
        </Directory>

        ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
        <Directory "/usr/lib/cgi-bin">
                AllowOverride None
                Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
                Order allow,deny
                Allow from all
        </Directory>

        ErrorLog ${APACHE_LOG_DIR}/error.log

        # Possible values include: debug, info, notice, warn, error, crit,
        # alert, emerg.
        LogLevel warn

        CustomLog ${APACHE_LOG_DIR}/access.log combined

    Alias /doc/ "/usr/share/doc/"
    <Directory "/usr/share/doc/">
        Options Indexes MultiViews FollowSymLinks
        AllowOverride None
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>

</VirtualHost>
```

/etc/apache2/mods-enabled/rpaf.conf
```
<IfModule mod_rpaf.c>
RPAFenable On
RPAFsethostname On
RPAFproxy_ips 127.0.0.1 ::1
</IfModule>

```

I don't see any reason why this would work at all.  Only because I don't see where anything is pointing anywhere.  That's where I'm stumped.  I don't know which numbers to plug in.

---

### Post by TheFu on 2012-12-09
I don't use apache. Can't help you there.

It seems that you are making this overly complicated.  I suggest drawing a picture to see how things need to fit together.  Be certain that only 1 listener is listening on a specific IP and specific port for each box. For example, the reverse proxy should probably be the only thing listening on port 80 on the incoming box.  The router should forward traffic only to the reverse proxy - nowhere else.  Any other web services running on that box need to be moved somewhere else a different port ... it doesn't matter, provided you use high ports (above 1024). Doing this also means that root doesn't need to start those other services - another good thing.  I prefer to have a single-purpose reverse proxy VM with no other services running.  From a "security best practices" standpoint, this is a solid design technique.

There are many nginx how-to guides.  The nginx.com website is very good.  I would highly recommend that you do not use the "default" file for your sites-enabled.  This file will be overwritten almost every time that a new nginx is released. Also, you probably want to use the nginx PPA, not the terribly out of date Ubuntu repo versions.  Hackers will seek out old versions with known flaws and specifically attack those.

If you are using other web interfaces on these boxes, perhaps for managing things,  be certain to move those listeners somewhere else that does not conflict.  Personally, I avoid using any web-app server admin tools. They are all buggy and prevent the thorough understanding required to secure the services.  Webmin and phpadmin and mysqladmin (sorry, I don't recall the real names - those are just guesses) have all had hacks recently. Anyway, I am not a fan.  Learn the CLI way and you'll never get confused.

What ports do openvz and proxmox use?

**lsof** is your friend to find listeners, so is **netstat**.  You'd be surprised what gets started without your knowledge.

As to virtual hosts - either let apache manage them 100% or let the reverse proxy manage them 100%. Pick and stick with it.  I find it easier to have every website listen on a different port and let the reverse proxy handle the name-based redirects. That's just me.

Good luck.

---

### Post by koenn on 2012-12-09
> **pepsifx357 said:**
> 
I don't see any reason why this would work at all.  Only because I don't see where anything is pointing anywhere.  That's where I'm stumped.  I don't know which numbers to plug in.

It's not all that hard, conceptually, but you're missing a copuple of things.

So, nginx is your reverse proxy, apache serves one or more websites. 

The apache config is easy, you just need to set up web sites there. Your proxy will refer to them by URL, just like a browser wouild call a site directly. Nothing special there. 


You do need control over DNS. 
You want all (external) traffic to come though your reverse proxy, so all your (relevant) websites should resolve to the (public) IP address of your web proxy. 


Speaking of which, an address of  192.168.1.139 won't work, you'll need an other solution for that (public address, NAT, ...) but that has nothing to do with reverse proxy per se. 


Lastly, your nginx needs a config that doesn't necessarily serve any content, but
- will accept requests for any of the sites your proxying for
- has rules about what to do with those requests 

re. those rules. In an apache reverse proxy those would be (at least) pairs of ProxyPass and ProxyPassReverse directives. I don't know what it is in nginx, i don't use it. 

So, generally speaking, your nginx config should say things like
* if there is a request for [www.example1.com](www.example1.com),  send it to server1.mydomain.xx
* if there is a request for somewebapp.example5.com,  send it to server2.mydomain.xx 
* if there is a request for [www.example1.com/downloads](www.example1.com/downloads), send it to download.mydomain.com

and so on. Usually that's sufficient. In some peculiar cases, you'd have to rewrite URLs etc, but you don't want to go there unless straight proxying is proven insufficient.


This looks like a good place to start :
[http://www.cyberciti.biz/tips/using-nginx-as-reverse-proxy.html](http://www.cyberciti.biz/tips/using-nginx-as-reverse-proxy.html)

---

### Post by dstnvns on 2012-12-10
If you need to allow inbound access to site/services while you are resolving the problem with a reverse proxy/load balancing solution using your routers port forwarding settings and assigning each server:port for an internal system a different port for wan traffic. I.e. 192.168.x.x:80 internal addresses on two HTTP servers can use two ports 80 and whatever, to allow the server not receiving incoming request on port 80 to be accessed if the external port that was configured is specified "http://yourdomain.ext:12345"

Not a solution but it worked for me when I was in a similar situation.

---

### Post by pepsifx357 on 2012-12-13
Well, this might be something I'm going to have to come back and visit.  I'm pretty frustrated at this point.  I tried to revert my apache settings back to normal, now I can't get to my server at all.  I just did the reverse proxy steps in reverse.  ports.conf is set back to 80, sites-enabled set to 80, and "Not Found."

I can install gentoo, but I can't configure a web server?  How useless am I?  lol

> If you need to allow inbound access to site/services while you are resolving the problem with a reverse proxy/load balancing solution using your routers port forwarding settings and assigning each serverort for an internal system a different port for wan traffic. I.e. 192.168.x.x:80 internal addresses on two HTTP servers can use two ports 80 and whatever, to allow the server not receiving incoming request on port 80 to be accessed if the external port that was configured is specified "http://yourdomain.ext:12345"

Not a solution but it worked for me when I was in a similar situation.

Like port mapping?

---

### Post by TheFu on 2012-12-13
Did you stop nginx?  If it is running and grabbing port 80 before apache starts and tries to get port 80, you're out of luck.

I really think that drawing a picture will help you. There are lots of details that need to be correct and a picture will help to ensure you don't forget one.

---

### Post by pepsifx357 on 2012-12-14
> **TheFu said:**
> I really think that drawing a picture will help you. There are lots of details that need to be correct and a picture will help to ensure you don't forget one.

Actually, you're right, that would be perfect.  Problem is, I need to see the picture in the first place to be able to understand how the "signal flow" works.

The Nginx server has been turned off and the router is pointing 80 back to the owncloud server like it was before.
  
I'm testing it from inside the network, so 192.168.1.13 should have gotten me there. Or "http://cloud," as I have it mapped via dns.


I'm not sure why port 80 isn't being listened to by the owncloud server.  At least I assume that is the problem.  I changed everything back and restarted apache.  That didn't work, so I rebooted.  Same thing.

"NOT FOUND"

I have a feeling that when I get this fixed back to normal, I will have a better understanding about what happened so I can make the reverse proxy actually work next time.




Edit:

HA!  I found the problem!

The /etc/apache2/sites-enabled/owncloud looked like this:

```
NameVirtualHost 127.0.0.1:80
NameVirtualHost *:443

<VirtualHost 127.0.0.1:80>
    UseCanonicalName Off
    ServerAdmin webmaster@localhost
    DocumentRoot /var/www/owncloud/
</VirtualHost>

<VirtualHost *:443>
    SSLEngine on
    SSLCertificateFile /etc/ssl/certs/cert.pem
    ServerAdmin webmaster@localhost
    DocumentRoot /var/www/owncloud/
</VirtualHost>

<Directory /var/www/owncloud/>
    Options +FollowSymLinks
    AllowOverride All
    order allow,deny
    allow from all
</Directory>

```


I just changed this line to revert back to normal.  How in the hell was I supposed to know that?  lol  I know, I know, RTFM.  Manuals aren't always "clear" you know.

```
<VirtualHost *:80>
```

---

### Post by TheFu on 2012-12-14
Making 1 change at a time is best with complex config files.
I also use '**git**' to manage those changes easily, so it is easy to see exactly what changed along the way.  I suppose your daily backups could be used in the same way as **git**, but many lab environments don't do backups at all, so putting everything under /etc/ into git control (sccs, rcs, cvs, hg, whatever source control system) is a great idea.

---

### Post by pepsifx357 on 2012-12-15
> **TheFu said:**
> Making 1 change at a time is best with complex config files.
I also use '**git**' to manage those changes easily, so it is easy to see exactly what changed along the way.  I suppose your daily backups could be used in the same way as **git**, but many lab environments don't do backups at all, so putting everything under /etc/ into git control (sccs, rcs, cvs, hg, whatever source control system) is a great idea.

That is a great idea.  Hadn't thought of versioning my system.

I have an ownCloud server here with versioning out of the box.  I have a git server too.  What would happen if I made a project out of my root folder?  Is that even feasable, or is that going too far?

Edit: I see how git works with single files instead of the whole folder like my ownCloud.  Much different beast.  I like the advanced functions of the branch and merging.  I'm playing around with some project files.


You have effectively sidetracked me.

By the way, I noticed your in Atlanta.  Take I-20 West, all the way to exit 5.  That's where I live.  :)

---

### Post by TheFu on 2012-12-15
> **pepsifx357 said:**
> That is a great idea.  Hadn't thought of versioning my system.

I have an ownCloud server here with versioning out of the box.  I have a git server too.  What would happen if I made a project out of my root folder?  Is that even feasable, or is that going too far?

Edit: I see how git works with single files instead of the whole folder like my ownCloud.  Much different beast.  I like the advanced functions of the branch and merging.  I'm playing around with some project files.

You have effectively sidetracked me.

I've never bothered with ownCloud. It is too easy to do all that yourself. Had something like it for 15 yrs. All-in-one solutions concern me. How do you stay current with patches for each part - is my first question. For the tools that are really just meta-packages with a config script, great. However, there are a few that have turned into full-blown distros and these are always 4-18 months behind on security patches.

Git can work at any level you like - single files to entire directory trees, however, it is NOT good for binary files, hence my suggestion to use /etc/ as the top level.  If you aren't into software development, learning git might be more trouble than it is worth. OTOH, if you are doing any development, learning git will repay the effort 100x. Git is state of the art source code control with easy branch, merge for entire projects. If you have interest, there are a few great youtube videos on git from Randall Schwartz and Linus that I consider MUST WATCH.  I use git for my personal projects AND for team 
development.

Many people also put their linux .dotfiles and .config-files in $HOME under some sort of version control. Using git for this makes it easy to clone you config between many different installations.

OTOH, if you are just being a sysadmin - then automatic, daily backups are definitely mandatory. Their are many different backup tools, just pick one that you can automate.  I like **rdiff-backup**, but there are at least 5 other tools that are just as good and easy to use.

I'm not really in Atlanta, but for a world-wide audience, that is close enough.  I am fairly active in ALE.org - both the central and NW versions. The central group is more grey beards running systems for their jobs. The NW version has some of those, but also a student element so we try to keep it at a less-than-expert level. Check out the website for our meeting dates and to sign up for the email listsrv. We have "members" from all around the USA who still participate online regardless of where they've moved. Consider this your personal invitation to join us.

---

### Post by pepsifx357 on 2012-12-15
> **TheFu said:**
> Git can work at any level you like - single files to entire directory trees, however, it is NOT good for binary files

How well would it work with audio files, say at most, 100MB in size a peice.  Our project folders get about 7 GBs in size.  If this could work, git is a Godsend.  We've been looking for something exactly like this for a long time.  We've been using dropbox/owncloud/sparkleshare.  Owncloud was the only one that worked without issues.  But to be able to work on our own branches?  That's a hell of a lot of flexibility.

---

### Post by TheFu on 2012-12-15
I cannot answer that for your system needs.  Spend 2 hours learning how it works, test it for yourself.  Yes, git "can work", but there are probably better solutions.

I would probably use a hard-link based backup tool and I'd ensure that hardlinks were used on the primary server so that multiple versions of identical files were only stored once with a reference count.  Until that count hits zero, the file is maintained on the system. There are many de-dup scripts that will automate that for you.  Slashdot had a question about that a few months ago. After reading the question, I decided it would be a fun script to create in a few hours, but there are programs that have been supported and in existence for 5-10 yrs that probably handle it better.  The exercise was fun.

This is thread has left the "need infrustructure advice" topic. Asking a new question would be recommended to get fresh ideas and expertise on the binary version control topic.  If you'd like more professional advice on this topic, feel free to PM me.

---

