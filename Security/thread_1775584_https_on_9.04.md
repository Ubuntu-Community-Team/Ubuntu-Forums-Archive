---
title: "https on 9.04"
date: 2011-06-04
forum: Security
---

### Post by cwscribner on 2011-06-04
Hi all.

I have an application hosted on a 9.04 server.  Access to this application is done via a port forward from a firewall to the 9.04 server.  How can I force all access to this application to be https?

---

### Post by BkkBonanza on 2011-06-05
Often this is done with a rewrite rule in apache. It can also be done with a redirect page on the regular http page forcing the user to the https version.

For the rewrite rule, which is pretty easy, a quick google turns up this page,
[http://www.besthostratings.com/articles/force-ssl-htaccess.html](http://www.besthostratings.com/articles/force-ssl-htaccess.html)

---

### Post by cwscribner on 2011-06-13
I've seen the rewrite rule method.  But that doesn't *actually* do the https...just redirects to it.  I can't figure out how to get the https prefix on the application.  I've tried several HowTo's but none have worked.  Any ideas?

---

### Post by BkkBonanza on 2011-06-13
I'm not sure what you mean. 

The redirect will cause the url to be changed to https automatically. 

If you mean how can you make some client application support https, then you can't - it has to be programmed in to be able to do it. Simply forcing it to use port 443 will not mean it can do ssl unless the client app has ssl support coded in. 

All browsers do have ssl support and when they get a redirect to an ssl page they will do the handshaking as needed. But some other app without ssl support isn't going to do that - it will error out when hitting an ssl page. Simply forwarding a port from 80 to 443 will not work in any case.

On the other hand, if by "application" you mean a web server app, running under Apache then - yes, you need to add config lines to Apache for the site to enable https support on the site. It's fairly easy but without them it won't answer port 443 correctly. There are lots of tutorials around on enabling ssl in Apache.

The redirect only makes sure that people can't access the http pages as they get sent to the https instead - but you still need to configure https to work otherwise the redirect isn't useful at all.

---

### Post by psusi on 2011-06-13
9.04 reached end of life 8 months ago and has not received security updates since then.  You need to upgrade ASAP.

---

### Post by cwscribner on 2011-06-14
> **psusi said:**
> 9.04 reached end of life 8 months ago and has not received security updates since then.  You need to upgrade ASAP.

Upgraded to 10.04.  However, my previous problem remains.  I'm thinking that the certificates are not properly installed but I've tried it with two different HowTo's (executed to the letter) and still no luck.  I don't know much about OpenSSL other than what I've read in the HowTo's.

---

### Post by BkkBonanza on 2011-06-14
Please provide info about what you've done, what error msg you get. With more specific details we may be able to help.

---

### Post by Het@l99 on 2011-06-15
I think you should configure the TLS and SSL certificates in this upgrade version. May that helps you to solve the problem.

---

### Post by cwscribner on 2011-06-16
I tried the following HowTo's along with the rewrite rule.  When I try to access the application, it just says that there's a server configuration error (Error 107).

[http://www.tc.umn.edu/~brams006/selfsign_ubuntu.html]("http://www.tc.umn.edu/~brams006/selfsign_ubuntu.html")

[http://www.linode.com/wiki/index.php/Apache2_SSL_in_Ubuntu]("http://www.linode.com/wiki/index.php/Apache2_SSL_in_Ubuntu")

---

### Post by bodhi.zazen on 2011-06-16
> **cwscribner said:**
> I tried the following HowTo's along with the rewrite rule.  When I try to access the application, it just says that there's a server configuration error (Error 107).

[http://www.tc.umn.edu/~brams006/selfsign_ubuntu.html]("http://www.tc.umn.edu/%7Ebrams006/selfsign_ubuntu.html")

[http://www.linode.com/wiki/index.php/Apache2_SSL_in_Ubuntu](http://www.linode.com/wiki/index.php/Apache2_SSL_in_Ubuntu)

I agree with the advice on upgrading your server.

In terms of your current problem, please post additional information, what rule did you add ?

See also : [http://www.cyberciti.biz/tips/howto-apache-force-https-secure-connections.html](http://www.cyberciti.biz/tips/howto-apache-force-https-secure-connections.html)

---

### Post by cwscribner on 2011-06-17
I used a method almost identical to the one you posted.

---

### Post by cwscribner on 2011-06-17
Do the HowTo's look legitimate?  It seems like the problem is with the certificate installation but I have no prior experience with this, so I can't be sure.

---

### Post by bodhi.zazen on 2011-06-17
> **cwscribner said:**
> I used a method almost identical to the one you posted.

How was your method almost different ?

---

### Post by cwscribner on 2011-06-18
The second part of the Redirect line was [https://localhost](https://localhost)

That's the only difference.  The process was the same

---

### Post by crispy_420 on 2011-06-18
> **cwscribner said:**
> I tried the following HowTo's along with the rewrite rule.  When I try to access the application, it just says that there's a server configuration error (Error 107).

[http://www.tc.umn.edu/~brams006/selfsign_ubuntu.html]("http://www.tc.umn.edu/~brams006/selfsign_ubuntu.html")

[http://www.linode.com/wiki/index.php/Apache2_SSL_in_Ubuntu]("http://www.linode.com/wiki/index.php/Apache2_SSL_in_Ubuntu")

I've used these exact howtos successfully before. Why not just posting the top portions of both sites-enabled feeling free to omit private info if any.

---

### Post by bodhi.zazen on 2011-06-18
> **cwscribner said:**
> The second part of the Redirect line was [https://localhost](https://localhost)

That's the only difference.  The process was the same

you can not use localhost, you need to use [https://fqdn](https://fqdn)

the same FQDN you used for you ssl.

---

### Post by cwscribner on 2011-06-20
> **bodhi.zazen said:**
> you can not use localhost, you need to use [https://fqdn](https://fqdn)

the same FQDN you used for you ssl.

So if my ssl files (.key, .pem, etc.) are named my_server.key(.pem) then the changes to sites-available must be my_server instead of localhost?

---

### Post by bodhi.zazen on 2011-06-20
> **cwscribner said:**
> So if my ssl files (.key, .pem, etc.) are named my_server.key(.pem) then the changes to sites-available must be my_server instead of localhost?

yes, all your config files must use your FQDN , and not 127.0.0.1 or localhost.

---

### Post by cwscribner on 2011-07-01
Okay so I've had some luck.  I can type in [https://ubuntu-netbook](https://ubuntu-netbook) and it'll prompt me to accept the certificate.  So I click accept/proceed but it then gives me a 403 Forbidden.  I'm assuming its something to do with the file permissions but I'm not quite sure what they need to be changed to.  I followed this HowTo: [http://www.tc.umn.edu/~brams006/selfsign.html]("http://www.tc.umn.edu/~brams006/selfsign.html")

The permissions for www/ and www-ssl/ are 766 (rwx_r-x_r-x).  They're currently owned by chad:root...should that be changed to a generic web user?  What should the permissions be changed to?

---

### Post by bodhi.zazen on 2011-07-02
Check your logs =)

I usually keep /var/www and contents owned by root with group of www-data and permissions of 750 for directories and 640 for files, sort of depends on what you are serving up though.

---

### Post by cwscribner on 2011-07-05
Its going to be a secure php based application.

What logs should I check?  Apache's?

Edit: I initially changed the permissions because when I opened any files in the documentroot to edit (like in geany) it wouldn't allow me to edit them.  How do the permission changes affect this?

---

