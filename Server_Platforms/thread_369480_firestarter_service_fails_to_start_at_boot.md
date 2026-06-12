---
title: "firestarter service fails to start at boot"
date: 2007-02-24
forum: Server Platforms
---

### Post by kevinlyfellow on 2007-02-24
When I boot my computer, firestarter does not start (I'm only talking about the service, not the gui).  I can easily get it to start (sudo /etc/init.d/firestarter start) but for whatever reason it does not want to do this when I boot.  I have used the program sysv-rc-conf to check to see if it is marked to start up and it is checked off at runlevel 2,3,4,5 (admittedly I do not know much about starting services).  Any suggestions?

---

### Post by r4ik on 2007-02-24
Try,

[http://www.fs-security.com/docs/faq.php](http://www.fs-security.com/docs/faq.php)

Good luck !

---

### Post by johnc4510 on 2007-02-24
The firewall in Ubuntu is installed by default. It is called iptables. Firestarter is a GUI frontend to make it easier to configure your iptables firewall. If you want to check to make sure iptables is installed, type this in a terminal: whereis iptables   If it shows you a path to a file, it is installed. If you type: dmesg iptables    in a terminal it should spit out all kinds of info showing that the firewall is working.

---

### Post by kevinlyfellow on 2007-02-24
> **johnc4510 said:**
> The firewall in Ubuntu is installed by default. It is called iptables. Firestarter is a GUI frontend to make it easier to configure your iptables firewall. If you want to check to make sure iptables is installed, type this in a terminal: whereis iptables   If it shows you a path to a file, it is installed. If you type: dmesg iptables    in a terminal it should spit out all kinds of info showing that the firewall is working.

I know firestarter has a gui, but it starts up the firewall using /etc/init.d/firestarter  This is the firestarter I am reffering to.  My issue is that the service /etc/init.d/firestarter is not starting when I boot up.  I do not care about the gui.  I know that I have iptables installed since firestarter does work. 

Does anyone know a way that I can check to see if firestarter is attempting to start?  Where can I look (beyond sysv-rc-conf) to check to see if it is set up properly to start during boot?

Precisely, after I boot
```
sudo /etc/init.d/firestarter status
 * Firestarter is stopped 
```

---

### Post by kevinlyfellow on 2007-02-24
I've tried removing and adding in the service again (using update-rc.d) but to no effect.

---

### Post by kevinlyfellow on 2007-02-24
after looking around I checked the startup script and led me to realize that it will not start up unless I've been assigned an address. Since I'm using a laptop, it naturally wouldn't start up until after I connect to my wireless network.  Any help on running firestarter on a laptop?

---

### Post by chggr on 2007-02-25
Try launching the firestarter GUI, click on "Preferences" -> "Firewall" -> Start/restart firewall on dial out.

If you check this option, firestarter service will start every time you connect to the internet.

---

### Post by kevinlyfellow on 2007-02-26
That didn't seem to work :-(  sigh... is there a good tutorial that anyone knows about on how to configure iptables?

---

### Post by _Draco on 2007-03-03
I'm using also a laptop and the way I solved it (or worked it around) was enabling the option "start on dial-out" in the wizard (even though I have cable shared from my wireless).  The firewall still fails to load on boot but as soon as you get an IP from your wireless connection firestarter starts automatically.  Hope that works for you, it did for me.

---

### Post by kevinlyfellow on 2007-03-03
yeah i tried that and it didn't seem to work out at first, but then recently it seems to be... i'm a little confused by how it didn't work until a a few reboots later, but I'm just starting to experiment with it again...

---

