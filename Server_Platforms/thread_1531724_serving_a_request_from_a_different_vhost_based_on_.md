---
title: "serving a request from a different vhost based on string in URI"
date: 2010-07-15
forum: Server Platforms
---

### Post by tapas_mishra on 2010-07-15
I am not clear with 
if I am getting a request as

[http://www.mydomain.com/example1](http://www.mydomain.com/example1)

then based on the presence of example1 in the URI I want to serve the request from a different vhost which is physically on a different IP and with a different servername than 
the vhost which has configuration for [www.mydomain.com](www.mydomain.com)
and the SeverName is also different for the server which will server a request for /example1
how can I achieve that.

---

### Post by cdenley on 2010-07-15
Let me see if I got this right.

1. [http://www.mydomain.com/example1](http://www.mydomain.com/example1)
2. [http://www.mydomain.com/some/other/path](http://www.mydomain.com/some/other/path)
3. [http://www.anythingelse.com/](http://www.anythingelse.com/)

All these requests are sent to server 1. Request 1 should get proxied to server 2. Request 2 should get proxied to server 3. Request 3, or any other requests, should get served by server 1 as normal. Correct?

---

### Post by tapas_mishra on 2010-07-15
Request 1 and 2 gets proxied to server2. 

Request 2 is served by server2 (with the domaim name of server 3)

There is no request 3.

---

### Post by cdenley on 2010-07-16
> **tapas_mishra said:**
> 
Request 2 is served by server2 **(with the domaim name of server 3)**


What? How does a "server 3" relate to this configuration? Are you proxying connections from server1 to server2 for multiple vhosts on server2? Do the hostnames provided to server1 match the ServerName's configured on server2?

---

### Post by tapas_mishra on 2010-07-16
> **cdenley said:**
> What? How does a "server 3" relate to this configuration? Are you proxying connections from server1 to server2 for multiple vhosts on server2? Do the hostnames provided to server1 match the ServerName's configured on server2?
Yes you got me right.

    A-----B-----C

request from internet comes at A it forwards that to B and then B 
 checks if it has to send that request to C or it can serve that from B itself.

Now since you have actually cracked the thing.
I am posting the configurations.

site1.abc.com
site2.abc.com
site3.abc.com
site4.abc.com

these sites above are having domain names which have been registered.

Any request to any of them i.e. site1.abc.com or site3.abc.com

Comes at A

Following is vhost configuration at A 
for 

site2.mydomain.com

```

<VirtualHost *:80>

	ServerAdmin webmaster@localhost
	ServerName site2.mydomain.com	
	ProxyRequests off
        <Proxy *>
        Order deny,allow
        Allow from all
        </Proxy>

	ProxyPreserveHost On

	
	ProxyPass /application http://nirvana/
	ProxyPassReverse /application http://nirvana/

        ProxyPass / http://server2
        ProxyPassReverse / http://server2

</VirtualHost>

```

Where server2 is B in above diagram.
and /application is forwarded to B which in turn forward to C.
In above configuration **nirvana** and **server2** are both pointing to same server B.


Following is configuration of Server B

for a request that comes with a server name for **nirvana**
```

<VirtualHost *:80>
        ServerAdmin webmaster@localhost
        ServerName **nirvana**
        ServerAlias 

        ProxyRequests Off

         <Proxy *>
        Order deny,allow
        Allow from all
        </Proxy>

        ProxyPreserveHost On
        ProxyPass / http://**papaserver**:9090/portal
        ProxyPassReverse / http://**papaserver**:9090/portal


```

Where **papaserver** is Server C which is a tomcat instance.Not apache and on C I can access it by 

[http://localhost:9090/portal](http://localhost:9090/portal)

Server B is serving a request which comes for a 
ServerName nirvana and also 
ServerName site2.abc.com

A request that comes at B forwarded by A 
if it has ServerName **nirvana** then vhost with ServerName **nirvana**
should response to it.

And actual working of this entire thing on internet is if any one  types
[http://site2.abc.com/application](http://site2.abc.com/application)

he can see the same content which I see as [http://localhost:9090/portal](http://localhost:9090/portal) on physically opening a browser at C.

My problem is if a request originally is coming for site2.abc.com
and I have kept ProxyPreserveHost On then orginial hostname requested is preserved in this process which is site2.abc.com
but for a request for site2.abc.com/application 
I need to proxy it to Server B so that Server B can respond with a different hostname than site2.abc.com

---

### Post by cdenley on 2010-07-16
You set "ProxyPreserveHost On", so the hostname you use for ProxyPass is irrelevant. The request sent by server A to server B will always have the same hostname as the request received by server A.

[http://httpd.apache.org/docs/2.2/mod/mod_proxy.html#proxypreservehost](http://httpd.apache.org/docs/2.2/mod/mod_proxy.html#proxypreservehost)

---

### Post by tapas_mishra on 2010-07-16
Yes I understand that.That is why I have asked this question.How do I change the hostname of incoming request.
Since if I do not preserver Hostname for a request which goes to B with site2.abc.com then the application would not be able to maintain session for logged in users.
So I have to preserve the requested hostname.
But for /application I have transfer it some how this thing I am not getting.

---

### Post by cdenley on 2010-07-16
> **tapas_mishra said:**
> Yes I understand that.That is why I have asked this question.How do I change the hostname of incoming request.
Since if I do not preserver Hostname for a request which goes to B with site2.abc.com then the application would not be able to maintain session for logged in users.
So I have to preserve the requested hostname.
But for /application I have transfer it some how this thing I am not getting.

You can't change the hostname AND preserve the hostname. That doesn't make any sense. Instead of sending a different hostname to server B, why not send a different directory?

[http://server1/application](http://server1/application) -> [http://server2/application](http://server2/application) -> [http://papaserver:9090/portal](http://papaserver:9090/portal)
[http://server1/](http://server1/) -> [http://server2/](http://server2/)

---

### Post by tapas_mishra on 2010-07-16
Hmmm is it not possible even by writing an Apache module also.
I am just asking if it can be made to work I will even try that.
Or in this case if you have some other solution that you think I can try to make that work.

---

### Post by cdenley on 2010-07-16
> **tapas_mishra said:**
> Hmmm is it not possible even by writing an Apache module also.
I am just asking if it can be made to work I will even try that.
Or in this case if you have some other solution that you think I can try to make that work.

You can only send one hostname in a request. That is how the HTTP protocol works. What would apache do with two hostnames? Why is it necessary to have 2 different vhosts on server B?

```

<VirtualHost *:80>

	ServerAdmin webmaster@localhost
	ServerName site2.mydomain.com	
	ProxyRequests off
        <Proxy *>
        Order deny,allow
        Allow from all
        </Proxy>

	ProxyPreserveHost On

        ProxyPass / http://server2
        ProxyPassReverse / http://server2

</VirtualHost>

```

```

<VirtualHost *:80>
        ServerAdmin webmaster@localhost
        ServerName server2
        ServerAlias 

        ProxyRequests Off

         <Proxy *>
        Order deny,allow
        Allow from all
        </Proxy>

        ProxyPreserveHost On
        ProxyPass /application http://papaserver:9090/portal
        ProxyPassReverse /application http://papaserver:9090/portal
...

```

---

### Post by tapas_mishra on 2010-07-16
> **cdenley said:**
>  Why is it necessary to have 2 different vhosts on server B?


I am using an application known as [sakai.]("http://confluence.sakaiproject.org/display/DOC/Sakai+Admin+Guide+-+Advanced+Tomcat++(and+Apache)+Configuration")


This application is accessible from Server B as
[http://IP](http://IP) of C:9090/portal

When I had directly forwarded the request from A to C as
```

ProxyPass http://Ip of C:9090/portal
ProxyPassReverse http://Ip of C:9090/portal

```
Upon accessing the application from internet with above configuration at A 
as [http:site2.abc.com/portal](http:site2.abc.com/portal)

we found from a client browser on internet
1) /portal in the URI is automatically generated by sakai so on it I do not have any control.
2) the page elements are generated
 /portal/path/to/some/css
only these elements which began after /portal were accessible 
when I had done 
```

ProxyPass http://Ip of C:9090/portal
ProxyPassReverse http://Ip of C:9090/portal

```
at A but some of the parts of the application which had generated URL's  as 
seen via apache response headers

```

GET **/library/**skin/default/portal.css
GET /portal/styles/portalstyles.css
GET **/library/**js/jquery.js

```
You can see this thread [here]("http://www.spinics.net/lists/apache-users/msg95655.html")

So what came to my mind was I configure a vhost at B which forwards the requests to C 
since the URLs were generated at /library
and some other path elements.
The documentation of sakai is not complete.
When I tried to contact them they could not help much.
As I got a suggestion on Apache community to configure the application that it does not generate urls as 

/library/skin/default/portal.css
and instead all URLs are generated as

/portal/skin/default/portal.css
so that all the requests which come at 

[http://site2.abc.com/portal](http://site2.abc.com/portal)

to A if I do 
at A 
```

ProxyPass /portal http://vhost at B/

ProxyPassReverse /portal http://vhost at B/

```
So I do not have to worry about different URLs generated in that application.
The way they defined their context root 
is given [here]("https://source.sakaiproject.org/svn/reference/trunk/docs/architecture/sakai_urls.doc")

I read this link it was written way back in 2005 contacted the original author also but no response.

I asked on sakai forum as how can I change the context root of sakai so that it does not generates URI's as 
/library/path/to/some/css

/library was one which I caught there are many which application is generating and if I have to each time check response headers from HTTP_LIVE 
then this defeats the whole purpose of ProxyPass
More over the server on which I am testing does not have a GUI.
So each time I had to remotely login and forward display on my local machine and then compare the response coming from firefox running at A and firefox running at a different machine on internet I compare the responses checked the log files and read the documentation.
Contacted sakai and apache forums all went in vain.
The only thing that came to mind was if I can have a vhost at B which will be a front end to sakai running at C ([http://localhost:9090/portal](http://localhost:9090/portal))
and Forward that from A to B I will be able to get sakai up and running.
It has been a month but I was not able to do so.
If you want to try on your local machine let me know.

---

### Post by cdenley on 2010-07-16
I think I get what your problem is, but I don't get how you're trying to work around it. You want to proxy requests from server A to another server on port 9090. You cannot proxy one server's root directory to another, presumably because you need to use server A to serve requests for the same host name which don't get proxied to that server. Is there a reason you can't proxy all directories which may have absolute URL references, like /portal AND /library?

You might want to look at mod_proxy_html:
[http://apache.webthing.com/mod_proxy_html/](http://apache.webthing.com/mod_proxy_html/)
[http://packages.ubuntu.com/lucid/libapache2-mod-proxy-html](http://packages.ubuntu.com/lucid/libapache2-mod-proxy-html)

---

### Post by tapas_mishra on 2010-07-16
> **cdenley said:**
> I think I get what your problem is, 
Yes you did got
> **cdenley said:**
> .
but I don't get how you're trying to work around it. 

I have described complete thing in this post as why I choosed to forward request to a vhost at B and then to C.
> **cdenley said:**
> .
You want to proxy requests from server A to another server on port 9090. 

No not only port 9090 but /portal.There is no root directory or any directory that is /portal which I serve.
On that give server to access the application one need to type in 
[http://localhost:9090/portal](http://localhost:9090/portal).
Apache instance on that machine is not there it is a tomcat instance.
If I configure vhost on this machine in Apache which is C then I have to do as
<VirtualHost>
ServerName papaserver
ProxyPass / [http://localhost:9090/portal](http://localhost:9090/portal)
ProxyPassReverse / [http://localhost:9090/portal](http://localhost:9090/portal)
</VirtualHost>
[/quote]

> **cdenley said:**
> 
You cannot proxy one server's root directory to another, presumably because you need to use server A to serve requests for the same host name which don't get proxied to that server.

I am not too sure about your this statement.
But rest of the sites I have proxied this way only.
The DocumentRoots are all proxied to A.

Take following diagram
```

    |---D
    |
A---|---B-----------C
    |---E
    |---M

```

I mentioned site1.abc.com,site2.abc.com,site3.abc.com,site4.abc.com

All those websites are on D,B,E,M in above diagram.

So on A for each of these I have 

```

<VirtualHost>
 ServerName site1.abc.com
 ProxyPass / htt://IP of D 
#(as on D only site1.abc.com is so by default that is getting served )
 ProxyPassReverse / htt://IP of D 
</VirtualHost>

```

and on D where site1.abc.com is actually hosted 
I have given nothing but in the default apache installation of Ubuntu /var/www/
there is an index.html page I replaced that with a Content Management System such as Drupal.
and Vhost at D which is where site1.abc.com is 
as follows
```

<VirtualHost>
ServerName site1.abc.com
DocumentRoot /var/www/
.
.usual stuff no proxy pass
.
</VirtualHost>

```

So here I have forwarded root / at D to A and the site 
site1.abc.com is known to world coming from A and D is hidden in this case.I think I have forwarded root if this is what you meant.



> **cdenley said:**
> 
 Is there a reason you can't proxy all directories which may have absolute URL references, like /portal AND /library?

Yes there is a reason.
The application is not documented so that it tells  me 
which are at /xyx or /abc or /something

The only way known to me is 
to check [http://localhost:9090/portal](http://localhost:9090/portal)

and I check response headers of each HTML element.

which I did.

Suppose I access the application as

[http://site2.abc.com/portal/](http://site2.abc.com/portal/)

when I do not ProxyPass to some other hostname instead I direclty at A do 

```

ProxyPass /portal http://IP of C:9090/portal
ProxyPassReverse /portal http://IP of C:9090/portal

```
Application is accessible on internet.I bypassed B here.

But then the HTML links are broken.
On seeing them

[http://site2.abc.com/portal/some/path/to/css](http://site2.abc.com/portal/some/path/to/css) 
is working fine
but there are some page requests
as 
[http://site2.abc.com/library/some/path/to/css](http://site2.abc.com/library/some/path/to/css)
which is broken.
If I add at A in this situation


```

ProxyPass /portal http://IP of C:9090/portal
ProxyPassReverse /portal http://IP of C:9090/portal

ProxyPass **/library** http://IP of C:9090/
ProxyPassReverse **/library** http://IP of C:9090/


```

The the 
[http://site2.abc.com/library/some/path/to/css](http://site2.abc.com/library/some/path/to/css)
is also accessible.
Application seems to work 90%.

But when some one logs in as admin or as user 
then 
[http://site2.abc.com/](http://site2.abc.com/)**admin**/some/path/to/css

[http://site2.abc.com/](http://site2.abc.com/)**user**/some/path/to/css

is coming.
If this is happening at a small number of URLs I will fix that by adding a ProxyPass Rule for each of such 
**user** or **admin** in above rule.
But the problem is on which which page application is using some elements like this that I do not know.
Had there been a way so that I can just do a 
```

ProxyPass /portal htt://IP of C:9090/portal
ProxyPassReverse /portal htt://IP of C:9090/portal

```

Then I Do not need to put a Vhost as B in between.

> **cdenley said:**
> 
You might want to look at mod_proxy_html:
[http://apache.webthing.com/mod_proxy_html/](http://apache.webthing.com/mod_proxy_html/)
[http://packages.ubuntu.com/lucid/libapache2-mod-proxy-html](http://packages.ubuntu.com/lucid/libapache2-mod-proxy-html)
yes I had looked at them and before starting the thread both of these are enabled in my server.

---

### Post by cdenley on 2010-07-16
I still don't understand why you can't do:
```

ProxyPass / http://serverc:9090/
ProxyPassReverse / http://serverc:9090/

```

Any absolute URL references should work fine. This is what I meant by proxying a root directory. By definition, there is always a root. You can't have a subdirectory (/portal) without a root directory (/). If you need users to be able to see /portal when they browse to /, and server C doesn't redirect them, you should be able to redirect them with apache using mod_rewrite.

---

### Post by tapas_mishra on 2010-07-17
> **cdenley said:**
> I still don't understand why you can't do:
```

ProxyPass / http://serverc:9090/
ProxyPassReverse / http://serverc:9090/

```

That is the way application has been developed.I have not developed it so I do not understand it completely.I have gone through its documentation.What you have said above I had tried that.
And then 
[http://site2.abc.com/application](http://site2.abc.com/application) did not reached any where.

> **cdenley said:**
> 
Any absolute URL references should work fine. This is what I meant by proxying a root directory. By definition, there is always a root. You can't have a subdirectory (/portal) without a root directory (/). 

There is no /portal directory in the root.
Here is a [link ]("http://source.sakaiproject.org/release/2.7.0/")

if possible download it and access it on your local machine.

You download [tomcat]("http://tomcat.apache.org/download-55.cgi")

You will need a file known as sakai.properties which as per their documentation you will not get in the binary I had contacted mailing list and some how was able to get.
Extract tomcat any where in your home directory and 
in CATALINA_HOME extract sakai binary. then create a folder named 
sakai in CATALINA_HOME in that folder you need to put this sakai.properties file.
Here is the [file ]("http://pastebin.com/3vczSs3W")

---

