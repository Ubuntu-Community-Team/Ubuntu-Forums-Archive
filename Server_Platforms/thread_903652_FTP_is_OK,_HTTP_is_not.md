---
title: "FTP is OK, HTTP is not"
date: 2008-08-28
forum: Server Platforms
---

### Post by Vegan on 2008-08-28
Well I have telnet working across the LAN, but until I added a default value to the httpd.conf I could not get anything up in HTML. Now with that default I can get a page to come up, by the local IP address, not by the URL in Firefox.

[ftp://domain.com](ftp://domain.com) works, [http://domain.com](http://domain.com) does not, any thoughts?

---

### Post by cdenley on 2008-08-28
> **Vegan said:**
> Well I have telnet working across the LAN, but until I added a default value to the httpd.conf I could not get anything up in HTML. Now with that default I can get a page to come up, by the local IP address, not by the URL in Firefox.

[ftp://domain.com](ftp://domain.com) works, [http://domain.com](http://domain.com) does not, any thoughts?

You mean [http://computer-chess.dyndns.biz/](http://computer-chess.dyndns.biz/)? It works fine for me. It's probably an issue with your router. Are you aware that telnet and ftp do not use any encryption? Use ssh instead.

---

### Post by Vegan on 2008-08-28
Can you connect and does the page render ok? I only get the same default page no matter where I go, I have 5 URLs and they all go back to the same index. Any thoughts?

---

### Post by skunkbad on 2008-08-28
I can see your website just fine. Maybe you have a DNS cache issue.

---

### Post by Vegan on 2008-08-28
I went to an outside place and my domains came up. Seems only to be locally for some reason? At least the public can see my sites.

[computer-chess.dyndns.biz]("http://computer-chess.dyndns.biz")
[contract-developer.dyndns.biz]("http://computer-chess.dyndns.biz")
[econ.dyndns.biz]("http://econ.dyndns.biz")
[vegan.dyndns.biz]("http://vegan.dyndns.biz")
[web-developer.dyndns.biz]("http://web-developer.dyndns.biz")

Are my domains, I needed to use F5 to get them to load properly. Must be a cache problem somewhere.

Sure a pain to up a server. Almost as bad as a Microsoft server. ewwww.

---

### Post by freebeer on 2008-08-29
> **Vegan said:**
> I went to an outside place and my domains came up. Seems only to be locally for some reason? 

My guess is that your router doesn't support loopback.  Many don't.  So edit the local /etc/hosts file so that "mydomain.com" points to the local IP address of the server.

---

### Post by Vegan on 2008-08-29
I tried using Internet Explorer and the pages came up fine. So the Linksys WRT54G does support loopback and full intranet. The problem is Firefox which cannot function properly.

Microsoft's telnet works with the ip address, not the URL. Same with the FTP client I use.

news flash (posted on Firefox's page too), 80% of page views are on an intranet.

Turns out I was wasting my time due to the Firefox defect. To debug a web server, I now suggest IE until Mozilla fixes this glaring defect.

---

### Post by windependence on 2008-08-30
I seriously doubt that Firefox is the cause of this. There is something (probably DNS) not configured correctly on your LAN. Make sure you aren't getting a cached site on IE, it's notorious for this.

-Tim

---

### Post by Vegan on 2008-08-31
I clear the caches regularly with all my browsers. Mainly for security reasons but also for making sure pages are live and correct. Need to put more scrutiny into this.

---

### Post by cdenley on 2008-09-01
```

Turns out I was wasting my time due to the Firefox defect. To debug a web server, I now suggest IE until Mozilla fixes this glaring defect.

```

Since it works for us, it obviously isn't a "Firefox defect". The best way to test a web server would be to talk to it directly with telnet.

[http://www.esqsoft.com/examples/troubleshooting-http-using-telnet.htm](http://www.esqsoft.com/examples/troubleshooting-http-using-telnet.htm)

```

telnet 24.69.183.2 80
GET / HTTP/1.0
host: computer-chess.dyndns.biz

```
```

telnet 24.69.183.2 80
GET / HTTP/1.0
host: vegan.dyndns.biz

```

---

### Post by Vegan on 2008-09-01
IE7,8 work, Opera OK, Safari OK, Firfox fail.

I realize I can use telnet on port 80, but as I pointed out. 80% of web page views are on an intranet.

---

### Post by cdenley on 2008-09-02
> **Vegan said:**
> IE7,8 work, Opera OK, Safari OK, Firfox fail.

I realize I can use telnet on port 80, but as I pointed out. 80% of web page views are on an intranet.

And? There is no reason for Firefox to receive a different result since all the browsers send the same request with the same "host" header. Until you post captured http traffic that proves otherwise, I would assume it is a caching or networking issue. It works correctly for us, and we're using firefox. Are you trying to suggest firefox isn't sending the "host" header?

---

### Post by Vegan on 2008-09-03
I am not going to up network management tools to diagnose the problem, I leave that to the program developers. IE works, Safari works, Opera works, Firefox and Chrome don't. I open each browser and same URL, real simple testing criteria.

Keep in mind some 80% of web page views are on an intranet.

---

### Post by cdenley on 2008-09-03
> **Vegan said:**
> I am not going to up network management tools to diagnose the problem, I leave that to the program developers. IE works, Safari works, Opera works, Firefox and Chrome don't. I open each browser and same URL, real simple testing criteria.

Keep in mind some 80% of web page views are on an intranet.

Except firefox works for us. We can see your pages fine. How do you expect program developers to fix a problem they can't even recreate or see evidence of?

---

### Post by Vegan on 2008-09-03
My web host is Ubuntu server, and my development machine is Windows XP x64. Everything is plugged into a Linksys WRT54G box to the net.

Behind the box, its called an intranet, outside the box its the internet.

So my views here are intranet.

I manage the Linux server with Telnet and FTP using IP addresses. Once I have the DNS setup properly I may be able to use the URLs better on the intranet.

---

### Post by cdenley on 2008-09-03
I don't have that router, so I can't really test it without access to your LAN, but I highly doubt what you are experiencing is a bug with firefox. If you get different results from your LAN than we get from the internet, it is a networking problem. Firefox would behave identically on the LAN as it would over the net, assuming your network is working properly.

---

### Post by windependence on 2008-09-03
> **Vegan said:**
> My web host is Ubuntu server, and my development machine is Windows XP x64. Everything is plugged into a Linksys WRT54G box to the net.

Behind the box, its called an intranet, outside the box its the internet.

So my views here are intranet.

I manage the Linux server with Telnet and FTP using IP addresses. Once I have the DNS setup properly I may be able to use the URLs better on the intranet.
You really need to just bite the bullet and put your server alias in your hosts file on the Windoze 64 machine. Everything should work well then.

-Tim

---

