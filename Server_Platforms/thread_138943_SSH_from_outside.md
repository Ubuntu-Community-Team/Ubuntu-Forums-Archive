---
title: "SSH from outside"
date: 2006-03-02
forum: Server Platforms
---

### Post by Zhukov on 2006-03-02
Hi there!
I'm having some problems acessing my ssh server from the outside.

I have a router and i've configured port forwarding (port 22) to my server.
I can login to the server inside de LAN but when i do it from the ouside i keep getting "wrong password"...

I can type my username and pass so i dont believe it is a port configuration issue.

Any help would be highly appreciated.

Thanks in advance.

---

### Post by encompass on 2006-03-02
it sounds like your router for sure...  But it my be you hae a firewall turned on... have you installed one? if not I would recommend it... sudo apt-get install firestarter.  Then from there I would turn the firewall off and goto [www.grc.com](www.grc.com) and do a shields up test to see if you have port 22 open or not.  Hope that helps.

---

### Post by csevcik on 2006-03-02
What kind of router are you using? If your router creates a LAN with fake IP numbers which cannot be sen from outside of the LAN, say something like the Belkin wireless routers which give you an IP like 192.186.2.xxx on ALL Belkin routers from within your LAN you won't be able to reach the machines from the outside. You will be able to reach the router using the IP number given by the internet provider (if it is a fixed number not assigned by a dhcp which changes often) but nothing else. 

Carlos

---

### Post by Zhukov on 2006-03-03
No firewall and no x either. I may set up some iptables rules but i believe i dont need more. Yes, the router is using 192.168.x.x ips but nevertheless it should work flawlessly.
As i said i can login from within the network but (even within the LAN) i cant login using the outside ip.
Duh, i just sorted it out. Im login into the router. Anyone knows how i bypass it? :confused:

---

### Post by bernardfrancois on 2006-03-03
Your router has to be told to forward the port to the local IP adress of the computer behind the router.

---

### Post by rich on 2006-03-03
When you say you can login from inside your LAN, I take it you mean directly to the IP of the sshd.

What about if you try logging onto your router's internal IP using 22 ? If it is correctly set up it should forward you to the sshd box again. 

If that works you can try logging into the public IP of your router. 

HTH

Rich

---

### Post by Zhukov on 2006-03-05
Now this is stupid...
I cant login from inside the LAN with the outside IP but i can login from outside the LAN with the same ip.

Problem solved, thanks everybody! :-D

---

