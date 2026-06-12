---
title: "gufw / ufw allowing ping ? failed firewall tests"
date: 2008-10-03
forum: Security
---

### Post by smooth3006 on 2008-10-03
i ran a test at grc shields up site and it says all of my ports are stealth but it says i failed because my firewall allows ping requests ? how can i fix this and am i vulnerable to hackers ?


Update : SOLVED !!!!

---

### Post by cdenley on 2008-10-03
> **smooth3006 said:**
> i ran a test at grc shields up site and it says all of my ports are stealth but it says i failed because my firewall allows ping requests ? how can i fix this and am i vulnerable to hackers ?
[https://answers.launchpad.net/ufw/+question/26585](https://answers.launchpad.net/ufw/+question/26585)

I wouldn't worry too much about letting people ping you, or whether your ports are "stealthed".

---

### Post by Nepherte on 2008-10-03
Are you behind a router? If so, then the site is testing that one instead of your computer.

---

### Post by smooth3006 on 2008-10-03
yeah but i passed the firewall test before ? i made no changes to the firewall other than to allow transmission. i just don't want to be vulnerable to any attacks.

---

### Post by cdenley on 2008-10-03
> **smooth3006 said:**
> yeah but i passed the firewall test before ? i made no changes to the firewall other than to allow transmission. i just don't want to be vulnerable to any attacks.

You aren't vulnerable to any attacks. You never were (unless you did something stupid). What do you mean you allowed "transmission"? Are you referring to your router's firewall, or an iptables frontend?

---

### Post by smooth3006 on 2008-10-03
i allowed transmission access to a recommended port in gufw. i am not behind a hardware firewall / router . the link you gave me worked, i only needed to append a line in gedit and now i successfully passed the grc leak test. 


thanks :)

---

### Post by nubdora on 2008-10-03
> **cdenley said:**
> You aren't vulnerable to any attacks. You never were (unless you did something stupid). What do you mean you allowed "transmission"? Are you referring to your router's firewall, or an iptables frontend?

I believe he was referring to the Transmission application, the default torrent client in Ubuntu.

---

### Post by nubdora on 2008-10-03
> **cdenley said:**
> You aren't vulnerable to any attacks. You never were (unless you did something stupid). What do you mean you allowed "transmission"? Are you referring to your router's firewall, or an iptables frontend?

I believe he was referring to the Transmission application, the default torrent client in Ubuntu. 

Also, since your problem is solved, please change the thread accordingly.

---

### Post by smooth3006 on 2008-10-03
> **nubdora said:**
> I believe he was referring to the Transmission application, the default torrent client in Ubuntu. 

Also, since your problem is solved, please change the thread accordingly.

yes i was referring to the transmission p2p app in ubuntu. yes it seems to be solved now, i just wanted to pass that leak test to make sure im secured. 


thanks guys.

---

### Post by cdenley on 2008-10-03
> **smooth3006 said:**
> yes i was referring to the transmission p2p app in ubuntu. yes it seems to be solved now, i just wanted to pass that leak test to make sure im secured. 

You probably were secure.
grc shields up = FUD
Blocking pings and dropping packets instead of rejecting them has no real security benefit.

I believe he was suggesting you click on "Thread Tools" at the top of your thread, then select "Mark this thread as solved".

---

