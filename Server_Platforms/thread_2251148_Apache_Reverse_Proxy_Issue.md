---
title: "Apache Reverse Proxy Issue"
date: 2014-11-02
forum: Server Platforms
---

### Post by Dale_Start on 2014-11-02
[COLOR=#555555][FONT=sans-serif]Hi folks,
I've got Guacamole 0.9.3 installed on a Ubuntu 14.04 and I'm having a problem getting Apache to proxy the front end. If anyone can spot my error it'd be greatly appreciated.
Guac is working fine in Tomcat7; if I go to [http://myserver:8080/guacamole](http://myserver:8080/guacamole)/ I have success. However if I go to [https://myserver/guacamole](https://myserver/guacamole)/, I get a basic 404 Not Found from Apache. The fact that the 404 is coming from Apache is what makes me suspect by proxy is wrong.
Here's my virtual server conf file:[/FONT][/COLOR]
```
[COLOR=#555555][FONT=sans-serif][COLOR=#008000]**<VirtualHost**[/COLOR] myserver.com:80[COLOR=#008000]**>**[/COLOR]
ServerName myserver.com
Redirect permanent / [https://myserver/](https://myserver/)
Redirect permanent /guacamole [https://myserver/guacamole](https://myserver/guacamole)

[COLOR=#008000]**</VirtualHost>**[/COLOR]

[COLOR=#008000]**<VirtualHost**[/COLOR] myserver:443[COLOR=#008000]**>**[/COLOR]
ServerName myserver
DocumentRoot /var/www/html/myserver

SSLEngine on
SSLCertificateFile /etc/ssl/certs/myserver.crt
SSLCertificateKeyFile /etc/ssl/certs/myserver.key

[COLOR=#008000]**<Location**[/COLOR] /guacamole[COLOR=#008000]**/>**[/COLOR]
Order allow,deny
Allow from all
ProxyPass ajp://localhost:8009/guacamole/ max=20 flushpackets=on
ProxyPassReverse [https://localhost/guacamole/](https://localhost/guacamole/)
[COLOR=#008000]**</Location>**[/COLOR]

[COLOR=#008000]**</VirtualHost>**[/COLOR][/FONT][/COLOR]
```[COLOR=#555555][FONT=sans-serif]
I've seen varying instructions for the ProxyPassReverse directive.
[http://guac-dev.org/doc/gug/installing-guacamole.html](http://guac-dev.org/doc/gug/installing-guacamole.html) says to use http (or https), but some other Google search results show some people using ajp. I've tried both with no luck either way. I even tried switching ProxyPass to use http, but still get the 404. So, **question #1 **is: Should I be using ajp or https for the ProxyPassReverse directive, and why? **Question #2**: If I should be using https for ProxyPassReverse, do I need to include the port number (443)?[/FONT][/COLOR]
[COLOR=#555555][FONT=sans-serif]I do have this in my /etc/tomcat7/server.xml:[/FONT][/COLOR]
```
[COLOR=#555555][FONT=sans-serif] [COLOR=#666666]<[/COLOR]Connector port[COLOR=#666666]=[/COLOR][COLOR=#BA2121]"8009"[/COLOR] protocol[COLOR=#666666]=[/COLOR][COLOR=#BA2121]"AJP/1.3"[/COLOR] URIEncoding[COLOR=#666666]=[/COLOR][COLOR=#BA2121]"UTF-8"[/COLOR] redirectPort[COLOR=#666666]=[/COLOR][COLOR=#BA2121]"8443"[/COLOR] [COLOR=#666666]/>[/COLOR][/FONT][/COLOR]
```
[COLOR=#555555][FONT=sans-serif]...and here's a few other things I've checked:
- libapache2-mod-proxy-html is installed
- The following Apache modules are installed and enabled with a2enmod: ssl, proxy, proxy_http, proxy_ajp
- The virtual site is enabled with a2ensite.
- I've restarted the Tomcat and Apache services.
- I use a self-signed cert but aside from the browser warning I still get a successful https connection.[/FONT][/COLOR]
[COLOR=#555555][FONT=sans-serif]I've spent a fair number of hours beating my head against this wall and decided it's time I ask for help. :)  I'm not even sure that the issue is related to my proxypass/proxypassreverse directives--but I'm not sure how to troubleshoot further. 

Thanks in advance,
Dale[/FONT][/COLOR]

---

### Post by koenn on 2014-11-03
If this was my problem, i'd start by simplifying the whole setup and then get something basic working. Once you have that, you can add complecity again.

So :
let your proxy do http (skip the https overhead and redirects)
proxy to the tomcat over http  (mostly because I don't know ajp myself, and you need additional apache modules to support it on the proxy server, i think

essentially, this leaves you with only 1 problem to solve : the correct ProxyPass and ProxyPass directives

Once you have those right, add the other stuff one at the time, and ttweak it till it works before you add/change something else (eg first add ssl/htttps; make sure it works, then see if ajp is something you want to add, etc)

---

### Post by Dale_Start on 2014-11-03
Thanks; I did try simplifying it: > [COLOR=#555555][FONT=sans-serif]I even tried switching ProxyPass to use http, but still get the 404.[/FONT][/COLOR]I removed the redirects and ditched the certs...which as you say (and I think) boils it down to the ProxyPass and ProxyPassReverse directives.

---

### Post by koenn on 2014-11-03
since I have access to a reverse proxy and a test setup of guacamole , I gave this a quick try and found that the following works.

```

<Location /guacamole/ >
       ProxyPass               http://webserver:8080/guacamole/
       ProxyPassReverse  http://webserver:8080/guacamole/
</Location>

```
note that the revers proxy and the web server are separate machines here
the above goes in the apache site conf of the proxy server
"webserver" runs guacamole at the given URL

guacamole can now also be reached via http(s)://proxyserver/guacamole/



If you have both on the same machine (and proxy to hide the port numbers) I guess you'll need something like
```

<Location /guacamole/>
ProxyPass              http://localhost:8080/guacamole/
ProxyPassReverse http://localhost:8080/guacamole/
</Location>

```
unless you have tomcat with SSL, that should be http, not https. Maybe ajp will work too, I've read about it but didn't try it. 
and check that you have the right port numbers, they vary by protocol (http, https, ajp, ...).  I have a pretty default setup of guacamole tomcat, and it speaks http on port 8080. 
In short, you need an URL there that would also work from a browser (or test it with wget) .



As a side note : Order allow,deny Allow from all  is deprecated in the apache version that comes with ubuntu 14.04, and normally apache would complain about it when you try to use it, but you probably already worked around that. You could replace it with
```

Require all granted

```

---

