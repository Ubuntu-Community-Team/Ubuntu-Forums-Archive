---
title: "apache2 virtualhost configuration nighmarre"
date: 2015-11-24
forum: Server Platforms
---

### Post by hoboy on 2015-11-24
I have a server that I access remotely it is ubuntu 14.04.
I have deployed an app on that under tomcat.
that app can be access remotely using the ip and 8080 witch is the port of the app.
[http://ip:8080/](http://ip:8080/)

I have configured apache2 to access the app I am using 
 default.conf
<VirtualHost *:80>
#
 ServerName xxxxxxx.con
#
   ProxyPreserveHost On
    ProxyRequests off
    ProxyPass /test [http://127.0.0.1:8080](http://127.0.0.1:8080)
   ProxyPassReverse /test [http://127.0.0.1:8080](http://127.0.0.1:8080)
</VirtualHost>

The problem is that this is not working 
when I used 
ip/test
what I am doing wrong ?

---

### Post by darkod on 2015-11-24
Are you sure you need to use 127.0.0.1 in the redirect? I have never tried somethng like this, so I really don't know. But look at it this way: if the redirect sends 127.0.0.1 to the client, the client will search for the page on the same machine, not the server.

Have you tried redirect like the IP of the server or [http://www.domain.com:8080?](http://www.domain.com:8080?) Not the local loop IP.

PS. Can something like this help you?
[http://serverfault.com/questions/594132/how-to-pass-arguments-through-proxypass-in-apache](http://serverfault.com/questions/594132/how-to-pass-arguments-through-proxypass-in-apache)

---

### Post by hoboy on 2015-11-24
I have tried with the server ip.
ProxyPass /test [http://server-ip:8080](http://server-ip:8080)
ProxyPassReverse /test [http://serverip:8080](http://serverip:8080)
the app is running on the same machine

---

### Post by darkod on 2015-11-24
See my PS in the previous post. It seems you are using it wrong. The explanation says it works like URL replacement, so you should not use /test only.

Probably something like ProxyPass [http://www.domain.com/test](http://www.domain.com/test) [http://www.domain.com:8080](http://www.domain.com:8080)

---

### Post by hoboy on 2015-11-24
Hi Darko
my plan is to make an url that the customer will use to access to the site
for example  [http://domain.com/test](http://domain.com/test)  in order word

ProxyPass /test [http://server-ip:8080](http://server-ip:8080)
ProxyPassReverse /test [http://serverip:8080](http://serverip:8080)
[http://domain.com/test](http://domain.com/test) that should hit the app.
I have an similar configuration that work fine but for some reason this is not working.

---

### Post by darkod on 2015-11-24
I know. According to the explanation in the link I posted, the ProxyPass does URL replacement. So you want to replace one URL with the second one in that parameter. In such case, shouldn't the parameter be as I posted it in the last post? That setup will "replace" [http://www.domain.com/test](http://www.domain.com/test) with [http://www.domain.com:8080](http://www.domain.com:8080) for any visitor. And that's what you want...

Also look into whether you need to activate (enable) some module first before it can work. Maybe you are only missing enabling the module.

If you have other web servers that work it also matters the apache version. With latest ubuntu comes apache 2.4 and earlier it was other version. There are some differences in 2.4.

---

### Post by hoboy on 2015-11-24
once again tks
I want the reverse:
 "replace" [http://www.domain.com/test](http://www.domain.com/test) with [http://www.domain.com:8080](http://www.domain.com:8080)

 "replace" [http://www.domain.com:8080](http://www.domain.com:8080) with [http://www.domain.com/test](http://www.domain.com/test)
the url to access the site shuold be [http://www.domain.com/test](http://www.domain.com/test)

---

### Post by darkod on 2015-11-24
We are talking about the same thing. But I am speaking from "forward looking" perspective. The client types domain.com/test and apache module replaces that with domain.com:8080 and that is the URL called. That article explains the same. It's called replacement from that perspective.

Just try it. Did you already had a chance to try?

---

### Post by hoboy on 2015-11-24
Darko... ok I need help here

here is my real configuration


<VirtualHost *:80>
#
 ServerName servername.com
#
   ProxyPreserveHost On
    ProxyRequests off
    ProxyPass /test [http://localhost:8080/main/](http://localhost:8080/main/)
    ProxyPassReverse /test  [http://localhost:8080/main/](http://localhost:8080/main/)
</VirtualHost>

the app run on tomcat on port 8080
the machine ip..xxxxxxxxxx
what is wrong with this ?
to test on my local pc U use he remote machine ip
[http://remote](http://remote) mcahine ip/test
please help

---

### Post by darkod on 2015-11-24
In ProxyPass and ProxyPassReverse replace the
/test [http://localhost:8080/main](http://localhost:8080/main)

with:
[http://domain.com/test](http://domain.com/test) [http://domain.com:8080/main](http://domain.com:8080/main)

Restart apache. Then you can test by typing domain.com/test either on your local network or from the internet.

I assume you will be using a domain name, right? Because you want to access this from the internet. The local IP can't be used from the internet. So best to try with domain.com in the Proxy parameters. Of course, the domain.com needs to be properly configured to lead to your server public IP. And also to be properly configured on the local network.

On top of the above, as I already said, you need to investigate if any module needs to be enabled, like for example mod_rewrite. I don't know if that's the module used for ProxyPass. I don't know apache in such detail.

---

### Post by volkswagner on 2015-11-24
You are mixing technologies.

Reverse proxy pass on your config file is expecting url to be >> ServerName xxxxxxx.con (which is an example of Apache Name based virtual host).


Yet you keep writing ipaddress and expect apache to serve your reverse proxy config. For this to work, you'd need Apache ip based virtual hosts (less common).

First step is to make sure [http://xxxxxxx.con:8080](http://xxxxxxx.con:8080) gets your Tomcat site to load. Only after this is working
can you expect [http://xxxxxxx.con](http://xxxxxxx.con) to point to your reverse proxy config.

The configuration in your original post should work, but you need to use the domain name, not the ipaddress, in the url.

---

### Post by hoboy on 2015-11-25
Darko
I have tried with:
[http://domain.com/test](http://domain.com/test) [http://domain.com:8080/main](http://domain.com:8080/main)
but no luck yet.
what about ServerName servername.com ?
where does it feet in ?
tks

---

### Post by hoboy on 2015-11-25
can some body send me a correct example ?

---

### Post by hoboy on 2015-11-25
here is the virtualhost config file 
<VirtualHost *:80>
#
 ServerName test1000.com
#
   ProxyPreserveHost On
    ProxyRequests off
    ProxyPass  /test [http://localhost:8080/](http://localhost:8080/)
    ProxyPassReverse  /test [http://localhost:8080/](http://localhost:8080/)
   </VirtualHost>
[http://test1000.com/test](http://test1000.com/test)
but this doesn't work
 [http://test1000.com:8080](http://test1000.com:8080) works
I want to get rid of 8080 and replace it with test
I will like ike [http://test1000.com/test](http://test1000.com/test)
thanks in advance

---

### Post by volkswagner on 2015-11-25
I never had success using the directory pointer. I often got unexpected results.

I suggest using a subdomain or separate domain name.

I think you'll get unexpected results.

Do you have proxy and rewrite modules enabled? I created a [small tutorial]("http://ubuntuforums.org/showthread.php?t=1920715") for this a while back.

Think about it this way, if you have your tomcat application in /folder/app/ and there are links that live in /folder/app/dir1, how will
Apache be able to handle relative links like /dir1 when you are trying domain.com/test.

I just tried using the directory pointer, I got Apache to load my application but CSS was broken, and any links I clicked on gave a 404 error.

---

### Post by hoboy on 2015-11-25
Yep it is not easy but, I have a configuration example like this that working very fine.
>Nothing is ever easy, but if it is difficult you must be doing it wrong.
you are 100% right
is is possible  to send me how you have done what you have mentioned off course not with the ips ?
then I will try with that as inspiration

---

### Post by volkswagner on 2015-11-25
Sure. This is the configuration file that got my app to load, but css was broken.
This is for internal LAN only, but with a real domain and proper port forwarding this should work on WAN

```
<VirtualHost *:80>
	ServerAdmin eric@mydomain.com
	ServerName leo
	ServerAlias leo.home
	ProxyPreserveHost on
	 <location />
          allow from all
     </location>


     	ProxyPass /test http://localhost:8072/
     	ProxyPassReverse /test http://localhost:8072/

</VirtualHost>
```

---

### Post by volkswagner on 2015-11-25
May I ask why you don't want to use a sub domain?

I'm not sure if you need the /test to actually exist and be one level up from your Tomcat root directory.

Again, I never had good results with the directory pointer.

Cheers!

---

### Post by hoboy on 2015-11-25
volkswagner:
Because I don't know how.
is it posible with a little example related to my setting ?
then you will make my day :)

---

### Post by hoboy on 2015-11-25
somme body ...
Help with an example of apache2 server  sub domain.
here is my config
here is the virtualhost config file 
<VirtualHost *:80>
#
ServerName test1000.com
#
ProxyPreserveHost On
ProxyRequests off
ProxyPass /test [http://localhost:8080/](http://localhost:8080/)
ProxyPassReverse /test [http://localhost:8080/](http://localhost:8080/)
</VirtualHost>
[http://test1000.com/test](http://test1000.com/test)
but this doesn't work
[http://test1000.com:8080](http://test1000.com:8080) works
I want to get rid of 8080 and replace it with test
I will like ike [http://test1000.com/test](http://test1000.com/test)
thanks in advance

---

