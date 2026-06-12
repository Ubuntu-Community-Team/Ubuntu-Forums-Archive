---
title: "Web server can only be accessed internally"
date: 2008-07-04
forum: Server Platforms
---

### Post by PureSamuel on 2008-07-04
Hi.
I'm trying to set up a web server and have successfully installed apache, php .. etc.
The problem is that I cannot access it externally, only internally using "http://192.168.2.4", "localhost" or "//office" in the address bar.
I've looked up port forwarding and configured my router to forward any requests on port 80 to port 80 on the server, however when I try to access the server using my external IP, the only thing that comes up is my routers configuration page.
Any ideas?
Sam.

---

### Post by sjwk on 2008-07-04
If you're getting the router's config page, it sounds like the router is already running a service on port 80, and has no way to distinguish requests that you intend to go to your server from requests that it thinks are meant for it...  If you can somehow find a way of configuring the router to do its management stuff on another port, then you should be able to forward incoming port 80 requests to your server.

Steve

---

### Post by cariboo on 2008-07-04
It would be way easier to setup apache to listen on a different port. You can change what port it listens to in /etc/apache2/ports.conf. If you look in the file it already listens on port 443 for https.

Jim

---

### Post by windependence on 2008-07-04
> **cariboo907 said:**
> It would be way easier to setup apache to listen on a different port. You can change what port it listens to in /etc/apache2/ports.conf. If you look in the file it already listens on port 443 for https.

Jim

I wouldn't do this, or people will have to use the port number to access it or he'll have to set up a redirect - both not great solutions. It would be much easier just to turn off remote administration on his router. It's a security hole anyway, and a BIG one if he is accessing it without SSL. 

To the OP, there is a setting in your router to turn off remote administration. Turn that off and you will be fine. You probably don't need to access your router config from the outside and if you do, you can do it other, more secure ways like tunneling ssh.

-Tim

---

### Post by PureSamuel on 2008-07-05
I already had remote administration turned off, although I could still access it "remotely" from any of my computers because it knew we were able to access it locally. (I used a proxy to make sure no-one else could access it).
Thanks
Sam

---

