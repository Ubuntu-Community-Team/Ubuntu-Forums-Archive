---
title: "ssh question"
date: 2005-02-26
forum: Server Platforms
---

### Post by Brian_X7 on 2005-02-26
I use ssh with X forwarding when I vpn to work.  However, the machine that I ssh into is not the machine I eventually want to go to.  I only ssh into it because it's the only box with an ssh daemon running.  I can rsh into any other machine, but then I can't get any X at home.  My question is, can I ssh into the host that will let me ssh and then from there, login into one of the other machines and still get my X at home?

Thanks,
Brian

---

### Post by rom on 2005-02-26
Hi, 

instead of using x forwarding, you might want to try vnc tunnelled thru the ssh server.

EDIT: [http://www.ltsp.org/contrib/vnc.html](http://www.ltsp.org/contrib/vnc.html)

Rom

---

### Post by msgyrd on 2005-03-06
Yes, technically you should be able to set up one box to the outside world, and set up the rest to only accept ssh connections from that one machine, using an exact IP address or public key. (I'm not sure how much safer this is, but it should work).

---

