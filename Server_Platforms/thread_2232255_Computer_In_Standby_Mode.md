---
title: "Computer In Standby Mode?"
date: 2014-06-30
forum: Server Platforms
---

### Post by rmaher84 on 2014-06-30
im running an ubuntu server in my home and i have programs running on it such as Sickbeard and SABnzbd.

the problem is that these programs (kind of) keep turning off. they show an error message when i try to go onto the port that they use. suggesting that they arent running as normal. but when i connect through SSH and then try again, they suddenly start working as normal.

i think if they are not being used, the server is going into some kind of standby mode. 

can anyone tell me what is happening? and how i can prevent it from doing this? it makes the point of the server always running pointless.

thanks in advanced. :)

---

### Post by papibe on 2014-06-30
Thread moved to **Server Platforms**.

---

### Post by tgalati4 on 2014-07-01
What is the make and model of the computer?  It's possible you have power management settings in BIOS.  Turn them off.

Install acpitool and examine how things are powered during sleep states.

```
sudo apt-get install acpitool
acpitool -w
```

---

