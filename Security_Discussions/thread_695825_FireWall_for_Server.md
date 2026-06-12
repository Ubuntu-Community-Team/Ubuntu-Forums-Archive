---
title: "FireWall for Server"
date: 2008-02-13
forum: Security Discussions
---

### Post by mattc908 on 2008-02-13
Hey what would be the best Firewall for an ubuntu server, that wouldn't stop my programs for running such as FTP, Apache, Ventrilo (Voice Communications software), SSH. I run everything in command Terminal not in a GUI.
-Mattc908

---

### Post by Dr Small on 2008-02-13
Iptables is your firewall by default on ubuntu. If you wish to configure it, install Firestarter :)

---

### Post by mattc908 on 2008-02-13
BUt firestarter will run in command form and not in a GUI correct?

---

### Post by Dr Small on 2008-02-13
Firestarter is GUI.
But I got it to work on my server by ssh'ing into it and then running Firestarter.

---

### Post by mojoman on 2008-02-13
> **mattc908 said:**
> BUt firestarter will run in command form and not in a GUI correct?

No. Firestarter is a GUI interface for IP-tables. If you have a server you do not want firestarter. You'll just have to configure IP-tables the old fashioned way.

An option might  or use some other firewall, such as shorewall, and then use webmin to configure it remotely using a GUI interface.

---

### Post by mattc908 on 2008-02-13
What is webmin? I SSH'd into it and installed firestarted.... Now how would I set it up through SSH?

---

### Post by mojoman on 2008-02-13
> **mattc908 said:**
> What is webmin? I SSH'd into it and installed firestarted.... Now how would I set it up through SSH?
[U][URL="http://www.webmin.com/"]
http://www.webmin.com/[/URL][/U]

---

### Post by mattc908 on 2008-02-13
I SSH in and install than it says: You Can Login in at [https://mattc908:10000/](https://mattc908:10000/) how do I make it say, my websites name or localhost?

---

### Post by Dr Small on 2008-02-13
> **mattc908 said:**
> What is webmin? I SSH'd into it and installed firestarted.... Now how would I set it up through SSH?
```
ssh -XC -c blowfish user@host
sudo firestarter
```

---

### Post by mattc908 on 2008-02-13
Alright Thanks, anyone know the webmin prob?

---

