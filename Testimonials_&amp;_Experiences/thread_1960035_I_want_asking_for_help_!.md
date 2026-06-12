---
title: "I want asking for help !"
date: 2012-04-16
forum: Testimonials &amp; Experiences
---

### Post by Mikler on 2012-04-16
I'm sorry but I was damn pissed that someone would change the protocol implementation like THAT ! I mean common !
When you change something, u call it version 2 so people are aware of it !
TCP should be used for however you want, not being limited to 200 ms lag ! At least if you DO change that parameter, make it an option to change it back  ! give me that much..
I come from a 512 mb server who worked perfectly, to a 8 gb that lags like hell !
That being said, do you know how to alter the "TCP delay ack" in ubuntu ? And yes im ready to recompile the whole lot even I never did something like that before.
And again, sorry for my outburst, just I've been working on this a lot, and maybe you  would react kind of similar.

---

### Post by Mikler on 2012-04-16
And TCP_NODELAY  is already set, and it makes no difference ( TCP_NODELAY is when sending, TCP DELAY ACK is when responding).
PS I apologize, I was way out of line.

---

### Post by jadtech on 2012-04-16
check this out may help may not worth a look 

[http://www.linuxquestions.org/questions/linux-networking-3/linux-change-tcp-kernel-parameter-for-tcp-delay-ack-ticks-475034/](http://www.linuxquestions.org/questions/linux-networking-3/linux-change-tcp-kernel-parameter-for-tcp-delay-ack-ticks-475034/)

[http://www.linuxquestions.org/questions/linux-networking-3/linux-change-tcp-kernel-parameter-for-tcp-delay-ack-ticks-475034/](http://www.linuxquestions.org/questions/linux-networking-3/linux-change-tcp-kernel-parameter-for-tcp-delay-ack-ticks-475034/)

[http://serverfault.com/questions/215674/latency-in-tcp-ip-over-ethernet-networks](http://serverfault.com/questions/215674/latency-in-tcp-ip-over-ethernet-networks)

---

### Post by jadtech on 2012-04-16
> **Mikler said:**
> And TCP_NODELAY  is already set, and it makes no difference ( TCP_NODELAY is when sending, TCP DELAY ACK is when responding).
PS I apologize, I was way out of line.

actually what they are recommending is TCP_NODELAY on both sides making other changes will cause system wide issues ..

either way the 200ms delay is not a ubuntu exclusive  thing it is from all I read and see Linux kernel in general distro aside windows  too ..

---

### Post by coffeecat on 2012-04-17
@Mikler, the forum membership, staff included, consists of Ubuntu users from a wide variety of backgrounds. Very few Ubuntu developers frequent the forums. All forum members are volunteers. If you want help with any technical matter, please post in a support section of the forum without all the emotion.

Since the first post is not a testimonial but a rant.... Thread closed.

---

