---
title: "Configuring Apache2 Virtual Hosts and gnump3d"
date: 2007-03-14
forum: Server Platforms
---

### Post by dfreer on 2007-03-14
Hey everyone, 

So I got my website up and running thanks to ubuntuforums help. Now I am trying to configure it to do some spiffy stuff.

I've been messing around with virtual hosts for apache, and I was wondering if there was a way to bind a port to a virtual host. Specifically, I'm running gnump3d on port 8888, which I currently access using [http://www.dfreer.org:8888](http://www.dfreer.org:8888). I was wondering if I could bind it to [http://gnump3d.dfreer.org](http://gnump3d.dfreer.org), and how I would be able to do that. I tried modifying my /etc/apache2/sites-enabled/000-default to this:

<VirtualHost *:8888>
       ServerName gnump3d.dfreer.org
       DocumentRoot    /var/music/
       <Directory />
               Options FollowSymLinks
               AllowOverride None
       </Directory>
</VirtualHost>

But it didn't work :(

On a side note, I wish to change the default directory behavior for video files. Currently, if I click on the video's file name directly, it links me to the .avi/.mov/.*** file itself. If I click on the [Info] link next to the file name, it shows me a short description and presents me with an option to [Play Track], which is the file with a .m3u extension. I would like to be able to reverse this, so that ALL video files when directly clicked are part of an .m3u playlist, if it is possible. I tried to email the developer but I haven't gotten a response :(

---

### Post by MJN on 2007-03-14
Just change the **8888** to **80** and you should be good to go.
 
For your other questions I don't know as I'm not familiar with GNUMP.
 
Mathew

---

### Post by dfreer on 2007-03-14
> Just change the 8888 to 80 and you should be good to go.
In my /etc/apache2/sites-enabled/000-default? This doesn't sound like a good idea, although I gave it a try:
```
$ sudo /etc/init.d/apache2 restart
 * Forcing reload of apache 2.0 web server...                                   
[Wed Mar 14 06:41:08 2007] [error] VirtualHost *:80 -- mixing * ports and non-* ports with a NameVirtualHost address is not supported, proceeding with undefined results
```

I also tried changing the default port in the /etc/gnump3d/gnump3d.conf file from 8888 to 80, JUST in case you meant that (didn't work, btw).

gnump3d runs it's own http server, from what I understand of it (it doesn't require that you install apache)...
It has no default settings in the apache2 directory, the <VirtualHost *:8888> part of the config file *I* wrote and put in there in attempts to bind it to gnump3d.dfreer.org.

---

### Post by MJN on 2007-03-14
> **dfreer said:**
> gnump3d runs it's own http server, from what I understand of it (it doesn't require that you install apache)...
It has no default settings in the apache2 directory, the <VirtualHost *:8888> part of the config file *I* wrote and put in there in attempts to bind it to gnump3d.dfreer.org.
 
Ah okay... I thought you'd just modified the Apache snippet that Gnump had created. I didn't realise it provided its own service (I thought it my just be a PHP-based solution running via Apache).
 
As I have no Gnump experience the rest is just guessing... but given that you say there's a port setting on Gnump's config file I'm surprised that doesn't work. Have you tried changing it to something else, say 81, just so you can rule out any conflict with other services (Apache in particular) that might already be listening on port 80?
 
Mathew

---

### Post by dfreer on 2007-03-14
Thanks for helping, btw.

> but given that you say there's a port setting on Gnump's config file I'm surprised that doesn't work. Have you tried changing it to something else, say 81, just so you can rule out any conflict with other services (Apache in particular) that might already be listening on port 80? 
gnump3d does work on port 8888, and I'm pretty sure it will work on port 81 (although I can test that if you think it would help). I believe that is the problem with changing the gnump3d default port to 80, is that it conflicted with my Apache service. 

What I am trying to do here is basically link [http://www.dfreer.org:8888](http://www.dfreer.org:8888) (or :81 if that would help) to [http://gnump3d.dfreer.org](http://gnump3d.dfreer.org). This makes things easier for proxy servers to access (for some reason the proxy I'm using strips the :8888 everytime I change pages), and also make the website just cleaner in general.

---

### Post by MJN on 2007-03-14
Okay, so you're running Apache anyway for your 'main' site - and this is running on port 80.
 
It's not possible to have two services listening on the same port (I think it's as clear cut as that - happy to be told otherwise) and so you won't be able to have Gnump also running on port 80.
 
If Gnump was being served by Apache then you would of course have no troubles - the different name in the URL would suffice to differentiate the two sites even though they're both on port 80. However, as it doesn't this info is of little use to you!
 
However, Apache might still be able to help by utilising the **mod_proxy** module. I don't use it myself but have vague recollections that this type of thing is what it can be used for so either do some searching or hang around for someone with mod_proxy experience to tell you how to achieve it...
 
Good luck!
 
Mathew
 
P.S. A quick search suggests something like the following might work: (having enabled mod_proxy with **sudo** **a2enmod proxy**)
 
```

<VirtualHost *:80>
ServerName gnump.dfreer.org
[FONT=Courier New]ProxyRequests Off[/FONT]
ProxyPass / [http://gnump.dfreer.org:8888/](http://gnump.dfreer.org:8888/)
ProxyPassReverse / [http://gnump.dfreer.org:8888/](http://gnump.dfreer.org:8888/)
</VirtualHost>
 
(note that the ProxyRequests Off may sound counter-intuitive
however this is just stopping your server acting as a proxy for
any destination, i.e. only those specified are valid.
See [http://httpd.apache.org/docs/2.0/mod/mod_proxy.html](http://httpd.apache.org/docs/2.0/mod/mod_proxy.html) for further details)

```
 
Incidentally, does your current <VirtualHost *:**?**> line have port 80 specified? It ought to if only to get rid of the uncertainty that the earlier error message alluded to.

---

### Post by dfreer on 2007-03-14
> Incidentally, does your current <VirtualHost *:?> line have port 80 specified? It ought to if only to get rid of the uncertainty that the earlier error message alluded to.
Well, that particular error message only appeared when I tried mapping the virtual host gnump3d to the same port as my default website, that error has not reappeared.

I read up on apache's docs on the mod_proxy and in particular [*_ProxyRemote_*]("http://httpd.apache.org/docs/2.0/mod/mod_proxy.html#proxyremote") . It seems like this is certainly possible, only question is on how to configure my virtual hosts?

I tried your code, and I also added the following line: 
        ErrorLog /var/log/apache2/gnump3d.error.log
This way I can see exactly what errors I'm getting. When I go to [http://gnump3d.dfreer.org](http://gnump3d.dfreer.org), I get an error in my web browser saying "You do not have the permissions to view /" I tried again using 127.0.0.1 instead of gnump3d.dfreer.org with the same results.

The error's in my custom error log"
[Wed Mar 14 09:09:22 2007] [error] [client 10.1.10.103] client denied by server configuration: proxy:[http://127.0.0.1:8888/](http://127.0.0.1:8888/)
[Wed Mar 14 09:10:48 2007] [error] [client 10.1.10.103] client denied by server configuration: proxy:[http://gnump3d.dfreer.org:8888/](http://gnump3d.dfreer.org:8888/)

Hmmm... well, I tried using the gnump3d default media directory /var/music instead of / that's listed in your original code. Somewhat success; I am able to navigate to [http://gnump3d.dfreer.org](http://gnump3d.dfreer.org), but the gnump3d server is not running (apache is just listing the contents of the directory).

Here is my /etc/apache2/sites-enabled/000-default:
```
$ sudo vi /etc/apache2/sites-enabled/000-default 
NameVirtualHost *
<VirtualHost *>
	ServerName www.dfreer.org
	DocumentRoot /var/www
	ErrorLog /var/log/apache2/error.log
	CustomLog /var/log/apache2/access.log combined
</VirtualHost>

<VirtualHost *>
        ServerName torrentflux.dfreer.org
        DocumentRoot    /localhd/torrentflux/
</VirtualHost>

<VirtualHost *>
	ServerName gnump3d.dfreer.org
	DocumentRoot	/var/music/
	ProxyRequests Off
	ProxyPass /var/music/ http://gnump3d.dfreer.org:8888/
	ProxyPassReverse /var/music/ http://gnump3d.dfreer.org:8888/
	ErrorLog /var/log/apache2/gnump3d.error.log
</VirtualHost>

```

---

### Post by dfreer on 2007-03-14
I would think this would be useful to just about anyone. From what I understand SSL uses port 453... so If I can get this figured out you should be able to have [http://insecure.yoursite.com](http://insecure.yoursite.com) and [https://secure.yoursite.com](https://secure.yoursite.com) without having to specifiy the ports... but maybe not, that's just my understanding of the issue.

---

### Post by MJN on 2007-03-14
As things currently stand your gnump virtual host is being ignored as a connection to [http://gnump.dfreer.org](http://gnump.dfreer.org) is serving the same content as your default site.
 
I would recommend slowing down a little as small hiccups shouldn't bounce you onto the next carriageway! Go back to my initial suggestion for the proxy config and let's iron out the hiccups... It could well be the default Apache access control taking effect (as we haven't overridden it).
 
Using SSL might be an acceptable workaround (it's port 443 by the way) however I can't see any reason the proxy method won't work and create the 'perfect' solution (i.e. only requiring name differentiation between URLs). The http: and https: prefixes imply to the client that you want to connect port 80 or 443 respectively so there's no proxying involved/required.
 
Mathew
 
P.S. More searching... try:
 
```

<Directory proxy:[COLOR=#0000ff]_http://gnump3d.dfreer.org:8888/_[/COLOR]>
 Order Allow,Deny
 Allow from all
</Directory>

```

---

### Post by dfreer on 2007-03-15
I am having a hard time understanding exactly what you wish me to do with this code:
```
<Directory proxy:http://gnump3d.dfreer.org:8888/>
 Order Allow,Deny
 Allow from all
</Directory>
```
Is this in addition to the previous code, replace the previous code, etc? I'm willing to try anything you suggest, but I don't know where you want me to put it... Let me post my original /etc/apache2/sites-enabled/000-default file, before I started this project:

```
NameVirtualHost *
<VirtualHost *>
        ServerName www.dfreer.org
        ServerAdmin daniel_freer@hotmail.com

        DocumentRoot /var/www
        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>
        <Directory /var/www/>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride None
                Order allow,deny
                allow from all
                # Uncomment this directive is you want to see apache2's
                # default start page (in /apache2-default) when you go to /
                #RedirectMatch ^/$ /apache2-default/
        </Directory>

        ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
        <Directory "/usr/lib/cgi-bin">
                AllowOverride None
                Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
                Order allow,deny
                Allow from all
        </Directory>

        ErrorLog /var/log/apache2/error.log

        # Possible values include: debug, info, notice, warn, error, crit,
        # alert, emerg.
        LogLevel warn

        CustomLog /var/log/apache2/access.log combined
        ServerSignature On

    Alias /doc/ "/usr/share/doc/"
    <Directory "/usr/share/doc/">
        Options Indexes MultiViews FollowSymLinks
        AllowOverride None
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>
</VirtualHost>

<VirtualHost *>
        ServerName torrentflux.dfreer.org
        DocumentRoot    /localhd/torrentflux/
        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>
        ErrorLog        /var/log/apache2/torrentflux.error.log
</VirtualHost>
```

Perhaps I could try adding specific code, testing if it works, and if it doesn't I want to then start back with the original file. I think this will make things eaiser to sort where to add replace code.  

Sorry that it took so long to reply, I had to work today and am working on this project when I really should be sleeping (it's almost 5 am lol).

---

### Post by MJN on 2007-03-15
No problem...

I've slotted the various bits in:

```

NameVirtualHost *
<VirtualHost *>
        ServerName www.dfreer.org
        ServerAdmin daniel_freer@hotmail.com

        DocumentRoot /var/www
        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>
        <Directory /var/www/>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride None
                Order allow,deny
                allow from all
                # Uncomment this directive is you want to see apache2's
                # default start page (in /apache2-default) when you go to /
                #RedirectMatch ^/$ /apache2-default/
        </Directory>

        ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
        <Directory "/usr/lib/cgi-bin">
                AllowOverride None
                Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
                Order allow,deny
                Allow from all
        </Directory>

        ErrorLog /var/log/apache2/error.log

        # Possible values include: debug, info, notice, warn, error, crit,
        # alert, emerg.
        LogLevel warn

        CustomLog /var/log/apache2/access.log combined
        ServerSignature On

    Alias /doc/ "/usr/share/doc/"
    <Directory "/usr/share/doc/">
        Options Indexes MultiViews FollowSymLinks
        AllowOverride None
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>
</VirtualHost>

<VirtualHost *>
        ServerName torrentflux.dfreer.org
        DocumentRoot    /localhd/torrentflux/
        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>
        ErrorLog        /var/log/apache2/torrentflux.error.log
</VirtualHost>

[B]<VirtualHost *>
        ServerName gnump.dfreer.org
[/B]**        AccessLog /var/log/apache2/gnump3d.access.log**
        [B]ErrorLog /var/log/apache2/gnump3d.error.log
        ProxyRequests Off
        ProxyPass / http://gnump.dfreer.org:8888/
        ProxyPassReverse / http://gnump.dfreer.org:8888/
[/B][B]
        <Directory proxy:http://gnump3d.dfreer.org:8888/>
                [/B][B]Order Allow,Deny
        [/B][B]        Allow from all
        [/B][B]</Directory>
</VirtualHost>
[/B]

```

---

### Post by dfreer on 2007-03-16
Ok, I pasted in the code exactly as shown and did a *sudo apache2ctl graceful*. I recieved this error message:
```
Syntax error on line 60 of /etc/apache2/sites-enabled/000-default:
Invalid command 'AccessLog', perhaps mis-spelled or defined by a module not included in the server configuration
```

So I commented out this line : *AccessLog /var/log/apache2/gnump3d.access.log*

Apache restarted, and I went to view [http://gnump3d.dfreer.org](http://gnump3d.dfreer.org). I found myself looking at my default webpage. Since I have been having problems with host name resolutions on my local LAN (see [_*this thread*_]("http://www.ubuntuforums.org/showthread.php?t=380451")), I figured I would try the same thing using [_*freeproxy.ca*_]("http://www.freeproxy.ca/"). Same thing.

I looked over the code you sent me, and noticed at some places you use gnump3d and at other places you use gnump. This might be part of the problem, and since I want the page to be gnump3d I changed all references to gnump to gnump3d. The final code thus far looks like this:
```
<VirtualHost *>
        ServerName gnump3d.dfreer.org
#       AccessLog /var/log/apache2/gnump3d.access.log
        ErrorLog /var/log/apache2/gnump3d.error.log
        ProxyRequests Off
        ProxyPass / http://gnump3d.dfreer.org:8888/
        ProxyPassReverse / http://gnump3d.dfreer.org:8888/

        <Directory proxy:http://gnump3d.dfreer.org:8888/>
                Order Allow,Deny
                Allow from all
        </Directory>
</VirtualHost>
```
freeproxy.ca and my laptop show gnump3d.dfreer.org to show my main webpage. Here's my gnump3d.error.log:
```

[Fri Mar 16 01:06:35 2007] [error] [client 209.172.57.70] client denied by server configuration: proxy:http://gnump3d.dfreer.org:8888/, referer: http://gnump3d.dfreer.org
[Fri Mar 16 01:06:46 2007] [error] [client 10.1.10.103] client denied by server configuration: proxy:http://gnump3d.dfreer.org:8888/-/includes/style/lagoona/aqua/body-bg.gif, referer: http://gnump3d.dfreer.org/
[Fri Mar 16 01:06:46 2007] [error] [client 10.1.10.103] client denied by server configuration: proxy:http://gnump3d.dfreer.org:8888/-/includes/style/lagoona/aqua/header.jpg, referer: http://gnump3d.dfreer.org/
[Fri Mar 16 01:06:46 2007] [error] [client 10.1.10.103] client denied by server configuration: proxy:http://gnump3d.dfreer.org:8888/-/includes/style/lagoona/aqua/footer-bg.gif, referer: http://gnump3d.dfreer.org/
[Fri Mar 16 01:06:49 2007] [error] [client 10.1.10.103] client denied by server configuration: proxy:http://gnump3d.dfreer.org:8888/-/includes/style/lagoona/aqua/body-bg.gif, referer: http://gnump3d.dfreer.org/
[Fri Mar 16 01:06:49 2007] [error] [client 10.1.10.103] client denied by server configuration: proxy:http://gnump3d.dfreer.org:8888/-/includes/style/lagoona/aqua/header.jpg, referer: http://gnump3d.dfreer.org/
[Fri Mar 16 01:06:49 2007] [error] [client 10.1.10.103] client denied by server configuration: proxy:http://gnump3d.dfreer.org:8888/-/includes/style/lagoona/aqua/footer-bg.gif, referer: http://gnump3d.dfreer.org/
[Fri Mar 16 01:06:57 2007] [error] [client 209.172.57.70] client denied by server configuration: proxy:http://gnump3d.dfreer.org:8888/, referer: http://gnump3d.dfreer.org
[Fri Mar 16 01:07:01 2007] [error] [client 209.172.57.70] client denied by server configuration: proxy:http://gnump3d.dfreer.org:8888/, referer: http://gnump3d.dfreer.org
[Fri Mar 16 01:08:44 2007] [error] [client 10.1.10.103] client denied by server configuration: proxy:http://gnump3d.dfreer.org:8888/-/includes/style/lagoona/aqua/body-bg.gif, referer: http://gnump3d.dfreer.org/
[Fri Mar 16 01:08:44 2007] [error] [client 10.1.10.103] client denied by server configuration: proxy:http://gnump3d.dfreer.org:8888/-/includes/style/lagoona/aqua/header.jpg, referer: http://gnump3d.dfreer.org/
[Fri Mar 16 01:08:44 2007] [error] [client 10.1.10.103] client denied by server configuration: proxy:http://gnump3d.dfreer.org:8888/-/includes/style/lagoona/aqua/footer-bg.gif, referer: http://gnump3d.dfreer.org/
[Fri Mar 16 01:08:46 2007] [error] [client 10.1.10.103] client denied by server configuration: proxy:http://gnump3d.dfreer.org:8888/-/includes/style/lagoona/aqua/body-bg.gif, referer: http://gnump3d.dfreer.org/
[Fri Mar 16 01:08:46 2007] [error] [client 10.1.10.103] client denied by server configuration: proxy:http://gnump3d.dfreer.org:8888/-/includes/style/lagoona/aqua/header.jpg, referer: http://gnump3d.dfreer.org/
[Fri Mar 16 01:08:46 2007] [error] [client 10.1.10.103] client denied by server configuration: proxy:http://gnump3d.dfreer.org:8888/-/includes/style/lagoona/aqua/footer-bg.gif, referer: http://gnump3d.dfreer.org/
[Fri Mar 16 01:08:50 2007] [error] [client 209.172.57.70] client denied by server configuration: proxy:http://gnump3d.dfreer.org:8888/, referer: http://gnump3d.dfreer.org
[Fri Mar 16 01:13:47 2007] [error] [client 209.172.57.70] client denied by server configuration: proxy:http://gnump.dfreer.org:8888/, referer: http://gnump.dfreer.org
[Fri Mar 16 01:13:56 2007] [error] [client 209.172.57.70] client denied by server configuration: proxy:http://gnump.dfreer.org:8888/, referer: http://gnump.dfreer.org
[Fri Mar 16 01:14:07 2007] [error] [client 10.1.10.103] client denied by server configuration: proxy:http://gnump.dfreer.org:8888/
[Fri Mar 16 01:14:07 2007] [error] [client 10.1.10.103] client denied by server configuration: proxy:http://gnump.dfreer.org:8888/favicon.ico
[Fri Mar 16 01:15:57 2007] [error] [client 10.1.10.103] client denied by server configuration: proxy:http://gnump.dfreer.org:8888/favicon.ico
[Fri Mar 16 01:21:57 2007] [error] [client 10.1.10.103] client denied by server configuration: proxy:http://gnump3d.dfreer.org:8888/-/includes/style/lagoona/aqua/body-bg.gif, referer: http://gnump3d.dfreer.org/
[Fri Mar 16 01:21:57 2007] [error] [client 10.1.10.103] client denied by server configuration: proxy:http://gnump3d.dfreer.org:8888/-/includes/style/lagoona/aqua/header.jpg, referer: http://gnump3d.dfreer.org/
[Fri Mar 16 01:21:57 2007] [error] [client 10.1.10.103] client denied by server configuration: proxy:http://gnump3d.dfreer.org:8888/-/includes/style/lagoona/aqua/footer-bg.gif, referer: http://gnump3d.dfreer.org/
[Fri Mar 16 01:22:03 2007] [error] [client 10.1.10.103] client denied by server configuration: proxy:http://gnump3d.dfreer.org:8888/-/includes/style/lagoona/aqua/body-bg.gif, referer: http://gnump3d.dfreer.org/
[Fri Mar 16 01:22:03 2007] [error] [client 10.1.10.103] client denied by server configuration: proxy:http://gnump3d.dfreer.org:8888/-/includes/style/lagoona/aqua/header.jpg, referer: http://gnump3d.dfreer.org/
[Fri Mar 16 01:22:03 2007] [error] [client 10.1.10.103] client denied by server configuration: proxy:http://gnump3d.dfreer.org:8888/-/includes/style/lagoona/aqua/footer-bg.gif, referer: http://gnump3d.dfreer.org/

```

The /-/includes/style/lagoona/aqua/header.jpg refer to an image background on my main page that no longer exists, I've been meaning to clean it up but have been busy :) Also, I'm pretty sure the IP:209.172.57.70 is the proxy server. I did notice some 403 "You do not have permission to view / on this Server", but for some reason I can't get them to reproduce reliably. Most of the time it goes straight to my main webpage...

Due to that hostname resolution on the LAN problem, I set up my /etc/hosts like so (on the laptop, not the web server):
```
10.1.10.102     www.dfreer.org torrentflux.dfreer.org gnump.dfreer.org gnump3d.dfreer.org

```

Whereas 10.1.10.102 is my server, and 10.1.10.103 is my laptop.
Messy, I know, but I haven't found a better solution for resolving the hostnames besides configuring my own DNS server. But that's a problem for another thread.

---

### Post by MJN on 2007-03-16
> **dfreer said:**
> Ok, I pasted in the code exactly as shown and did a *sudo apache2ctl graceful*. I recieved this error message
<snip>
So I commented out this line : *AccessLog /var/log/apache2/gnump3d.access.log*

 
Sorry, my mistake. It should be **CustomLog**
 
> I looked over the code you sent me, and noticed at some places you use gnump3d and at other places you use gnump.
 
Again sloppiness on my part. The name should of course be consistent throughout.
 
To be honest, as you've probably gathered by now I'm stabbing in the dark here. It might be better if someone with some experience of mod_proxy steps in to walk you through the process. Whilst I can't solve it I do recognise that it's a trivial problem you're trying to solve here and we are likely just tripping up on the dotting the i's and crossing the t's, particularly with regards to ensuring the permisions are set just right.
 
So, anyone used mod_proxy before and can take the lead...?
 
Mathew

---

