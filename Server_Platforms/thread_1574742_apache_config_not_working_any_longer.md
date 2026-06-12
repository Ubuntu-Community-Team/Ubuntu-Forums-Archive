---
title: "apache config not working any longer"
date: 2010-09-14
forum: Server Platforms
---

### Post by jonny.milano on 2010-09-14
Hi, and thank you for the help in advance. 

Here's my sitch: I have a home server that I've been using to teach myself many linux related things: [http://herb.homelinux.com/](http://herb.homelinux.com/) 

Now, if you click that URL you'll notice that it no longer loads. At first I thought that maybe my ISP had changed our home IP again or that my DNS was not configured but I am baffeled. (sp?) 

I did not make any changes to Apache2 directly nor did I install any new software. I am able to ping and SSH into the server. Also, I'm able to get here: [http://herbpublic.homelinux.com:8080/alfresco/faces/jsp/login.jsp](http://herbpublic.homelinux.com:8080/alfresco/faces/jsp/login.jsp) which also sits on this server but not to [http://herbpublic.homelinux.com/](http://herbpublic.homelinux.com/)

Does anyone have any ideas? Could this be Apache? I have restarted Apache twice now.

---

### Post by jonny.milano on 2010-09-14
furthermore: FTP works but webDAV does not!! (????)

---

### Post by Richard1979 on 2010-09-14
Quick tip:

If you want to see if your server is available to the outside world, put the URL into here:
[http://validator.w3.org/](http://validator.w3.org/)

---

### Post by jonny.milano on 2010-09-14
> **Richard1979 said:**
> Quick tip:

If you want to see if your server is available to the outside world, put the URL into here:
[http://validator.w3.org/](http://validator.w3.org/)

OK! Here is a crrrrazzzzy thing! 
I did just that and because I have apache protecting the directory I needed to access I entered my user and password and validator checked out my server. However, when I put the address straight into a browser, no dice! WTF....?

---

### Post by arrrghhh on 2010-09-14
Are you connecting to it from within your LAN?  If that's the case you may not be able to hit the site from the DNS-friendly address, and you'll have to use the local IP of the box.

FYI, I hit your box and get a login page so it appears to be working no problem...

---

### Post by jonny.milano on 2010-09-14
> **arrrghhh said:**
> Are you connecting to it from within your LAN?  If that's the case you may not be able to hit the site from the DNS-friendly address, and you'll have to use the local IP of the box.

FYI, I hit your box and get a login page so it appears to be working no problem...

No, I'm connecting from an external network over the internet.. But here's another crazy thing: Now that I am on Firefox I am able to connect no prob. Perhaps the issue was IE before???? Who knows.. Can someone else try? [http://herbpublic.homelinux.com/](http://herbpublic.homelinux.com/) [http://herb.homelinux.com/](http://herb.homelinux.com/)

---

### Post by arrrghhh on 2010-09-15
> **jonny.milano said:**
> No, I'm connecting from an external network over the internet.. But here's another crazy thing: Now that I am on Firefox I am able to connect no prob. Perhaps the issue was IE before???? Who knows.. Can someone else try? [http://herbpublic.homelinux.com/](http://herbpublic.homelinux.com/) [http://herb.homelinux.com/](http://herb.homelinux.com/)

Not sure what to tell you, both sites work just fine in FF & IE7.

---

### Post by jonny.milano on 2010-09-15
> **arrrghhh said:**
> Not sure what to tell you, both sites work just fine in FF & IE7.

Thank you for checking, arrrghhh. I think that all along it was frick'n IE!! I can connect now about 30% of the time using this box. Wow, what a frickn nightmare of Apache config checks...

---

