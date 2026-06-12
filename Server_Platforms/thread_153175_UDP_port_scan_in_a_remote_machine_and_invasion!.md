---
title: "UDP port scan in a remote machine and invasion!"
date: 2006-03-31
forum: Server Platforms
---

### Post by ispmarin on 2006-03-31
I just got a log from a windows machine running sygate firewall, saying that one machine in my network (my router!) has done a UDP port scan, twice. The range of the ports was 5000 to 6000. I have seven machines under the router via NAT, all ubuntu. I have runned nmap and netcat, and chkrootkit, and checked all logs: just ssh (port 22) and openvpn (1194) are running, no log is tampered with, and the machines under are (in a first view) all ok. The server runs just ssh and routes everything else, and the clients under NAT runs skype, etc etc. Can be this a false positive, an error in the scan, a invaded machine (with an undetectable log), or just confusion?

---

### Post by franklee on 2006-04-03
Its confusion. Dont trust Sygate to report adequately. I often cause all sorts of false positives on my partners machine simply by nmapping our network. Ports that are closed often report traffic....its a miracle! Im blind.

---

### Post by ispmarin on 2006-04-04
Nice news... I already had searched my server thousands times for something strange, and nothing found. Damn you sygate!
But, anyway, it is still a preocupation...

---

