---
title: "strange network behavior whilst using nmap"
date: 2013-06-19
forum: Security
---

### Post by fun lovin criminal on 2013-06-19
i was scanning my external ip address with nmap and noticed during the scan the internet connectivity on my iphone which is on the network wireless really suffered, couldn't load a webpage.. but was connected to the internet.

the connection to my other 2 devices which are hardwired to my router seemed to be unaffected.

so the nmap scan itself appeared to be causing a dos on my wireless devices...

is this usual, or not possible..

scan settings were - ```
**[FONT=arial][COLOR=#2c2b2b]-sS -sU -T4 -A -v -PE -PP -PS80,443 -PA3389 -PU40125 -PY -g 53 &#8211;script[/COLOR][/FONT]**
```
[FONT=arial][COLOR=#2c2b2b]
i did get an error regarding syntax at beginning of the scan if i remember rightly, think it was the wrong type of ip address or perhaps mising a script..

has anyone ever had this happen or aware of it?

thanks..[/COLOR][/FONT]

---

### Post by duke.tim on 2013-06-19
It is possible that your router is dropping packets due to it's ram being filled.

If the Nmap is running on wireless it is probably collisions in the wifi signal.

---

### Post by fun lovin criminal on 2013-06-20
right, nmap wasn't wireless.. but i see what you mean.. my router was probably low on resources from running the scan as opposed to actually being scanned?

this makes sense now... thanks duke.tim.

---

### Post by SeijiSensei on 2013-06-20
Doing a "stealth" scan with -sS creates a huge amount of traffic.  Nmap will try each port multiple times with a variety of source addresses.  What happens if you simply run 

```
sudo nmap -sT ip.of.your.router
```

That runs a simple TCP scan of most commonly used ports.

---

### Post by fun lovin criminal on 2013-06-23
thanks..results are filtered, i tried several different scan types.. mainly just to play with nmap and test my security too..

---

