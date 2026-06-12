---
title: "LAMP and security"
date: 2008-03-17
forum: Security Discussions
---

### Post by theshrewddude on 2008-03-17
[SIZE="3"]I've just installed LAMP on a fresh install of Kubuntu 7.10 using tasksel, for the purpose of testing PHP scripts. However I do not intend to use the laptop I installed it on as a web server... what can I do to ensure that the server apps that I've just installed don't compromise my computer's security?

Thanks for your help![/SIZE]

---

### Post by p_quarles on 2008-03-17
Set Apache to listen only on localhost.

---

### Post by theshrewddude on 2008-03-17
How can I access apache settings?

---

### Post by p_quarles on 2008-03-17
It should already be the default setting. To make sure:
```
gksudo gedit /etc/apache2/ports.conf
```
Make sure it says this:
```
Listen 127.0.0.1:80
```

---

### Post by FakeOutdoorsman on 2008-03-17
or for KDE:
```
kdesu kate /etc/apache2/ports.conf
```

or via command-line using vi (or nano):
```
sudo vi /etc/apache2/ports.conf
```

Always a good idea to backup first:
```
sudo cp /etc/apache2/ports.conf{,.bak}
```

---

