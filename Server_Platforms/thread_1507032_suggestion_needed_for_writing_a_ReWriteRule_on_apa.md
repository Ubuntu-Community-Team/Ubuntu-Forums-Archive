---
title: "suggestion needed for writing a ReWriteRule on apache"
date: 2010-06-11
forum: Server Platforms
---

### Post by tapas_mishra on 2010-06-11
[COLOR=#000000][FONT=Times New Roman][FONT=arial]Hi,

I installed an application mingle running on port 8080 on a
computer on our LAN.Which is also hosting a website.
[/FONT][/FONT][/COLOR][COLOR=#000000][FONT=Times New Roman][FONT=arial]To access that from internet some one will type in
[http://site.mydomain.com]("http://site.mydomain.com/")
Then you will get the website.

Coming to the problem I need suggestion the application is also hosted on same webserver (which is masked from outside)
[/FONT][/FONT][/COLOR][COLOR=#000000][FONT=Times New Roman][FONT=arial]
Application is accessible http://<IP of application>:8080

Some one  within LAN can access it with  a URL

[http://192.168.1.5:8080/profile/login](http://192.168.1.5:8080/profile/login)

and a login page he gets.



```

Server A---------------------------------------------------------------Server B

Public IP-----------------------------------------------------------192.168.1.5
```[/FONT][/FONT][/COLOR]```
[COLOR=#000000][FONT=Times New Roman][FONT=arial]
                                                                                            -A website is running  here[/FONT][/FONT][/COLOR]
[COLOR=#000000][FONT=Times New Roman][FONT=arial]Sysadmins govern it-------------------------------------------( We want to run mingle also here.)

[/FONT][/FONT][/COLOR]
```[COLOR=#000000][FONT=Times New Roman][FONT=arial]

I tried to format above properly many times but each time I saved a line \[code\] \[\\code\]
got automatically added on this forum.

I need to tell the sysadmin what ReWriteRule they have to put so that
application is accessible on internet.




in Apache vhost on Server A we have  as follows
```

ProxyPass / [http://192.168.1.5]("http://192.168.1.5/")
ProxyPassReverse / [http://192.168.1.5]("http://192.168.1.5/")

```So some one from internet can reach the site. [http://site.mydomain.com]("http://site.mydomain.com/")
which is running on 192.168.1.5

We want application which is also running on 192.168.1.5 where website is running to be accessible as
[http://site.mydomain.com/application]("http://site.mydomain.com/mingle")

I suggested the sysadmin to write a ReWrite Rule on Server A as follows
```

<IfModule mod_rewrite.c>
ReWriteEngine on

RewriteRule ^/application(.*) [http://192.168.1.5:8080/$1]("http://172.21.100.193:8080/$1") [R]
 </IfModule>

```[/FONT][/FONT][/COLOR][COLOR=#000000][FONT=Times New Roman][FONT=arial]After this  if some one accesses it from within our network
by typing in URL
```

http://site.mydomain.com

``` then he can see it
but the URL in the browser 
```

http://site.mydomain.com

```gets converted to internal IP where it is hosted.

```

[http://192.168.1.5:8080/login/profile]("http://site.mydomain.com/mingle")

```On LAN it is directly accessible by IP also so it is not a problem
but even the URL should not get converted to IP.I am not clear if the above ReWriteRule is doing that.


But if some one from internet does that then they are not able to
reach the login page.Since I do not know if on internet it (URL to access application)
is getting converted to internal IP (which obviously does not exist on internet)

So what can/should I added delete in the above ReWriteRule so that my application becomes accessible.[/FONT][/FONT][/COLOR]
[COLOR=#000000][FONT=Times New Roman][FONT=arial]
[/FONT][/FONT][/COLOR]

---

### Post by dapperdanny77 on 2010-06-11
hi,

for me your rewrite looks ok - are you sure your admin didn't put anything like that in the config ?
```
[COLOR=#000000][FONT=Times New Roman][FONT=arial]RewriteRule ^/(.*) [http://192.168.1.5:8080/$1]("http://172.21.100.193:8080/$1") [R][/FONT][/FONT][/COLOR]
```[COLOR=#000000][FONT=Times New Roman][FONT=arial]

it seems your entire site is gonna rewritten 

cheers
[/FONT][/FONT][/COLOR]

---

### Post by tapas_mishra on 2010-06-11
The headers of this instance from my laptop are (I have posted more
headers from all servers)
```

http://site.mydomain.com/mingle

GET /mingle HTTP/1.1
Host: site.mydomain.com
User-Agent: Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.8)
Gecko/2009033100 Ubuntu/9.04 (jaunty) Firefox/3.0.8
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,*/*;q=0.8
Accept-Language: en-us,en;q=0.5
Accept-Encoding: gzip,deflate
Accept-Charset: ISO-8859-1,utf-8;q=0.7,*;q=0.7
Keep-Alive: 300
Proxy-Connection: keep-alive
Cookie: SESS440c87567d2953541cb9726c24c2fe5f=dpc7834qqbv8ds8ct7b18129o1;
SESSc7d2ae400a554b03caf14d856186f992=7l2b3etbtgmf15s0scbgg2uke7

HTTP/1.0 302 Moved Temporarily
Date: Fri, 11 Jun 2010 16:19:23 GMT
Server: Jetty(6.1.19)
Content-Type: text/html; charset=utf-8
Cache-Control: no-cache
Location: http://site.mydomain.com/mingle/profile/login
X-Runtime: 80
Set-Cookie: mingle_3_1_session_id=92be88f857dbe501e520b97a75cc2ebb;
path=/; HttpOnly
Vary: Accept-Encoding
Content-Encoding: gzip
Content-Length: 110
X-Cache: MISS from cachingserver
X-Cache-Lookup: MISS from cachingserver:80
Via: 1.0 site.mydomain.com, 1.0 cachingserver:80 (squid/2.6.STABLE6)
Proxy-Connection: keep-alive
----------------------------------------------------------
http://site.mydomain.com/mingle/profile/login

GET /mingle/profile/login HTTP/1.1
Host: site.mydomain.com
User-Agent: Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.8)
Gecko/2009033100 Ubuntu/9.04 (jaunty) Firefox/3.0.8
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,*/*;q=0.8
Accept-Language: en-us,en;q=0.5
Accept-Encoding: gzip,deflate
Accept-Charset: ISO-8859-1,utf-8;q=0.7,*;q=0.7
Keep-Alive: 300
Proxy-Connection: keep-alive
Cookie: SESS440c87567d2953541cb9726c24c2fe5f=dpc7834qqbv8ds8ct7b18129o1;
SESSc7d2ae400a554b03caf14d856186f992=7l2b3etbtgmf15s0scbgg2uke7;
mingle_3_1_session_id=92be88f857dbe501e520b97a75cc2ebb

HTTP/1.0 404 Not Found
Date: Fri, 11 Jun 2010 16:19:23 GMT
Server: Jetty(6.1.19)
Content-Type: text/html; charset=utf-8
Cache-Control: no-cache
Vary: Accept-Encoding
Content-Encoding: gzip
Content-Length: 1068
X-Cache: MISS from cachingserver
X-Cache-Lookup: MISS from cachingserver:80
Via: 1.0 site.mydomain.com, 1.0 cachingserver:80 (squid/2.6.STABLE6)
Proxy-Connection: close
----------------------------------------------------------
http://site.mydomain.com/javascripts/base_packaged.js?1270057297

GET /javascripts/base_packaged.js?1270057297 HTTP/1.1
Host: site.mydomain.com
User-Agent: Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.8)
Gecko/2009033100 Ubuntu/9.04 (jaunty) Firefox/3.0.8
Accept: */*
Accept-Language: en-us,en;q=0.5
Accept-Encoding: gzip,deflate
Accept-Charset: ISO-8859-1,utf-8;q=0.7,*;q=0.7
Keep-Alive: 300
Proxy-Connection: keep-alive
Referer: http://site.mydomain.com/mingle/profile/login
Cookie: SESS440c87567d2953541cb9726c24c2fe5f=dpc7834qqbv8ds8ct7b18129o1;
SESSc7d2ae400a554b03caf14d856186f992=7l2b3etbtgmf15s0scbgg2uke7;
mingle_3_1_session_id=92be88f857dbe501e520b97a75cc2ebb

HTTP/1.0 404 Not Found
Date: Fri, 11 Jun 2010 16:19:23 GMT
Server: Apache/2.2.14 (Ubuntu)
Vary: Accept-Encoding
Content-Encoding: gzip
Content-Length: 256
Content-Type: text/html; charset=iso-8859-1
X-Cache: MISS from cachingserver
X-Cache-Lookup: MISS from cachingserver:80
Via: 1.0 site.mydomain.com, 1.0 cachingserver:80 (squid/2.6.STABLE6)
Proxy-Connection: close
----------------------------------------------------------
http://site.mydomain.com/stylesheets/base_packaged.css?1270057297

GET /stylesheets/base_packaged.css?1270057297 HTTP/1.1
Host: site.mydomain.com
User-Agent: Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.8)
Gecko/2009033100 Ubuntu/9.04 (jaunty) Firefox/3.0.8
Accept: text/css,*/*;q=0.1
Accept-Language: en-us,en;q=0.5
Accept-Encoding: gzip,deflate
Accept-Charset: ISO-8859-1,utf-8;q=0.7,*;q=0.7
Keep-Alive: 300
Proxy-Connection: keep-alive
Referer: http://site.mydomain.com/mingle/profile/login
Cookie: SESS440c87567d2953541cb9726c24c2fe5f=dpc7834qqbv8ds8ct7b18129o1;
SESSc7d2ae400a554b03caf14d856186f992=7l2b3etbtgmf15s0scbgg2uke7;
mingle_3_1_session_id=92be88f857dbe501e520b97a75cc2ebb

HTTP/1.0 404 Not Found
Date: Fri, 11 Jun 2010 16:19:24 GMT
Server: Apache/2.2.14 (Ubuntu)
Vary: Accept-Encoding
Content-Encoding: gzip
Content-Length: 255
Content-Type: text/html; charset=iso-8859-1
X-Cache: MISS from cachingserver
X-Cache-Lookup: MISS from cachingserver:80
Via: 1.0 site.mydomain.com, 1.0 cachingserver:80 (squid/2.6.STABLE6)
Proxy-Connection: close
----------------------------------------------------------
http://site.mydomain.com/images/mingle-logo.png?1270057297

GET /images/mingle-logo.png?1270057297 HTTP/1.1
Host: site.mydomain.com
User-Agent: Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.8)
Gecko/2009033100 Ubuntu/9.04 (jaunty) Firefox/3.0.8
Accept: image/png,image/*;q=0.8,*/*;q=0.5
Accept-Language: en-us,en;q=0.5
Accept-Encoding: gzip,deflate
Accept-Charset: ISO-8859-1,utf-8;q=0.7,*;q=0.7
Keep-Alive: 300
Proxy-Connection: keep-alive
Referer: http://site.mydomain.com/mingle/profile/login
Cookie: SESS440c87567d2953541cb9726c24c2fe5f=dpc7834qqbv8ds8ct7b18129o1;
SESSc7d2ae400a554b03caf14d856186f992=7l2b3etbtgmf15s0scbgg2uke7;
mingle_3_1_session_id=92be88f857dbe501e520b97a75cc2ebb

HTTP/1.0 404 Not Found
Date: Fri, 11 Jun 2010 16:19:24 GMT
Server: Apache/2.2.14 (Ubuntu)
Vary: Accept-Encoding
Content-Encoding: gzip
Content-Length: 253
Content-Type: text/html; charset=iso-8859-1
X-Cache: MISS from cachingserver
X-Cache-Lookup: MISS from cachingserver:80
Via: 1.0 site.mydomain.com, 1.0 cachingserver:80 (squid/2.6.STABLE6)
Proxy-Connection: close
----------------------------------------------------------
http://site.mydomain.com/mingle.ico?1270057297

GET /mingle.ico?1270057297 HTTP/1.1
Host: site.mydomain.com
User-Agent: Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.8)
Gecko/2009033100 Ubuntu/9.04 (jaunty) Firefox/3.0.8
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,*/*;q=0.8
Accept-Language: en-us,en;q=0.5
Accept-Encoding: gzip,deflate
Accept-Charset: ISO-8859-1,utf-8;q=0.7,*;q=0.7
Keep-Alive: 300
Proxy-Connection: keep-alive
Cookie: SESS440c87567d2953541cb9726c24c2fe5f=dpc7834qqbv8ds8ct7b18129o1;
SESSc7d2ae400a554b03caf14d856186f992=7l2b3etbtgmf15s0scbgg2uke7;
mingle_3_1_session_id=92be88f857dbe501e520b97a75cc2ebb

HTTP/1.0 404 Not Found
Date: Fri, 11 Jun 2010 16:19:27 GMT
Server: Apache/2.2.14 (Ubuntu)
Vary: Accept-Encoding
Content-Encoding: gzip
Content-Length: 244
Content-Type: text/html; charset=iso-8859-1
X-Cache: MISS from cachingserver
X-Cache-Lookup: MISS from cachingserver:80
Via: 1.0 site.mydomain.com, 1.0 cachingserver:80 (squid/2.6.STABLE6)
Proxy-Connection: close
----------------------------------------------------------

```
When I accessed from the Proxy Server where these tests were done I
got a 404 not found.

Here are the headers on Proxy Server 
```

http://site.mydomain.com/mingle

GET /mingle HTTP/1.1
Host: site.mydomain.com
User-Agent: Mozilla/5.0 (X11; U; Linux x86_64; en-US; rv:1.9.2.3)
Gecko/20100423 Ubuntu/10.04 (lucid) Firefox/3.6.3
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,*/*;q=0.8
Accept-Language: en-us,en;q=0.5
Accept-Encoding: gzip,deflate
Accept-Charset: ISO-8859-1,utf-8;q=0.7,*;q=0.7
Keep-Alive: 115
Connection: keep-alive
Cookie: SESS440c87567d2953541cb9726c24c2fe5f=tdn7dej7oh2mnak8cj9k4jc532

HTTP/1.1 404 Not Found
Date: Fri, 11 Jun 2010 16:13:38 GMT
Server: Apache/2.2.14 (Ubuntu)
Vary: Accept-Encoding
Content-Encoding: gzip
Content-Length: 241
Keep-Alive: timeout=15, max=100
Connection: Keep-Alive
Content-Type: text/html; charset=iso-8859-1
----------------------------------------------------------

```

And here are the headers when site was accessed locally on that PC
where it is hosted.


posting if it can give some clue.
```


http://localhost:8080/

GET / HTTP/1.1
Host: localhost:8080
User-Agent: Mozilla/5.0 (X11; U; Linux x86_64; en-US; rv:1.9.2.3)
Gecko/20100423 Ubuntu/10.04 (lucid) Firefox/3.6.3
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,*/*;q=0.8
Accept-Language: en-us,en;q=0.5
Accept-Encoding: gzip,deflate
Accept-Charset: ISO-8859-1,utf-8;q=0.7,*;q=0.7
Keep-Alive: 115
Connection: keep-alive

HTTP/1.1 302 Found
Content-Type: text/html; charset=utf-8
Set-Cookie: mingle_3_1_session_id=0c2d5039406a3b81568d55e544a5a13d;
path=/; HttpOnly
Cache-Control: no-cache
Location: http://localhost:8080/profile/login
X-Runtime: 86
Content-Length: 101
Server: Jetty(6.1.19)
----------------------------------------------------------
http://localhost:8080/profile/login

GET /profile/login HTTP/1.1
Host: localhost:8080
User-Agent: Mozilla/5.0 (X11; U; Linux x86_64; en-US; rv:1.9.2.3)
Gecko/20100423 Ubuntu/10.04 (lucid) Firefox/3.6.3
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,*/*;q=0.8
Accept-Language: en-us,en;q=0.5
Accept-Encoding: gzip,deflate
Accept-Charset: ISO-8859-1,utf-8;q=0.7,*;q=0.7
Keep-Alive: 115
Connection: keep-alive
Cookie: mingle_3_1_session_id=0c2d5039406a3b81568d55e544a5a13d

HTTP/1.1 200 OK
Content-Type: text/html; charset=utf-8
Set-Cookie: mingle_3_1_session_id=0c2d5039406a3b81568d55e544a5a13d;
path=/; HttpOnly
Cache-Control: no-cache
X-Runtime: 113
Content-Length: 6222
Server: Jetty(6.1.19)
----------------------------------------------------------

```
and when on the same machine where mingle is hosted I tried to access
it like this

http://site.mydomain.com/mingle

then following were headers
```

http://site.mydomain.com/mingle

GET /mingle HTTP/1.1
Host: site.mydomain.com
User-Agent: Mozilla/5.0 (X11; U; Linux x86_64; en-US; rv:1.9.2.3)
Gecko/20100423 Ubuntu/10.04 (lucid) Firefox/3.6.3
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,*/*;q=0.8
Accept-Language: en-us,en;q=0.5
Accept-Encoding: gzip,deflate
Accept-Charset: ISO-8859-1,utf-8;q=0.7,*;q=0.7
Keep-Alive: 115
Connection: keep-alive

HTTP/1.1 404 Not Found
Date: Fri, 11 Jun 2010 16:37:46 GMT
Server: Apache/2.2.14 (Ubuntu)
Vary: Accept-Encoding
Content-Encoding: gzip
Content-Length: 241
Keep-Alive: timeout=15, max=98
Connection: Keep-Alive
Content-Type: text/html; charset=iso-8859-1
----------------------------------------------------------

```

---

### Post by dapperdanny77 on 2010-06-12
hi,

is it possible for you to post the apache configs - it's a bit harder to do it the reverse engineering way...

cheers - dapperdan

---

### Post by tapas_mishra on 2010-06-14
Hi,
Thanks for the reply I have been able to make it work.

[Here]("http://community.thoughtworks.com/posts/1954e8961c") is a discussion which made it work.

The modification was needed in a file jetty.xml in mingle application server to serve every thing in context root /mingle.

---

