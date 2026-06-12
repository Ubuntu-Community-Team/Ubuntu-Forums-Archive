---
title: "Multiple (active) Connections to the Internet"
date: 2009-01-19
forum: Server Platforms
---

### Post by afotey on 2009-01-19
Hi friends, 

      I have an Ubuntu Box running Intrepid Ibex, I would like to set it up as a router. I want to know how to setup two dedicated Internet connections in such a way that both connections will be active and working simultaneously.

    Normally Ubuntu tends to make the most recently added connection the default connection/route. But i want to have both connections working simultaneously. Please can anyone help me. It's driving me crazy!

:confused:

thanks

---

### Post by stefangr1 on 2009-01-19
Can you give some more details about what you tried?

Am I right if I understand that you have two connections between the server and the internet, and need some kind of load balancer to make sure that both connections are used?

---

### Post by afotey on 2009-01-19
Yes i have two internet connections. each are from different ISP's, what i would like to do is to to ensure that both of them are active and working. Yeah it's almost like a load balancer.

---

### Post by rickyjones on 2009-01-19
I'm afraid I'm unsure of how to do it in Ubuntu but I'm sure it'll use some sort of IP Tables configuration.

However I do know that there are small business routers on the market for about $80USD that will do this for you automatically and out of the box. Just another avenue to consider.

Please note I'm not trying to discourage you, just offering up some alternatives. :-)

Thanks,
Richard

---

### Post by afotey on 2009-01-19
yeah that's true but i wanted to try out on my own and see if i could do it :-) thanks for the suggestion :-)

---

### Post by HermanAB on 2009-01-19
You need to read the Advanced Routing Howto on tldp.org.

Maybe see this:
[http://aeronetworks.ca/doublebarrel.html](http://aeronetworks.ca/doublebarrel.html)

Cheers,

Herman

---

### Post by afotey on 2009-01-19
ok thanks i'l check it out and then tell u how it goes :-)

---

