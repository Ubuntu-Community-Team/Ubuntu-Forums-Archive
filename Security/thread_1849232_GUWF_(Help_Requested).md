---
title: "GUWF (Help Requested)"
date: 2011-09-24
forum: Security
---

### Post by Jiggle156 on 2011-09-24
I am relatively new to Ubuntu (11.04), and I was wondering - how do you know which ports to block/allow when configuring UFW?   By default it is set to deny all incoming traffic, yet I can still use the internet, spotify and other things.  Lil' help please :)

---

### Post by Ryan Dwyer on 2011-09-24
You can use the internet and whatnot because your computer started the communication. Your computer makes the outgoing connection, then the firewall lets incoming traffic through if it's a response to that connection. Any other incoming data is blocked.

You know which ports to block and allow based on which services you run. If you're setting up a webserver then you'll probably know that traffic will come in on port 80 so that port would need to be unblocked. Also, specific programs might instruct you to allow certain ports through your firewall to allow the program to work properly.

---

### Post by haqking on 2011-09-24
> **Ryan Dwyer said:**
> You can use the internet and whatnot because your computer started the communication. Your computer makes the outgoing connection, then the firewall lets incoming traffic through if it's a response to that connection. Any other incoming data is blocked.

You know which ports to block and allow based on which services you run. If you're setting up a webserver then you'll probably know that traffic will come in on port 80 so that port would need to be unblocked. Also, specific programs might instruct you to allow certain ports through your firewall to allow the program to work properly.

+1

No ports are open in Linux by default, only when you add or start services do certain ports start listening for traffic, then you allow or block those ports in your firewall if you need to.

Most home users are also protected by the router firewall anyways, UFW/GUFW are merely interfaces to the built in firewall in the Linux kernel known as IPTables/Netfilter.

Remember that your router is also responsible and probably more responsible for the traffic that comes to your machine, so the settings in its firewall are important

---

### Post by PeteAsdf on 2011-09-30
My understanding is that the default settings (allow out, deny in) should be fine unless you want to allow some specific services or apps that specifically require open ports- someone pls correct me if I'm wrong.

---

### Post by haqking on 2011-09-30
> **PeteAsdf said:**
> My understanding is that the default settings (allow out, deny in) should be fine unless you want to allow some specific services or apps that specifically require open ports- someone pls correct me if I'm wrong.

yes correct

---

