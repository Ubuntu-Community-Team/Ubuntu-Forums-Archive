---
title: "apache 2 redirect to another server"
date: 2009-10-23
forum: Server Platforms
---

### Post by Dave.Wynne on 2009-10-23
I've got a 3 server domain. one is PDC, Web, File, etc. and the other is a dedicated mail and webmail server.
 
What I'm doing at the moment is a bit ugly I have the web on port 80 and webmail on port 8080.
 
I'm a complete newbie with apache 2 with IIS this is no problem.
 What I'd like to do is create a link from [www.mydomain.com/mail]("http://www.mydomain.com/mail") to //mymailserver/webmail. I'm sure this is an easy thing to do, but reading the apache2 website I get lost.
 
Anyone got a quick howto?

---

### Post by cdenley on 2009-10-23
First of all, what is with the UNC path? Is it a web server you're trying to "link" to? Do you want [http://www.mydomain.com/mail](http://www.mydomain.com/mail) to simply redirect to [http://mymailserver/webmail](http://mymailserver/webmail)? If so, mymailserver must either be an IP address directly accessible by any user attempting to access it, or a domain which resolves to such an IP.

If you cannot allow direct access to your webmail server from outside your LAN, then you will need to proxy connections. This basically routes all traffic to/from your webmail server through your web server.

---

### Post by Dave.Wynne on 2009-10-23
> **cdenley said:**
> First of all, what is with the UNC path? Is it a web server you're trying to "link" to? Do you want [http://www.mydomain.com/mail](http://www.mydomain.com/mail) to simply redirect to [http://mymailserver/webmail](http://mymailserver/webmail)? If so, mymailserver must either be an IP address directly accessible by any user attempting to access it, or a domain which resolves to such an IP.
 
If you cannot allow direct access to your webmail server from outside your LAN, then you will need to proxy connections. This basically routes all traffic to/from your webmail server through your web server.
 
