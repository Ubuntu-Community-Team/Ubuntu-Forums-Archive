---
title: "Ubuntu Desktop, VirtualBox Server, for seamless Web Development (Need your ideas)"
date: 2008-10-30
forum: Server Platforms
---

### Post by lifestream on 2008-10-30
I'm fishing for some ideas: how should I go about setting this up?

Here's a simple idea of how I plan to work:

[LIST=1]
[*]Have my ~/projects folder on the host.
[*]Edit a project from that folder on the host
[*]Log in to the server(Guest) to test the results of my work.
[/LIST]

How can I go to [http://localhost](http://localhost) on the GUEST, yet my projects are on the HOST? 
[LIST]
[*]Should  I make /var/www (GUEST) point/symlink to my (HOST) ~/projects? (Is it possible, since it's a SHARE?:P
[*]Any other ideas?
[/LIST]

**No, I won't install LAMP on my Desktop -_-; **



BTW Happy Ubuntu Intrepid Ibex day!

---

### Post by dantrevino on 2008-12-09
If you change the IP address of localhost on your guest, you'll possibly break other things.  Why not go to [http://host/](http://host/)  instead?  If thats acceptable, just add "<ipaddr> host" to the /etc/hosts on your guest machine.

---

