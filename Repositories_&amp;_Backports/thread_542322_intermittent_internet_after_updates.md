---
title: "intermittent internet after updates"
date: 2007-09-03
forum: Repositories &amp; Backports
---

### Post by frenchcr on 2007-09-03
Any one know of feisty *or* gutsy updates that can break wired network connections or cause intermittency???

Just installed 7.04 for someone and installed updates. When they boot up the internet works. However, the connection is very intermittent and doesnt last long when it is working. Any ideas on where to start.

I also have a laptop (ACER aspire 5920g) that i upgraded to gutsy. When i boot internet doesnt connect, I have to go into network settings and uncheck then reselect the wired connection. Ubuntu reconfigures connection and this fixes problem. How do i get it to connect by itself after booting up :confused:

---

### Post by frenchcr on 2007-09-05
no one? :(

---

### Post by frenchcr on 2007-09-05
The intermittent wired desktop is still a problem.

...and although no-one helped, i just fixed the laptop problem...yay!

What fixed it, incase any other poor sole gets tormented by the same problem...

I went into System/Admin/Network tools,
In network device pull down box selected eth0,
Then clicked on IPv6,
Clicked on configure on the right to open eth0 properties,
In there i ticked the enable roaming mode button.

Rebooted and internet connected on boot up.

I still dont know why ...can someone explain...the answer probably lies in the following...I use my laptop at home and in my office...both are wired connections...the problem of "not connecting at boot up" occured in both places.

---

