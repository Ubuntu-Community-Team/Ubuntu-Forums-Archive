---
title: "fail2ban help needed :)"
date: 2006-12-18
forum: Server Platforms
---

### Post by PetePete on 2006-12-18
hi,
I've installed fail2ban was messing about with it (testing if i'd set it up correctly) and sucessfully managed to ban an IP. 

Question i have now is , where is this record kept so i can unban myself?!

i've checked /etc/hosts.deny but not there....

thanks.

---

### Post by PetePete on 2006-12-18
actually i'm not sure if i have managed to ban myself :D

---

### Post by PetePete on 2006-12-18
can somoene tell me the file where i can see if a host has been banned?

---

### Post by PetePete on 2006-12-18
found out.
sudo iptables -L

---

