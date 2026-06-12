---
title: "Issue with ReverseProxy"
date: 2011-02-06
forum: Server Platforms
---

### Post by HectorG on 2011-02-06
For the life of me I cant figure this out. I have been trying to get a reverse proxy working all da and I cant find any good documentation on this.  Below is the config I have in my virtual host. I am trying to get a webserver on a different machine that doesn't support https to go through this apache box. 




  ```
      ProxyRequests Off

        ProxyPass /svr/ http://192.168.1.2/
        ProxyPassReverse /svr/ http://192.168.1.2/
        SetOutputFilter INFLATE;proxy-html;DEFLATE
        ProxyHTMLURLMap  /      /svr/
        ProxyHTMLURLMap  /svr  /svr
```
It goes to the initial authentication page that the webserver at 192.168.1.2 has but when it goes to redirect after I log in it redirects without the /svr/ in the path.

For example lets say my site is [http://www.example.com](http://www.example.com)

the other server is suppose to answer to [http://www.example.com/srv/](http://www.example.com/srv/) and display what I see locally at 192.168.1.2

if I try to go to  192.168.1.2/web/test.html  I should see [http://www.example.com/srv/web/test.html](http://www.example.com/srv/web/test.html) but I see [http://www.example.com/web/test.html](http://www.example.com/web/test.html) and of course that gives me a 404 since that page doesn't exist. Any help would be appreciated.

---

### Post by HectorG on 2011-02-07
By the way I am not sure if it makes a difference but I am using https...

---

### Post by HectorG on 2011-02-10
to troubleshoot I took it off the https and did it as regular port 80 or http

Here is my current config still nothing...


        <IfModule mod_proxy.c>
                ProxyRequests Off
                ProxyPass /srv [http://srv.example.com/](http://srv.example.com/)
                ProxyHTMLURLMap [http://srv.example.comt/](http://srv.example.comt/) /srv
                
<Location /srv>

                       ProxyPreserveHost yes 
                       RequestHeader unset Cookie
                       RequestHeader unset Referer                   
                #     ProxyPassReverse /srv [http://srv.example.net/](http://srv.example.net/)
                       ProxyPassReverse [http://srv.example.net/](http://srv.example.net/)
                        SetOutputFilter proxy-html
                #      SetOutputFilter INFLATE;proxy-html;DEFLATE
                        ProxyHTMLURLMap /               /srv/
                        ProxyHTMLURLMap /srv/          /srv/
                </Location>
        </IfModule>

---

