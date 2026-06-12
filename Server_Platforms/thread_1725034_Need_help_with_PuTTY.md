---
title: "Need help with PuTTY"
date: 2011-04-09
forum: Server Platforms
---

### Post by kainijssen on 2011-04-09
Hey guys,
im new to ubuntu and i'm trying to set up an vps, but i cant manage to get past the first screen where i have to fill ip and port 22
when i click open, it says connection refused

now is my question, can anyone help me with this via teamviewer? 


Regards,

Kai

---

### Post by falko on 2011-04-09
I don't have teamviewer. Please make sure that OpenSSH is runnning on your VPS and that the firewall doesn't block port 22.

---

### Post by kainijssen on 2011-04-09
> **falko said:**
> I don't have teamviewer. Please make sure that OpenSSH is runnning on your VPS and that the firewall doesn't block port 22.


go download teamviewer then please, i cant manage to get the open SSH


:O

---

### Post by rubylaser on 2011-04-09
Paste in your Teamviewer ID and Password, and I'll take a look. Have you installed ssh on your VPS?
```
sudo apt-get install ssh
```
and have you made sure ssh is listening?
```
root@nas:~# netstat --listen | grep ssh
tcp        0      0 *:ssh                   *:*                     LISTEN     
tcp6       0      0 [::]:ssh                [::]:*                  LISTEN   
```

---

### Post by kainijssen on 2011-04-09
> **rubylaser said:**
> Paste in your Teamviewer ID and Password, and I'll take a look. Have you installed ssh on your VPS?
```
sudo apt-get install ssh
```and have you made sure ssh is listening?
```
root@nas:~# netstat --listen | grep ssh
tcp        0      0 *:ssh                   *:*                     LISTEN     
tcp6       0      0 [::]:ssh                [::]:*                  LISTEN   
```


my teamviewer ID     590 289 339
password                  7586



=D


Back.

---

