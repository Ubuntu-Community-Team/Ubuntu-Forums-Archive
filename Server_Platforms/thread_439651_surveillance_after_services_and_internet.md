---
title: "surveillance after services and internet"
date: 2007-05-10
forum: Server Platforms
---

### Post by queency on 2007-05-10
Hi all 

I need to have couple of shell commands or even gui surveillance program in order to watch and see :

whice running task (service or backround program) are using tcp ports and transmitting data to the internet

i know about the netstat -t but it does not give me the program that uses that port.
i know about the netstat -l and still don't understand how i can use this information
in order to understand whice program is using whice port and how much data is passed and so on

thank you all

---

### Post by H3g3m0n on 2007-05-11
You could try Ethereal (Its called Wire Shark now) which will dump the packets (GUI), but its not live and is more for debugging/reverse engineering network protocols.

EtherApe will give you a visual list of the connections your system is making and bandwidth usage in live time.

Some console programs,
tcpdump will tell you the connections things are making and with the -xX option will give you an ascii dump of whats inside the packets.

iptraf and iftop will show you bandwidth information with information such as what servers the bandwidth is going to and on what port.

Slurm gives you an overall bandwidth usage but nothing indepth.

you can also use a port scanner like nmap to port scan your self and see what ports are open, although local ports aren't necessarily accessible from an external system (depending on your router/firewall), this is just what is listening though not what is actually happening.

---

### Post by queency on 2007-05-11
thanks very much you have been most helpfull

---

