---
title: "How can i go back to default iptables settings in Ubuntu?I'm running Ubuntu 9.04 and"
date: 2009-08-16
forum: Security
---

### Post by judoka1113 on 2009-08-16
I'm running Ubuntu 9.04 and started messing around with my firewall, it got a little too complecated for me, so I just would like to be able to somehow restore the default iptables setting. Any idea how I can do this?   And since I installed some programs already if I do $ iptables -F won't it put my system in jeopardy since some port could have been unblocked as a result of installing some packages?

---

### Post by HermanAB on 2009-08-16
If you are not running FTP or VNC servers, then your system will be OK after iptables -F.  Since the demise of telnet, those two are the main hacking culprits.

---

### Post by dfreer on 2009-08-16
I'm pretty sure there are no default ubuntu firewall settings: or phrased differently, the default setting is blank (all traffic accepted). However, there is also no default installed programs that listen on incoming ports (excepting the loopback adapter). 

So flushing your iptables is safe as long as you didn't install any programs that listen to incoming ports. Beyond that though, why not just remove your PC from the network before doing all this, secure your firewall, then reconnect?

---

### Post by donato roque on 2009-09-03
I'm posting my question in this thread because I have a related question.  I have a regular Ubuntu 9.04 desktop (homeuser) but I have used several tools to configure iptables like firestarter and gufw.  I made a couple of rules using the gui and I also want to go back to the default state of the iptables.  Do I just delete the rules using the gui?  Is deleting the rules (using gufw) the same as 'iptables -F'?

---

### Post by automaton26 on 2009-09-03
```
sudo ufw disable
sudo ufw default deny
sudo ufw enable
sudo ufw status
```

(I think)

---

