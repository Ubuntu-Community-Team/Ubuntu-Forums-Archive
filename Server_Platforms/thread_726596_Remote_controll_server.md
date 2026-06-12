---
title: "Remote controll server"
date: 2008-03-16
forum: Server Platforms
---

### Post by Dr_Deadmeat on 2008-03-16
Is it possible to remote controll my server through a web-page on port 80 instead of a normal ssh-connection on port 22, as that port is closed on my school network... I would appreciate all help I can get, and I would be very relieved if this was possible...

---

### Post by netlogic on 2008-03-16
move your ssh port to 80.

---

### Post by Dr_Deadmeat on 2008-03-16
> **netlogic said:**
> move your ssh port to 80.

I've tried, but that resulted in me not being able to use my apache, rendering me unable to use my homepage =(

---

### Post by Dr Small on 2008-03-16
If your school has port 443 (HTTPS) open, then set SSH to listen on port 443.

---

### Post by Dr Bones on 2008-03-16
Hello could you please elaborate on how you go about reassigning which programs access the internet from which ports as I would also like to know how to do this.  Sorry if this has already been explain but I searched the forum here and came up with nothing.

---

### Post by netlogic on 2008-03-16
1) vi  /etc/ssh/sshd_config
2) change Port 22 to Port 443
3) sudo /etc/init.d/ssh restart

---

### Post by Dr Bones on 2008-03-16
Thanks so simple it hurts.    :lolflag:

---

### Post by Dr_Deadmeat on 2008-03-16
> **Dr Small said:**
> If your school has port 443 (HTTPS) open, then set SSH to listen on port 443.

Thank you, I will try that when my vacation is over...

---

