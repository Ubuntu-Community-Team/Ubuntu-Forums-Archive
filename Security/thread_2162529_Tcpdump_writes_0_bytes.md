---
title: "Tcpdump writes 0 bytes"
date: 2013-07-14
forum: Security
---

### Post by duke.tim on 2013-07-14
At work we have setup a sniffer, on a Cent-OS machine. It seems to caputure and write pcap files fine.However if tcpdump is ran on the pcap file and set to write a new filtered pcap, it writes a 0 byte file.The thing that is strange is if tcpdump is to filter without writing the file, stdout shows up fine.```
 tcpdump -r /pcap/location port 80 
```Sucess```
 tcpdump -r /pcap/location -w /newpcap/location port 80 
```Writes a 0 byte file
and```
 tcpdump -i eth0 -w /pcap/location 
```suceeds
Any ideas on what could be wrong?

---

### Post by duke.tim on 2013-07-15
Well I managed to figure what the problem was. As it turns out, tcpdump was using the wrong permissions. Needed to use the -Z option!

---

