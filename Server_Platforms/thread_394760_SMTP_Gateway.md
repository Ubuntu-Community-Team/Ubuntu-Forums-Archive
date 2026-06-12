---
title: "SMTP Gateway"
date: 2007-03-27
forum: Server Platforms
---

### Post by cragmonkey on 2007-03-27
OK, so I have played with Ubuntu quite a bit at home but have never had to use it in my workplace but the other day Ubuntu finally got a chance to shine and I was hoping someone could help me out a little.

So here's the deal: 
We have an M$ exchange server at work. We also have 2 windows boxes that are running as a paired SMTP gateway. The other day one of the SMTP servers died and our IT dept decided to revamp the whole SMTP thing. That's where Ubuntu comes in.... We have installed 6.10 server on the machines. All the hardware is up and running(yay). 
I need some help with figuring out how to setup the 2 new Ubuntu servers to be the replacement SMTP gateway for exchange. Can someone please direct me to a how-to or some packages to look at to get this project rolling?

Thanks in advance for any helpful posts....

---

### Post by Mr. C. on 2007-03-27
Good choice.

You haven't indicated if you have a preference for mailers, but I will recommend postfix.

Lots of help available by some of the industry's best:

[http://www.postfix.org](http://www.postfix.org)

MrC

---

### Post by tonym on 2007-03-28
Alternatively EXIM.  Lots of documentation on [http://www.exim.org]("http://www.exim.org")

---

### Post by rickyjones on 2007-03-28
> **cragmonkey said:**
> OK, so I have played with Ubuntu quite a bit at home but have never had to use it in my workplace but the other day Ubuntu finally got a chance to shine and I was hoping someone could help me out a little.

So here's the deal: 
We have an M$ exchange server at work. We also have 2 windows boxes that are running as a paired SMTP gateway. The other day one of the SMTP servers died and our IT dept decided to revamp the whole SMTP thing. That's where Ubuntu comes in.... We have installed 6.10 server on the machines. All the hardware is up and running(yay). 
I need some help with figuring out how to setup the 2 new Ubuntu servers to be the replacement SMTP gateway for exchange. Can someone please direct me to a how-to or some packages to look at to get this project rolling?

Thanks in advance for any helpful posts....

You should be able to install the MTA (Postfix is preferred I do believe), then configure it to allow SMTP Relaying from within your LAN. After that you should be able to point the exchange server to those boxes. Now, if the role of these gateways are to also intercept incoming email and forward it to exchange... I'm not sure on the configuration for that, but I'm sure it can't be too awfully difficult.

Cheers!

-Richard

---

### Post by ndefontenay on 2007-03-28
EXIM was brilliant.

I've tried that at my previous office. It got configured in just a couple of questions asked by EXIM. It never failed until we closed the company and shutdown the boxes.

---

### Post by astrogazer on 2007-03-29
Postfix on Ubuntu has worked great for us.

Here is a very HowTo to get you started:

[http://www.howtoforge.com/ubuntu6.06_firewall_gateway](http://www.howtoforge.com/ubuntu6.06_firewall_gateway)

---

### Post by cragmonkey on 2007-03-29
Thank you to everyone that offered their help. For those of you that said Postfix worked really well,....you were absolutely right. It took my team about 20-30 minutes to get smtp up and running. It was all just so easy.

Those of you that suggested Exim, I didn't get a chance to check it out but it sounds intriguing

Thanks again for all your help. This community ROCKS!!

---

