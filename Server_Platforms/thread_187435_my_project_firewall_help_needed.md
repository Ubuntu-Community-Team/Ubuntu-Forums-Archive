---
title: "my project firewall help needed"
date: 2006-06-03
forum: Server Platforms
---

### Post by mrweirdo on 2006-06-03
I recently picked up a dell poweredge server and installed ubuntu server dapper on it. 
I plan on doing the following with it:
- run apache
- run proftpd
- share internet conection for lan via nat
- provide DNS(bind9) for lan
- provide DHCP for lan

Basicly before this I had two seperate boxes doing the same functions. One ran ipcop which was my networks router to the outside world and the other was the server runing ubuntu. I'm looking to combine the two into one box. I have installed webmin along with OpenSSH for management purposes. The trouble I am having is how to setup the firewall. Other then that everything else works. I have two nics eth0 goes to the cable modem assigned dynamicly a public ip while eth1 is a static ip(192.168.1.1). 

I so far have managed to get nat working using the following script.
```
#!/bin/bash
IPTABLES='/sbin/iptables'

# Set interface values
EXTIF='eth0'
INTIF1='eth1'

# enable ip forwarding in the kernel
/bin/echo 1 > /proc/sys/net/ipv4/ip_forward
                                                                               
# flush rules and delete chains
$IPTABLES -F
$IPTABLES -X
                                                                               
# enable masquerading to allow LAN internet access
$IPTABLES -t nat -A POSTROUTING -o $EXTIF -j MASQUERADE
                                                                               
# forward LAN traffic from $INTIF1 to Internet interface $EXTIF
$IPTABLES -A FORWARD -i $INTIF1 -o $EXTIF -m state --state NEW,ESTABLISHED -j ACCEPT
```

Now I need to figure out the rest. I'm looking to steal all the ports coming in from the internet or public network like ipcop did. Also protect myself from portscans, dos attacks. Probably will leave ping availible for my public ip like it is now with ipcop because on occasion I like to ping my ip when I'm away from home to test the conection but it will need to be so in a way that its not accessible to attacks. I have gone through much reading about iptables. Any ideas on how to complete the rest of the firewall? Preferably I could finish the rest of it in Webmins Linux Firewall module under networking.

---

### Post by mrweirdo on 2006-06-03
hrm well Im stupid part of my trouble was because I was runing both networks through the same old ethernet hub only seperated virtualy by different subnets and it was causing all kinds of network issues. So now I think I got it down after lots of google searching and iptables reasearch involved.

---

### Post by cyracks on 2006-06-04
The best place to start is 
[http://iptables-tutorial.frozentux.net/iptables-tutorial.html](http://iptables-tutorial.frozentux.net/iptables-tutorial.html)

or you could use a gui like fwbuilder
[http://www.fwbuilder.org/](http://www.fwbuilder.org/)

---

