---
title: "Custom firewall hardware"
date: 2010-01-02
forum: Security
---

### Post by R.Bucky on 2010-01-02
I have not been pleased with the Comcast business router/modem that is provided with my account. I am seriously considering opening up the Comcast hardware and pushing traffic to a Soekris box with pfSense. I use this combo on another network that I maintain, but wonder what other hardware/software combinations people are using as a firewall. 

What custom hardware firewall or configurations do you use?

---

### Post by Bobulous on 2010-01-02
I used to use an EPIA board in a fanless case, and ran FreeBSD to act as a firewall (IPFW and later PF) and network server:

[http://www.bobulous.org.uk/imho/e-OtonashiEPIA.html](http://www.bobulous.org.uk/imho/e-OtonashiEPIA.html)

It lasted a year before the 2.5-inch HDD in it ground to a halt, and less than a year after that the power or motherboard must have failed because the whole thing died.

I did see the Soekris boards, and I liked the idea, but it all seemed a little too obscure. Now I'm thinking it would have been a better bet. What would you use for storage on such a box?

---

### Post by R.Bucky on 2010-01-02
The Soekris board is not used for storage. The Soekris on my network at work operates at 53 degrees C and has operated flawlessly for over three years. It protects a number of Linux servers and a MS server with ease. I really like the pfSense web interface too. I looked at the Soekris board last month and it was around $200.

---

