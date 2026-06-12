---
title: "Cannot connect to Ubuntu server from any computer in my work group"
date: 2013-02-01
forum: Server Platforms
---

### Post by msk31 on 2013-02-01
Hi everyone! I am a new member in the Ubuntu forums, and I have a problem that I have no clue how to solve. From what I know, the server is a Linux environment (Ubuntu). It was working fine until a power outage, and now none of the computers in my work group can connect to the server at all, or if it does, it is disconnected in a few minutes. I asked my co-workers if the IP address changed after the power outage, but they did not know. I tried pinging any of the computer's from the server and it said Destination Host Unreachable. Most of the computers are Macs, but some are just PCs. On a Mac, I went to Go -> Connect to Server, and then I typed in the IP address that appeared from the server when I typed in the command, ifconfig. It would then say Connection Failed: Server may not exist or it is not operational at this time. Check the server name or IP address and try again.

I really need help with this! Thank you so much!

---

### Post by dannyboy79 on 2013-02-01
are you in direct control of the server? have you attempted to restart the server properly, it's possible it auto-restarted but didn't restart some of it's services? 

Is there a firewall issue? Did some network switch get unplugged or power go out and not restored? Does your server have a vaild IP? Before the power outage were you able to ping the client machines before? 

When you say clients can't connect, what services are they trying to connect to? FTP, SMB, Webserver, or what? We can't help troubleshoot if we don't know in what way these Mac's and WIndows PCs interact with the server.

We need to really start at the very beginning of troubleshooting and make sure your server has a vaild IP address and can first at least ping other machines on the network

---

### Post by msk31 on 2013-02-01
I tried pinging to the router first and it could not reach it. On the Ubuntu server, I typed in sudo ping 192.168.1.254, and it said Destination Host Unreachable. Here are the settings of the Ubuntu server:

IP address: 192.168.1.250
Subnet mask: 255.255.255.0
Broadcast address: 192.168.1.255
Gateway and DNS-nameserver: 192.168.1.254

Before the power outage, the clients were able to connect to the server. I am not really sure what type of server it is, but the server is just used to store files that they do not use anymore, but want to archive them.

I hope that this helps a bit!

---

### Post by Neo@Matrix on 2013-02-01
> **msk31 said:**
> 
IP address: 192.168.1.250
Subnet mask: 255.255.255.0
Broadcast address: 192.168.1.255
Gateway and DNS-nameserver: 192.168.1.254


Hello :) 

On networks like 192.168.1.x  the router is usually on 192.168.1.1
U should try to log in on routers http interface and see the ARP list and address reservation. If ur network used static IP adresses for addressing boxes , might the power failure changed some settings and DHCP changed the IP address of the server or some other box on the network, and ended up with duplicated IP or just simple no network  on server.

I'd try 
 ```
sudo reboot now
```
and see if it fix the network config issues.

---

### Post by msk31 on 2013-02-01
On the Mac, I went into System Preferences and to Network, and that is how I find out what the router's IP address is. I did the reboot, but it did not fix anything. This power outage happened a while ago when I was not working in this workplace. I do not think that I can change the router's IP address. The router seems to be working just fine since I can connect to the Internet on the Mac. I just can't get the computer or any other computer to connect to the server. The server has a Linux operating system on it (Ubuntu 12.04 LTS). When I try pinging it to the router and to the Mac, they both fail. I just want the computers at my workplace to be able to connect to this server, so that files that are not in use anymore can be stored in the server.

---

### Post by zealibib slaughter on 2013-02-01
have you tried to ping an outside ip from the server?  that is I am assuming that the server is configured to have access to the internet and not just local.

---

### Post by msk31 on 2013-02-01
I have tried pinging the router and a Mac from the server, and it cannot reach both of them. I do not want the server to access the internet. The server is just used to store files that are not in use, but needs to be archived.

---

### Post by zealibib slaughter on 2013-02-01
You can try to bring the interface down then bring it back up and watch for errors

```
sudo ifdown eth0
sudo ifup -v eth0

or 
sudo ifup --verbose --all
```

---

### Post by msk31 on 2013-02-01
When I typed in those two commands, I did not see any errors. It brought up the interface just fine. Is it possible that after the power outage, the IP address of the server changed? I kept wondering about that, and my co-workers do not know what was the IP address of the server before the power outage.

