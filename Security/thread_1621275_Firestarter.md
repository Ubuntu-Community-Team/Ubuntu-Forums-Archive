---
title: "Firestarter"
date: 2010-11-14
forum: Security
---

### Post by chippy_250 on 2010-11-14
I've installed Firestarter but I'm a bit weary of configuring the wizard. The first two questions it asks is: 

1. Start the firewall on dial-out (tick or un-tick?)

2. IP address is assigned via DHCP (tick or un-tick?) 
I do have a DHCP turned on, on the router but I've assigned all the Pc's & laptops as static IP's.

---

### Post by Soul-Sing on 2010-11-14
Hi chippy_250 I would go for ufw or [COLOR="Red"]GUFW[/COLOR]. An outstanding frontend "firewall" and very easy to set up:

```
sudo ufw enable
```

Firestarter is not maintained anymore.(for several years)

---

### Post by Rubi1200 on 2010-11-14
If you have a firewall enabled on your router there is probably no need to use one on Ubuntu as well.

That said, if you still decide to do so, I am in total agreement with leoquant regarding Firestarter (which is not maintained or developed) and GUFW (my recommendation for new users).

---

### Post by bodhi.zazen on 2010-11-14
If firestarter is already installed, you have to purge it , then install gufw

```
sudo apt-get purge firestarter
sudo apt-get install gufw
```

---

### Post by chippy_250 on 2010-11-15
> **Rubi1200 said:**
> If you have a firewall enabled on your router there is probably no need to use one on Ubuntu as well.

That said, if you still decide to do so, I am in total agreement with leoquant regarding Firestarter (which is not maintained or developed) and GUFW (my recommendation for new users).
OK so a router's firewall should be alright for now then?

---

### Post by brian_p on 2010-11-15
> **chippy_250 said:**
> OK so a router's firewall should be alright for now then?

It's perfect. As good as having no firewall at all, which is my preference.

---

