---
title: "web server at home"
date: 2010-11-23
forum: Server Platforms
---

### Post by Jolicoeur on 2010-11-23
HI,

I have been reading about web servers, building your own with perhaps LAMP. It appears the purpose of one is to test websites?  Is it not possible to use your server on the web and actually host a website or blog or whatever?



Can anybody recommend a good document or book or website for trying this out?

Thanks

---

### Post by lukeiamyourfather on 2010-11-23
Check with your ISP first. Most strictly prohibit hosting a website on a consumer/residential connection. If they do allow it then check out the web server section of the server guide.

[https://help.ubuntu.com/10.04/serverguide/C/web-servers.html](https://help.ubuntu.com/10.04/serverguide/C/web-servers.html)

If you have a router then you'll need to forward port 80 requests to the server, or make it the DMZ. Note there are limitations even if the ISP allows hosting a server. For example it will probably have a dynamic IP so you won't be able to have a domain name.

---

### Post by Jolicoeur on 2010-11-23
> **lukeiamyourfather said:**
> Check with your ISP first. Most strictly prohibit hosting a website on a consumer/residential connection. If they do allow it then check out the web server section of the server guide.

[https://help.ubuntu.com/10.04/serverguide/C/web-servers.html](https://help.ubuntu.com/10.04/serverguide/C/web-servers.html)

If you have a router then you'll need to forward port 80 requests to the server, or make it the DMZ. Note there are limitations even if the ISP allows hosting a server. For example it will probably have a dynamic IP so you won't be able to have a domain name.

Did not know that, thanks.  How does one get access to the web to run their own server?

---

### Post by CharlesA on 2010-11-23
> **Jolicoeur said:**
> Did not know that, thanks.  How does one get access to the web to run their own server?

You'd forward port 80 on the router to the internet. That being said, most of the ISPs I've used have blocked port 80 on residential connections.

If you are serious about running a website and don't have a very good upload speed at home (or port 80 is blocked), you could check out getting a VPS. That's what I'd do if I was going to run a website.

---

### Post by Wtower on 2010-11-23
> **Jolicoeur said:**
> Did not know that, thanks.  How does one get access to the web to run their own server?

Well I suppose you do have access to the internet right now. What kind of connection does your ISP provide you? Most residentials offer a dynamic IP connection, which means that your [IP address]("http://en.wikipedia.org/wiki/IP_address"), the address with which your computer is known to the Internet, changes every time your connection drops. You can use a site like [http://www.whatismyip.org/]("http://www.whatismyip.org/") to check it out. If you have a web server like apache running, the rest of the world can use that ip address to see what you serve.

Regards

---

### Post by lukeiamyourfather on 2010-11-23
> **Jolicoeur said:**
> How does one get access to the web to run their own server?

I assume you mean have someone else host your website? There are many commercial services that provide anywhere from hosting a pre-configured blog to your own dedicated server online. Go Daddy is a popular hosting service.

[http://www.godaddy.com/](http://www.godaddy.com/)

For a monthly/yearly fee they will handle all of the hardware, storage, networking, etc. You just upload and install what you want on the server. If you want to do everything yourself, you'll need a business ISP with a static IP address for starters. Then register that IP address with ICANN so you can have a domain (whatever dot com).

---

### Post by Silverfox on 2010-11-23
> **lukeiamyourfather said:**
> Note there are limitations even if the ISP allows hosting a server. For example it will probably have a dynamic IP so you won't be able to have a domain name.


Just an FYI, there are Domain services out that that offer DynamicDNS (many home routers are preconfigured with Dynamic DNS tools). A small program or your router updates your IP with your domain host if/when it changes. I use DynDNS, but there are many companies out that that offer Dynamic DNS services.

---

