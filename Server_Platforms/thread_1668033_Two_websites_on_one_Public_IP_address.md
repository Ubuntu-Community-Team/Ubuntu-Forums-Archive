---
title: "Two websites on one Public IP address"
date: 2011-01-15
forum: Server Platforms
---

### Post by Captainnow on 2011-01-15
I'm running ubuntu server 10.10.

I have it set to where I have one website running and working fine. 
I have a dns routing set from another site for it so people don't have to use my IP address to get to my site.

Now a friend has asked me to host a website on my server for him and he would like to have his own dns routing to the site.

Now can I run two separate sites on my box and have two domains routing to them.

[www.mysite.net](www.mysite.net)
[www.friends-site.net](www.friends-site.net) 

Those are just examples of course. Remember I only have one public IP. So how can I create both sites and have them each have their own public domains?

---

### Post by psusi on 2011-01-15
I don't recall the exact config but you can set up apache to create virtual servers based on the host name in the http request.

---

### Post by Captainnow on 2011-01-15
> **psusi said:**
> I don't recall the exact config but you can set up apache to create virtual servers based on the host name in the http request.

Anyone know where I can find some steps on setting that up?

---

### Post by stlsaint on 2011-01-15
Start with the apache site docs.

[http://httpd.apache.org/docs/current/](http://httpd.apache.org/docs/current/)

there you can also find the guide on vhost.

---

### Post by sj1410 on 2011-01-16
a very basic example that i use to do that and works for me


[http://blog.swapnil.me/2011/01/hosting-multiple-websites-with-apache.html](http://blog.swapnil.me/2011/01/hosting-multiple-websites-with-apache.html)

---

### Post by SeijiSensei on 2011-01-16
See [http://ubuntuforums.org/showpost.php?p=10016541&postcount=3](http://ubuntuforums.org/showpost.php?p=10016541&postcount=3).

---

