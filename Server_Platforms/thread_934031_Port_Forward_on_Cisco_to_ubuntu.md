---
title: "Port Forward on Cisco to ubuntu"
date: 2008-09-30
forum: Server Platforms
---

### Post by maidei on 2008-09-30
What will be the commands to port forward on cisco router..
So that the outside world can access server....
I have added these two commands into my router

ip nat inside source static udp 192.168.1.10 53 192.168.5.5 53
ip nat inside source static tcp 192.168.1.10  80  192.168.5.5 80

And still cant access the sites from the internet

Here is my set up

..........................Internet
............................"
..........................."wan ip address
............................" 
............................ADSL modem
............................"192.168.1.1
........................"(static ,no dhcp from adsl to firewal)
.........................."192.168.1.10
...........................Firewall Machine(with 2 NIC)
.........................."192.168.5.5
............................."..................................................."
............................."...................................................."
.....................192.168.5.6 (Server)(static ip address)

---

