---
title: "trying to figure out how to do a secure proxy server that references private DNS serv"
date: 2012-07-11
forum: Server Platforms
---

### Post by bbjuju on 2012-07-11
Hi all,

I'm sort of new to Ubuntu, been playing with it in a VM for about 2 months, trying to learn everything I can about it. 

Anyway, my question, and I'm hoping someone can either assist me or point me in the correct direction.

Scenario:  I have an Ubuntu 12.04 Server x64, with Ubuntu Desktop installed for GUI uses.  I want to configure this server to act as a proxy server for me, and others, to access, but it has to be securely, preferably encrypted.  This proxy server also needs to reference a private DNS server, located on the same machine, that I can assign redirects to.  basically, if you log into my proxy server securely (I'm assuming SSH) and surf the web, if you type [www.SomeBadWebsite.com]("http://www.SomeBadWebsite.com") you will be redirected to [www.GoodWebSite.com]("http://www.GoodWebSite.com")

Please, if anyone can assist me with this, it'd be wonderful.  This is an assignment from my boss and I've literally spent hundreds of hours on and off the clock trying to figure this out.. I need help!

Thank you a TON for any/all help/assistance/pointing in the correct direction anyone can provide me!!!

---

### Post by SeijiSensei on 2012-07-11
If you can drop the encryption requirement, you could use Squid in transparent mode and a local DNS server.  This isn't at all an easy task, though, since you'd need to maintain local zone files for every possible domain your users might access.  Alternatively, if you just want to block designated remote sites and dump people to another page when they try to access them, Squid can handle that using "access control lists."  [This page](http://wiki.squid-cache.org/ConfigExamples) will give an overview of the types of things Squid can do.

If you're committed to proxying SSL connections, you need to understand how the browser will interpret this as a "man-in-the-middle" attack.  The user's browser will complain that the certificate it sees doesn't match the one from the remote server.  Squid has some new features where the proxy spoofs the remote site's certificate.  To make this work you need to set up a Certificate Authority and install certificates in every browser.  See this discussion of [ssl_bump]("http://wiki.squid-cache.org/Features/SslBump") and [certificate spoofing]("http://wiki.squid-cache.org/Features/DynamicSslCert") for details.  Note that Squid does not yet support transparent bumps though that should be available sometime later this year when [version 3.3]("http://wiki.squid-cache.org/Features/MimicSslServerCert") is released.

In the absence of proxying, your only other real alternative for SSL connections is to add an array of iptables rules on the proxy server that blocks connections to TCP port 443 on designated remote sites.

You probably need to give us some more details.  What precisely is the problem you're trying to solve?  Some problems may not be soluble at all; this could be one of them.  How knowledgeable is your boss about the technologies involved?  If the answer is, "we cannot do that," what will the consequences be?

---

### Post by bbjuju on 2012-07-12
ok, so I'm not sure exactly what my boss wants to do with this, he's being VERY cryptic about it, he just wants to know if its do able.  As for his tech knowledge, he's the CTO and knows his stuff, he's not just someone with a business degree running the IT department...

He explained what he wants as such:

Can you create a proxy server, that can be accessed remotely and securely, that references its own DNS server so that we can redirect web traffic from [www.example1.com](www.example1.com) to [www.companywebsite.com](www.companywebsite.com)

He doesn't want to do it in Windows, don't blame him with the costs associated, but he wont give me more details like what the heck he wants this for.

I do know he's not trying to recreate the wheel and let people browse anonymously, or anything like that.

The encryption/security of it is of utmost importance.  

Basically, I know what he wants, but have no idea why and have given all the details that I can think of....

Please, any help is greatly appreciated.  

Thanks

---

### Post by SeijiSensei on 2012-07-12
Is "www.example1.com" a specific site, or do you need to do this for a number of pre-designated sites, or do you need to do it for all sites?  Are you in control of the example1.com domain?

If it's just one site, then you can run Apache with SSL to accept requests for [noparse]https://www.example1.com/[/noparse] and use [mod_proxy]("http://httpd.apache.org/docs/2.2/mod/mod_proxy.html") to redirect them to www.companywebsite.com.  You wouldn't need any sort of DNS massaging as long as the public DNS record for www.example1.com points to the proxy.  If that's a site you don't control, then I don't how this is supposed to work. 

It would be one thing if you were talking about redirecting requests from people in your office.  Then you could create a zone file on your local DNS server to handle requests for the example1.com zone and redirect them to the proxy.  If we're talking about somehow intercepting public requests for a website on a domain that's not yours, I don't see any way you can do that, and thank goodness you can't.  (Actually you could do this by spreading malware that rewrites people's local hosts files or poisons their DNS caches like the [item]("http://www.fbi.gov/DNS-changer-malware.pdf") that has been in the news recently, but we're obviously not going to help you do that.)

---

### Post by bbjuju on 2012-07-12
Ok, spoke with him some more....

He wants a list of sites in the DNS server that will redirect to [www.ourcompanysite.com](www.ourcompanysite.com) and then if it isn't found in OUR DNS server, he wants it to fail-over to 4.4.2.2 (AT&T) or any other major, public DNS server.

The end-user will be aware that they are browsing using this proxy server.

So basically, I need a secure connection to a proxy server (secure traffic between proxy and end-user) that has its own DNS server while setup to use fail-over DNS server if no listing is found in our DNS server.

:confused:

Also, this proxy server will be accessed remotely.

Thank you!!

---

### Post by SeijiSensei on 2012-07-12
I'm still not clear who is using the proxy.  Members of your company?  From inside and outside the building?

Here's a possible solution.  Put all the hosts to be redirected into in the proxy's  /etc/hosts.  Have them all be aliases for 127.0.0.1.  Install apache on that machine and have it listen on that IP.  Set up a VirtualHost container like this:
```

<VirtualHost 127.0.0.1:80>
    ProxyRequests Off

    <Proxy *>
        Order deny,allow
        Allow from all
    </Proxy>

    ProxyPass /           [http://www.yourcompany.com/](http://www.yourcompany.com/)
    ProxyPassReverse /    [http://www.yourcompany.com/](http://www.yourcompany.com/)

</VirtualHost>

```

Apache calls this a "reverse" proxy.  See the documentation for [mod_proxy]("http://httpd.apache.org/docs/2.2/mod/mod_proxy.html") for details.

Now install squid.  It will use the local hosts files to resolve names and direct any requests to the hosts tied to 127.0.0.1 through Apache, which will forward them to the yourcompany.com site.

There's more that needs to be done here, like handling HTTPS, but start with plain HTTP requests and see if you can use this method to perform the redirection you want.  No promises, of course, but I think there's a way to put these pieces together and make them do what you want.

---

