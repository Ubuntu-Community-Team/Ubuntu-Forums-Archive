---
title: "hack wireless"
date: 2006-02-07
forum: Server Platforms
---

### Post by bionnaki on 2006-02-07
hello. I have a wireless network (linksys router + ubuntu) and I would like to see if I can hack into my wireless network from another computer running ubuntu. my friend has a laptop across the hall in his apartment with ubuntu on it - how would we go about hacking my network? what is the exact process?

I've heard of a ubuntu based live distro with all of the necessary security tools on it that is available. I believe this is it: [http://nubuntu.org](http://nubuntu.org) - will this have everything I need?

here is a list of what it has installed:

Aircrack 
Airsnort 
Bluesnarfer 
DSniff 
EtherApe 
Ethereal 
Ettercap 
ExploitTree 
FragRouter 
Honeyd 
IISEmulator 
John the Ripper 
Kismet 
Metasploit 
Nemesis 
Nessus 
Nikto 
NMap 
Samdump2 
SSLDump 
VNCrack 
Void11 
Some of main packages:

Aterm 
Firefox 
Fluxbox 
Gaim 
gFTP 
XChat

---

### Post by imagine on 2006-02-07
If you're searching some short tutorials: [http://iwhax.net/index.php/Tutorials](http://iwhax.net/index.php/Tutorials)
Of course you cannot learn everything about WEP/WPA cracking in five minutes, but it is a start.

---

### Post by ice60 on 2006-02-07
it depends how you have it setup, why don't you just secure it instead of trying to crack it? wpa and a strong password is a good place to start.

---

### Post by bionnaki on 2006-02-08
[QUOTE=imagine]If you're searching some short tutorials: [http://iwhax.net/index.php/Tutorials](http://iwhax.net/index.php/Tutorials)
Of course you cannot learn everything about WEP/WPA cracking in five minutes, but it is a start.[/QUOTE]

thanks!

---

### Post by bionnaki on 2006-02-08
[QUOTE=ice60]it depends how you have it setup, why don't you just secure it instead of trying to crack it? wpa and a strong password is a good place to start.[/QUOTE]

the point is I'd like to see *how* strong my security is- it's just an experiment.

---

### Post by yanik on 2006-02-09
There is everything you need in the knoppix std livecd: [http://www.knoppix-std.org/](http://www.knoppix-std.org/)

I remember there was a how-to in one the 'The Broken' show: [http://thebroken.org/](http://thebroken.org/)

---

### Post by lexor on 2006-02-12
The only bad thing is that so little wireless cards/adapters are supported at the moment that Kismet and others will run from a live cd.

If you have one that will run then its always a good idea to have a crack at your own network. I'll be checking it out myself with my own w/l cards, after I download the iso's.

---

### Post by godskill on 2006-11-18
Another great live distro for this time of fun is backtrack [http://www.remote-exploit.org/index.php/BackTrack](http://www.remote-exploit.org/index.php/BackTrack)

---

### Post by tturrisi on 2006-11-19
> **bionnaki said:**
> the point is I'd like to see *how* strong my security is- it's just an experiment.
post your wan ip address

---

### Post by fakie_flip on 2007-02-17
> **godskill said:**
> Another great live distro for this time of fun is backtrack [http://www.remote-exploit.org/index.php/BackTrack](http://www.remote-exploit.org/index.php/BackTrack)

I tried Backtrack, but I didn't really know how to use it. I tried many things, but nothing seemed to work. What were you able to do with it?

Now I am trying to sniff traffic on my network from another computer, but it's not working. Can you help? 

dsniff doesn't seem to be doing anything. I even tried Wireshark, but what good is the packet information it shows if it is all in hex code? What does all that packet information mean, and what good is it to know? This is what I have tried.

Is this correct? The default gateway (the router) of the network is 192.168.1.1, and the computer that I want to sniff packets of on my home network is 192.168.1.100. 

```
sudo arpspoof -i eth0 -t 192.168.1.100 192.168.1.1
0:14:2a:bd:89:a2 0:a:48:12:f9:17 0806 42: arp reply 192.168.1.1 is-at 0:14:2a:bd:89:a2
0:14:2a:bd:89:a2 0:a:48:12:f9:17 0806 42: arp reply 192.168.1.1 is-at 0:14:2a:bd:89:a2
0:14:2a:bd:89:a2 0:a:48:12:f9:17 0806 42: arp reply 192.168.1.1 is-at 0:14:2a:bd:89:a2
0:14:2a:bd:89:a2 0:a:48:12:f9:17 0806 42: arp reply 192.168.1.1 is-at 0:14:2a:bd:89:a2
0:14:2a:bd:89:a2 0:a:48:12:f9:17 0806 42: arp reply 192.168.1.1 is-at 0:14:2a:bd:89:a2
... keeps going
```

While letting that run, shouldn't I be able to see some packets that were supposed to go to the 192.168.1.100 computer or packets being sent from it? I run these commands, but they aren't outputting anything.

```
sudo webspy -i eth0 192.168.1.100
Password:
webspy: listening on eth0
```

```
sudo urlsnarf -i eth0
Password:
urlsnarf: listening on eth0 [tcp port 80 or port 8080 or port 3128]
```

```
sudo dsniff -i eth0 
Password:
dsniff: listening on eth0
```

I tried Wireshark too and it showed some packets, but it is all in hex code and strange symbols, so what good is it?

---

### Post by sent17inel on 2008-05-15
are you using a wireshark that has a gui? if so you can just select the packet you want to investigate and a panel on the left will decode the hex for you. Its useful for reading things that arent encrypted when they are sent out. for example instant messages sent out over msn yahoo aim and myspace messenger arent encrypted. So you might also want to take a look at etherape. if someone logs onto your home network there ip will appear in etherape and you will be able to filter the packets in wireshark to look for that persons computer. and in doing so you can search through his packets and read his instant messaging conversations. thats the best i've been able to do so far. Im still a newb.  Any other helpful fun ideas guys? i know i got a little off topic here but i kant resist ranting about the cool possibilities of linux/ubuntu.

---

