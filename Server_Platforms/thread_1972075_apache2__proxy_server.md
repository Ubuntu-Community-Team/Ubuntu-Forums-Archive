---
title: "apache2  proxy server"
date: 2012-05-03
forum: Server Platforms
---

### Post by winzip on 2012-05-03
my  ubuntu server box  has version

**$apache2 -v**
[I]Server version: Apache/2.2.14 (Ubuntu)
[/I]
I see it has two conf  files...i.e

**httpd.conf**

[B]apache2.conf
[/B]

Which file I need to configure  if I  want to use apache2 as proxy server to  my application server ?

---

### Post by lisati on 2012-05-03
*Thread moved to **Server Platforms**.*

---

### Post by winzip on 2012-05-03
> **lisati said:**
> *Thread moved to **Server Platforms**.*


comments please.

---

### Post by Jonathan L on 2012-05-03
Hi Winzip

>  I  want to use apache2 as proxy server to  my application server 

It's pretty much a few lines, but please **do** read [http://httpd.apache.org/docs/2.4/mod/mod_proxy.html](http://httpd.apache.org/docs/2.4/mod/mod_proxy.html) _first_.

In Ubuntu, it's more normal to use the provided-configuration files (in mods_available) and link them

```
a2enmod proxy
```

Do then check your configurations and do testing before you get surprises.

Hope that's helpful.

Kind regards,
Jonathan.

---

### Post by winzip on 2012-05-03
> **Jonathan L said:**
> Hi Winzip



It's pretty much a few lines, but please **do** read [http://httpd.apache.org/docs/2.4/mod/mod_proxy.html](http://httpd.apache.org/docs/2.4/mod/mod_proxy.html) _first_.

In Ubuntu, it's more normal to use the provided-configuration files (in mods_available) and link them

```
a2enmod proxy
```Do then check your configurations and do testing before you get surprises.

Hope that's helpful.

Kind regards,
Jonathan.

I'm still  confused.  I still dont get  which file needs modification.

httd.conf  
apache2.conf

Your tutorial link does not talk about these files. Does that mean you dont  need to modify these files ?

---

### Post by Jonathan L on 2012-05-03
Hi again

> I'm still  confused.  ... Does that mean you dont  need to modify these files ?That's right, you don't modify the files.  In the usual Ubuntu setup, httpd.conf is empty, and apache2.conf includes all the files required from the various "enabled" directories.

What you do is:[FONT=monospace]
[/FONT]```
sudo a2enmod proxy proxy_http
```

then edit the /etc/apache2/mods-enabled/proxy.conf to look something like this: the red parts are non-default.
```
<IfModule mod_proxy.c>
        #turning ProxyRequests on and allowing proxying from all may allow
        #spammers to use your proxy to send email.

        ProxyRequests [COLOR=Red]On[/COLOR]

        <Proxy *>
                AddDefaultCharset off
                Order deny,allow
                Deny from all
                 Allow from [COLOR=Red]127.0.0.1[/COLOR]
                #Allow from .example.com
        </Proxy>

        # Enable/disable the handling of HTTP/1.1 "Via:" headers.
        # ("Full" adds the server version; "Block" removes all outgoing Via: headers)
        # Set to one of: Off | On | Full | Block

        ProxyVia On
</IfModule>
```That gets you a basic proxying system which you can test from the local host.

Hope the concrete example is more helpful.

Kind regards,
Jonathan.

---

### Post by winzip on 2012-05-03
> **Jonathan L said:**
> Hi again

That's right, you don't modify the files.  In the usual Ubuntu setup, httpd.conf is empty, and apache2.conf includes all the files required from the various "enabled" directories.

