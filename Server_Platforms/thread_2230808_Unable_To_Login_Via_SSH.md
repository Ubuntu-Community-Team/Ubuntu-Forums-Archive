---
title: "Unable To Login Via SSH"
date: 2014-06-21
forum: Server Platforms
---

### Post by rmaher84 on 2014-06-21
i am getting a weird behaviour on my Ubuntu 14.04 server.

after a recent restart, i cannot login with SSH. 

if i type in an **incorrect password**, it will tell me that it is incorrect and lets me try again, but if i type the** correct password**, the cursor moves to the next line but it doesn't seem to complete the login and gets stuck in the position.

i am running a tomcat on the system which i am still able to access. so the server seems to be running fine.

the only way i have access to the server is by SSH or by car, so i am unable to see any logs.

does anyone know what could the problem here? and information would be appreciated.

thanks in advanced. [IMG]http://ubuntuforums.org/images/icons/icon11.png[/IMG]

---

### Post by Lars Noodén on 2014-06-21
Welcome.  

Well, short of looking at the server's sshd logs about the only clue you can gather would be increasing the verbosity of your client using -v or -vv or -vvv.

```

ssh -vvv rmaher84@server.example.com

```
  
That will show you half of what's going on and might help.  Otherwise, a car trip is in your near future.  Between the last successful reboot and the first failed reboot, have you changed anything in /etc/ssh/sshd_config?

---

### Post by rmaher84 on 2014-06-21
i have tried to logging again using the -vvv flag, and after the password is entered, is get:

> debug2: we sent a password packet, wait for reply


Could this be caused by the firewall?

---

### Post by Doug S on 2014-06-21
> **rmaher84 said:**
> Could this be caused by the firewall?I doubt it. You have an established tcp connection between the two machines, and no obvious reason for any firewall intervention.

---

### Post by DJ_Max on 2014-06-21
Could be a router issue. What router do you have, is it up to date? Next step would be to fire up Wireshack and see where the packet is going.

---

