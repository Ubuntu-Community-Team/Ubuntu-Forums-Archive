---
title: "Lost .conf files"
date: 2006-05-27
forum: Server Platforms
---

### Post by ManicMike on 2006-05-27
I was messing around with bind trying to set up dns and completely messed up one of the .conf files.
I then apt-get removed bind9 and deleted the folder /etc/bind.
I though installing bind9 again would get me new conf files but no.
How do I get new .conf files??

---

### Post by meng on 2006-05-27
Would it be too much to expect that you might have a .conf~ backup file? I guess it would be ... sorry, I can't help much more except to suggest googling for someone else's .conf file.

---

### Post by Jussi Kukkonen on 2006-05-27
Did you do 
```
apt-get *--purge* remove bind9
```
?

---

### Post by ManicMike on 2006-05-27
No but I have now and it works!! :D
Thank you!

---

