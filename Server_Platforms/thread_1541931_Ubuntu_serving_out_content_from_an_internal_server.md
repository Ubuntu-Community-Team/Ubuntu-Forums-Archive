---
title: "Ubuntu serving out content from an internal server"
date: 2010-07-29
forum: Server Platforms
---

### Post by wmgries on 2010-07-29
Hey, I have a relatively simple question: can Ubuntu/Apache display content from a server on my intranet? My Ubuntu server currently serves out pages with Apache, but I need to have IIS installed on one of my Windows boxes for work (I know, I know, I hate IIS/ASP.NET too). It would be really nice if I could create a folder on my server that basically pipes out content from that internal server.

Please let me know if I need to clarify what I am trying to do a little bit more. Thanks for the help!

---

### Post by volkswagner on 2010-07-29
I'm thinking you should be able to use a virtual host file with the directive pointing to your IIs server ip.

IE:
Rather than

```
<VirtualHost *>

```

try

```
<VirtualHost 192.168.IIS.ipaddress>

```

So if your router has port 80 forwarded to your Ubuntu box, your Ubuntu box will forward the request to your windows box when the domain for IIS sites is requested.

---

### Post by wmgries on 2010-07-30
Ok, I'm not entirely sure how to edit the Virtual Hosts file to keep my existing site going to Ubuntu/Apache and only get one folder to direct to the IIS box. Here is my first stab at it - THIS DOES NOT WORK:

```

<VirtualHost 192.168.1.109>
  DocumentRoot "/home/www/IIS/"
</VirtualHost>

```

Thanks for the quick response!

---

### Post by Vegan on 2010-07-30
You can use http redirects to send specific URLs to the other server. That requires some configuration. Consult Google for it.

:guitar:

---

### Post by wmgries on 2010-07-30
Will that work if my IIS server is behind the firewall? The only thing exposed is my Ubuntu server and I intend to keep it that way.

---