Sorry Yes I want to redirect to [http://mymailserver/webmail](http://mymailserver/webmail). Resolving the IP is not an issue. what I don't know is what to do with apache 2. I like the sound of using a proxy though, how would I go about setting it up. 
 
My system has a router which is set up to port forward; port 80 to the domain server, port 25, 143 & 8080 (*presently*) to mail server. I would like to close port 8080 and connect solely through my domain server.

---

### Post by cdenley on 2009-10-24
> **Dave.Wynne said:**
> Sorry Yes I want to redirect to [http://mymailserver/webmail](http://mymailserver/webmail). Resolving the IP is not an issue. what I don't know is what to do with apache 2. I like the sound of using a proxy though, how would I go about setting it up. 
 
My system has a router which is set up to port forward; port 80 to the domain server, port 25, 143 & 8080 (*presently*) to mail server. I would like to close port 8080 and connect solely through my domain server.

Well, redirecting to [http://mymailserver:8080/webmail](http://mymailserver:8080/webmail) would be much more efficient, but if you want to go the proxy route:

add this to your vhost config
(probably /etc/apache2/sites-available/default)
```

ProxyRequests Off
<Proxy *>
Order deny,allow
Allow from all
</Proxy>

ProxyPass /mail http://mymailserver:8080/webmail
ProxyPassReverse /mail http://mymailserver:8080/webmail 

```
```

sudo a2enmod proxy
sudo /etc/init.d/apache2 restart

```

[http://httpd.apache.org/docs/2.2/mod/mod_proxy.html](http://httpd.apache.org/docs/2.2/mod/mod_proxy.html)

---

### Post by Dave.Wynne on 2009-10-25
> **cdenley said:**
> Well, redirecting to [http://mymailserver:8080/webmail](http://mymailserver:8080/webmail) would be much more efficient, but if you want to go the proxy route:
 
add this to your vhost config
(probably /etc/apache2/sites-available/default)
```

ProxyRequests Off
<Proxy *>
Order deny,allow
Allow from all
</Proxy>
 
ProxyPass /mail http://mymailserver:8080/webmail
ProxyPassReverse /mail http://mymailserver:8080/webmail 

```
```

sudo a2enmod proxy
sudo /etc/init.d/apache2 restart

```
 
[http://httpd.apache.org/docs/2.2/mod/mod_proxy.html](http://httpd.apache.org/docs/2.2/mod/mod_proxy.html)
 
I tried above except I changed it to real values and this is the result.
```

**Internal Server Error**

The server encountered an internal error or misconfiguration and was unable to complete your request.
Please contact the server administrator, webmaster@localhost and inform them of the time the error occurred, and anything you might have done that may have caused the error.
More information about this error may be available in the server error log.
Apache/2.2.11 (Ubuntu) Server at www.artimech.com.au Port 80
```
 
this what I actually put in /etc/apache2/sites-available/default
```
    </Directory>
        ProxyRequests Off
        <Proxy *>
        Order deny,allow
        Allow from all
        </Proxy>
        ProxyPass /exchange [http://192.168.0.20:8080/groupware](http://192.168.0.20:8080/groupware)
        ProxyPassReverse /exchange [http://192.168.0.20:8080/groupware](http://192.168.0.20:8080/groupware)
</VirtualHost>
```
 
What have I done wrong?

---

### Post by cdenley on 2009-10-25
Did you enable the proxy module and restart apache? What is in /var/log/apache2/error.log?

---

### Post by Vegan on 2009-10-25
The easiest way to redirect HTTP is with a standard redirect.

---

### Post by cdenley on 2009-10-25
> **Vegan said:**
> The easiest way to redirect HTTP is with a standard redirect.
He doesn't want a redirect, he wants a proxy.
> **Dave.Wynne said:**
> I like the sound of using a proxy though, how would I go about setting it up.

---

### Post by Dave.Wynne on 2009-10-25
> **cdenley said:**
> Did you enable the proxy module and restart apache? What is in /var/log/apache2/error.log?
 
This is the output rom my log.
[html][Sun Oct 25 16:25:42 2009] [warn] proxy: No protocol handler was valid for the URL /exchange. If you are using a DSO version of mod_proxy, make sure the proxy submodules are included in the configuration using LoadModule.
[Sun Oct 25 16:26:28 2009] [error] [client 65.55.106.179] File does not exist: /var/www/robots.txt
[Sun Oct 25 16:27:18 2009] [notice] caught SIGTERM, shutting down
[Sun Oct 25 16:27:19 2009] [notice] Apache/2.2.11 (Ubuntu) configured -- resuming normal operations
[Sun Oct 25 16:27:33 2009] [warn] proxy: No protocol handler was valid for the URL /exchange. If you are using a DSO version of mod_proxy, make sure the proxy submodules are included in the configuration using LoadModule.
[Sun Oct 25 16:27:39 2009] [warn] proxy: No protocol handler was valid for the URL /exchange. If you are using a DSO version of mod_proxy, make sure the proxy submodules are included in the configuration using LoadModule.
[Sun Oct 25 16:37:27 2009] [notice] caught SIGTERM, shutting down
[Sun Oct 25 16:38:27 2009] [notice] Apache/2.2.11 (Ubuntu) configured -- resuming normal operations
[Sun Oct 25 16:40:12 2009] [warn] proxy: No protocol handler was valid for the URL /exchange. If you are using a DSO version of mod_proxy, make sure the proxy submodules are included in the configuration using LoadModule.
[/html]
 
There seems to be some confusion as to what I want.
If a simple redirect will work I'll do it. I would like to close the port that acesses my mail server, (*I'm a bit paranoid we has had a windows 2000 server for nearly 10 years, and it was hacked an a daily basis for all of that time. This time I've tried to make it as secure as I can.*)

---

### Post by cdenley on 2009-10-26
I guess you need to enable another module.
```

sudo a2enmod proxy_http
sudo /etc/init.d/apache2 restart

```

Or, if you want to go the redirect route:
```

Redirect /mail http://mymailserver:8080/webmail

```
then make sure the alias module is enabled
```

sudo a2enmod alias
sudo /etc/init.d/apache2 restart

```

---

### Post by Dave.Wynne on 2009-10-26
> **cdenley said:**
> I guess you need to enable another module.
```

sudo a2enmod proxy_http
sudo /etc/init.d/apache2 restart

```
 
Or, if you want to go the redirect route:
```

Redirect /mail http://mymailserver:8080/webmail

```
then make sure the alias module is enabled
```

sudo a2enmod alias
sudo /etc/init.d/apache2 restart

```
 
 
 
Went the quick root and enabled the extra module and still no joy, unfortunately I'm on holidays in Japan and I.E. on the machine I'm using is in Japanese so....[html][IMG]res://ieframe.dll/info_48.png[/IMG] **Internet Explorer &#12391;&#12399;&#12371;&#12398;&#12506;&#12540;&#12472;&#12399;&#34920;&#31034;&#12391;&#12365;&#12414;&#12379;&#12435;**
 
    **&#21487;&#33021;&#24615;&#12398;&#12354;&#12427;&#21407;&#22240;:**
 
&#12452;&#12531;&#12479;&#12540;&#12493;&#12483;&#12488;&#12395;&#25509;&#32154;&#12373;&#12428;&#12390;&#12356;&#12394;&#12356;&#12290; Web &#12469;&#12452;&#12488;&#12395;&#21839;&#38988;&#12364;&#30330;&#29983;&#12375;&#12390;&#12356;&#12427;&#12290; &#12450;&#12489;&#12524;&#12473;&#12395;&#20837;&#21147;&#12398;&#38291;&#36949;&#12356;&#12364;&#12354;&#12427;&#21487;&#33021;&#24615;&#12364;&#12354;&#12427;&#12290;   **&#23550;&#20966;&#26041;&#27861;:**
 
  **[IMG]res://ieframe.dll/bullet.png[/IMG] &#25509;&#32154;&#12398;&#21839;&#38988;&#12434;&#35386;&#26029; **
 
  **[IMG]res://ieframe.dll/down.png[/IMG] &#35443;&#32048;&#24773;&#22577;**
 
 
&#12371;&#12398;&#21839;&#38988;&#12399;&#20197;&#19979;&#12434;&#21547;&#12416;&#27096;&#12293;&#12394;&#21407;&#22240;&#12395;&#12424;&#12426;&#30330;&#29983;&#12375;&#12414;&#12377;: &#12452;&#12531;&#12479;&#12540;&#12493;&#12483;&#12488;&#25509;&#32154;&#12364;&#20999;&#26029;&#12373;&#12428;&#12383;&#12290; Web &#12469;&#12452;&#12488;&#12364;&#19968;&#26178;&#30340;&#12395;&#21033;&#29992;&#12391;&#12365;&#12394;&#12356;&#12290; &#12489;&#12513;&#12452;&#12531; &#12493;&#12540;&#12512; &#12469;&#12540;&#12496;&#12540; (DNS) &#12395;&#21040;&#36948;&#12391;&#12365;&#12394;&#12356;&#12290; &#12489;&#12513;&#12452;&#12531; &#12493;&#12540;&#12512; &#12469;&#12540;&#12496;&#12540; (DNS) &#12395;&#12289;&#12371;&#12398; Web &#12469;&#12452;&#12488;&#12398;&#12489;&#12513;&#12452;&#12531;&#21517;&#12398;&#19968;&#35239;&#12364;&#12394;&#12356;&#12290; &#12371;&#12428;&#12364; HTTPS (&#23433;&#20840;&#12394;) &#12450;&#12489;&#12524;&#12473;&#12391;&#12354;&#12427;&#22580;&#21512;&#12289;[&#12484;&#12540;&#12523;]&#12289;[&#12452;&#12531;&#12479;&#12540;&#12493;&#12483;&#12488; &#12458;&#12503;&#12471;&#12519;&#12531;]&#12289;[&#35443;&#32048;&#35373;&#23450;] &#12398;&#38918;&#12395;&#12463;&#12522;&#12483;&#12463;&#12375;&#12390;&#12289;[&#12475;&#12461;&#12517;&#12522;&#12486;&#12451;] &#12398;&#38917;&#30446;&#12398;&#19979;&#12395;&#12354;&#12427;&#12289;SSL &#12392; TLS &#12398;&#12503;&#12525;&#12488;&#12467;&#12523;&#12364;&#26377;&#21177;&#12395;&#12394;&#12387;&#12390;&#12356;&#12427;&#12371;&#12392;&#12434;&#30906;&#35469;&#12375;&#12390;&#12367;&#12384;&#12373;&#12356;&#12290; 
&#12458;&#12501;&#12521;&#12452;&#12531;&#12398;&#12518;&#12540;&#12470;&#12540;&#12395;&#12399;
 
&#36092;&#35501;&#12373;&#12428;&#12383;&#12501;&#12451;&#12540;&#12489;&#12362;&#12424;&#12403;&#26368;&#36817;&#34920;&#31034;&#12375;&#12383; Web &#12506;&#12540;&#12472;&#12434;&#12356;&#12367;&#12388;&#12363;&#34920;&#31034;&#12377;&#12427;&#12371;&#12392;&#12364;&#12391;&#12365;&#12414;&#12377;&#12290;
&#36092;&#35501;&#12373;&#12428;&#12383;&#12501;&#12451;&#12540;&#12489;&#12434;&#34920;&#31034;&#12377;&#12427;&#12395;&#12399; [&#12362;&#27671;&#12395;&#20837;&#12426;&#12475;&#12531;&#12479;&#12540;] &#12398;&#12508;&#12479;&#12531;[IMG]res://ieframe.dll/favcenter.png[/IMG]&#12434;&#12463;&#12522;&#12483;&#12463;&#12375;&#12390; &#12289;[&#12501;&#12451;&#12540;&#12489;] &#12434;&#12463;&#12522;&#12483;&#12463;&#12375;&#12390;&#12363;&#12425;&#12289;&#34920;&#31034;&#12377;&#12427;&#12501;&#12451;&#12540;&#12489;&#12434;&#12463;&#12522;&#12483;&#12463;&#12375;&#12390;&#12367;&#12384;&#12373;&#12356;&#12290; 
&#26368;&#36817;&#34920;&#31034;&#12375;&#12383; Web &#12506;&#12540;&#12472;&#12434;&#34920;&#31034;&#12377;&#12427;&#12395;&#12399; (&#21205;&#20316;&#12375;&#12394;&#12356;&#12506;&#12540;&#12472;&#12418;&#12354;&#12426;&#12414;&#12377;) [&#12484;&#12540;&#12523;] [IMG]res://ieframe.dll/tools.png[/IMG]&#12434;&#12463;&#12522;&#12483;&#12463;&#12375;&#12390;&#12363;&#12425; [&#12458;&#12501;&#12521;&#12452;&#12531;&#20316;&#26989;] &#12434;&#12463;&#12522;&#12483;&#12463;&#12375;&#12390;&#12367;&#12384;&#12373;&#12356;&#12290; [&#12362;&#27671;&#12395;&#20837;&#12426;&#12475;&#12531;&#12479;&#12540;] &#12398;&#12508;&#12479;&#12531;[IMG]res://ieframe.dll/favcenter.png[/IMG]&#12434;&#12463;&#12522;&#12483;&#12463;&#12375;&#12390;&#12289;[&#23653;&#27508;] &#12434;&#12463;&#12522;&#12483;&#12463;&#12375;&#12390;&#12363;&#12425;&#12289;&#34920;&#31034;&#12377;&#12427;&#12506;&#12540;&#12472;&#12434;&#12463;&#12522;&#12483;&#12463;&#12375;&#12390;&#12367;&#12384;&#12373;&#12356;&#12290; 
[/html]
 
I'll get the translation in the morning, from my missus. Which means one more day of your time for which I am extremely greateful

---

### Post by cdenley on 2009-10-26
```

<Proxy *>
Order deny,allow
Allow from all
</Proxy>

ProxyPass / http://internalserver/
ProxyPassReverse / http://internalserver/

```
This works for me. With these modules enabled:
[LIST]
[*]alias
[*]auth_basic
[*]authn_file
[*]authz_default
[*]authz_groupfile
[*]authz_host
[*]authz_user
[*]autoindex
[*]cgi
[*]dir
[*]env
[*]mime
[*]negotiation
[*]php5
[*]proxy_http
[*]proxy
[*]setenvif
[*]ssl
[*]status
[/LIST]

You should only need proxy and proxy_http.

---

### Post by Dave.Wynne on 2009-10-26
> **cdenley said:**
> I guess you need to enable another module.
```

sudo a2enmod proxy_http
sudo /etc/init.d/apache2 restart

```
 
Or, if you want to go the redirect route:
```

Redirect /mail http://mymailserver:8080/webmail

```
then make sure the alias module is enabled
```

sudo a2enmod alias
sudo /etc/init.d/apache2 restart

```
 
Went tthe second route using redirect and it works but I'll have to keep port 8080 open unless you can help! As I said I'll ask the boss in the morning.
 
On an other matter I have a new thread that you could perhaps help with
[http://ubuntuforums.org/showthread.php?t=1301464](http://ubuntuforums.org/showthread.php?t=1301464)

---

### Post by Dave.Wynne on 2009-10-26
I think I've worked out what the problem is, I'm not running a DNS server, *at present* and so the web server is looking outside for my IP address and so not connecting. so either I'll have to set up my own DNS or go the redirect route.
 
I'm not sure if it is a big deal to set up a DNS in Linux, I suppose I'd only have to add 1 address in the forward lookup as I'm using netbios for my domain. Any thoughts?

---

### Post by ildella on 2009-11-05
I am having the same problem. I have enabled both proxy and proxy_http, and enabled a new site with this descriptor in the file sites-available/ildella.net

<VirtualHost *:80>

ProxyRequests Off
ProxyPreserveHost On

<Proxy *>
    Order deny,allow
    Allow from all
</Proxy>

ProxyPass /newsletter [http://danieledellafiore:8080/newsletter](http://danieledellafiore:8080/newsletter)
ProxyPassReverse /newsletter [http://danieledellafiore:8080/newsletter](http://danieledellafiore:8080/newsletter)

</VirtualHost>

I note that in every guide and help, no one ever talk about this line:

<VirtualHost *:80>

is that right? And it seems that defining this site, along with enabling it and enabling the proxy module, is enough. Nothing to to on the other side (jetty, in my scenario)?

Now, if I do:

ildella /etc/apache2: a2enmod proxy_http
Considering dependency proxy for proxy_http:
Module proxy already enabled
Module proxy_http already enabled
ildella /etc/apache2: a2ensite ildella.net
Site ildella.net already enabled

the restart apache but no answer at:

[http://danieledellafiore.net/newsletter/](http://danieledellafiore.net/newsletter/)

just at

[http://danieledellafiore.net:8080/newsletter/](http://danieledellafiore.net:8080/newsletter/)

any idea?

---

### Post by cdenley on 2009-11-05
> **ildella said:**
> 
ProxyPass /newsletter [http://danieledellafiore:8080/newsletter](http://danieledellafiore:8080/newsletter)
ProxyPassReverse /newsletter [http://danieledellafiore:8080/newsletter](http://danieledellafiore:8080/newsletter)

Shouldn't that be
```

ProxyPass /newsletter http://danieledellafiore.net:8080/newsletter
ProxyPassReverse /newsletter http://danieledellafiore.net:8080/newsletter

```

Does [http://danieledellafiore.net:8080/newsletter/](http://danieledellafiore.net:8080/newsletter/) work from the server itself?
```

wget -O /dev/null http://danieledellafiore.net:8080/newsletter/

```

Is there another vhost configured that is handling connection on port 80?

---

### Post by ildella on 2009-11-05
sorry I copied from a wrong source. actually site descriptor is correct:

<VirtualHost *:80>

ProxyRequests Off
ProxyPreserveHost On
<Proxy *>
    Order deny,allow
    Allow from all
</Proxy>

ProxyPass /newsletter [http://danieledellafiore.net:8080/newsletter](http://danieledellafiore.net:8080/newsletter)
ProxyPassReverse /newsletter [http://danieledellafiore.net:8080/newsletter](http://danieledellafiore.net:8080/newsletter)

</VirtualHost>

and as you can see [http://danieledellafiore.net:8080/newsletter](http://danieledellafiore.net:8080/newsletter) works but 
[http://danieledellafiore.net/newsletter](http://danieledellafiore.net/newsletter) does not.

---

### Post by ildella on 2009-11-05
Is there another vhost configured that is handling connection on port 80?[/QUOTE]

yes! that is the trick. 
the site "blog", which run wordpress on port 80. I d2dissite that and now works!

Btw, now I need a way to make them work togheter. any advice? Should I provice a NamveVirtualHost?

Consider that in a future I would like also to make this kind of proxy:

[http://newdomain.com/](http://newdomain.com/)   --> danieldellafiore.net:8080/webapp

---

### Post by cdenley on 2009-11-05
Simply add your proxy configuration to your blog vhost, assuming you don't need a newsletter directory. Or you could set a ServerName on your proxy vhost so apache knows when to use that (assuming it has a different domain from your blog).

---

### Post by ildella on 2009-11-05
rocknroll! :)

now I will try new configuration to manage something like

newsletter.danieledellafiore.net

or even from a different domanin like

newsletter.com -> [http://danieledellafiore.net/newsletter/](http://danieledellafiore.net/newsletter/)

here we go :)
thanks!

---

### Post by akoymakoy on 2010-06-09
Hi i know this thread is half a year old, but i am encountering a most likely similar problem.

i am trying to make a apache to forward to my jetty server when it recieves request like localhost/testjetty to localhost:8090/jettyTest

localhost:8090 is my jetty server
localhost:80 is my apache server

when i run localhost:8090/testjetty it runs ok. 

this i my httpd.conf entry:


<VirtualHost *:80>
 
ProxyRequests Off
ProxyVia Off
ProxyPreserveHost On

<Proxy *:80>
Order deny,allow
Allow from all
</Proxy>

ProxyPass /test [http://localhost:8090/jetty](http://localhost:8090/jetty)
ProxyPassReverse /test [http://localhost:8090/jetty](http://localhost:8090/jetty)

ProxyStatus On
</VirtualHost>


any help will do . Thanks

edit:
im getting an error 404 message

url is getting changed to localhost/testjetty
the port is being omitted

---

### Post by Dave.Wynne on 2010-06-09
> **akoymakoy said:**
> Hi i know this thread is half a year old, but i am encountering a most likely similar problem.

i am trying to make a apache to forward to my jetty server when it recieves request like localhost/testjetty to localhost:8090/jettyTest

localhost:8090 is my jetty server
localhost:80 is my apache server

when i run localhost:8090/testjetty it runs ok. 

this i my httpd.conf entry:


<VirtualHost *:80>
 
ProxyRequests Off
ProxyVia Off
ProxyPreserveHost On

<Proxy *:80>
Order deny,allow
Allow from all
</Proxy>

ProxyPass /test [http://localhost:8090/jetty](http://localhost:8090/jetty)
ProxyPassReverse /test [http://localhost:8090/jetty](http://localhost:8090/jetty)

ProxyStatus On
</VirtualHost>


any help will do . Thanks

edit:
im getting an error 404 message

url is getting changed to localhost/testjetty
the port is being omitted

If you do not have a working DNS server on your domain then proxypass will not work.
Try this code at the end ***</Directory>** is existing code*

```
</Directory>
Redirect /test http://192.???.???.???:8090/jettyTest
```

Where 192.???.???.??? is the IP address of Jetty *I assume you have a static IP address for jetty*

Also you will need this module

```
sudo a2enmod alias
sudo /etc/init.d/apache2 restart
```


Hope this helps

---

### Post by Dave.Wynne on 2010-06-09
Another thing I'm not using httpd.conf, but /etc/apache2/sites-enabled/000-default

---

### Post by akoymakoy on 2010-06-09
<VirtualHost *:80>

ProxyRequests Off
ProxyVia Off
ProxyPreserveHost On

<Proxy *:80>
Order deny,allow
Allow from all
</Proxy>

ProxyPass /test [http://localhost:8090/jetty](http://localhost:8090/jetty)[COLOR="red"]/[/COLOR]
ProxyPassReverse /test [http://localhost:8090/jetty](http://localhost:8090/jetty)[COLOR="red"]/[/COLOR]

ProxyStatus On
</VirtualHost>

Thanks but i got it to work last night.I added that slash at the end of my URL and it worked already. Would you be able to explain why?

---

### Post by akoymakoy on 2010-06-25
Hi im now applying it to my server. 
port 80 is my apache
port 8080 is my jetty

when i access localhost:8080 it returns something but when i access localhost:80/test it returns a 503 error

<VirtualHost *:80>

ProxyRequests Off
ProxyVia Off
ProxyPreserveHost On

<Proxy *:80>
Order deny,allow
Allow from all
</Proxy>

ProxyPass /test [http://localhost:8080](http://localhost:8080)

ProxyStatus On
</VirtualHost>

Thanks in advance

---

### Post by akoymakoy on 2010-07-26
Here i have all my setup written:

for my httpd.conf
```

LoadModule jk_module  modules/mod_jk.so

 	JkWorkersFile "C:/xampp1_7_3/xampp/apache/conf/worker.properties"
 	JkLogFile "C:/xampp1_7_3/xampp/apache/logs/mod_jk.log"
 	JkLogLevel info
 	
<VirtualHost *:80>
	ServerName localhost
 	JkMount /jetty/* jetty
</VirtualHost>

```

for my worker.properties
```

worker.list=jetty

worker.jetty.port=8090

worker.jetty.host=localhost

worker.jetty.type=ajp13

worker.jetty.lbfactor=1

```

added on my jetty.xml these 
```

<Call name="addConnector">
    <Arg>
       
	   <New class="org.mortbay.jetty.ajp.Ajp13SocketConnector">
			<Set name="host">localhost</Set>
			<Set name="port">8009</Set>
       </New>
    </Arg>
  </Call>

   <Call name="addConnector">
      <Arg>
			<New class="org.mortbay.jetty.nio.SelectChannelConnector">
				<Set name="host">localhost</Set>
				<Set name="port">8090</Set>
				<Set name="forwarded">true</Set>
			</New>
      </Arg>
    </Call>

```
im trying to use the JkMount with apache to forward requests to my jetty instance which is running fine when i run: e.g. (localhost:8090/jetty) it runs a servlet fine. Is there any other  setting i should make?

i run my jetty with this parameter

```
java -jar start.jar etc\jetty.xml
```



This is the log from mod_jk.log

```

[Tue Jul 27 11:15:51 2010] [4804:1680] [error] jk_ajp_common.c (969): wrong message format 0x4854 from 127.0.0.1:8090
[Tue Jul 27 11:15:51 2010] [4804:1680] [error] jk_ajp_common.c (1536): (jetty) Tomcat is down or refused connection. No response has been sent to the client (yet)
[Tue Jul 27 11:15:51 2010] [4804:1680] [info]  jk_ajp_common.c (1828): (jetty) receiving from tomcat failed, recoverable operation attempt=0
[Tue Jul 27 11:15:51 2010] [4804:1680] [info]  jk_ajp_common.c (1867): (jetty) sending request to tomcat failed,  recoverable operation attempt=1
[Tue Jul 27 11:15:51 2010] [4804:1680] [error] jk_ajp_common.c (969): wrong message format 0x4854 from 127.0.0.1:8090
[Tue Jul 27 11:15:51 2010] [4804:1680] [error] jk_ajp_common.c (1536): (jetty) Tomcat is down or refused connection. No response has been sent to the client (yet)
[Tue Jul 27 11:15:51 2010] [4804:1680] [info]  jk_ajp_common.c (1828): (jetty) receiving from tomcat failed, recoverable operation attempt=1
[Tue Jul 27 11:15:51 2010] [4804:1680] [info]  jk_ajp_common.c (1867): (jetty) sending request to tomcat failed,  recoverable operation attempt=2
[Tue Jul 27 11:15:51 2010] [4804:1680] [error] jk_ajp_common.c (1879): (jetty) Connecting to tomcat failed. Tomcat is probably not started or is listening on the wrong port
[Tue Jul 27 11:15:51 2010] [4804:1680] [info]  mod_jk.c (2063): Service error=0 for worker=jetty

```

---

