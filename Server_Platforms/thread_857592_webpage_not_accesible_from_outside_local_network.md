---
title: "webpage not accesible from outside local network"
date: 2008-07-12
forum: Server Platforms
---

### Post by jucadizo on 2008-07-12
Hi,
I'm trying to set up apache2 to host my own website, however it works from the local network but not from anyone outside. Browsers get time out error trying to reach my router's ip address.
** I tried changing the listening port to 8119 but no success.
** I wouldn't think it's a fire wall issue since other pcs in my local network can get to the web server.
** the router is pingable and it has port forwarding from port 80 to 8888 toward the server.
** nothing shows up on the error logs

Is there any configuration line missing?

I've attached the configurations files
Help greatly appreciated
thanks

---

### Post by windependence on 2008-07-12
Why are you trying to forward one port to another. Generally that won't work. You need to forward 80 on the router back to 80 on the server. Then, go to canyouseeme.org and see if your port is open. You must have Apache running to do this and it should be listening on 80.

-Tim

---

### Post by jucadizo on 2008-07-12
> **windependence said:**
> Why are you trying to forward one port to another. Generally that won't work. You need to forward 80 on the router back to 80 on the server. Then, go to canyouseeme.org and see if your port is open. You must have Apache running to do this and it should be listening on 80.

-Tim

I was forwarding a range of ports. I've changed it to forward only incoming traffic through port 8119. I would like to use port 8119 instead of 80 to discard ISP port 80 blocking

* could it be a setting on the iptables?

---

### Post by windependence on 2008-07-12
Check 8119 from the outside once you have Apache listening on that port. If you installed Uuntu with the firewall active ( I don't) then yes you will have to open the port. I am sorry for that you are on your own as I use a BSD firewall for my machines, or a hardware box. I don't know crap about IPtables.

-Tim

---

### Post by jucadizo on 2008-07-12
It works now!,
some how tcp ports were closed. I installed Firestarter (firewall) instead if dealing with the iptables and added the incoming traffic rule through port 8119. That opened the port.

Before,  when I tried using the [http://canyouseeme.org/](http://canyouseeme.org/) website service it showed time out error, so that must have been it.
Thanks for the help

---

### Post by Master Chief on 2008-07-12
> **jucadizo said:**
> It works now!,
some how tcp ports were closed. I installed Firestarter (firewall) instead if dealing with the iptables...

That's because you installed the Firestarter GUI earlier on ;)

---

