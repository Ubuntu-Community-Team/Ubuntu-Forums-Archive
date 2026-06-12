---
title: "http not working"
date: 2006-11-16
forum: Server Platforms
---

### Post by bobjr777 on 2006-11-16
i have a apache server i just installed. i can view it on my lan but not on the internet. i have all the ports forwarded i know that because ssh works at my school.

---

### Post by Joe_CoT on 2006-11-16
Try setting the listen port in your httpd.conf to something that's not port 80, ie 8081 or something like that.

If you're on, uh, any home broadband isp ever, they blocked port 80 on you :mad: I've been there.

---

### Post by wieman01 on 2006-11-16
Some internet service providers block port 80 by default so as to prevent that people set up their own webservers. Try to use port 8080 instead & see if you can connect from school.

---

### Post by bobjr777 on 2006-11-17
it works now when i put :8080 on the end of the url. how can i make it so i don't need the :8080

---

### Post by anarky on 2006-11-17
"Listen 80"
use that... should fix the problem ;)

---

### Post by tturrisi on 2006-11-18
> **anarky said:**
> "Listen 80"
use that... should fix the problem ;)
That won't work IF the isp filters port80.
If use Listen 8080 then must port-forward 8080.
No way to eliminate the use of :8080 in the url.
If use Listen: 80 then must have unfiltered wan connection.

---

### Post by MJN on 2006-11-19
A workaround would be to use a DNS provider that will provide port redirects. That is, clients connect to [http://example.com](http://example.com) (on default port 80) which resolves to your DNS provider's web server, which then throws back a 301 Permanent Redirect to the client of [http://example.com:8080/](http://example.com:8080/) to connect to yours.

Of course, the clients browser will now read example.com:8080 but they didn't have to type/know it. You could even hide the 'true' address using a frameset but I wouldn't go down that road.

I don't know a suitable DNS provider off-hand (mine doesn't provide it), but I do know there are many available so hopefully someone else can recommend one.

Mathew

---

### Post by tturrisi on 2006-11-19
re redirect:
many domain registrars now offer Domain Parking/Domain Forwarding.  What that means is you can register a domain name at for example DomainDirect.com and get free domain parking.  In your admin panel at Domain Direct, at the Domain Forwarding section, you can enter a public ip for your domain name (your isp assigned public ip) and the port number :8080.  The DNS servers used are the registrar's dns servers.

example:
You register the name MySite.com and get free domain parking.  You config your server to listen on port 8080 or some other port and config your router to forward port 8080 requests to the private ip of the server.  Someone types in [www.mysite.com](www.mysite.com) and the request is routed to your server and their address bar looks like [xx.xx.xx.xx:8080/](xx.xx.xx.xx:8080/) but they don't have to type the :8080.

However, if your isp public ip address changes then you have to go back to your registrar and manually update your public ip address.

Here's one of mine:
[www.statrecorder.org](www.statrecorder.org)

---

### Post by MJN on 2006-11-19
Many DNS providers support dynamic updates so that won't be a problem.

Mathew

---

