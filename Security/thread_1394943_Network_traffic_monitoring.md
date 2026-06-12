---
title: "Network traffic monitoring"
date: 2010-01-31
forum: Security
---

### Post by 289531.EXE on 2010-01-31
Is there a program that monitors and displays 'who' is on your wireless Internet signal that one may not be aware of? Like, the ability to see when someone that you don't know is accessing your locked wireless? Going on and off.

---

### Post by warfacegod on 2010-01-31
Use your Network Summary. Type the modems IP into your address bar.

---

### Post by cariboo on 2010-02-06
Moved to Security Discussions.

I use:

```
sudo nmap -sP 192.168.1.0/24
```

to get a quick list of ip addresses in use on my network. Desktop and servers on my network all have static ip addresses, so the only addresses that will be different are the wireless computers which use DHCP.

If you are graphically incline you an install zenmap from the repositories.

---

### Post by warfacegod on 2010-02-06
For cariboos' code to work you will need to install nmap:

```
sudo apt-get install nmap
```

---

### Post by cariboo on 2010-02-06
If you enter the **command** not code, as is, Ubuntu will tell you, you have to install nmap first, and even tell you how to do it.

---

### Post by 289531.EXE on 2010-02-08
will this display hardware  attempting to go in or that  has  already gone through our wireless signal?

---

### Post by juancarlospaco on 2010-02-08
Wireshark

---

### Post by warfacegod on 2010-02-08
> **289531.EXE said:**
> will this display hardware  attempting to go in or that  has  already gone through our wireless signal?

Your network summary should show you any computers that have been "allowed".

---

### Post by 289531.EXE on 2010-02-08
to check it i have to dl nmap? Because I downloaded zenmap and it did the scan but to be honest, i couldn't understand the info.

---

### Post by warfacegod on 2010-02-08
To look at your Network Summary type the modem or routers IP address into the address bar of the internet browser you use.

---

