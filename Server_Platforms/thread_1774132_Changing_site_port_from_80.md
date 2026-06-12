---
title: "Changing site port from 80"
date: 2011-06-02
forum: Server Platforms
---

### Post by poker158149 on 2011-06-02
Right now my server is being used as a [Minecraft]("http://minecraft.net") server. I have a site hosted on it, but my ISP blocks port 80, so I'm the only one who is able to view the site. I want to be able to change the port the site is on so that anyone can view it. I've looked it up and apparently that is possible; however, I haven't found out how to do it. I've changed the ports.conf file in /etc/apache2 and the default file in /etc/apache2/sites-available, but it didn't work. All that did was take my site off of 80, but it did not put it on the new port I specified. What exactly do I have to change so that when I go to mysite:port, it loads my website?

Thanks for any replies!

EDIT: Also, just for extra information, the two ports I tried were 8080 and 81.

---

### Post by R.Bucky on 2011-06-02
When you changed the port, did you open up your hardware to ensure it can be accessed? Did you reload Apache after you made the changes? Does your site configuration in /etc/apache2/sites-available look like this below? 

```
<VirtualHost *:80>
ServerName nwlinux.com
DocumentRoot /your/document/root/
</VirtualHost>
```

Depending on your configuration, you could always use Varnish or Squid proxy.

---

### Post by poker158149 on 2011-06-02
I'm not sure what you mean by open up my hardware, but I did restart Apache and my configuration does look like that.

I might have to end up using one of those proxies.

---

### Post by CharlesA on 2011-06-03
You wouldn't even have to change anything on the local machine, just change which port you are forwarding to.

---

### Post by poker158149 on 2011-06-03
@CharlesA

Wow, I didn't even think about forwarding the port. 

Thanks a bunch, that did it.

---

