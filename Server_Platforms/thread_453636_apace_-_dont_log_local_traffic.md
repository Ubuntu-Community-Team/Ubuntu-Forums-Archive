---
title: "apace - dont log local traffic"
date: 2007-05-24
forum: Server Platforms
---

### Post by ninocass on 2007-05-24
ive had a good google search and found some code hat could make apache not local my local access to it

```

SetEnvIf Remote_Addr "192\.168\.11\." nolog
CustomLog /var/log/apache2/access.log combined env=!nolog

```

I have this in my defaults file:

/etc/apache/sites-available/httpd.conf

its still logging the traffic

---

### Post by ninocass on 2007-05-25
Ive managed to get it to split the traffic into 2 logs using:

```

        SetEnvIf Request_URI \.gif$ images
        SetEnvIf Request_URI \.png$ images
        SetEnvIf Request_URI \.jpg$ images
        SetEnvIf Remote_Addr "127\.0\.0\.1" trust
        SetEnvIf Remote_Addr "192\.168\.11" trust
 
        CustomLog /var/log/apache2/access_images.log combined env=images
        CustomLog /var/log/apache2/access_https_trusted.log combined env=trust
        CustomLog /var/log/apache2/access_https_untrusted.log combined env=!trust

```

However i want to incorperate this no images logging as well so i need someone way of getting the program to do trust AND !images i was thinking:

CustomLog /var/log/apache2/access_https_trusted.log combined env=(trust\.!images)

but alas it doesnt work i think my logic is off

Thanks

nino

---

