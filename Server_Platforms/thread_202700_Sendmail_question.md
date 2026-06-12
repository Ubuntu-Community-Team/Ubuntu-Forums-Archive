---
title: "Sendmail question"
date: 2006-06-23
forum: Server Platforms
---

### Post by Kilz on 2006-06-23
Just a question to be safe. I have turned an old computer into a small lamp server with Ubuntu. I want to setup a form mailer for a small animal rescue my wife belongs to. If I have sendmail setup on the server, is it possible for people outside my home network to access it and send spam? The router dose not forward port 25. I think Im safe, but a friend said not to install sendmail. If it isnt safe out of the box, is it possible to make it safe, or use something else?

Thanks for any guidence
Kilz

---

### Post by lamego on 2006-06-24
Your friend is some years behind. Ubuntu uses postfix (which is sendmail) based, the default setup  will not allow remote relay.
Anyway if you have a router and the 25 is not redirected then it would be impossible to relay.

---

### Post by Kilz on 2006-06-24
[QUOTE=lamego]Your friend is some years behind. Ubuntu uses postfix (which is sendmail) based, the default setup  will not allow remote relay.
Anyway if you have a router and the 25 is not redirected then it would be impossible to relay.[/QUOTE]
Thanks for the info. I figured as much, but its better to be safe and ask, than become a spam sender. I kept getting errors setting up postfix, so I installed sendmail. Since Im the only one who can put files on apache I think Im pretty safe. Since port 25 isnt forwarded by the router, and a portscan of the machines lan address dosnt list 25 as open no one else should be able to send mail from the machine.

---

