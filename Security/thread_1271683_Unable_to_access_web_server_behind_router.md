---
title: "Unable to access web server behind router"
date: 2009-09-21
forum: Security
---

### Post by dabhijit on 2009-09-21
Hello everybody,

I am setting up my web server behind my Netgear ADSL modem+router. I am using dyndns.org service to run my web server with dynamic IP.

However the apache server is not responding to access from outside - <mysite>.dyndns.org  I am trying to debug what went wrong.

1. My apache2 server is up and running and listening to port 80. I can access the localhost from within the LAN network. firewall in the web server is disabled

2. I have configured the ADSL modem+router to allow access on port 80 and forwarded port 80 to the web server (LAN static IP). Setup the DDNS setting for dyndns.org setup in the router.

Symptom:- when I access <mysite>.dyndns.org I see that it is accessing my ADSL router and popping up the Admin access page instead of forwarding the traffic to my web server.

I checked with nmap to see that the port 80 is open in the router and the web server.

I am confused and need some expert opinion as what I can try out to pinpoint the cause of the problem.

My LAN configuration:

ADSL+Router <=> switch (Wireless router with DHCP disabled) <=> Web server.

Thanks

---

### Post by Rob_H on 2009-09-21
> **dabhijit said:**
> Symptom:- when I access <mysite>.dyndns.org I see that it is accessing my ADSL router and popping up the Admin access page instead of forwarding the traffic to my web server.

The *router's* admin page? That's not good. First things first, you should go into your router configuration and disable WAN access to the admin UI. That might solve your problem in addition to improving your security.

If you're still having problems after that, check again to see if port 80 is accessible from the outside world. If not, try hitting it by IP address instead of name to rule out any DNS problem.

---

### Post by sanderj on 2009-09-21
I agree with Rob_H that your router admin page should not be accessible to the outside world; with access to that admin page, anyone can try to gain access to all settings.

So close that interface.

Now back to your original question: If it's not possible to close the outside web access AND forward to your internal webserver, you can forward another port (like 8888 ) to your internal webserver on port 80.
After that you access your webserver via [http://blabla.dyndns.org:8888/](http://blabla.dyndns.org:8888/)

Oh, the real solution solution is of course to use IPv6. ;-) 
Begin by installing "miredo" on your Ubuntu machine and you'll have IPv6 connectivity with the outside world.

HTH

---

### Post by cdenley on 2009-09-21
Accessing your WAN IP from inside your LAN is not the same as accessing your WAN IP from over the internet.

---

### Post by rickyjones on 2009-09-21
I agree with the other posters - find the configuration option that allows you to access the Admin interface from the WAN and disable that. This should allow the port forwarding to work.

It sounds like the router is listening on port 80 instead of forwarding that traffic.

Thanks,
Richard

---

