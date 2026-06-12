---
title: "Problem configuration virtualhost apache2 in ubuntu server 18.04"
date: 2018-12-06
forum: Server Platforms
---

### Post by blanrok95 on 2018-12-06
When creating the virtual files in Apache2 with bind9, I copy the default-ssl.conf file (since they are secure virtual hosts) and I call it sri.conf. and iis.conf
I edit it and add ServerName 2asir.es, ServerAlias sri.2asir.es, DocumentRoot / var / www / sri. and within iis.conf ServerName 2asir.es, ServerAlias iis.2asir.es, DocumentRoot / var / www / iis. In addition to certificates.

when I raise them with a2ensite sri.conf and iis.conf I test in the host's browser by testing sri.2asir.es and iis.2asir.es. What is my surprise? the page sri.2asir.es redirects me to the page iis.2asir.es, they do not show me the 2 web pages, and each one has a different one.

In the DNS I have:

2asir.es. IN A (IP)
sri IN CNAME 2asir.es.
iis IN CNAME 2asir.es.

I need help!!

---

### Post by blanrok95 on 2018-12-10
Any idea why this bug happens?

---

### Post by SeijiSensei on 2018-12-11
SSL virtual hosts are complicated:  [https://www.digicert.com/ssl-support/apache-multiple-ssl-certificates-using-sni.htm](https://www.digicert.com/ssl-support/apache-multiple-ssl-certificates-using-sni.htm)

Each fully-qualified hostname requires a separate matching SSL certificate unless you're using a "wildcard" cert.

---

### Post by volkswagner on 2018-12-12
Why do you have the same servername in each vHost file?

Is that a typo or do you have the following in both vhost files?
```
ServerName 2asir.es
```

It's a lot easier for people to read actual config files, vs a description of a config file.

I believe Apache2 is behaving as expected. Since both of your vhost files
have the same servername, Apache2 will "display/serve" the vhost file that
comes first alfa-numerically which is iis.conf.


In the future please post the actual file contents.

---

### Post by LHammonds on 2018-12-12
If I were you, I would have a default site for any inbound requests that were not expected and have that page present a link to your other sites.  This can help with troubleshooting.

If you have 2 domains pointing to the same IP, Apache will direct incoming requests based on the URL that the web browser is using to get to you.

So, if you have sri.2asir.es and iis.2asir.es, make sure you ping both of those domains and get the expected IP address.

Make sure you have the following server names in the apache configs:

```
ServerName sri.2asir.es
DocumentRoot /var/www/sri

```
```
ServerName iis.2asir.es
DocumentRoot /var/www/iis
```

Do not use this server name:

```
ServerName 2asir.es
```

LHammonds

---

### Post by blanrok95 on 2018-12-16
> **LHammonds said:**
> If I were you, I would have a default site for any inbound requests that were not expected and have that page present a link to your other sites.  This can help with troubleshooting.

If you have 2 domains pointing to the same IP, Apache will direct incoming requests based on the URL that the web browser is using to get to you.

So, if you have sri.2asir.es and iis.2asir.es, make sure you ping both of those domains and get the expected IP address.

Make sure you have the following server names in the apache configs:

```
ServerName sri.2asir.es
DocumentRoot /var/www/sri

```
```
ServerName iis.2asir.es
DocumentRoot /var/www/iis
```

```
ServerName 2asir.es
```

LHammonds


Thank you very much to all for answering :)
I have served what you asked me, by putting the name servers in each host configuration works for me as I want.

But now I have another doubt. When something virtualhost with https, if I type [http://sri.2asir.es](http://sri.2asir.es) (unsecured form) I get the default page, the page ([www.2asir.es]("http://www.2asir.es")), and what I want is that when typing [http://sri.2asir.es](http://sri.2asir.es) do not show any page.

How could it be configured for this?

[ATTACH=CONFIG]281939[/ATTACH][ATTACH=CONFIG]281940[/ATTACH][ATTACH=CONFIG]281941[/ATTACH][ATTACH=CONFIG]281942[/ATTACH]

Thank you

Do not use this server name:

---

### Post by blanrok95 on 2018-12-16
I forgot to add some more screenshots
this would be the result, and what I would like is that when typing sri.4asir.es being not sure no page will appear

[ATTACH=CONFIG]281946[/ATTACH][ATTACH=CONFIG]281947[/ATTACH][ATTACH=CONFIG]281948[/ATTACH]

---

### Post by volkswagner on 2018-12-17
> **blanrok95 said:**
> 

But now I have another doubt. When something virtualhost with https, if I type [http://sri.2asir.es](http://sri.2asir.es) (unsecured form) I get the default page, the page ([www.2asir.es]("http://www.2asir.es")), and what I want is that when typing [http://sri.2asir.es](http://sri.2asir.es) do not show any page.

How could it be configured for this?

Do not use this server name:

I don't think you should purposely configure a system to "not show any page".

From what I'm reading a better choice would be to force all traffic over https://
To do this you create a vhost file for port 80 and configure a permanent redirect to https://

Here is an example of my config to redirect all requests to port 443/https

```
<VirtualHost *:80>
	ServerName www.hvgeek.com
	ServerAlias hvgeek.com www.hudsonvalleygeek.com hudsonvalleygeek.com
	Redirect "/" "https://www.hudsonvalleygeek.com/"
	ServerAdmin webmaster@localhost
	DocumentRoot /var/www/html

	ErrorLog ${APACHE_LOG_DIR}/error.log
	CustomLog ${APACHE_LOG_DIR}/access.log combined

</VirtualHost>
```

---

### Post by blanrok95 on 2018-12-20
> **volkswagner said:**
> I don't think you should purposely configure a system to "not show any page".

From what I'm reading a better choice would be to force all traffic over https://
To do this you create a vhost file for port 80 and configure a permanent redirect to https://

Here is an example of my config to redirect all requests to port 443/https

```
<VirtualHost *:80>
    ServerName www.hvgeek.com
    ServerAlias hvgeek.com www.hudsonvalleygeek.com hudsonvalleygeek.com
    Redirect "/" "https://www.hudsonvalleygeek.com/"
    ServerAdmin webmaster@localhost
    DocumentRoot /var/www/html

    ErrorLog ${APACHE_LOG_DIR}/error.log
    CustomLog ${APACHE_LOG_DIR}/access.log combined

</VirtualHost>
```

Thank you!! :)

---

