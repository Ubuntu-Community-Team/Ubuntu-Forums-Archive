---
title: "Properly configureing Lamp"
date: 2005-12-19
forum: Server Platforms
---

### Post by Darkness3477 on 2005-12-19
G'day folks, I'm currently in the process of making a website on my computer (It'll be up with a domain name and a hosting company soon as it is finished). Anyway, the company i wish to host it on has some features I have never  used before, mainly php, MySQL and some other things. 

Anyway, I have gotten the local host to work (usuing apache and php) but i would like  to add MySQL to it, and have it all configured correctly.
So, could any of you point me to a website that could tell me what i need, (Simple terms, I'm very new to Ubuntu..And Linux distro's.)
OR maybe you could tell me what to do in the terminal.

---

### Post by invalid on 2005-12-19
[https://wiki.ubuntu.com/ApacheMySQLPHP](https://wiki.ubuntu.com/ApacheMySQLPHP)

---

### Post by Darkness3477 on 2005-12-20
Oh, what extra security should i think about getting if i decide to make my computer into a server so other people can connect to it?

I've tried searching around on this site (Breifly), and also on google but none of it seems to apply directly to ubuntu 5.10 and as i said, i'm a beginner, so i need things to be simple.

Thanks.

---

### Post by Darkness3477 on 2005-12-20
Wow, that was quick. Thankyou.

---

### Post by invalid on 2005-12-20
You can work with IPtables, which is a firewall.
If you want to do it in a graphical interface get firestarter.
```
sudo apt-get install firestarter
```

---

### Post by Darkness3477 on 2005-12-20
Hey, i've installed firestarter. Now where do i find it?

---

### Post by invalid on 2005-12-20
```
sudo firestarter
```
from a terminal.

---

### Post by Darkness3477 on 2005-12-20
Ahhh, when i close the terminal (After starting firestarter), the firewall window closes, am i still being protected or is it (The fire wall), only going when i have the terminal up?

---

### Post by invalid on 2005-12-20
I do not use firestarter, so I can not guarantee how it works.. if I remember reading correctly, there should be a small icon on your task bar. Maybe try searching the forums to pull up some more information.

---

### Post by Spudgun on 2005-12-20
[QUOTE=Darkness3477]Ahhh, when i close the terminal (After starting firestarter), the firewall window closes, am i still being protected or is it (The fire wall), only going when i have the terminal up?[/QUOTE]

Firestarter starts up with your PC regardless of you running the GUI. All Firestarter is is an interface to IP Tables.

---

