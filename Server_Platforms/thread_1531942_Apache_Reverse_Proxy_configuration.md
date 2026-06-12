---
title: "Apache Reverse Proxy configuration"
date: 2010-07-15
forum: Server Platforms
---

### Post by skflyfish on 2010-07-15
I am trying to configure a reverse proxy in Apache so that one can log onto a site, then go to a remote web server(s). All the web sites run the same software, just are hosted on different servers.

My test goes like this. I have an index.html that has the links to the servers based on the reverse proxy config. 

Here is the reverse proxy config:


<VirtualHost *:80>

        ServerAdmin webmaster@localhost
        ServerName ezbiz.xyz.com
        ServerAlias *.ezbiz.xyz.com

        DocumentRoot /var/www/ezbiz/

        ProxyRequests Off
        SetOutputFilter proxy-html
        RequestHeader unset Accept-Encoding

        ProxyHTMLLogVerbose On
        LogLevel Info

        <Proxy *>
           Order deny,allow
           Allow from all
           AllowOverride All
        </Proxy>

        ProxyPass /site1/ [http://somedomain1.com/](http://somedomain1.com/)
        ProxyPass /site2/ [http://somedomain2.com/](http://somedomain2.com/)
        ProxyHTMLURLMap [http://somedomain1.com/](http://somedomain1.com/) /site1/
        ProxyHTMLURLMap [http://somedomain2.com/](http://somedomain2.com/) /site2/

        <Location /site1/>
           ProxyPassReverse /
           ProxyHTMLExtended On
           ProxyHTMLURLMap /   /site1/
        </Location>

        <Location /site2/>
           ProxyPassReverse /
           ProxyHTMLExtended On
           ProxyHTMLURLMap /  /site2/
        </Location>

</VirtualHost>


Here is the index.html:

<html>
        <body>
                <h1>EzBiz Testing web site.</h1>
                <p>
                <a href="http://ezbiz.xyz.com/site1/net/ez001"> EzBiz Server USA<a>
                <p>
                <a href="http://ezbiz.xyz.com/site2/net/ez001"> EzBiz Server Canada<a>
                <p>

        </body>
</html>

This is generating two problems.

First the absolute links in the HTML are being prefixed with /site1/ or /site2/ and the corresponding css and javascripts cannot be retrieved. The address bar looks okay to me.

[http://ezbiz.xyz.com/site2/net/ez001](http://ezbiz.xyz.com/site2/net/ez001)

The application uses absolute links and unfortunately I can't change that.

Example:
 
<html><head><link rel="stylesheet" type="text/css" href="/site2/style/CMSEasy.css"><script type="text/javascript" src="/site2/script/CMSEasy_navigation.js"></script><script type="text/javascript" src="/site2/script/CMSEasy_footer.js"></script><script type="text/javascript" src="/site2/script/EZ001-Main.js"></script></head><body> 
  <noscript>This site requires the use of <b><i>JavaScript</i></b>.
  Please enable this feature in your browser and try again.</noscript> 
  <script type="text/javascript"> 
    buildPage()
  </script> 
 </body></html>

This is basically a logon page.

The second issue is when I try to login, the path for the resulting page is wrong.

[http://ezbiz.xyz.com/net/EZ001](http://ezbiz.xyz.com/net/EZ001) the /site1/ has been stripped off.

I have been pulling my hair out over this for a couple of days and can't seem to find the problem.

I am on Ubuntu 9.04 with all the latest patches. 

Any help would be greatly appreciated.

Thx,

Jay

---

### Post by HectorG on 2011-02-08
Having same issue with the absolute path did you ever get a solution?

---

