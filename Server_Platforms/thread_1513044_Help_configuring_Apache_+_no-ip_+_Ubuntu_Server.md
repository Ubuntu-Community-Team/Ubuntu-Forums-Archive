---
title: "Help configuring Apache + no-ip + Ubuntu Server"
date: 2010-06-18
forum: Server Platforms
---

### Post by nautica17 on 2010-06-18
So I have Ubuntu Server edition installed, as well as LAMP. I made a no-ip account and got a domain. I'm basically trying to set up an apache web server. It only works locally though. 

So now my question is, how I do set up the server so that anyone online can go on it. I've tried a few tutorials out there and I still can't get it to work. What files do I need to edit (if any)? I've been playing around with the "default" file under /etc/apache2/sites-available/default, but to no avail. 

Any help appreciated. :)

---

### Post by Ryan Dwyer on 2010-06-18
You need to forward port 80 in your router.

---

### Post by nautica17 on 2010-06-18
It works! :D Thank you so much! I can go cure my headache now.

---

