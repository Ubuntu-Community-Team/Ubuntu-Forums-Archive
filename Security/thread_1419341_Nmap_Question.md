---
title: "Nmap Question"
date: 2010-03-01
forum: Security
---

### Post by bbourdet on 2010-03-01
Hello -

Should be an easy answer. I just want to know the command to scan the current network I am on to find out what ports are open. How do I tell it to scan for what ports are open, and what other ip addresses or mac addresses are currently on.

Thanks!

Tarken

---

### Post by uRock on 2010-03-01
I don't know the exact commands but Ubuntu offers a GUI in the repos called Zenmap that I use often. You can also run ```
man nmap
``` to get all of the commands for the program. Zenmap is in Synaptic or you can add it with ```
sudo apt-get install zenmap
```

---

### Post by bodhi.zazen on 2010-03-01
You can use zenmap if you want a gui and the nmap on line tutorial is fantastic =)

```
nmap 192.168.0.0/24
```

---

### Post by rookcifer on 2010-03-02
For any given IP address try:

```
sudo nmap -PN -sT -A -p- -v <ip address>
```

To find machines, use bodhi's command.

---

