---
title: "Server help."
date: 2009-03-03
forum: Server Platforms
---

### Post by Hartless on 2009-03-03
I have a apache server set up and working and the domain that i bought (thetuxhouse.com) is working and going to the apache It Works! page. the problem is that it works locally only. My ISP does not allow for static IP's (or servers, for that matter) and im using a dns provider (freedns.afraid.org) to work around that. I am also aware that my port 80 is blocked and think that that is the problem. Does anybody know of any workarounds for this? 

Thanks a lot,
Hartless

---

### Post by koenn on 2009-03-03
DNS only returns your domain name and a mail server, you might want to create an entry for your webserver's hostname (eg www) - makes things easier to follow.

assuming your webserver is at 
```
thetuxhouse.com.	3600	IN	A	96.235.179.164
``` your port 80 shows up 'filtered' which might mean you're behind a NAT router. You need to set up portforwarding so that traffic to your router's port 80tcp is forwarded to your web server's port 80tcp

If your ISP (Verizon, isn't it ?) is blocking traffic to your router's port 80, you can forward an arbitrary high port ( say 88888 ) from the router to 80tcp on the web server. That would mean you need port numbers in your URLs a well, like so: [http://thetuxhouse.com:88888](http://thetuxhouse.com:88888), or [http://www.thetuxhouse.com:88888](http://www.thetuxhouse.com:88888)

---

### Post by Hartless on 2009-03-03
would the user have to type in the :8080 or would it go automatically?
And how would i go about doing that in the verizon cp?

---

### Post by koenn on 2009-03-03
the user would have to type it, unless it's already typed by someone else in the form of a clickable link.

---

### Post by Hartless on 2009-03-03
Alright, I set up port forwarding to work with 80, 8080, 8000, 8888, and 81. It worked and after working on this for like, 4 days im pretty happy about it. But is there any way to get this to work without the :8080?

---

### Post by koenn on 2009-03-04
not to work around a blocked port. 
Your ISP blocks traffic coming towards port 80tcp of your router. So you want the traffic to arrive at a different port which isn't blocked.
That means the people coming to your website need to instruct their browser to go to your port 8888 in stead of the default port 80. So its something that needs to be handled at the 'client' side, which you do not control.

Occasionally, when stuff like this comes up, people imagine DNS could (should?) handle this, eg by translating thetuxhouse.com to 96.235.179.164:8888, but so far DNS doesn't do that, and it isn't designed to do that, and it would be messy if it did do that because this arrangement would only make sense for http, not for any other networking going on on the internet.

bottomline: if you want to run a public web server, get an iSP / internet access account that lets you use port 80.

---

### Post by Hartless on 2009-03-05
I was thinking and can't i just get apache to host [www.thetuxhouse.com](www.thetuxhouse.com) and then tell my dns to forward thetuxhouse.com to [www.thetuxhouse.com:8080?](www.thetuxhouse.com:8080?) How would i go about doing this?

---

### Post by koenn on 2009-03-05
> **Hartless said:**
> I was thinking and can't i just get apache to host [www.thetuxhouse.com](www.thetuxhouse.com) and then tell my dns to forward thetuxhouse.com to [www.thetuxhouse.com:8080?](www.thetuxhouse.com:8080?) How would i go about doing this?
Do you actually read the replies sometimes ?
> **koenn said:**
> 
Occasionally, when stuff like this comes up, people imagine DNS could (should?) handle this, eg by translating thetuxhouse.com to 96.235.179.164:8888, but so far DNS doesn't do that, and it isn't designed to do that, and it would be messy if it did do that because this arrangement would only make sense for http, not for any other networking going on on the internet.

bottomline: if you want to run a public web server, get an ISP / internet access account that lets you use port 80.

You can do such thing maybe with a redirection in your web server, or a proxy, or with iptables and such, but this is not going to work for you because the traffic needs to be redirected to the 8080 port (or any arbitrary port) **before** it enters your network.

---

### Post by E_K on 2009-03-05
Or just use the free port 80 redirect service from no-ip.org problem solved.

---

### Post by Hartless on 2009-03-05
alright, I just thought that i'd get apache to host [www.thetuxhouse.com](www.thetuxhouse.com) and tell my dns provider to redirect thetuxhouse.com (no [www.)](www.)) to [www.thetuxhouse.com:8080](www.thetuxhouse.com:8080) And as far as i'd checked to even get a domain name onto no-ip costs atleast $15/year.

---

### Post by koenn on 2009-03-05
> **E_K said:**
> Or just use the free port 80 redirect service from no-ip.org problem solved.
interesting, didn't know such service existed.

---

### Post by Hartless on 2009-03-05
alright nope, i got it. I used my dns to redirect thetuxhouse.com to [www.thetuxhouse.com:8080](www.thetuxhouse.com:8080) and now it works from everywhere.
wait.... just went down again....

---

