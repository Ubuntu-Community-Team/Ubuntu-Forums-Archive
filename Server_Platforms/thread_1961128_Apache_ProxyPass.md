---
title: "Apache ProxyPass"
date: 2012-04-18
forum: Server Platforms
---

### Post by vragec on 2012-04-18
Hello, 

I have major problems with setting up my apache with proxypass. 
I have my domain like.com which is redirected with proxy redirect to tomcat7 on apps1. 
Now I would like to redirect like.com/something to tomcat7 apps2, like.com/somemore to apps3 on tomcat7.
In apps1 and apps2 is everything ok, but then in apps3 there are missing some CSS files and *.js files.

Can someone help me ?

This is my config file:
```
<IfModule proxy_http_module>

        ProxyRequests Off
        ProxyPreserveHost On
        ProxyHTMLInterp On
        ProxyHTMLLogVerbose On
        LogLevel Debug
        SetOutputFilter INFLATE;proxy-html;DEFLATE

        <Proxy *>
            Order deny,allow
            Allow from all
        </Proxy>

</IfModule>

        <Location /apps2>
            Order allow,deny
            Allow from all
            ProxyHTMLURLMap /apps2
            ProxyPassReverse /apps2/
            ProxyPass http://localhost:8080/apps2/
            ProxyPassReverse http://localhost:8080/apps2/
        </Location>

        <Location /apps3>
            Order allow,deny
            Allow from all
            ProxyHTMLURLMap /apps3
            ProxyPassReverse /apps3/
            ProxyPass http://localhost:8080/apps3/
            ProxyPassReverse http://localhost:8080/apps3/
        </Location>


        <Location />
            Order allow,deny
            Allow from all
            ProxyHTMLURLMap /apps1
            ProxyPassReverse /apps1/
            ProxyPassReverseCookiePath /apps1 /
            ProxyPass http://localhost:8080/apps1/
            ProxyPassReverse http://localhost:8080/apps1/
        </Location>

```

---

### Post by SeijiSensei on 2012-04-19
> **vragec said:**
> In apps1 and apps2 is everything ok, but then in apps3 there are missing some CSS files and *.js files.

That sounds more like a coding problem than an Apache problem.  Are you using absolute paths in the URLs for the CSS and JS files?  

If you open the page in Firefox and choose View > Source, you can click on the links and see where they go.  This is often a quick way to diagnose bad links.

---

### Post by dharmavir on 2012-04-22
[Seiji]("http://ubuntuforums.org/member.php?u=698195") is right it seems to be a problem with your web-app. Sometimes programmer tends to hardcode or may be parameterize some url for css/js include which can cause this error.

---

