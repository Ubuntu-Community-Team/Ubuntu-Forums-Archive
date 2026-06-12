---
title: "ufw not working from ubuntu 10.04"
date: 2011-05-21
forum: Security
---

### Post by jao_madn on 2011-05-21
Hi

I would like to ask if someone is using ufw in the ubuntu 10.04. I just notice now that my ufw is not working if i block the ports. i used the gufw which deny all incoming and outgoing but still my applications like firefox ,chrome still got connection. i try on firestarter lock down and works. why my ufw doesn't working.

As i send this thread i block all my incoming and outgoing but as you see still can post.

---

### Post by Soul-Sing on 2011-05-21
you use both firewalls next to each other?

---

### Post by jao_madn on 2011-05-21
nup when i used ufw and enable port blocking and try to connect but still have connection.. also the same in gufw.but i try the firestarter lock down its work..i dont want to use firestarter just install it for backup..

---

### Post by bodhi.zazen on 2011-05-21
This is because ufw / gufw by default only blocks NEW inbound connections, it allows RELATED and ESTABLISHED traffic.

You can block outbound traffic if you wish, but that is no needed by the vast majority of desktop users.

---

