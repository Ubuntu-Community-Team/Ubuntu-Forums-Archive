---
title: "Telnet on a machine that I did not install it on"
date: 2012-01-21
forum: Security
---

### Post by mrhobbeys on 2012-01-21
One of the machines in my network has a telnet service running. I would like to figure out why/how it got there and who is using it for what.

I was thinking the best way would be to log in but I am embarrassed to say I am not entirely sure which machine it is, although I think it would be 1 of 2 machines that were used and could have had stuff already on them.

All I have for now is the ip address, like I said I could log into each machine and check the ip, but then I would have no clue what to do after that point. These are windows machines but I want to use my Ubuntu to try and connect to the telnet and trying to figure that out has not gone smoothly so far.

---

### Post by CharlesA on 2012-01-21
You have one Windows machine that has telnet running for some unknown reason and you know the IP of that machine but not which machine it is? Is this at a home or work environment?

---

### Post by Dangertux on 2012-01-21
> **mrhobbeys said:**
> One of the machines in my network has a telnet service running. I would like to figure out why/how it got there and who is using it for what.

I was thinking the best way would be to log in but I am embarrassed to say I am not entirely sure which machine it is, although I think it would be 1 of 2 machines that were used and could have had stuff already on them.

All I have for now is the ip address, like I said I could log into each machine and check the ip, but then I would have no clue what to do after that point. These are windows machines but I want to use my Ubuntu to try and connect to the telnet and trying to figure that out has not gone smoothly so far.

I bet it's your router ;-)

---

### Post by emiller12345 on 2012-01-22
you could try arp pinging the ip that has the telnet service running, like 
```
$ arping -c 1 -I eth0 192.168.1.100
```or what ever the ip is, as long as it's on your lan.
then you might get a clue by looking up the first three bytes of the MAC address here:
[http://standards.ieee.org/develop/regauth/oui/oui.txt](http://standards.ieee.org/develop/regauth/oui/oui.txt)
The manufacture may tell you something (like your router:)

---

