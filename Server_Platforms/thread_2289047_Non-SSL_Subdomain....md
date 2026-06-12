---
title: "Non-SSL Subdomain..."
date: 2015-07-31
forum: Server Platforms
---

### Post by n_s_simpson on 2015-07-31
Hi Everyone

I have a website, which I force SSL on every page.

I use webmin but can't get a subdomain to work (we currently don't have any subdomains).

Basically I have paid for an SSL certificate to cover the main domain and nothing else.

I want a HTTP non-SSL subdomain but can't figure out how to stop the browser from being forced to use SSL. That's causing the browser to not load the page due to an SSL mismatch.

I think I need to go into the apache2.conf and mess around with RewriteCond and RewriteRule but I really can't figure it out.

Please can someone help?

Thanks

Nick

---

### Post by TheFu on 2015-08-01
Don't use webmin, so I don't know how to do it that way.
What you need is a virtual host.
[https://httpd.apache.org/docs/2.4/vhosts/examples.html](https://httpd.apache.org/docs/2.4/vhosts/examples.html)
[https://httpd.apache.org/docs/current/vhosts/name-based.html](https://httpd.apache.org/docs/current/vhosts/name-based.html)
Every different DNS name is a virtualhost.

---

### Post by n_s_simpson on 2015-08-03
Does anyone have any ideas because I'm at a loss.

What I can confirm is that I use Prestashop and I've enabled the option within its admin section so that it uses SSL for every page. I've no idea if that's somehow causing my subdomain to also try and use SSL.

---

### Post by TheFu on 2015-08-03
Sorry you don't like my answer.
I run multiple domains - primary and sub-domains. Some with SSL, most without it. I think the issue is with all the extra stuff you use "over" the web server. Learn apache, not some webgui.

---

### Post by n_s_simpson on 2015-08-03
Sorry, I didn't even spot your first post. Unfortunately I can't just learn Apache, I'm guessing it takes years of tinkering, reading and asking questions so here I am.

Anyway, I've got the subdomain to work with another SSL for that subdomain but if I disable the SSL or type in a subdomain that doesn't exist, it tries to use the main domain's SSL, so just comes up with a security error in the browser.

Very annoying.

I did make sure I get an A+ rating on SSLLabs so perhaps there's a setting I changed that's forcing SSL onto every page and subdomain.

---

### Post by n_s_simpson on 2015-08-03
I've figured something out after a load of messing about. Firstly I turned off "Header always set Strict-Transport-Security "max-age=31536000; includeSubDomains"".

That clarified what's actually going on. Any subdomain that I've not specified is being redirected to my main webpage. Without the above code that works fine but I want to know how I stop it forwarding and instead displays a page not found error.

Any ideas?

Cheers

---

### Post by nerdtron on 2015-08-04
what is the SSL cert taht your purchased? is it a wildcard cert like *.mydomain.com or a single domain certificate like [www.mydomain.com]("http://www.mydomain.com").

If you purchased a single domain certificate then you can only use that certificate for [www.mydomain.com]("http://www.mydomain.com"), and you'll need another certificate for your other subdomains. And when you use SSL on domains, you'll need explicitly define the IP address on which to bind that domain. Generic virtual host like "<VirtualHost *:443>" won't work.
Also, posting your vhost configs and apache error logs will be helpful for us to know better on what your situation is.

> Unfortunately I can't just learn Apache, I'm guessing it takes years of tinkering, reading and asking questions so here I am.
It just takes a few days, a lot of reading, testing and patience to learn apache and configurevhosts, ssl etc. If you want a fast track, a lot videos are available on youtube. Just search ubuntu, apache, and ssl.

---

### Post by Henrik_Iivonen on 2015-08-06
As advised earlier by TheFu, use Virtualhost for that subdomain and another one for your site matching the certificate.
Make subdomain listen on port 80 and the main site (with cert) on 443.
And it does not take years, just minutes to read this through.
[https://httpd.apache.org/docs/2.2/vhosts/examples.html](https://httpd.apache.org/docs/2.2/vhosts/examples.html)

No need to tinker with headers, just use virtualhosts.

---

