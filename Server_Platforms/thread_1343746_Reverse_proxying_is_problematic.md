---
title: "Reverse proxying is problematic"
date: 2009-12-02
forum: Server Platforms
---

### Post by Treeh on 2009-12-02
**I know this is a long read...but I really need help, and felt the best way for anyone to help me remotely is to explain the issues in their entirety.**

Also, I know this is SUSE Linux and not Ubuntu...but it's virtually the same thing with Apache and you guys have been pretty awesome in the past for all my Ubuntu needs, so I figured it wouldn't hurt to ask here.

Hello,

I'm trying to set a reverse proxy, but first, some context:

My office is subscribed to few academic journals. These journals verify the subscription via IP, such that anyone connected to the internet through our connection can access the journals. However, some individuals would like to access the journals away from the office as well. We have a VPN, but it only connects them to our intranet. Therefore, we want to create a reverse proxy such that the users with connect to the VPN, then to our intranet, and then to the proxy server, and then, ultimately, to the journal at hand. This works because the proxy server will be within our intranet, which they have access to through the VPN. So it will look like so:

Client --> VPN --> Our Intranet --> Reverse Proxy --> Journal

Note that I'm an intern and have had very little experience with Apache and networking in general (and Linux!)...so please explain things fully.

I have attempted to follow this guide: [http://www.apachetutor.org/admin/reverseproxies](http://www.apachetutor.org/admin/reverseproxies)

I'm running SUSE Linux Enterprise 11, and have installed apache through zypper. I installed the mod_proxy_html and mod_xml2enc modules via compiling. They are fully functional. (mod_proxy_html to rewrite links).

In the examples below I'm attempting to reverse proxy both [http://aip.org](http://aip.org) and [http://apl.aip.org](http://apl.aip.org). So basically want I want to do is have anything that is [http://aip.org/somepage.html](http://aip.org/somepage.html) to be [http://proxysrv1/aip/somepage.html](http://proxysrv1/aip/somepage.html) and anything that is [http://apl.aip.org](http://apl.aip.org) to be [http://proxysrv1/apl/somepage.html](http://proxysrv1/apl/somepage.html). All of the content on the page must go through the proxy (note: I know that many of the links lead to other sub-domains, I will include those as well...but later, I figured I should get these two working first). Please do not suggest a different server application like Squid, I'm required to use Apache.

So far, I have the following modifications to the http.conf file:

```

Include /etc/apache2/vhosts.d/*.conf

ProxyHTMLEnable On
ProxyHTMLExtended On

ProxyHTMLLinks  a               href
ProxyHTMLLinks  area            href
ProxyHTMLLinks  link            href
ProxyHTMLLinks  img             src longdesc usemap
ProxyHTMLLinks  object          classid codebase data usemap
ProxyHTMLLinks  q               cite
ProxyHTMLLinks  blockquote      cite
ProxyHTMLLinks  ins             cite
ProxyHTMLLinks  del             cite
ProxyHTMLLinks  form            action
ProxyHTMLLinks  input           src usemap
ProxyHTMLLinks  head            profile
ProxyHTMLLinks  base            href
ProxyHTMLLinks  script          src for
ProxyHTMLLinks  iframe          src

ProxyHTMLEvents onclick ondblclick onmousedown onmouseup \
                onmouseover onmousemove onmouseout onkeypress \
                onkeydown onkeyup onfocus onblur onload \
                onunload onsubmit onreset onselect onchange

ProxyRequests Off
ProxyPass /aip/ http://aip.org/
ProxyPassReverse /aip/ http://aip.org/
ProxyHTMLURLMap http://www.aip.org http://proxysrv1/aip
ProxyPass /apl/ http://apl.aip.org/
ProxyPassReverse /apl/ http://apl.aip.org/
ProxyHTMLURLMap http://apl.aip.org http://proxysrv1/apl

<Location /aip/>
        ProxyHTMLEnable On
        ProxyHTMLExtended On
        ProxyPassReverse /
        ProxyHTMLURLMap / /
        RequestHeader unset Accept-Encoding
</Location>

<Location /apl/>
        ProxyHTMLEnable On
        ProxyHTMLExtended On
        ProxyPassreverse /
        ProxyHTMLURLMap / /
        RequestHeader unset Accept-Encoding
</Location>

ProxyHTMLLogVerbose On
LogLevel Info


```

And the following modifications to the vhost.conf file:

```

NameVirtualHost *:80

<VirtualHost *:80>
    ServerName proxysrv1
    DocumentRoot /srv/www/htdocs
    HostnameLookups Off
    UseCanonicalName On

    ServerSignature On
    <Directory "/srv/www/htdocs">
        Options Indexes All
        AllowOverride None
        Order allow,deny
        Allow from all
    </Directory>
</VirtualHost>


<VirtualHost *:80>
        Documentroot /srv/www/htdocs/aip
        Servername proxysrv1/aip
        HostnameLookups Off
        UseCanonicalName On
        ServerSignature On
        <Directory "/srv/www/htdocs/aip">

                Options Indexes All
                AllowOverride None
                Order allow,deny
                Allow from all
        </Directory>
</VirtualHost>


<VirtualHost *:80>

        Documentroot /srv/www/htdocs/apl
        Servername proxysrv1/apl
        HostnameLookups Off
        UseCanonicalName On
        ServerSignature On
        <Directory "/srv/www/htdocs/apl">

                Options Indexes All
                AllowOverride None
                Order allow,deny
                Allow from all
        </Directory>
</VirtualHost>


```

The mass of issues:

1) [http://proxysrv1/aip/](http://proxysrv1/aip/) looks like this: 
[IMG]http://imgur.com/n6m0L.png[/IMG]

The page source: [http://paste.ubuntu.com/333007/](http://paste.ubuntu.com/333007/)

Instead of [http://aip.org](http://aip.org)

2) [http://proxysrv1/apl/](http://proxysrv1/apl/) looks like this: 
[IMG]http://imgur.com/mNv92.png[/IMG]

The page source: [http://paste.ubuntu.com/333009/](http://paste.ubuntu.com/333009/)

Instead of [http://apl.aip.org](http://apl.aip.org)

3) I created a virtual host & proxy at [http://proxysrv1/apl/](http://proxysrv1/apl/), yet links like [http://apl.aip.org/about/about_the_journal](http://apl.aip.org/about/about_the_journal)

redirect to [http://proxysrv/about/about_the_journal](http://proxysrv/about/about_the_journal) rather than [http://proxysrv/apl/about/about_the_journal](http://proxysrv/apl/about/about_the_journal)


4) All the pages look like crap. I had aip.org working previously, but only if I set its directory to / (so by going to [http://proxysrv1/](http://proxysrv1/) you went to aip.org/), 

and had no virtual hosts.

5) That's actually all I can think of. But the pages are pretty darn broken. 

Please explain any fixes in a step-by-step process. Again, I'm new to this.

---

### Post by shirubia on 2009-12-02
Hi, I was having a similar problem. (And still am actually.. sorta). I got it rendering things correctly by putting this in:

```
ProxyPass / http://www.apple.com/
ProxyPassReverse / http://www.apple.com/
SetOutputFilter INFLATE;proxy-html;DEFLATE
ProxyHTMLURLMap / /
```

When I browse to my server: 192.168.0.123/ it takes me strait to apples website, however. when I modify the code to this:

```
ProxyPass /test/ http://www.apple.com/
ProxyPassReverse /test/ http://www.apple.com/
SetOutputFilter INFLATE;proxy-html;DEFLATE
ProxyHTMLURLMap / /test/
```

and go to: 192.168.0.123/test/ everything renders wrong, links are broken etc.. I'm back here to find a solution..

heres my original post (it worked with google's site): 

[http://ubuntuforums.org/showthread.php?p=8277618#post8277618](http://ubuntuforums.org/showthread.php?p=8277618#post8277618)

---

### Post by shirubia on 2009-12-18
Were you able to find a solution?

---

### Post by t4thfavor on 2010-01-24
Also looking for a solution..

---

### Post by BkkBonanza on 2010-01-24
You're doing this the way hard way. Don't use Apache proxying for this.

You can do what you want very simply with ssh and it's SOCKS proxy built in.

Any user who can connect to a ssh server inside your network can then use it to access out via your network's connection, and hence appear to be using your IP.

To do this they can use VPN or even not VPN since ssh is secure on it's own.

Let's say you have a server in your network running ssh at mydomain.com port 2345.

Any user on the web connects to it with,

ssh -D 8080 -p 2345 [email]userid@mydomain.com[/email] -N

(if you use port 22 then you don't need -p option)
(you can automate this with a script or use gSTM gui tool to make it easier)
(you can use a key instead of a password if you like)

Now your user sets Firefox to use SOCKS5 proxy at localhost:8080 (same port as indicated above but can be any port you like).

That's it. Your user is now proxying through your ssh server to the net via your office net IP. 

...

The only thing that could make this easier is if gSTM would auto-set the Firefox proxy but the author of that tool stopped short of that useful feature. It hasn't been updated in years. gSTM is in the Ubuntu repos though.

---

