---
title: "Ubuntu Server VirtualBox Apache2 blank page not displaying it works page"
date: 2016-08-05
forum: Server Platforms
---

### Post by Lukasz Tarkowski on 2016-08-05
Ubuntu Server VirtualBox Apache2 blank page not displaying it works page,  also webmin not displaying, Servername not determined  I have Ubuntu server 16.04.
Sorry if I posted in a wrong section

---

### Post by howefield on 2016-08-05
> **Lukasz Tarkowski said:**
> ... Sorry if I posted in a wrong section

Toss up between "*Server Platforms*" and "*Virtualisation*", let's put it here in "*Server Platforms*" for the time being.

---

### Post by darkod on 2016-08-05
You really should give more info from the start...

1. How do you know it's not working, which IP are you trying to access?

In VBox, in the VM network settings, did you leave the default NAT option or you set it to bridged?

If you use NAT the VM is behind that NAT and it's not easy to access it from your home LAN. That's why I always use bridged and assign static IP from the home LAN subnet to VMs, and they can easily be accessed from any machine in the home network.

---

### Post by Lukasz Tarkowski on 2016-08-05
I am going to try to reinstall it ubuntu server

---

### Post by Lukasz Tarkowski on 2016-08-05
My name Lukasz@Lukasz,  I cannot access localhost, it gives me blank page.  I am using Apache2 and Ubuntu Server

---

### Post by darkod on 2016-08-05
> **Lukasz Tarkowski said:**
> My name Lukasz@Lukasz,  I cannot access localhost, it gives me blank page.  I am using Apache2 and Ubuntu Server

Sorry, but you are not making any sense.

You test web pages by opening them in a browser. Ubuntu Server by default has no GUI and no browser.

You need to be testing from another PC I guess, and in this case you can't use 'localhost'. That means querying the local machine and of course it shows error.

You need to try and open the server IP or domain in the browser, and only if you can reach it (within the same network, or correct dns, etc).

---

### Post by Lukasz Tarkowski on 2016-08-05
Hey everyone everything works now.  I downloaded the newer version of Ubuntu Server,  Installed the system then,  I  selected no automatic updates,  Selected Lamp Server, standard packages, openssh, dns server option.  I use virtualbox Ubuntu Server, and I access it through my ip address,  I got the IP address from terminal ifconfig

---

