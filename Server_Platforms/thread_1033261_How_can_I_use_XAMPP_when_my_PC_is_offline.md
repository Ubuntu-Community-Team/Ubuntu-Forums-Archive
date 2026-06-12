---
title: "How can I use XAMPP when my PC is offline ?"
date: 2009-01-07
forum: Server Platforms
---

### Post by solidussnake on 2009-01-07
I can get into the PHPMyAdmin page with the link
"http://localhost/phpmyadmin"
when my computer is cannected to a LAN wire.

However, if I do not connect my PC to the LAN,
(that means I am offline)
the FireFox said that it cannot find the page.

How can I use the phpmyadmin when my computer is offline ?

---

### Post by volkswagner on 2009-01-07
what is in /etc/hosts file?

---

### Post by solidussnake on 2009-01-11
> **volkswagner said:**
> what is in /etc/hosts file?

Thanks for your answer.
I have solved it by myself.

When I do not connect to the LAN,
I need to disable "work offline" in the firefox.

file -> work offline -> unclick the box

---

### Post by windependence on 2009-01-11
You could also try 127.0.0.1

-Tim

---

