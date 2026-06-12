---
title: "[SOLVED] Apache startup problem"
date: 2008-03-04
forum: Server Platforms
---

### Post by jay019 on 2008-03-04
Hi all,

I've looked at a few other threads that have described the same problem yet apache2 is not auto starting for me. I linked /etc/init.d/apache2 to /etc/rc2.d/S91apache2 but still no joy, infact it now takes longer to boot. 

Any idea where i should start looking for problems.

Jay

---

### Post by Alekc on 2008-03-04
Hmm why have you linked it manualy? with apt-get install it should part automaticaly. What does error.log say?

---

### Post by jay019 on 2008-03-04
Sorry to waste your time. 
I failed to notice that there was a S50apache2 link in the /etc/rc2.d folder. :oops:

Alekc: I linked it manually as I thought it wasnt there at all (was looking for S91apache2 and therefore didnt notice S50apache2)
I think it all went belly up when I started using virtual hosts on the ip address i use for wireless. Oh well, as long as it works now I'm happy.

---

