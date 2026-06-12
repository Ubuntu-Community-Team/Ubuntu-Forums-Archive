---
title: "evil ISP, how to redirect address AND ports ?"
date: 2011-08-29
forum: The Cafe
---

### Post by noob+1 on 2011-08-29
Hi guys,  
This post may have its place in another category, but I don't know which one (it's not system related).

So in short, my ISP (orange, in france) is filtering everything going to port 25, except when it's going to their server of course. So I can't send mail with another service.

I did some research, without results, to find a redirection service (free if possible), the kind of dyndns et co, but which would allow me to redirect ports as well as urls. 
In short, I want a service that does this : 
 mycustomeurl.theservice.com:6666  --->  smtp.mymailservice.com:25   

Got ideas ?
thanks 

noob+1  

[What is this crappy pagination ? it's impossible to insert blank lines !]
[edit : ah, javascipt my love :-@ ]

---

### Post by Artemis3 on 2011-08-29
I don't think this is particularly evil, it is done to reduce spam from malware (windows) ridden machines... 

Try asking them if this can be disabled, otherwise use a proxy. Some authenticated and encrypted smtp servers use a different port (eg. gmail).

---

### Post by zitch on 2011-08-29
Artemis3 is right, in fact, I'd consider this almost due diligence by the ISP to reduce the amount of spam sent out by zombied customer's machines. Really, there's a port for email submission (587) that should be used for outgoing email, as port 25 is supposed to be for server-to-server communication (some [info](http://mostlygeek.com/tech/smtp-on-port-587/comment-page-1/)). I think connections to port 587 is required to be authenticated, and optionally encrypted.

For example, with gmail, I have my mail client's SMTP settings set to smtp.gmail.com:587, with authentication and TLS encryption, and my gmail address for the username. My personal email server is similarly setup. 

Basically, check with the "other" service to see if you can connect to port 587, with authentication and preferably encryption. No need for a proxy then, and if you have encryption on, your ISP won't even see what you're sending.

---

### Post by CharlesA on 2011-08-29
> **Artemis3 said:**
> I don't think this is particularly evil, it is done to reduce spam from malware (windows) ridden machines... 

Try asking them if this can be disabled, otherwise use a proxy. Some authenticated and encrypted smtp servers use a different port (eg. gmail).

This.

> **zitch said:**
> Artemis3 is right, in fact, I'd consider this almost due diligence by the ISP to reduce the amount of spam sent out by zombied customer's machines. Really, there's a port for email submission (587) that should be used for outgoing email, as port 25 is supposed to be for server-to-server communication (some [info](http://mostlygeek.com/tech/smtp-on-port-587/comment-page-1/)). I think connections to port 587 is required to be authenticated, and optionally encrypted.

For example, with gmail, I have my mail client's SMTP settings set to smtp.gmail.com:587, with authentication and TLS encryption, and my gmail address for the username. My personal email server is similarly setup. 

Basically, check with the "other" service to see if you can connect to port 587, with authentication and preferably encryption. No need for a proxy then, and if you have encryption on, your ISP won't even see what you're sending.

And that. I use a gmail relay to send email from my home server.

---

### Post by noob+1 on 2011-08-31
Thanks for your answers.

Using a service with SSL on another port is of course an obvious solution. But if I were able to do that, i wouldn't have asked the question...
(my mail service IS using ssl, but still listening on port 25, bad luck !)

But in fact, if I were able to use port 25, I would have installe my own mail server a long time ago. 
The simple fact that it's impossible is, de facto, an UNACCEPTABLE limitation of my internet accecs. Of course it's to prevent spam, and it may be efficient, but it CAN'T BE DISABLED, unless you have a professional acces...

Moreover, if we forget the problem of the network neutrality, i'm somewhat puzzled to have people advise me to use google mail, reputed for its invasion against privacy, on a  LINUX forum ! I would gladly use my ISP's mail service rather than google's !

---

### Post by cariboo on 2011-08-31
I'd check to see what the cost of a commercial account is, as then you'd probably be able to setup your own email server. Either that or use another ISP, my relatives in the Netherlands seem to change ISP's about as often as I install a new testing version. :)

---

