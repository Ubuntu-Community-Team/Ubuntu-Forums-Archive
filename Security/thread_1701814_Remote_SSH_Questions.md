---
title: "Remote SSH Questions"
date: 2011-03-06
forum: Security
---

### Post by akester on 2011-03-06
I have a real quick question, I mainly want to see if I am violating any best practices or anything.

Pretty much I need to have a group of computers that connect to a remote site and run lynx to view some php pages that interface with mysql (that's a mouthful)
For version control, I would like to keep only one central copy of the web files.

Personal data is sent, so rather than setup https server or SSL mysql encryption, I decided to create a "tunnel" to a Terminal Server using SSH.

I flirted with the idea of setting up VPN tunnels between the clients and a DMZ network but I don't want to add a bunch of complexity.

I just wanted to make sure that I wasn't creating a gaping security hole.


Thanks,
kester

---

### Post by bodhi.zazen on 2011-03-07
As long as you are tunnelling over SSH you will be fine.

---

### Post by akester on 2011-03-07
Ok,  Thanks for the reply.

I just wanted to double check, I'm a bit paranoid.

Thanks again

---

