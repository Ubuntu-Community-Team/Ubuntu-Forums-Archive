---
title: "Multiple IP on single Nick"
date: 2009-05-03
forum: Server Platforms
---

### Post by w8tah on 2009-05-03
Hi folks -- looking at my firewall / router unit -- is it possible to have more than one public ip on the outside nick of the firewall and do the routing internally?

Tim

---

### Post by koenn on 2009-05-03
yes; you'd make 'aliases' such as eth0:0 and eth0:1
I think you'd do that simply be defining them in /etc/network/interfaces, or by running ifconfig as shown here (skip the part about kernel modules and assume this feature is present in your kernel)
[http://www.faqs.org/docs/Linux-mini/IP-Alias.html](http://www.faqs.org/docs/Linux-mini/IP-Alias.html)

What are you trying to do ?

---

### Post by w8tah on 2009-05-03
Im kinda re-organizing our school firewall - and trying to streamline operations some -- ive had a machine thats been sitting outside the firewall totally that id like to bring back inside -- and another one id like to establish that is public facing but would be inside our network -- they each need separate public IP's.  I used to be able to do it with our cisco pix, but wasnt sure about a ubuntu firewall machine.

TIM

---

### Post by koenn on 2009-05-03
sounds fun.

linux is quite capable when it comes to networking, and iptables is a great help, not only for firewalls but also fur stuff where straightforward routing doesn't cut it. There's a good chance you can pull this off.

have fun.

---

### Post by tux-helper on 2009-05-03
Hi

Not sure if you've had any luck with what you're trying to do but you might like to take a look at this post:

[http://www.linux-solved.com/post/SOLVED-Multiple-IP-Addresses-16603.html](http://www.linux-solved.com/post/SOLVED-Multiple-IP-Addresses-16603.html)

Looks like the poster's doing what you're trying to do. I wouldn't mind having a go at this myself sometime in the near future...

Good luck!

---

