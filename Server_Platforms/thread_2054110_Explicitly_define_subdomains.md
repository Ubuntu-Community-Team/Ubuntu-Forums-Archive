---
title: "Explicitly define subdomains"
date: 2012-09-06
forum: Server Platforms
---

### Post by bradhawk08 on 2012-09-06
This may seem like a strange thing to do, but here is my thought.

If my A records define www, @, test1, and test2 subdomains for example.com, I only want those defined by apache2 on my server to respond. 

For instance, if I haven't defined test2.example.com as a virtual host, the current behavior is that a request for test2.example.com would go to the same place as example.com or [www.example.com](www.example.com). But what I want is for apache2 to basically reject all requests to any subdomain that's not defined explicitly.

It would be nice if the rejection acted exactly like if the DNS did not resolve to an IP but since it will, maybe just an unknown request or http error or some sort of error would be nice.

Thanks in advance!!

---

### Post by DJ_Max on 2012-09-06
You must have Apache setup to accept all subdomains for that domain. Simply define which sub-domains you want to allow on each vhost

---

### Post by bradhawk08 on 2012-09-06
Thanks for the quick response!

Can you tell me how exactly to do that? I have the default configuration.

Thanks in advance!

---

### Post by sandyd on 2012-09-07
Right now, you only have one virtualhost. Since I don't run apache on Ubuntu, I can't safely answer that question.

However, I do know that you have to create a virtualhost for each subdomain you want to use
Something like this may suffice.
```

sudo cp /etc/apache2/sites-avaliable/000-default /etc/apache2/sites-avaliable/subdomain.name
#Change the values to suit your own in the below file
sudo nano /etc/apache2/sites-avaliable/subdomain.name

a2ensite subdomain.name

```
replacing **subdomain.name** with your subdomain, just for organization's sake.


Set
```
ServerName
``` for each subdomain. to set the subdomain (i.e. sandy.sandyd.me)

---

### Post by Bachstelze on 2012-09-07
If the server is accessed with some name and no virtualhost matches that name, the default virtualhost will be used. The corollary is obvious: just create a "catch-all" virtualhost that will serve only a blank page (or an error page if you really want to), and move it to the bottom of the list so that it will be used only if the name that was used does not match any of your virtualhosts.

---

