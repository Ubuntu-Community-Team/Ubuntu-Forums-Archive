---
title: "Apache Mod_Proxy, Reverse Proxying and mod_proxy_connect"
date: 2010-08-22
forum: Server Platforms
---

### Post by Ooolalashop on 2010-08-22
Hi All, I am trying to create solution with Reverse Proxy, mod_proxy and mod_proxy_connect. I haven't really used this before so I am just curious if I am doing it right. I have attached what I am trying to do plus a copy of the config:

Here is my current requirement


We are going to have 3 servers, right now our top level domain is [http://www.ooolalashop.com](http://www.ooolalashop.com)


We have an E-Commerce Server in Production Right now that already has an SSL Cert on it so right now the production server for E-Commerce is [http://www.ooolalashop.com](http://www.ooolalashop.com)


However, as we are growing, we don't want to use subdomains, so instead, we want to use the reverse proxying feature on apache. We are running mostly windows servers and IIS for the E-Commerce, CMS and the Wordpress Server. So this is what we need to accomplish


Assume the following - 

Apache Proxy Server 10.100.10.60
E-Commerce Server 10.100.10.3 ([www.ooolalashop.com](www.ooolalashop.com))
Content Management Server 10.100.10.3 (cms.ooolalashop.com)
Word Press Blog Server 10.100.10.3 (blog.ooolalashop.com)


1) We need the following mapped

[http://www.ooolalashop.com](http://www.ooolalashop.com) - maps to ecommerce server - since ssl cert is going to stay on the server, on the proxy we just create a static host that points to the e-commerce server

[http://www.ooolalashop.com/dnn](http://www.ooolalashop.com/dnn) maps to content management server 

[http://www.ooolalashop.com/blogs](http://www.ooolalashop.com/blogs) maps to Word Press Blog Server

All of these should be pretty easy to reverse proxy


2) We need to be able to proxy the SSL connection or have it pass through to the server on the back end with the domain [https://www.ooolalashop.com](https://www.ooolalashop.com) right now we are getting some errors

Here is the error I get with SSL [Sun Aug 22 01:51:30 2010] [warn] proxy: No protocol handler was valid for the URL /. If you are using a DSO version of mod_proxy, make sure the proxy submodules are included in the configuration using LoadModule.



Here is a copy of the config



<VirtualHost *:80>
        ServerAdmin [email]support@cometcomputing.com[/email]
		ServerName	[www.ooolalashop.com](www.ooolalashop.com)
        DocumentRoot	/var/www/ooo
		ErrorLog /var/log/apache2/ooolalashop-error.log
		CustomLog /var/log/apache2/ooolalashop-access.log combined
		RewriteEngine On
		
		
			<Proxy *>
	                AddDefaultCharset off
	                Order deny,allow
	                Allow from all
	                #Allow from .example.com
	        </Proxy>
			
		ProxyPass /dnn [http://cms.ooolalashop.com/](http://cms.ooolalashop.com/)
		ProxyPass / [http://www.ooolalashop.com/](http://www.ooolalashop.com/)
		ProxyHTMLURLMap [http://cms.ooolalashop.com](http://cms.ooolalashop.com) /dnn
		ProxyHTMLURLMap [http://www.ooolalashop.com](http://www.ooolalashop.com) /
		
		<Location /dnn/>
		        Order allow,deny
		        Allow from all
				ProxyPassReverse /
				ProxyHTMLURLMap / /dnn/
		</Location>
		<Location />
		        Order allow,deny
		        Allow from all
				ProxyPassReverse /
				ProxyHTMLURLMap / /
		</Location>
		
</VirtualHost>
<VirtualHost *:443>
		
        <Proxy *>
                AddDefaultCharset off
                Order deny,allow
                Allow from all
                #Allow from .example.com
        </Proxy>
		ProxyPass               /       [https://www.ooolalashop.com/](https://www.ooolalashop.com/)
        ProxyPassReverse        /       [https://www.ooolalashop.com/](https://www.ooolalashop.com/)
		ErrorLog /var/log/apache2/ooolalashop-ssl-error.log
		CustomLog /var/log/apache2/ooolalashop-ssl-access.log combined
</VirtualHost>


Harry Yeh
CEO / CTO
[Ooolalashop.com]("http://www.ooolalashop.com")
When you think [thong]("http://www.ooolalashop.com"), think [Ooolalashop.com]("http://www.ooolalashop.com")!

---

### Post by Ooolalashop on 2010-08-22
Oh yes the question I actually have is that I am not currently using the mod_ssl, I have tried it with that but do I actually need it? When  you are proxying an SSL connection, does the SSL Certificate need to be on the Proxy server or on the actual web server? 

Right now I have it on the actual web server, my understanding of mod_proxy_connect is that you don't need the mod_ssl and that mod_proxy_connect tunnels any ssl request to the server in the back.

Is this correct? I don't mind having to get another SSL cert just as long as this proxying actually works.



Harry Yeh
CEO / CTO
[Ooolalashop.com]("http://www.ooolalashop.com")
When you think [thong]("http://www.ooolalashop.com"), think [Ooolalashop.com]("http://www.ooolalashop.com")!

---

