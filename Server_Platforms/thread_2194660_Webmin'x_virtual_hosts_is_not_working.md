---
title: "Webmin'x virtual hosts is not working"
date: 2013-12-19
forum: Server Platforms
---

### Post by kavex1988 on 2013-12-19
Ok so I decided to check out webmin because it seems a nice way to setup a virtual hosts. I've done this the old fashion way a few years back and didn't have any issues then. 

I used "A" Record Type point to my IP for my VPS

In webmin I created a new virtual host

Handle connections to address: Any address [Selected]
Add name virtual server address (if needed) [Checked]
Listen on address (if needed) [Checked]
Port: Default [Selected]
Document Root: /home/domain.com/public_html
Server Name: domain.com
New file under virtual servers directory /etc/apache2/sites-available [Seletced]
Copy directives from: Nowhere [Selected]

I've watched videos on people making a domain and it seems to work flawless for them

When i go to my domain after adding a test html file it doesn't show (Not a cache issue)

Any idea whats going wrong?

Ubuntu 12.04

---

### Post by volkswagner on 2013-12-20
Ubuntu does not support Webmin.  It creates a mangled config.  I suggest dropping Webmin for vhosts.

Have you looked at the vhost file created by Webmin?

Please post it here.


Also saying it does not work is not descriptive.  What happens in the browser?  What does apache2 log show?

---

### Post by kavex1988 on 2013-12-20
Well that explains a lot 

 The file is empty ... I knew I should have done it the old fashion way instead of trying to do a shortcut which the end cost me more time. I think I got it from. I at least now I know i'm not crazy.

---

### Post by sparticle2000 on 2013-12-20
I have been using Webmin/Virtualmin for years and have humdreds of domains configured and managed this way, and I can assure you that it creates perfect name based virtual hosts on Ubunutu noth secure and standard http.. My advice would be to install virtualmin and let it do all the hard work for you configuring the vhosts and other shared services per domain. If you don't want email etc. you can simply turn off that capability per vhost using a template or at creation time.

My main production machnes are all Ubuntu 12.04.x and webmin/Virtualmin.

Cheers
Spart

---

