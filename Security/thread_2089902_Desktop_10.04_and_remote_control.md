---
title: "Desktop 10.04 and remote control"
date: 2012-11-30
forum: Security
---

### Post by jaho22 on 2012-11-30
I have a ubuntu 10.04 desktop on my server.

I have x2go remote desktop server program as a remote desktop graphical screen.

I want to remove all other ubuntu remote desktop and all other programs that listen tcp or udp ports.

What all kind of programs there is on basic ubuntu 10.04 desktop edition, what programs i should remove to add some more security.

I ofcourse have full iptables and fail2ban and sshguard setups, but, there is no need for extra programs that listen ports, so i need some advices to remove all unnessessary programs.

---

### Post by CharlesA on 2012-11-30
Why are you running a GUI on a server?

---

### Post by dannyboy79 on 2012-11-30
there shouldn't be any other programs listening besides the ones you set up yourself. You can always check using netstat

---

### Post by Ms. Daisy on 2012-12-01
> **jaho22 said:**
> I have a ubuntu 10.04 desktop on my server.

I have x2go remote desktop server program as a remote desktop graphical screen.

I want to remove all other ubuntu remote desktop and all other programs that listen tcp or udp ports.

What all kind of programs there is on basic ubuntu 10.04 desktop edition, what programs i should remove to add some more security.

I ofcourse have full iptables and fail2ban and sshguard setups, but, there is no need for extra programs that listen ports, so i need some advices to remove all unnessessary programs.
+1 to CharlesA, if you want a more secure setup you should remove the GUI from the server.  ```
dpkg -l | less
```will give you all the packages installed on your server. I highly recommend you familiarize yourself with what's on your server anyway. 
```
sudo netstat -antp
``` will give you a detailed list of listening services (as suggested by dannyboy79).

---

