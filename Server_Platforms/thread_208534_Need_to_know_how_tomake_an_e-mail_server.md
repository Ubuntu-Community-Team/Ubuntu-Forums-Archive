---
title: "Need to know how tomake an e-mail server"
date: 2006-07-03
forum: Server Platforms
---

### Post by midpipps on 2006-07-03
I need help I need to make an e-mail server on my linux box so that I can use it to send out newsletters.  I don't really care if it recieves e-mail would be nice but not a  big deal I just need help thanks in advance.

---

### Post by Tortanick on 2006-07-04
Google flurdy and you will find a good guide, it includes a bit more than outward connection though.

---

### Post by MJN on 2006-07-04
That is awful advice - talk about using a sledgehammer to crack a nut! That guide is way, way over the top for the requirements here.
 
Just install Postfix - I think the default config should be sufficient to get you started (it ought to work safely out of the box).
 
If you're only after outgoing mail provision, why not just point yourself at your ISPs mail server? Is there anything you hope to achieve by running your own mail server? There're certainly drawbacks with your intended approach... (e.g. some MTAs refusing connections from dynamic IPs etc)
 
Mathew

---

### Post by faultyCPU on 2006-07-04
i smell spam ;)

---

