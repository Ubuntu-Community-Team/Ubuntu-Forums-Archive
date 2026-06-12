---
title: "Apache webserver proxypass with Apache Tomcat"
date: 2017-11-07
forum: Server Platforms
---

### Post by albertocastillo2001 on 2017-11-07
Hello
I am trying to setup Apache2 to server airsonic connections using a subdomain. I have created these 2 subdomains in NameCheap: airsonic.domainname.com madsonic.domainname.com

Apache Tomcat is running both Madsonic and Airsonic properly when you open domainname.com:8080/madsonic and /airsonic

I created 2 virtual hosts, one for airsonic like this:
```

<VirtualHost *:80>
	ServerName airsonic.domainname.com
	LogLevel warn CustomLog ${APACHE_LOG_DIR}/airsonic-access.log combined
	ErrorLog ${APACHE_LOG_DIR}/airsonic-error.log
	ProxyPass /airsonic http://127.0.0.1:8080/airsonic
	ProxyPassReverse /airsonic http://127.0.0.1:8080/airsonic
	#RequestHeader set X-Forwarded-Proto "http"
</VirtualHost>

```

It seems that if I use this setup, I can access airsonic typing airsonic.domainname.com/airsonic
But I don't want this. I want to use airsonic.domainname.com

So I leave it like this as
```
ProxyPass / http://127.0.0.1:8080/airsonic
ProxyPassReverse / http://127.0.0.1:8080/airsonic
```


I assume this way, it should work by typing airsonic.domainname.com, so I reload the configuration and restart the server


As soon as I type in, it redirects airsonic.domainname.com to airsonic.domainname.com/airsonic (which shouldn't happen as far as I know) and shows this:
```
Estado HTTP 404 - /airsonicairsonic/
type Informe de estado
mensaje /airsonicairsonic/
descripción El recurso requerido no está disponible.
Apache Tomcat/8.0.32 (Ubuntu)

```

Why is it doing so? it seems it's not taking the right path somehow
Thanks

---

### Post by albertocastillo2001 on 2017-11-16
Any idea?

Thanks

---

