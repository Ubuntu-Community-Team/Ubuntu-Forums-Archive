---
title: "seeking advice on web hosting company"
date: 2013-05-08
forum: The Cafe
---

### Post by satimis on 2013-05-08
Hi all,

I'm now subscribing Deluxe plan of Godaddy with unlimited domain hosting.  They require installing a copy of WordPress on each domains.  I'm encountering following problem running WordPress on hosted domains.

On Hosted Domains panel/page
say,
aaa.com	/
bbb.com	/
ccc.com	/

It is required installing WordPress on a folder/directory of each domain.

say,
/aaa.com/wp-aaa-folder
/bbb.com/wp-bbb-folder
/ccc.com/wp-ccc-folder

However on browsing website I have to run;

[http://www.aaa.com/wp-aaa-folder](http://www.aaa.com/wp-aaa-folder)
[http://www.bbb.com/wp-bbb-folder](http://www.bbb.com/wp-bbb-folder)
[http://www.ccc.com/wp-ccc-folder](http://www.ccc.com/wp-ccc-folder)
respectively.

running;
[http://www.aaa.com](http://www.aaa.com)
[http://www.bbb.com](http://www.bbb.com)
[http://www.ccc.com](http://www.ccc.com)
don't work

I have sent dozens of emails to their Support Team for assistance without a result.

I'm prepared changing the hosting company.  On searching I found following link;
Five Best Web Hosting Companies
[http://lifehacker.com/5911651/five-best-web-hosting-companies](http://lifehacker.com/5911651/five-best-web-hosting-companies)

Have any folks using their service before?  

Hostgator offers unlimited domain hosting on "Baby Plan"

Unlimited Web Hosting
[http://www.hostgator.com/shared](http://www.hostgator.com/shared)

Application Hosting...
- WordPress Hosting - Host your very own WordPress blog
- Joomla Hosting & Drupal Hosting - Professional CMS Solutions
- Magento Hosting - Free E-commerce platform for your own store
- Wiki Hosting - Start a Wiki web site with MediaWiki

Has any folk on the forum using Hostgator web hosting service?  Would the problem mentioned above happen?

OR any other suggestions?  TIA

B.R.
satimis

---

### Post by SeijiSensei on 2013-05-08
I just rent virtual machines from [Linode]("http://www.linode.com/") myself, so I can configure everything the way I want it to be.  The naming problems you have, for instance, would be easily fixable if you could control your web server configuration.

That WordPress requirement is absurd.  I run one WP instance where I host my blog.  Every other website runs custom-designed PHP and HTML.

---

### Post by oldos2er on 2013-05-08
Moved to Cafe.

---

### Post by satimis on 2013-05-08
> **SeijiSensei said:**
> I just rent virtual machines from [Linode]("http://www.linode.com/") myself, so I can configure everything the way I want it to be. 
Thanks for your advice.

I have my own server here running on virtualizer.  I'm subscribing Static/Fixed IP at 6M/6M up/down.  It would be quite easy for me operating my own server at home.  But I couldn't run 7x24.  For such a reason I have to hosting website somewhere. 

```

The naming problems you have, for instance, would be easily fixable if you could control your web server configuration.

```
I could touch .htaccess and index.php on Godaddy website.  Any advice on how to modify .htaccess?

> 
That WordPress requirement is absurd.  I run one WP instance where I host my blog. 
It is easy to build blogs on WP using their themes and plugin

Rgds
satimis

---

### Post by SeijiSensei on 2013-05-08
> **satimis said:**
> 
```

The naming problems you have, for instance, would be easily fixable if you could control your web server configuration.

```
I could touch .htaccess and index.php on Godaddy website.  Any advice on how to modify .htaccess?

Only some Apache directives can be put in .htaccess.  Unfortunately the [Alias]("http://httpd.apache.org/docs/current/mod/mod_alias.html#alias") directive, which might be helpful here, is one of them.  But you can only use directives like that in the server configuration file, at which point the easiest solutioin is simply to point the DocumentRoot to the directory of your choosing.

> It is easy to build blogs on WP using their themes and plugin

I probably misunderstood your comment.  I read it to mean that everyone had to use WP to design and mange their sites on this GoDaddy service.  If the service is designed to host blogs, that is a much different matter.

---

### Post by satimis on 2013-05-08
> **SeijiSensei said:**
> Only some Apache directives can be put in .htaccess. 

This is a new site, nothing built yet.  I have been playing around on ./htaccess on Godaddy as follow;

Have .htaccess duplicated as .htaccess_copy

WordPress was installed on /WPReynold

./htaccess```

<IfModule mod_rewrite.c>
RewriteEngine On
RewriteBase /WPReynold/
RewriteRule ^index\.php$ - [L]
RewriteCond %{REQUEST_FILENAME} !-f
RewriteCond %{REQUEST_FILENAME} !-d
RewriteRule . /WPReynold/index.php [L]
</IfModule>
....
....

```

Add following lines to the bottom of the above section```

RewriteCond %{HTTP_HOST} ^reynoldstocks\.com$
RewriteRule (.*) http://www.reynoldstocks.com/$1 [R=301,L]
RewriteRule ^$ WPReynold [L]

```
Reload the webpage

On browser ran;
```
http://www.reynoldstocks.com
```
it popup "Future home of something quite cool" page

Ran;```

http://www.reynoldstocks.com/WPReynold
```

It changed back to 
```

http://www.reynoldstocks.com

```
immediately.

Deleted the tesing .htaccess file and changed the duplicated file back to .htaccess

Restart the browser (this step is important others it won't work)

Then running /reynoldstocks.com/WPReynold works again displaying WordPress front page.

Any advice?  TIA

> 
Unfortunately the [Alias]("http://httpd.apache.org/docs/current/mod/mod_alias.html#alias") directive, which might be helpful here, is one of them.  But you can only use directives like that in the server configuration file, at which point the easiest solutioin is simply to point the DocumentRoot to the directory of your choosing.
Could you please explain in more detail?  Thanks

B.R.
satimis

---

### Post by CharlesA on 2013-05-09
> **SeijiSensei said:**
> I just rent virtual machines from [Linode]("http://www.linode.com/") myself, so I can configure everything the way I want it to be.  The naming problems you have, for instance, would be easily fixable if you could control your web server configuration.

I moved from shared hosting to a VPS ([serverdragon/securedragon]("http://serverdragon.com/")) and I am so much happier with the service and performance of my site. There is no way I would go back to shared hosting again. Granted setting up the server for the first time can be a pain, cuz it's unmanaged, but it isn't too bad.

> That WordPress requirement is absurd.  I run one WP instance where I host my blog.  Every other website runs custom-designed PHP and HTML.

I agree. I haven't really touched WP, but my site is mostly HTML and PHP.. and I would be really annoyed if I had to install wordpress just to host my site there.

As far as Apache goes, I do not use it, so I don't really know much about the configuration. =/

EDIT: If you want to stay with godaddy, just ask them to change your document roots to point to the folder with the wordpress install.

I think they use a .htaccess file to do that on my shared host and it screwed everything up because of the way it was set up.

---

### Post by satimis on 2013-05-09
> **CharlesA said:**
>  - snip -
There is no way I would go back to shared hosting again. Granted setting up the server for the first time can be a pain, cuz it's unmanaged, but it isn't too bad.

- snip -

Absolutely agreed.  I have been struggling at least 3 weeks.  Godaddy Suppot only turned me around.  Each time to my request for support they just copied and pasted the online document on their emails as reply.

Now I have sorted out my problem.

To make multi-domains to work on WordPress(WP) perform steps as follow;
(I'm not going to mention "Hosted Domains" setup here)

1) Install WP on a directory/folder of the domain (not root/webroot)
say, aaa.com (directory)

2) Create a directory /aaa.com/wpaaa for WP and install WP on it

3) After installation completed and effective, go to File Manager.  Copy both .htaccess and index.php on /aaa.com directory

4) On index.php 

change the line - require('./wp-blog-header.php');

to - require('./wpaaa/wp-blog-header.php');

reload the page.  That is all, not necessary touching .htaccess


On browser running [http://www.aaa.com](http://www.aaa.com) or /aaa.com displays WP front page.  That's it.

However to login WP it still requires full path, /aaa.com/wpaaa/wp-admin.  I haven't found a solution yet,.

Edit:

Do serverdragon.com has MediaWiki installed on their site?  Hostgator has this application which I expect.

B.R.
satimis

---

### Post by d4m1r on 2013-05-09
No such thing as unlimited bandwidth, storage, etc. All servers including those run by the big guys have limitations. Unlimited is just a marketing gimmick and you are better of just searching for reviews of a host you are interested in :)

---

### Post by SeijiSensei on 2013-05-09
Even a $20/month virtual server at Linode gets 2 TB of traffic per month.  Suffice it to say I don't come close to that figure.  The basic server comes with 24 GB of storage. Not enough for large multimedia archives, but certainly enough for ordinary web hosting and email.

> ```
 Unfortunately the Alias directive, which might be helpful here, is one of them. But you can only use directives like that in the server configuration file, at which point the easiest solutioin is simply to point the DocumentRoot to the directory of your choosing.
```
Could you please explain in more detail? Thanks

The Alias directive lets you choose a directory to be represented by a URI.  The directory can be anywhere on the operating system where the Apache user ("www-data" in Ubuntu) has read rights.  An alias usually looks like this:

```
Alias /news /path/to/some/directory
```

then requests for [noparse]http://www.example.com/news[/noparse] are directed to the specified location.

You cannot issue an Alias request in a .htaccess file, because things like aliasing must take place before the document root is determined.  If you follow the link in my earlier posting, you'll see that the Apache documentation gives the locations where each directive may be used.

However if you can manage the server configuration, then the solution to your problem would have been to define the DocumentRoot for each virtual server to point to the directory where the WP site was located.  You cannot do this from .htaccess either since the DocumentRoot is already determined to be the directory where the .htaccess would reside.

---

### Post by CharlesA on 2013-05-09
> **satimis said:**
> 
Do serverdragon.com has MediaWiki installed on their site?  Hostgator has this application which I expect.

They have an [knowledge base]("https://my.securedragon.net/knowledgebase.php") and their support is very responsive. Granted I had a simple question, but I got a response in less than 5 minutes when I contacted them the other day.

With that being said, they might not be the biggest VPS provider, but they were cheap and were recommended to me by a member here.

With my current VPS plan, I've got a 512MB VPS with 20GB of HDD space, and 1TB of bandwidth for 54.99 a year.

The ironic part about that is that is around the price I was paying for my shared hosting originally.

---

### Post by sandyd on 2013-05-09
> **satimis said:**
> Absolutely agreed.  I have been struggling at least 3 weeks.  Godaddy Suppot only turned me around.  Each time to my request for support they just copied and pasted the online document on their emails as reply.

Now I have sorted out my problem.

To make multi-domains to work on WordPress(WP) perform steps as follow;
(I'm not going to mention "Hosted Domains" setup here)

1) Install WP on a directory/folder of the domain (not root/webroot)
say, aaa.com (directory)

2) Create a directory /aaa.com/wpaaa for WP and install WP on it

3) After installation completed and effective, go to File Manager.  Copy both .htaccess and index.php on /aaa.com directory

4) On index.php 

change the line - require('./wp-blog-header.php');

to - require('./wpaaa/wp-blog-header.php');

reload the page.  That is all, not necessary touching .htaccess


On browser running [http://www.aaa.com](http://www.aaa.com) or /aaa.com displays WP front page.  That's it.

However to login WP it still requires full path, /aaa.com/wpaaa/wp-admin.  I haven't found a solution yet,.

Edit:

Do serverdragon.com has **MediaWiki installed on their site**?  Hostgator has this application which I expect.

B.R.
satimis

If you open a new topic in server platforms on how to setup MediaWiki, you will probably get instructions :D

What I reccomend: Use Nginx instead of Apache
Nginx with PHP5-FPM uses much less RAM then the standard Apache2+mod_php, and will make it easier to fit in the 512MB that CharlesA mentioned (CharlesA currently runs Nginx on that VPS)

There is an easy guide to getting nginx working with wordpress here -> [http://codex.wordpress.org/Nginx](http://codex.wordpress.org/Nginx)

---

### Post by CharlesA on 2013-05-10
> **sandyd said:**
> 
What I reccomend: Use Nginx instead of Apache
Nginx with PHP5-FPM uses much less RAM then the standard Apache2+mod_php, and will make it easier to fit in the 512MB that CharlesA mentioned (CharlesA currently runs Nginx on that VPS)

+1. I could probably even get it to run well on a 256MB VPS, but I bumped it up to 512 because I was messing with iRedMail (which used Apache, and a bunch of other stuff I didn't really need).

I'll check the memory usage when I get home, but it's nowhere near 256MB used.

---

### Post by satimis on 2013-05-10
> **CharlesA said:**
> They have an [knowledge base]("https://my.securedragon.net/knowledgebase.php") and their support is very responsive. Granted I had a simple question, but I got a response in less than 5 minutes when I contacted them the other day.
Noted with thanks

satimis

---

### Post by satimis on 2013-05-10
> **sandyd said:**
> If you open a new topic in server platforms on how to setup MediaWiki, you will probably get instructions

- snip -

Thanks for your advice.

I already have MediaWiki installed on my server running on LAMP.  Installation was straight-forwards without difficulty.  But if the service provider for web-hosting don't have MediaWiki installed can I install a copy of MediaWiki on their server which is NOT absolutely under my controller?

satimis

---

### Post by sandyd on 2013-05-10
> **satimis said:**
> Thanks for your advice.

I already have MediaWiki installed on my server running on LAMP.  Installation was straight-forwards without difficulty.  But if the service provider for web-hosting don't have MediaWiki installed can I install a copy of MediaWiki on their server which is NOT absolutely under my controller?

satimis

If your using CPanel, you just need to export the database with phpmyadmin, and download the mediawiki files thru ftp

---

### Post by satimis on 2013-05-10
> **sandyd said:**
> If your using CPanel, you just need to export the database with phpmyadmin, and download the mediawiki files thru ftp
Thanks for your advice.

I doubt whether Godaddy would allow me to install MediaWiki upload to their server.

On searching I found some good news and bad news as well.

MediaWiki 1.20.4
[http://hostingconnection.godaddy.com/Application/MediaWiki.aspx](http://hostingconnection.godaddy.com/Application/MediaWiki.aspx)

I just tested it.  Seemingly Godaddy allowed me installing MediaWiki.  I'll create a subdomain testing it.

Also I found following links;

MediaWiki on Godaddy.com servers
[http://www.gossamer-threads.com/lists/wiki/mediawiki/46825](http://www.gossamer-threads.com/lists/wiki/mediawiki/46825)

Manual:Installation guide
[http://www.mediawiki.org/wiki/Manual:Installation_guide](http://www.mediawiki.org/wiki/Manual:Installation_guide)

ISPs - MediaWiki at GoDaddy 
[http://mc-computing.com/ISPs/MediaWiki.html](http://mc-computing.com/ISPs/MediaWiki.html)

Generating a sitemap for MediaWiki hosted on GoDaddy
Posted on September 13, 2008
[http://jjhale.com/blog/2008/09/generating-a-sitemap-for-mediawiki-hosted-on-godaddy/](http://jjhale.com/blog/2008/09/generating-a-sitemap-for-mediawiki-hosted-on-godaddy/)

A folk failed installing MediaWiki on Godaddy's server

satimis

---

### Post by satimis on 2013-05-10
Hi sandyd and folks,

I successfully installed MediaWiki on Gododdy.  No complaint popup during installation.  They notified me on email;```

MediaWiki is ready.
MediaWiki 1.20.4 is installed and ready for your personal touch.
IMPORTANT INFO
MediaWiki login:
http://wiki.satimis.com/mwsat/
Hosting account:
Log in
....

```

But I could not start MediaWiki and login.

On browser running;
```

http://wiki.satimis.com/mwsat/

```
Server not found.

index.php is found on /wiki.satimis.com/mwsat/

MediaWiki was installed on /wiki.satimis.com/mwsat/ directory.  I'm now fiddling around for a solution.  Any suggestion?  TIA


Edit:
Do I need to install WordPress ???

B.R.
satimis

---

### Post by sandyd on 2013-05-10
Not familiar with GoDaddy but you need to create a DNS record (A/CNAME) to point the subdomain towards the server.

---

### Post by CharlesA on 2013-05-10
> **sandyd said:**
> Not familiar with GoDaddy but you need to create a DNS record (A/CNAME) to point the subdomain towards the server.

+1. If you want to test it before messing with DNS, you can add an entry to your hosts file:

/etc/hosts
c:\windows\system32\drivers\etc\hosts

You shouldn't need wordpress unless you are going to be blogging or using it for a CMS.

EDIT:
Even though it doesn't look like you are going to be going the VPS route:
> **CharlesA said:**
> 
I'll check the memory usage when I get home, but it's nowhere near 256MB used.

Memory usage is currently sitting at 29MB out of 512 with 0 swap usage.
The VPS in question is running Nginx, dovecot and postfix.

---

### Post by satimis on 2013-05-10
> **sandyd said:**
> Not familiar with GoDaddy but you need to create a DNS record (A/CNAME) to point the subdomain towards the server.
I have 5 domains setup/running on Godaddy.  

On Zone File Editor;
All of them point to the same IP address at A (Host)

On the local copy of MediaWiki, on browser running;```

http://localhost/mediawiki/

```

it popup;
```

http://localhost/mediawiki/index.php/Main_Page

```
displaying the Main Page of MediaWiki

---

### Post by satimis on 2013-05-10
> **CharlesA said:**
> +1. If you want to test it before messing with DNS, you can add an entry to your hosts file:

/etc/hosts
c:\windows\system32\drivers\etc\hosts
Sorry I don't follow.  The local copy of MediaWiki is running on Ubuntu 12.04.  Godaddy's is supposed running on Linux

satimis

---

### Post by sandyd on 2013-05-10
> **satimis said:**
> I have 5 domains setup/running on Godaddy.  

On Zone File Editor;
All of them point to the same IP address at A (Host)

On the local copy of MediaWiki, on browser running;```

http://localhost/mediawiki/

```

it popup;
```

http://localhost/mediawiki/index.php/Main_Page

```
displaying the Main Page of MediaWiki
```

sandyd@sandyd-devel:~$ dig @ns31.domaincontrol.com wiki.satimis.com

; <<>> DiG 9.9.2-P1 <<>> @ns31.domaincontrol.com wiki.satimis.com
; (2 servers found)
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NXDOMAIN, id: 42938
;; flags: qr aa rd; QUERY: 1, ANSWER: 0, AUTHORITY: 1, ADDITIONAL: 1
;; WARNING: recursion requested but not available

;; OPT PSEUDOSECTION:
; EDNS: version: 0, flags:; udp: 4096
;; QUESTION SECTION:
;wiki.satimis.com.              IN      A

;; AUTHORITY SECTION:
satimis.com.            3600    IN      SOA     ns31.domaincontrol.com. dns.jomax.net. 2013051002 28800 7200 604800 600

;; Query time: 93 msec
;; SERVER: 216.69.185.16#53(216.69.185.16)
;; WHEN: Fri May 10 13:34:00 2013
;; MSG SIZE  rcvd: 113
```

I dont know what godaddy is doing, but im pretty sure their not doing it right.
```

sandyd@sandyd-devel:~$ dig @8.8.8.8 wiki.satimis.com

; <<>> DiG 9.9.2-P1 <<>> @8.8.8.8 wiki.satimis.com
; (1 server found)
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NXDOMAIN, id: 12052
;; flags: qr rd ra; QUERY: 1, ANSWER: 0, AUTHORITY: 1, ADDITIONAL: 1

;; OPT PSEUDOSECTION:
; EDNS: version: 0, flags:; udp: 512
;; QUESTION SECTION:
;wiki.satimis.com.              IN      A

;; AUTHORITY SECTION:
satimis.com.            1795    IN      SOA     ns31.domaincontrol.com. dns.jomax.net. 2013051002 28800 7200 604800 600

;; Query time: 108 msec
;; SERVER: 8.8.8.8#53(8.8.8.8)
;; WHEN: Fri May 10 13:33:02 2013
;; MSG SIZE  rcvd: 113

sandyd@sandyd-devel:~$ 

```

---

### Post by VinDSL on 2013-05-10
> **satimis said:**
> [...] any other suggestions?  TIA
Well... I'll try to keep it short.

I've been on the web, since the last century... and ran a BBS for years before that, before Al Gore invented the Internet.

I won't bore you with all the hardware/software combinations that I've used.  Suffice to say, I've been around the track a few times.

I cannot run my sites on conventional web hosting.  I typically get 100K page views on my production web site (give_or_take) and the combined traffic has brought down every shared server I've been on.  Plus, I don't run canned software.  I've had to hack everything, to keep the perps at bay, so I need unrestricted freedom to change the core files, as necessary.

Having said that, the only place I've found that can handle it all -- from lowly shared hosting, to fully-managed dedicated web servers, is JaguarPC.  That's my highly considered recommendation.

I'm about halfway up the food chain -- with room to expand:  [http://www.jaguarpc.com/hybrid-server/](http://www.jaguarpc.com/hybrid-server/)

Been working great, for the past couple of years.  And, when I start killing that server, I won't need to change hosts.  I'll just need to upgrade the level of service -- dedi or colo, probably.

Oh, BTW, MediaWiki is powering one of my sites.  MediaWiki doesn't work all that great without Squish, but it's fast enough for serving pics.  That's all I use MediaWiki for nowadays -- serving screen shots.  LoL!  :D

Wikis are a PITA!  You need to watch, like a hawk, or the pron bots will take control of your site.  I got tired of spending all my time dialing it back.  So, I locked it down, and use it for a pic server.

Here's a demo:


[INDENT][[IMG]http://vindsl.com/images/vindsl-desktop-9-may-2013-1(650x520).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-9-may-2013-1.png")[/INDENT]


Overkill, using MediaWiki for this, but it works, so...

Okay, I'll quit now.  JagPC for the win!

---

### Post by VinDSL on 2013-05-10
> **d4m1r said:**
> No such thing as unlimited bandwidth, storage, etc. All servers including those run by the big guys have limitations.
True!

One of the many, many, ways 'they' get you is by limiting inodes to 100K (give_or_take)

Read 'em & weep:  [https://startpage.com/do/search?query=inode+limit](https://startpage.com/do/search?query=inode+limit)

I can get by with 400K inodes, but a million is better!

That's what JagPC support gave me.  And, they said, if/when that isn't enough, let them know. ;)

---

### Post by VinDSL on 2013-05-10
> **satimis said:**
> I have my own server here running on virtualizer.  I'm subscribing Static/Fixed IP at 6M/6M up/down.  It would be quite easy for me operating my own server at home.
I don't know about your ISP, but...

My ISP considers that an unauthorized redistribution of their bandwidth and services.  And, they'll red-flag your account, in a heartbeat, if they catch you.

Around here, if you want to run servers in your home, you are expected to get a business account.

Just saying...  ;)

---

### Post by CharlesA on 2013-05-10
> **satimis said:**
> Sorry I don't follow.  The local copy of MediaWiki is running on Ubuntu 12.04.  Godaddy's is supposed running on Linux

satimis

If you want to test the *remote* site before messing with the DNS entries, you can add an entry to either your hosts file or your local dns and test it that way.

> **VinDSL said:**
> I don't know about your ISP, but...

My ISP considers that an unauthorized redistribution of their bandwidth and services.  And, they'll red-flag your account, in a heartbeat, if they catch you.

Around here, if you want to run servers in your home, you are expected to get a business account.

Just saying...  ;)

Same thing happens here and they block port 25 and 80 because of it.

---

### Post by satimis on 2013-05-10
> **sandyd said:**
> ```

sandyd@sandyd-devel:~$ dig @ns31.domaincontrol.com wiki.satimis.com

; <<>> DiG 9.9.2-P1 <<>> @ns31.domaincontrol.com wiki.satimis.com
; (2 servers found)
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NXDOMAIN, id: 42938
;; flags: qr aa rd; QUERY: 1, ANSWER: 0, AUTHORITY: 1, ADDITIONAL: 1
;; WARNING: recursion requested but not available

;; OPT PSEUDOSECTION:
; EDNS: version: 0, flags:; udp: 4096
;; QUESTION SECTION:
;wiki.satimis.com.              IN      A

;; AUTHORITY SECTION:
satimis.com.            3600    IN      SOA     ns31.domaincontrol.com. dns.jomax.net. 2013051002 28800 7200 604800 600

;; Query time: 93 msec
;; SERVER: 216.69.185.16#53(216.69.185.16)
;; WHEN: Fri May 10 13:34:00 2013
;; MSG SIZE  rcvd: 113
```

I dont know what godaddy is doing, but im pretty sure their not doing it right.
```

sandyd@sandyd-devel:~$ dig @8.8.8.8 wiki.satimis.com

; <<>> DiG 9.9.2-P1 <<>> @8.8.8.8 wiki.satimis.com
; (1 server found)
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NXDOMAIN, id: 12052
;; flags: qr rd ra; QUERY: 1, ANSWER: 0, AUTHORITY: 1, ADDITIONAL: 1

;; OPT PSEUDOSECTION:
; EDNS: version: 0, flags:; udp: 512
;; QUESTION SECTION:
;wiki.satimis.com.              IN      A

;; AUTHORITY SECTION:
satimis.com.            1795    IN      SOA     ns31.domaincontrol.com. dns.jomax.net. 2013051002 28800 7200 604800 600

;; Query time: 108 msec
;; SERVER: 8.8.8.8#53(8.8.8.8)
;; WHEN: Fri May 10 13:33:02 2013
;; MSG SIZE  rcvd: 113

sandyd@sandyd-devel:~$ 

```
I have 5 domains setup/running on Godaddy;

reynoldstocks.com (WordPress(WP) installed)
wiki.reynoldstocks.com (MediaWiki installed)
satimis.com (WP installed)
food.satimis.com (WP installed)
wiki.satimis.com (MediaWiki installed)

(no website has been built yet)

I can browse;
reynoldstocks.com
satimis.com
food.satimis.com

but can't ping them on terminal.  I can ping their IP address (all same address on Godaddy website)

(remark:
several years ago.  I set up a server box running Oracle VirtualBox/KVM as virtualizer.  All web/mail servers pointed to different internal IP but used same(one) public IP.  I made it work.  It is not easy.  I suppose Godaddy is doing the same arrangement)

To login WP I have to run on browser;
reynoldstocks.com/wordpress/wp-admin
satimis.com/WPSat/wp-admin
food.satimis.com/WPFood/wp-admin

but I can't ping them on terminal, unknown host.
reynoldstocks.com
satimis.com
food.satimis.com

12 packets transmitted, 0 received, 100% packet loss

MediaWiki has been installed on;
wiki.reynoldstocks.com 
wiki.satimis.com

Godaddy notified me on email;
1)
wiki.reynoldstocks.com 
MediaWiki is ready.
MediaWiki 1.20.4 is installed and ready for your personal touch.
IMPORTANT INFO
MediaWiki login:```

http://wiki.reynoldstocks.com/

```
Hosting account:
Log in

2)
MediaWiki is ready.
MediaWiki 1.20.4 is installed and ready for your personal touch.
IMPORTANT INFO
MediaWiki login:
```

http://wiki.satimis.com/mwsat/

```
Hosting account:
Log in

But I can't browse them.  Server not found

On terminal I can ping;
yahoo.com
google.com

without problem.  I'm now contacting Godaddy.

satimis

---

### Post by satimis on 2013-05-11
> **CharlesA said:**
> If you want to test the *remote* site before messing with the DNS entries, you can add an entry to either your hosts file or your local dns and test it that way.

- snip -

I got it.  Thanks

satimis

---

### Post by CharlesA on 2013-05-11
FYI, MediaWiki 1.20.5 was released a couple weeks ago.

I checked my site and it looks way different from the way Godaddy has your DNS set up, but if it works, it works.

---

### Post by sandyd on 2013-05-11
> **satimis said:**
> I have 5 domains setup/running on Godaddy;

reynoldstocks.com (WordPress(WP) installed)
wiki.reynoldstocks.com (MediaWiki installed)
satimis.com (WP installed)
food.satimis.com (WP installed)
wiki.satimis.com (MediaWiki installed)

(no website has been built yet)

I can browse;
reynoldstocks.com
satimis.com
food.satimis.com

but can't ping them on terminal.  I can ping their IP address (all same address on Godaddy website)

(remark:
several years ago.  I set up a server box running Oracle VirtualBox/KVM as virtualizer.  All web/mail servers pointed to different internal IP but used same(one) public IP.  I made it work.  It is not easy.  I suppose Godaddy is doing the same arrangement)

To login WP I have to run on browser;
reynoldstocks.com/wordpress/wp-admin
satimis.com/WPSat/wp-admin
food.satimis.com/WPFood/wp-admin

but I can't ping them on terminal, unknown host.
reynoldstocks.com
satimis.com
food.satimis.com

12 packets transmitted, 0 received, 100% packet loss

MediaWiki has been installed on;
wiki.reynoldstocks.com 
wiki.satimis.com

Godaddy notified me on email;
1)
wiki.reynoldstocks.com 
MediaWiki is ready.
MediaWiki 1.20.4 is installed and ready for your personal touch.
IMPORTANT INFO
MediaWiki login:```

http://wiki.reynoldstocks.com/

```
Hosting account:
Log in

2)
MediaWiki is ready.
MediaWiki 1.20.4 is installed and ready for your personal touch.
IMPORTANT INFO
MediaWiki login:
```

http://wiki.satimis.com/mwsat/

```
Hosting account:
Log in

But I can't browse them.  Server not found

On terminal I can ping;
yahoo.com
google.com

without problem.  I'm now contacting Godaddy.

satimis

There is no A/CNAME record for wiki.satimis.com, which is why you cant ping.

---

### Post by satimis on 2013-05-11
> **CharlesA said:**
> FYI, MediaWiki 1.20.5 was released a couple weeks ago.

I checked my site and it looks way different from the way Godaddy has your DNS set up, but if it works, it works.
Whether you meant following file ???
mediawiki-1.20.5/includes/DefaultSettings.php

Version MediaWiki 1.20.4 is installed on Godaddy

MediaWiki 1.15.5-7 is installed on my local pc.  I can evoke it running;
```

http://localhost/mediawiki

```

then it refers to;
```

http://localhost/mediawiki/index.php/Main_Page
```

satimis

---

### Post by CharlesA on 2013-05-11
> **sandyd said:**
> There is no A/CNAME record for wiki.satimis.com, which is why you cant ping.

That would be why it looks different. :)

@ satimis:
Unless you upgraded the install of mediawiki that godaddy installed, you would still need to get it updated. A list of changed between 1.20.4 and 1.20.5 are here:
[http://www.mediawiki.org/wiki/Release_notes/1.20#MediaWiki_1.20.5](http://www.mediawiki.org/wiki/Release_notes/1.20#MediaWiki_1.20.5)

---

### Post by satimis on 2013-05-11
> **sandyd said:**
> There is no A/CNAME record for wiki.satimis.com, which is why you cant ping.
DNS Manager
Zone File Editor

(all domains)```

A (Host)	
Host		Points to
@		IP address

CNAME (alias)
Host		Points to
www		@

```

Where shall I edit?  Thanks


Edit:
Just received a reply from Godaddy```

Some of our servers are configured to ignore ping requests.

With the new installations on subdomains, the appropriate DNS records might not have been automatically updated. You may need to manually update the DNS settings for the domain. The records should look something like this:

Host: wiki
Points to: [Hosting IP address]

This article explains how to work with the DNS settings of your domain name:

http://support.godaddy.com/help/article/680/managing-dns-for-your-domain-names

```

Whether;```

CNAME (alias)
Host		Points to
wiki   	@

```

not;```

Host	   Points to
www   @

```
?

satimis

---

### Post by lisati on 2013-05-11
The layout is a bit different to that of my domain provider. Having said that, I would suggest that you put your server's *public* IP address in the space labelled **IP address**, the line dealing with "@".

---

### Post by satimis on 2013-05-11
> **lisati said:**
> The layout is a bit different to that of my domain provider. Having said that, I would suggest that you put your server's *public* IP address in the space labelled **IP address**, the line dealing with "@".

Changed made on wiki.satimis.com
A (Host)	```

Host		Points to
@		IP address

```
replace @ with wiki.satimis.com
(it changed back to @ automatically at saving Zone File)

CNAME (alias)```

Host		Points to
www		@

```
change www to wiki
change @ to IP address (warning popup.  It is only allowed adding either @ or wiki.satimis.com here)

-> Save Zone File
```

Your changes have been submitted.
These changes usually take 1 hour. However, it may take up to 48 hours for these changes to take effect. These time frames are estimates and not guaranteed.

```
-> OK

satimis

---

### Post by rewyllys on 2013-05-11
With respect to this thread's title, ". . . advice on web hosting company", I can report that I've had excellent service and support from Simple Online Solutions, whose URL is:

[http://www.simpleurl.com/](http://www.simpleurl.com/)

It is a small company that has stayed in business for 16 years by giving personalized service.  I've gotten quick responses, and easily understandable, very helpful explanations that have solved all the few problems I had in setting up my domain about a year ago.

---

### Post by satimis on 2013-05-11
> **rewyllys said:**
> With respect to this thread's title, ". . . advice on web hosting company", I can report that I've had excellent service and support from Simple Online Solutions, whose URL is:

[http://www.simpleurl.com/](http://www.simpleurl.com/)

It is a small company that has stayed in business for 16 years by giving personalized service.  I've gotten quick responses, and easily understandable, very helpful explanations that have solved all the few problems I had in setting up my domain about a year ago.
Thanks for your advice.

Do they offer multsite hosting?
What applications are available?  WordPress? MediaWiki? any others?

---

### Post by rewyllys on 2013-05-11
> **satimis said:**
> Thanks for your advice.

Do they offer multsite hosting?
What applications are available?  WordPress? MediaWiki? any others?
Since I'm not sure about the answers to your questions, I'd suggest that the best way to get answers would probably be to go their Website, look for how to contact them, and then ask them your questions directly.

---

### Post by rewyllys on 2013-05-11
> **VinDSL said:**
> Well... I'll try to keep it short.

I've been on the web, since the last century... and ran a BBS for years before that, before Al Gore invented the Internet.

I won't bore you with all the hardware/software combinations that I've used.  Suffice to say, I've been around the track a few times.

I cannot run my sites on conventional web hosting.  I typically get 100K page views on my production web site (give_or_take) and the combined traffic has brought down every shared server I've been on.  Plus, I don't run canned software.  I've had to hack everything, to keep the perps at bay, so I need unrestricted freedom to change the core files, as necessary.

Having said that, the only place I've found that can handle it all -- from lowly shared hosting, to fully-managed dedicated web servers, is JaguarPC.  That's my highly considered recommendation.

I'm about halfway up the food chain -- with room to expand:  [http://www.jaguarpc.com/hybrid-server/](http://www.jaguarpc.com/hybrid-server/)

Been working great, for the past couple of years.  And, when I start killing that server, I won't need to change hosts.  I'll just need to upgrade the level of service -- dedi or colo, probably.

Oh, BTW, MediaWiki is powering one of my sites.  MediaWiki doesn't work all that great without Squish, but it's fast enough for serving pics.  That's all I use MediaWiki for nowadays -- serving screen shots.  LoL!  :D

Wikis are a PITA!  You need to watch, like a hawk, or the pron bots will take control of your site.  I got tired of spending all my time dialing it back.  So, I locked it down, and use it for a pic server.

Here's a demo:
[INDENT][[IMG]http://vindsl.com/images/vindsl-desktop-9-may-2013-1(650x520).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-9-may-2013-1.png")[/INDENT]


Overkill, using MediaWiki for this, but it works, so...

Okay, I'll quit now.  JagPC for the win!
VinDSL, I'd very much appreciate it if you would tell me how to get a copy of the wallpaper you used in your Ubuntu 13.10 desktop.  It's a gorgeous picture.  What bridge is it that is so beautifully night-lighted?

Thanks in advance for your response.

---

### Post by mike acker on 2013-05-12
I use CoreComm
thier Beginners' package is like $15 per quarter

---

### Post by VinDSL on 2013-05-12
> **rewyllys said:**
> VinDSL, I'd very much appreciate it if you would tell me how to get a copy of the wallpaper you used in your Ubuntu 13.10 desktop.  It's a gorgeous picture.  What bridge is it that is so beautifully night-lighted?

Thanks in advance for your response.
Sorry it took so long to reply!  I'm on the trot, right now, going from airport_to_airport.  Still several hours from home...

I'm not sure where I got that wall, but TinEye is showing:  [http://love-hotel.jp/sysimg/cms/100516103250_da7c3f.JPG](http://love-hotel.jp/sysimg/cms/100516103250_da7c3f.JPG)

Wherever I got it, I worked it over with GiMP, so...

Hrm... let me check my Dropbox... nope, don't see it in there.

Anyway, if you can't find a larger image, let me know, and I'll attach it to a thread in the Cafe, when I get back home, to my desktop box.  ;)

---

### Post by rewyllys on 2013-05-23
> **VinDSL said:**
> Sorry it took so long to reply!  I'm on the trot, right now, going from airport_to_airport.  Still several hours from home...

I'm not sure where I got that wall, but TinEye is showing:  [http://love-hotel.jp/sysimg/cms/100516103250_da7c3f.JPG](http://love-hotel.jp/sysimg/cms/100516103250_da7c3f.JPG)

Wherever I got it, I worked it over with GiMP, so...

Hrm... let me check my Dropbox... nope, don't see it in there.

Anyway, if you can't find a larger image, let me know, and I'll attach it to a thread in the Cafe, when I get back home, to my desktop box.  ;)
VinDSL, thanks for your response.  

Using the URL you provided, I've searched several hundred pictures of cable bridges in Japan as yielded by searching in Google Images, searching on "cable bridges Japan" and "cable stay bridges Japan", but without success.  I've also searched on "cable bridges" and "cable stay bridges", again looking through several hundred images, also without success. 

So, if you can provide any further suggestions after you've gotten home, I'll be very grateful.

Thanks again.

---

### Post by rewyllys on 2013-05-23
VinDSL, after considerable further searching, I've identified the bridge as the Meiko Chuo Bridge, Nagoya, Japan.  (The name translates as "Big Central Bridge".)

But after further searching for images of that particular bridge, I haven't yet found any with beauty comparable to the image in your desktop. 

So I'll eagerly await further information after you've gotten home.

---

### Post by VinDSL on 2013-05-23
Give this a shot...  ;)

LINK"  [http://wallpoper.com/wallpaper/cityscapes-night-395854](http://wallpoper.com/wallpaper/cityscapes-night-395854)

---

### Post by rewyllys on 2013-05-24
VinDSL, many, many thanks for your help.:popcorn:

I now have that gorgeous scene as my laptop wallpaper.

(BTW, I see that you're in Arizona.  I grew up in Tempe in the 1930s and 1940s, when -- believe it or not -- the population was only around 2,500.)

---

### Post by VinDSL on 2013-05-24
My pleasure!

Thanks, for performing the forensics.

I wondered about the name and location of that bridge...  ;)

---

