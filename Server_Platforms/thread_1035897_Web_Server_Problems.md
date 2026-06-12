---
title: "Web Server Problems"
date: 2009-01-10
forum: Server Platforms
---

### Post by Jeff B.J. on 2009-01-10
I have problems making my web server accessible to the internet. I first started a LAN without any connection to the net. I'm using ubuntu server 8.10.

Here's the processes that led to my problem:

(1) I've already installed apache2, bind9 (DNS), and dhcp3-server.

(2) I've already configured apache2, bind9, and dhcp3-server.

(3) I've already created a web page and copied it into "/var/www/".

(4) The web page can already be viewed on another computer (within my LAN) using the domain name that I've given.

(5) Now I've disabled my DHCP to connect to my router.

(6) I've configured my router to port forward to my web server's LAN IP.

Now here's the problem:

(1) I can't view the website from a different computer (a computer that's not within the LAN of my web server).

I'll really appreciate it if you'll help me with this problem.

---

### Post by hrod beraht on 2009-01-10
> **Jeff B.J. said:**
> (6) I've configured my router to port forward to my web server's LAN IP.

Now here's the problem:

(1) I can't view the website from a different computer (a computer that's not within the LAN of my web server).

Is your server LAN IP static (e.g. 192.168.1.100), and are you sure it hasn't changed? If so, and you've forwarded port 80 to your server through your router, then it should just direct all http traffic there assuming you are actually getting to the router. How are you trying to access it? With a domain name, as in [http://jeff.org?](http://jeff.org?) If so, perhaps the domain name isn't directing correctly. In that case, what happens if you try to access it by using the actual internet IP address of your router, as in [http://123.456.789.0?](http://123.456.789.0?) (or whatever your IP address is)

Bob

---

### Post by Jeff B.J. on 2009-01-10
> Is your server LAN IP static (e.g. 192.168.1.100), and are you sure it hasn't changed?

Yes, it's static. And I'm very sure that it hasn't changed at all. I'm using 192.168.11.200 though...

> How are you trying to access it? With a domain name, as in [http://jeff.org?](http://jeff.org?)

Yea. [www.deheritageweb.com](www.deheritageweb.com) to be exact. Try it if it works but the server will be running from 10am to 10pm, GMT+8 (It'll be on until 4am for today though).

> In that case, what happens if you try to access it by using the actual internet IP address of your router, as in [http://123.456.789.0?](http://123.456.789.0?)

Did you mean the external IP address? Yea. I tried that. But it brought me to my router's configuration page... Any leads on that?

---

### Post by leg on 2009-01-10
If you have your connection to the Internet through an isp your ip address will change every 90 minutes of so. If this is the case then you can get around it but you need some external service to map back to your router and I can't remember what that is.

---

### Post by volkswagner on 2009-01-10
> **Jeff B.J. said:**
> 
Did you mean the external IP address? Yea. I tried that. But it brought me to my router's configuration page... Any leads on that?

Check your router to disable remote admin or login.

---

### Post by Jeff B.J. on 2009-01-11
> If you have your connection to the Internet through an isp your ip address will change every 90 minutes of so.

Nah. Our ISP gives us a static external IP to use.

> Check your router to disable remote admin or login.

Well... I've tried it again. When, I use the external IP within my intranet it takes me to my router's configuration page. But when I tried it on a computer outside my intranet, it takes me to my web servers web page (a test web page though...). I never get to try the disabling remote admin and login (couldn't find it in the router's setting page).

I suspect that the DNS is not working at some point... perhaps the port forwarding settings on my DNS server? (which is my web server too) Or maybe something else?

---

### Post by Jeff B.J. on 2009-01-11
Please... Any leads? Links to guides of "Making my web server accessible to the internet" or that sort of thing might be useful.

I suspect either my ISP, DNS, or Firewall.

---

### Post by volkswagner on 2009-01-12
> **Jeff B.J. said:**
> Please... Any leads? Links to guides of "Making my web server accessible to the internet" or that sort of thing might be useful.

I suspect either my ISP, DNS, or Firewall.

I am not sure what the problem is.  You stated others outside your lan can access the "test Page".  Sounds like apache2 is working and port 80 is going to your server.  Are the only issues getting to the site from inside the lan while using the external ip?  That could be due to NAT enabled on the router.

---

### Post by Jeff B.J. on 2009-01-12
The problem is still unresolved (although it wasn't the original problem...)

The problem now is that anyone outside my intranet cannot access my website using the domain name ([www.deheritageweb.com](www.deheritageweb.com)). You can, however, access my website my typing in my external IP address.

I'd post my external IP but I'm not sure whether doing that would jeopardize my security or not...

---

### Post by volkswagner on 2009-01-12
> **Jeff B.J. said:**
> The problem is still unresolved (although it wasn't the original problem...)

The problem now is that anyone outside my intranet cannot access my website using the domain name ([www.deheritageweb.com](www.deheritageweb.com)). You can, however, access my website my typing in my external IP address.

I'd post my external IP but I'm not sure whether doing that would jeopardize my security or not...
  I assume "www.deheritageweb.com" is a typo, according to whois, it is not a registered domain name.

That domain is listed as still available to register.

---

