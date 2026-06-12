---
title: "Regarding 'Encrypted Private Directory'.  Did i get my mount passphrase?"
date: 2011-08-26
forum: Security
---

### Post by satya ub on 2011-08-26
Hi, i am new to Ubuntu. It's three days since i installed Natty Narwhal. I googled my doubts to know. But to really embrace the change i have joined this forum. 

I wanted to lock some files. And i read about "Encrypted Private Directory" on Ubuntu Help page. I followed the first 4 steps. After logging in i got a read window and i selected "Run this now". Then i got a long alpha-numeric string. I didn't knew what to do. So i closed the Terminal. Is the string the passphrase?

I have knowledge of C and Data Structures. I have a inner curiosity to learn about Ubuntu. Apart from giving me an answer, if you can suggest me some basic books & also to gain proficiency i would be really happy:KS

---

### Post by Bachstelze on 2011-08-26
> **satya ub said:**
> 
I wanted to lock some files. And i read about "Encrypted Private Directory" on Ubuntu Help page. I followed the first 4 steps. After logging in i got a read window and i selected "Run this now". Then i got a long alpha-numeric string. I didn't knew what to do. So i closed the Terminal. Is the string the passphrase?

Yes, it's the passphrase which is needed to decrypt your home folder in case something happens to your system and you want to recover the data from another system. You can also get it with ecryptfs-unwrap-passphrase from a terminal.

---

### Post by dave01945 on 2011-08-26
> **Bachstelze said:**
> Yes, it's the passphrase which is needed to decrypt your home folder in case something happens to your system and you want to recover the data from another system. You can also get it with ecryptfs-unwrap-passphrase from a terminal.

after doing this you should probably write it down and put it somewhere safe it's not a good idea to keep it on your computer defeats the idea of encryption also if you keep it in the encrypted part you won't be able to get it if something does go wrong

---

### Post by satya ub on 2011-08-26
Thank you for helping me out. Yes i did note it down.

---

