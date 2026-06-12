---
title: "Site down after a2enmod headers"
date: 2018-12-05
forum: Server Platforms
---

### Post by phixate on 2018-12-05
I was trying to put a redirect from http to https in my example.com.conf file like this: 

```

<VirtualHost *:80> 
[...] 
ServerName example.com 
Redirect permanent / [https://example.com/](https://example.com/)
```

I saved the file and did this a2enmod headers to prepare for HSTS setup (which I'm not sure if I need Nginx for that??). After this my website no longer works. Prior to this it worked fine over http or https. 

I tried a2dismod headers and removing the redirect line but the site is still down. Anyone know what I did to hose it and how to fix it? 

I'm looking at the error log and it appears it might be a WordPress issue. I'm getting a database error after installing WooCommerce and upping the PHP memory limit to 256M, the two steps I took before installing my SSL. I'll try disabling the plugin to see if it fixes the issue. 

It's still trying to redirect to https though. Are those conf files cached or something? 

I tried changing the wordpress URL to https and renamed woocommerce directory to disable but that didn't work. 

I reinstalled WordPress and WooCommerce and I can get into the back end but the site won't load on the front via http or https. This leads me to think it's a problem with the Apache virtualhost configuration or module. I've checked the apache2, 000-default and example.com conf files and everything looks fine. There are no redirects. I tried sudo a2dissite 000-default.conf. Nothing. Still hangs and then triese to go to https before the connection times out.

EDIT: So I opened the HTTPS port on AWS (oops forgot about that) and now it's no longer hanging BUT it's still not connecting to the site. It just kicks over to HTTPS and says "This site can&#8217;t provide a secure connection"

EDIT2: So I'm guessing it had something to do with my virtualhost config for my site. I added 

```

SSLEngine on 
SSLCertificateFile /etc/ssl/example.com_crt 
SSLCertificateKeyFile /etc/ssl/private/example.com.key 
SSLCertificateChainFile /etc/ssl/example_com.ca-bundle
```

and ran a apachectl -t and it says the SSLCertificateKeyFile does not exist or is empty. I put the file in the etc/ssl/private folder twice. Is this a permissions issue maybe? Oh and the file is not empty.

[COLOR=#333333][FONT=Verdana]EDIT3: OK so I got it. I accidentally placed a / in front of my directory when moving my key file and it wound up in the root with a different name. I had to chagne the name back and chown it to root and mv it to the /etc/ssl/private directory. Now to figure out this HSTS stuff. Not sure if I want to go there just yet after all this.[/FONT][/COLOR]

---

### Post by QIII on 2018-12-05
Hello!

Please use the default font and color unless there is a compelling reason to draw attention to a particular part of your thread.

Also, enclose all code, terminal commands and their results in code tags.

To use code tags, either:

1.  Click the # button in the toolbars above the text entry box, place your cursor between the code tags that appear and type or paste your text.  Alternatively, type or paste your text, highlight it and then click the # button.

2.  Type [noparse]```
[/noparse] before your text and [noparse]
```[/noparse] after it.  The square brackets are required.

---

