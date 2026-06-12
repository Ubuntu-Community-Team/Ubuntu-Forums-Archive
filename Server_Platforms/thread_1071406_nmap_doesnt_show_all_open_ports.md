---
title: "nmap doesnt show all open ports"
date: 2009-02-16
forum: Server Platforms
---

### Post by sipickles on 2009-02-16
Hello,

I am a beginner with nmap and am trying to use it to show whether a port is open on my server. The port I have opened on server (and forwarded on router) is 2455.

```
simon@urth-webserver:~/test$ sudo nmap -PO my.ip.address

Starting Nmap 4.53 ( http://insecure.org ) at 2009-02-16 10:23 GMT
Interesting ports on xxx.xxx.xxx.xxx:
Not shown: 1709 filtered ports
PORT     STATE  SERVICE
21/tcp   open   ftp
22/tcp   open   ssh
502/tcp  open   asa-appl-proto
5000/tcp closed UPnP
5060/tcp closed sip

Nmap done: 1 IP address (1 host up) scanned in 20.249 seconds
```

2455 is not there, but testing the port at [http://ping.eu/](http://ping.eu/) shows it is open.

How come nmap doesnt show it?

Thanks

Simon

---

### Post by brian_p on 2009-02-16
> **sipickles said:**
> 

How come nmap doesnt show it?

A port is open only if there is a service listening on it. What service do you have listening on port 2455?

---

### Post by sipickles on 2009-02-16
Its a Wago Industrial Control PLC, using Ethernet/TCP driver. Its connected to our network, and the router is sending external traffic on port 2455 to it.

We will use modbus to access it anyway (port 502), port 2455 is just for programming.

The modbus port shows as open!

---

### Post by brian_p on 2009-02-16
> **sipickles said:**
> Its a Wago Industrial Control PLC, using Ethernet/TCP driver. Its connected to our network, and the router is sending external traffic on port 2455 to it.

We will use modbus to access it anyway (port 502), port 2455 is just for programming.

The modbus port shows as open!

Could the UDP protocol be being used? The -sU switch in nmap.

---

### Post by Phlee on 2009-02-16
Just a thought, you don't have any firewalls running by chance eh?

---

