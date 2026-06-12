---
title: "Squeezebox server and urw firewall"
date: 2011-01-09
forum: Security
---

### Post by SteveTyrer on 2011-01-09
I am running Ubuntu 10.10 (server) and have just set up the urw firewall with the help of the brilliant blog by bodhi.zazen.
all works fine expect i cannot work out how to let my Squeezebox serve communicate with the network, i have tried the following

sudo urw allow mysql
sudo urw allow port 9000

and allow Squeezebox serve which is not recognised

can some one point me in the right direction    

all the best Steve

---

### Post by bodhi.zazen on 2011-01-09
If you are talking about connecting to mysql, you nee to configure mysql to accept connections from other machines and configure a mysql user.

Otherwise I can not tell the problem from your post.

---

### Post by SteveTyrer on 2011-01-09
> **bodhi.zazen said:**
> If you are talking about connecting to mysql, you nee to configure mysql to accept connections from other machines and configure a mysql user.

Otherwise I can not tell the problem from your post.

Okay sorry did not get it over well,

My server at this time is serving films and music around my home, all is working 100% so my next step(in my steep learning curve) is to set up Apache2 and my own web site, to this end i have enabled the firewall. got all working through the firewall except my Logitech radio; this uses Squeezbox server to play music from the Ubuntu server it works with the firewall off but not with the firewall enabled, the question is how can i get it to work with the firewall on?

Thanks for you help
Steve

---

### Post by bodhi.zazen on 2011-01-09
> **SteveTyrer said:**
> Okay sorry did not get it over well,

My server at this time is serving films and music around my home, all is working 100% so my next step(in my steep learning curve) is to set up Apache2 and my own web site, to this end i have enabled the firewall. got all working through the firewall except my Logitech radio; this uses Squeezbox server to play music from the Ubuntu server it works with the firewall off but not with the firewall enabled, the question is how can i get it to work with the firewall on?

Thanks for you help
Steve

Well, you hae to allow the correct ports. Do you know what ports to allow ? Apache uses port 80. Not sure about the other ports you use.

I assume from my blog you understand the basic syntax ?

---

### Post by sj1410 on 2011-01-10
Squeezebox Radio works on  TCP Port 3483 and 9000 and UDP Port 3483.

You need to allow this in your firewall rules.

all the best Steve

---

### Post by SteveTyrer on 2011-01-10
> **sj1410 said:**
> Squeezebox Radio works on  TCP Port 3483 and 9000 and UDP Port 3483.

You need to allow this in your firewall rules.

all the best Steve

Thanks to both of you; that works perfectly. :KS

Steve

---