What you do is:[FONT=monospace]
[/FONT]```
sudo a2enmod proxy proxy_http
```then edit the /etc/apache2/mods-enabled/proxy.conf to look something like this: the red parts are non-default.
```
<IfModule mod_proxy.c>
        #turning ProxyRequests on and allowing proxying from all may allow
        #spammers to use your proxy to send email.

        ProxyRequests [COLOR=Red]On[/COLOR]

        <Proxy *>
                AddDefaultCharset off
                Order deny,allow
                Deny from all
                 Allow from [COLOR=Red]127.0.0.1[/COLOR]
                #Allow from .example.com
        </Proxy>

        # Enable/disable the handling of HTTP/1.1 "Via:" headers.
        # ("Full" adds the server version; "Block" removes all outgoing Via: headers)
        # Set to one of: Off | On | Full | Block

        ProxyVia On
</IfModule>
```That gets you a basic proxying system which you can test from the local host.

Hope the concrete example is more helpful.

Kind regards,
Jonathan.


where do you write  proxypass and reverseproxy ?

---

### Post by SeijiSensei on 2012-05-03
> **winzip said:**
> where do you write  proxypass and reverseproxy ?

If you're trying to forward requests from Apache to another server, you need to set up what Apache calls a "[reverse proxy]("http://httpd.apache.org/docs/2.2/mod/mod_proxy.html#forwardreverse")."  Create a file (as root with sudo) named /etc/apache2/sites-available/myproxysite:

```

<VirtualHost *:80>
    ServerName  www.example.com
    ProxyPass        /   http://my.application.server.com/
    ProxyPassReverse /   http://my.application.server.com/
</VirtualHost>

```

Then run 
```

sudo a2ensite myproxysite
sudo service apache2 restart

```

Now requests that arrive at Apache for [www.example.com](www.example.com) should be passed to my.application.server.com.

---

### Post by winzip on 2012-05-03
This is confusing ...too many config files are floating around here..

does  post  #6  and post #8  do same thing ?

Are they doing same  thing ?

---

### Post by SeijiSensei on 2012-05-04
No.  The type of proxying that Jonathan described uses Apache as a outbound proxy much like Squid.  What I think you're looking for is, as I said, what Apache calls a "reverse proxy" where requests sent to Apache are forwarded to another server.

Now if you just have one web site on one server, it's often much easier to implement this by port forwarding with iptables.  Using Apache as a proxy server lets you have more fine-grained control over which specific requests get proxied.  For instance, you can have an Apache reverse proxy which answers requests for [http://www.example.com/](http://www.example.com/) itself, but forwards requests for [http://www.example.com/app/](http://www.example.com/app/).  The example I gave proxies the entire "/" URI so all requests get forwarded, but the example in the documentation on the Apache site shows how to proxy "/foo" but not requests for "/bar" or "/".

---

### Post by winzip on 2012-05-04
> **SeijiSensei said:**
> No.  The type of proxying that Jonathan described uses Apache as a outbound proxy much like Squid. 


outbound proxy  ...what is that ?   Please give an example here .  ...is it also called forward proxy ?


> 
What I think you're looking for is, as I said, what Apache calls a "reverse proxy" where requests sent to Apache are forwarded to another server.
yup .  I  understand this part.  by the way you are forwarding requests here ...what is reverse here ?  I think the naming "reverse proxy"  does not make sense .

---

### Post by SeijiSensei on 2012-05-04
> **winzip said:**
> outbound proxy  ...what is that ?   Please give an example here .  ...is it also called forward proxy ?

Yes.  You would configure your browser to use it.  In Firefox, you'd use Edit > Preferences > Advanced, and then click the button to "configure how Firefox connects to the Internet."  With this type of proxy all your outbound HTTP requests are sent to the proxy which resends them on your behalf then returns the results back to your browser.  These are commonly used by people whose browsing is limited by network policies or political repression.

I agree that "reverse" is probably not the best term for the other type of proxy.  I prefer "inbound" since you're forwarding requests coming into Apache.

---

### Post by winzip on 2012-05-04
Case1: i use a proxy ip to access gmail in my work place . Is this outbound proxy /forward proxy ?

Case 2: i call apache server ip. Apache calls other server to get me the result.
Is it reverse proxy?

---

### Post by SeijiSensei on 2012-05-04
Yes and yes.

---

### Post by winzip on 2012-05-04
Thanks. I got it. Thanks for your time.

---