---

### Post by zealibib slaughter on 2013-02-01
thats possible but the router and server really needs to have a static config.  ifconfig will give you the current ip address.  if the ip has changed then your problem may be with the router and port forwarding.  also while i am thinking about it issue a sudo ufw status command to examine your firewall rules.  ive had problems like this over the firewall

---

### Post by msk31 on 2013-02-01
I have issued the ifconfig command a lot, and the IP address is the same as the post above where I have posted it. I also issued sudo ufw status as you suggested, and it said status: inactive. Also, I am not sure if the ip changed from before to after the power outage, because no one knew the IP address of the server before the incident. What would other suggestions be to have computers that need to access the server to connect to it? Can it be a hardware issue even though the server is connected to a surge protector?

---

### Post by dannyboy79 on 2013-02-01
issue
```
ifconfig
```
in a terminal window to find out the server's IP address

it really bothers me that you can't even ping the router from the server. I'd bet you want your server to always have the same IP, so do you use MAC address IP reservation within your router or did you setup a static IP within your network manager within the server?
Not being able to ping the router almost leads me to believe that your network card isn't working or that you aren't receiving an IP address the DHCP server (which I will assume is your router)

---

### Post by zealibib slaughter on 2013-02-01
it bothers me too that you cant ping. its possible that a port has gone bad on the router.  what brand router is it?

you can try to switch ports for the server on the router or even rebooting the router.  you really need to access the routers setup page and view the connected clients and port forwarding for the server.

---

### Post by msk31 on 2013-02-01
I issued the ifconfig command many times and I posted the server's IP address above in one of the previous posts. I do want the server to always have the same IP. I do not know how it was setup before, but if I did, I would have typed in this command: ifconfig eth0 192.168.1.250 netmask 255.255.255.0 broadcast 192.168.1.255. I do not know what else to do. I do not even know if all the subnetting is correct.

---

### Post by zealibib slaughter on 2013-02-01
```
cat /etc/network/interfaces
```

should print out the configuration for your interfaces

---

### Post by msk31 on 2013-02-01
> **msk31 said:**
> I tried pinging to the router first and it could not reach it. On the Ubuntu server, I typed in sudo ping 192.168.1.254, and it said Destination Host Unreachable. Here are the settings of the Ubuntu server:

IP address: 192.168.1.250
Subnet mask: 255.255.255.0
Broadcast address: 192.168.1.255
Gateway and DNS-nameserver: 192.168.1.254

Before the power outage, the clients were able to connect to the server. I am not really sure what type of server it is, but the server is just used to store files that they do not use anymore, but want to archive them.

I hope that this helps a bit!

That is what I posted before, and that was when I initiated vi /etc/network/interfaces.

---

### Post by msk31 on 2013-02-01
Also, when I pinged the router from the Mac, it was successful

---

### Post by zealibib slaughter on 2013-02-01
then it should be a static ip. I believe you may have a hardware problem. try switching ports.

---

### Post by dannyboy79 on 2013-02-01
IP address: 192.168.1.250
Subnet mask: 255.255.255.0
Broadcast address: 192.168.1.255
Gateway and DNS-nameserver: 192.168.1.254

is NOT the correct formating for the interfaces file. I need you to post the entire file contents from /etc/network/interfaces
also, this may sound silly but does the server have more then 1 network interface? also, is there an ethernet cable going from the servers NIC to the router? 

You really need to be able to view the settings of your router, which router are you using? Most times it's easily managable by entering it's IP address and you can edit setting using it's built in web-server configuration pages.

try to enter the following within your browser on your Mac
```
192.168.1.254
```
then it should prompt you for a username and password

---

### Post by msk31 on 2013-02-01
I have fixed the problem. I was stupid and didn't check that the ethernet cable connected from the server to the router was bad and the port light on the router was not on. It was a bad ethernet cable. Thank you so much zealibib!!!

---

### Post by Neo@Matrix on 2013-02-02
Glad U find solution to the problem. Funny that we all focused on 
- problem started with power drop part, and never gave second chance to utp cable :)
On the other hand, I think that it has zero to none chance  that power failure messed ur UTP cable :D

---

