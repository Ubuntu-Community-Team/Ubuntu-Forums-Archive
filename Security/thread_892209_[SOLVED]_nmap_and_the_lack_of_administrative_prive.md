---
title: "[SOLVED] nmap and the lack of administrative priveleges"
date: 2008-08-16
forum: Security
---

### Post by adamogardner on 2008-08-16
So I'm playing with nmap, and Im targeting my friends machine (yeah he knows. We're good like that.) and I'm starting from the beginning with -A option. then I try -sN and it objected on grounds that I don;t have root priveledge or something to that effect.  What does this mean?  On my computer or his?  Any references?

---

### Post by tamoneya on 2008-08-16
it is privileges on your computer.  Use this instead:```
sudo nmap -sN <IP_Address>
```

---

### Post by adamogardner on 2008-08-17
> **tamoneya said:**
> it is privileges on your computer.  Use this instead:```
sudo nmap -sN <IP_Address>
```

thanks tamoneya,  I'm sorry I fell asleep on you last night.  Do you understand why I need to sudo for some of these options but not others?

---

### Post by tamoneya on 2008-08-17
> **adamogardner said:**
> thanks tamoneya,  I'm sorry I fell asleep on you last night.  Do you understand why I need to sudo for some of these options but not others?

Most likely because you are directly accessing the underlying transport layer.  [http://en.wikipedia.org/wiki/OSI_model](http://en.wikipedia.org/wiki/OSI_model)

---

