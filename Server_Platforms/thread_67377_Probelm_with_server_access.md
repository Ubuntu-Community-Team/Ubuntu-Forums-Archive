---
title: "Probelm with server access"
date: 2005-09-20
forum: Server Platforms
---

### Post by themelis on 2005-09-20
Hi,

I setup Ubuntu 5.04 on a machine and i am facing a strange problem (which i hadnt faced before). The computer i have installed Ubuntu is part of a big Lan on my institution. The problem is that i can access this computer (www,ftp,ssh etc) from my lan but i cant access this computer outside of the lan. I checked iptables and no problem. 
Is there something that causes this problem?

---

### Post by herrpoon on 2005-09-20
Correct me if I'm wrong but I'm pretty sure you have to forward ports for each of those things:

ssh/sftp - port 22
www - port 80

---

### Post by themelis on 2005-09-20
[QUOTE=herrpoon]Correct me if I'm wrong but I'm pretty sure you have to forward ports for each of those things:

ssh/sftp - port 22
www - port 80[/QUOTE]

I am sorry but I am not sure how to do that thing. Can you tell me how to that, please?

P.S. I have on ports.conf (of Apache2) Listen 80.

Thanks in advance...

---

### Post by herrpoon on 2005-09-20
It's not something you have to change in any config file, it's more of a networking issue.

If you're in an institution as you say, then you'll have to talk to your systems administrator although I doubt he/she would be willing to forward any ports for you.

For most people at home, it's just a matter of forwarding those ports in your router.

---

### Post by themelis on 2005-09-20
Thanks for your help. I will talk to admins.  :)

---

