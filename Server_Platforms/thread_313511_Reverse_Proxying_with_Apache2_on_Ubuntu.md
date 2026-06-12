---
title: "Reverse Proxying with Apache2 on Ubuntu"
date: 2006-12-06
forum: Server Platforms
---

### Post by Roddles on 2006-12-06
Hi

I have been sifting through web site after web site for the past 4 days trying to work out how to set up simple reverse procying using apache2 on Ubuntu.

This has been a frustrating and fruitless effort thus far - so I have to admit defeat and ask for help...

I am not familiar with Apache, so have been trying to learn it as I go along which of course has made things seem a lot more difficult then Im sure they are.

What I am trying to set up is an Ubuntu server (done - that part was easy), running apache2 with the proxy and ssl modules enabled (that was done pretty simply as well).

I have several web servers running on a private network that i want to reverse proxy to.

eg, for the url [http://www.site1.com](http://www.site1.com) - it will go to my proxy server, then that server will reverse proxy to [http://internal1.local](http://internal1.local)

for [http://www.site2.com](http://www.site2.com) - again resolves to my proxy server and is then reverse proxied to http:internal2.local

internal1 is a windows 2003 web server and internal2 is a ubuntu server running apache.

What I am looking for is a guide or a link to a site which will explain how I need to set this up, including which configuration files I need to make modifications to in order to get this working. 

half my problem is I can only find information peice meal and that information doesnt indicate which configuration file I am supposed to be modifying.

Any help that someone can offer in how to set this up properly in Ubuntu would be much appreciated.

As i mentioned - I have not been able to find the right information yet.

Cheers and thanks in advance..

Rod.
](*,)

---

### Post by cronholio on 2006-12-06
I don't think a web server is needed to accomplish what you want. The easiest way to do it will be to install dnsmasq (a DNS server) and add entries to the /etc/hosts file of that machine, those should contain the internal IPs and external hostnames. Then make your clients use the Ubuntu machine as DNS server.

---

### Post by Roddles on 2006-12-06
Hi 

Thanks for your response - and I can see how that will work well for all internal clients - but this is internet traffic coming in via a single IP address mapped to multiple domain names.

based on the host header value, i want the traffice to be reverse proxied to the appropriate internal web server and then back out again.

Does this make sense?

Regards

Rod.

---

### Post by Brazen on 2006-12-06
just put this in /etc/apache2/sites-available/default:

```
NameVirtualHost *

<VirtualHost www.site1.com:80>
    ProxyPass / http://internal1.local/
    ProxyPassReverse / http://internal1.local/
</VirtualHost>


<VirtualHost www.site2.com:80>
    ProxyPass / http://internal2.local/
    ProxyPassReverse / http://internal2.local/
</VirtualHost>
```

---

### Post by Brazen on 2006-12-06
by the way, you could also proxy both servers through a single dns name with something like this:
```
NameVirtualHost *

<VirtualHost www.dnsname.com:80>
    ProxyPass /site1/ http://internal1.local/
    ProxyPassReverse /site1/ http://internal1.local/

    ProxyPass /site2/ http://internal2.local/
    ProxyPassReverse /site2/ http://internal2.local
</VirtualHost>
```

With this you would access site1 at [http://www.dnsname.com/site1/](http://www.dnsname.com/site1/) and site2 at [http://www.dnsname.com/site2/](http://www.dnsname.com/site2/)

---

### Post by Roddles on 2006-12-06
Hi 

Thanks for your response

Should i only have what you listed below in the defualt file, or should i just add this to the bottom of the file?

Just want to clarify exactly what should be in the default file in sites-available

Many thanks

Rod.:)

---

### Post by cronholio on 2006-12-07
Depends on what you want: By default, there is one Virtualhost entry (<VirtualHost *>...</VirtualHost) in this file, its main purpose is to enable pages in your /var/www directory. If you don't want that, you can delete it.

---

### Post by Roddles on 2006-12-07
Hi again

ok - its working now - I created a new file in the /etc/apache2/sites-available directory whcih contained the information for a virtualHost, then used a2ensite <filename> to enable it

At this point it was trying to proxy but giving me permission denied errors.

I also had to open /etc/apache2/mods-available/proxy.conf and set the proxy to  allow from all, it defaults to Deny all when apache is installed.

after this the http proxy worked fine.

Now - I have one more hurdle - enabling proxying of https requests as well.

thats proving to be alittle more elusive.

any hints?

Cheers

Rod.

:D

---

