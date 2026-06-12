---
title: "Firewall Configuration if needed?"
date: 2008-11-12
forum: Security
---

### Post by oiad on 2008-11-12
I have recently switched over from windows completely (sick of ms bs) and am slowly getting a grasp on the new os but have a question about firewall security.  
  I see multiple posts that say I don't need to enable the firewall, and others that say its built in and to enable it.  I have a couple of ports I use (ssh, transmission, etc) and I need to know if I need a firewall at all?  I am behind a router.  I understand how to control the ports with ufw but not sure how to say stealth them all if needed.  Thanks

---

### Post by cdtech on 2008-11-12
You can use "firestarter" to configure your firewall. It's a frontend GUI to the "iptables".

System > Administration > Firestarter

---

### Post by oiad on 2008-11-12
> **cdtech said:**
> You can use "firestarter" to configure your firewall. It's a frontend GUI to the "iptables".

System > Administration > Firestarter

isn't ufw and gufw the same type of thing?

---

### Post by cdtech on 2008-11-12
My bad... when you enabled "ufw" did you check stealth such as grc.com (shieldsup)?

---

### Post by cariboo on 2008-11-12
Using a firewall is not going to stealth ports on your router, as GRC only scans for open ports on the first device it sees.

Jim

---

### Post by brian_p on 2008-11-12
> **oiad said:**
> 

I have a couple of ports I use (ssh, transmission, etc) and I need to know if I need a firewall at all?  I am behind a router.  I understand how to control the ports with ufw but not sure how to say stealth them all if needed.  Thanks

You have a port on your router forwarded to a computer for the ssh service and another one forwared for the file sharing service. The machine is running sshd and transmission. I imagine you have this setup because you are offering services.

If you use ufw to reject packets or something else to drop packets the services are no longer available. If you want to control the availability of a service why not just switch it off? A firewall appears completely superfluous.

---

### Post by oiad on 2008-11-12
> **brian_p said:**
> You have a port on your router forwarded to a computer for the ssh service and another one forwared for the file sharing service. The machine is running sshd and transmission. I imagine you have this setup because you are offering services.

If you use ufw to reject packets or something else to drop packets the services are no longer available. If you want to control the availability of a service why not just switch it off? A firewall appears completely superfluous.

You're right on my setup.  My router forwards ports to my workstation for the programs.  I'm trying to find out if I should be using Ubuntu's built in firewall ufw for all of the ports for protection or if that isn't needed.  I know I will have to have certain ports open for my select services to work but am confused on if I need to do anything from default to all of the ports I won't be using.  An exampple is when I had windows I would forward a port to the workstation for a program and then the firewall on the win box would be set to allow connections on that port only and ignore all other requests.  Do I need this type of extra security in linux/ubuntu or since the os works differently is it overkill?  Thanks

---

### Post by brian_p on 2008-11-12
> **oiad said:**
> You're right on my setup.  My router forwards ports to my workstation for the programs.  I'm trying to find out if I should be using Ubuntu's built in firewall ufw for all of the ports for protection or if that isn't needed.  I know I will have to have certain ports open for my select services to work but am confused on if I need to do anything from default to all of the ports I won't be using.  An exampple is when I had windows I would forward a port to the workstation for a program and then the firewall on the win box would be set to allow connections on that port only and ignore all other requests.  Do I need this type of extra security in linux/ubuntu or since the os works differently is it overkill?  Thanks

Would I also be right in thinking that apart from the forwarded ports for ssh and transmission no other ports are forwarded? If so, only the two services you have allowed can get to the machine so there is no need for any firewall rules on the machine.

It's not that Linux works differently but a consequence of basic networking. You could play about with ufw and close all the ports (other than the two you want) on the computer but considering nothing will ever arrive at them via the router nothing is added to the already secure setup you have.

---

### Post by oiad on 2008-11-13
> **brian_p said:**
> Would I also be right in thinking that apart from the forwarded ports for ssh and transmission no other ports are forwarded? If so, only the two services you have allowed can get to the machine so there is no need for any firewall rules on the machine.

It's not that Linux works differently but a consequence of basic networking. You could play about with ufw and close all the ports (other than the two you want) on the computer but considering nothing will ever arrive at them via the router nothing is added to the already secure setup you have.

Then I'm going to just leave it alone.  Thanks

---

