---
title: "Connecting to an Ubuntu server"
date: 2010-11-09
forum: Server Platforms
---

### Post by petersull on 2010-11-09
Hi, I am new to Ubuntu and not well versed in setting up devices, so looking for some clues.

I have a laptop with Ubuntu 10.10 and have been given a secondhand server device with Ubuntu 10.10 Server installed. I want to use device this for extra storage. The server is just a box about one third the height of a desktop pc case with a cd drive and hard disk but without a monitor or keyboard. It has all the usual sockets but no connections other than the mains lead.

I have the server, laptop and router all in the same room so the wifi signal should be at max strength. The server has been previously set up (by others) to work with my router/laptop ip addresses (provided by me), but until now the setup has not been tested. 

The server is switched on, and on the laptop I type into terminal 

'ssh adminuser@192.168.1.253'

(as per the instructions I have with the server device) and then I expect to be asked for a password which I have also been given. After the ssh command it says

'port 22: No route to host'

I have searched the various forums, and Youtube tutorials etc. but cannot find anything directly relating to my specific problem area.

Can someone please give me an idea how to progress further with this and gain access to the device?

Thanks in advance.

---

### Post by Fafler on 2010-11-09
The two devices aren't on the same subnet. This means that even though they are connected to the same physical network, they can't speak to each other. There are several solutions to this. One could be to change the IP of the server to match you network, but you can't really do that without a keyboard and a monitor connected. Another is to reconfigure the rest of your network to use the same subnet as the server. You probably have a DHCP server in your router, so you should consult your router manual as how to do that.

---

### Post by iponeverything on 2010-11-09
make sure the server is still at 192.168.1.253. 


install nmap and scan your network listening ssh servers.

```
sudo apt-get install nmap

sudo nmap -sV -p 22 192.168.1.253/24
```

---

### Post by petersull on 2010-11-09
Thanks iponeverything,

I installed nmap but it came up with 'host is down'

I also installed knmap thinking the GUI might be easier for me, but I'm still not sure what I am doing.

Is there a way to do a general scan to try and locate it and/or get any further info, assuming the device is actually working and capable of transmitting/receiving some signal? Perhaps I have not got the correct address.

Any ideas that I may be able to try (with my limited abilities), or do I need to get an expert in to sort it hands-on?

Best regards.

---

### Post by iponeverything on 2010-11-09
post the output of:

```
route -n
```

---

### Post by petersull on 2010-11-09
Here is the output of 'route -n'

route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     2      0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 wlan0

Regards,

Pete.

---

### Post by iponeverything on 2010-11-09
you should not have gotten "host is down" -- it should have just not shown up. did you scan the /24? The point is that we are looking for other ip's on your subnet where it might be hiding.

 by doing the "nmap -sV -p 22 192.168.1.155/24" we will scan every host on your subnet for a ssh server listening on port 22. Machines that are down will not show up in the scan results.

---

### Post by petersull on 2010-11-10
Thanks for all your help and suggestions.

I think I will have to spend some money and get someone in to sort it hands-on.

---

