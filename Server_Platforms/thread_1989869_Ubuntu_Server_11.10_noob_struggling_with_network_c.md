---
title: "Ubuntu Server 11.10 noob struggling with network connectivity"
date: 2012-05-28
forum: Server Platforms
---

### Post by theM4dM4n on 2012-05-28
Hello everybody!

As the title says, I'm new to Ubuntu Server (and in fact only vaguely familiar with Ubuntu) and I am having difficulty connecting to my router. Unfortunately, I am running the server on a different PC than this one, so screen shots are not an option, but I will try my best to give as much information as possible.

After getting US11.10 installed I plugged the tower into my router via cat5. I then added eth0 to /etc/network/interfaces with all the appropriate information - static IP address, gateway, network, and netmask.

I then proceeded to check my network connection by attempting to ping the router.  I get DESTINATION HOST UNREACHABLE over and and over until I ctrl+c to stop. However, when I try to ping the local host (127.0.0.1) every packet is received.

When I check ifconfig everything looks correct, and I am getting no error messages. Hostname for the server is correct too.

I'm really at a loss and any advice or suggestions would be greatly appreciated!

Thanks!

---

### Post by chexun on 2012-05-28
Hi. use 'netstat -rn' to display its routing table. post the output here.

---

### Post by theM4dM4n on 2012-05-28
> **chexun said:**
> Hi. use 'netstat -rn' to display its routing table. post the output here.

Kernal IP routing table
Destination      Gateway            Genmask         Flags       MSS  Window      irtt  Iface
0.0.0.0             192.168.1.1       0.0.0.0             UG               0   0                  0  eth0
192.168.1.0     0.0.0.0               255.255.255.0 U                 0    0                  0 eth0

Sorry its not lined up well, had to type it out since I'm using two different systems.

---

### Post by spynappels on 2012-05-29
Are you trying to ping the router by hostname or by IP address?

Pings to the loopback interface are fine so the TCP stack is fine. If you cannot ping the router by name, check DNS, if you cannot ping by IP address first thing to try is a new cable and/or a different port on the router.

---

### Post by theM4dM4n on 2012-05-29
> **spynappels said:**
> Are you trying to ping the router by hostname or by IP address?

Pings to the loopback interface are fine so the TCP stack is fine. If you cannot ping the router by name, check DNS, if you cannot ping by IP address first thing to try is a new cable and/or a different port on the router.


I'm trying to ping by IP address. I've already tried switching ports on the router and using a different cable. I even plugged my Windows 7 laptop into the router through the same cord just to double check and it works fine on all the ports as well. :(

---

### Post by kennethconn on 2012-05-30
Check your settings again.
What is the IP address of the server and what is the IP address of the router. Ping the server by IP address (not 127.0.0.1) then the router.
Have you a crossover cable that you can connect directly between Windows 7 and server?
 
Use ping -c 4 xxx.xxx.xxx.xxx for the typical Windows command line ping.

---

### Post by theM4dM4n on 2012-06-09
> **kennethconn said:**
> Check your settings again.
What is the IP address of the server and what is the IP address of the router. Ping the server by IP address (not 127.0.0.1) then the router.
Have you a crossover cable that you can connect directly between Windows 7 and server?
 
Use ping -c 4 xxx.xxx.xxx.xxx for the typical Windows command line ping.

server IP is 192.168.1.205. I do have a crossover cable. Never tried to access the internet via another computer. I will try some of these and let you know what happens!

---

### Post by darkod on 2012-06-09
Double check the configuration of /etc/network/interfaces again. You don't have to enter 'network', it works without it, and sometimes you can make a typo in it.

Keep it simple at start, only:
address
netmask
gateway
dns-nameservers (optional)

Which editor are you using? Since you are not used to ubuntu server, maybe you are not editing the file correctly. I prefer nano since it's easy to use (at least to me).

In any case, make sure the content of the file /etc/network/interfaces is what you expect it to be.

---

### Post by theM4dM4n on 2012-06-27
I am using the vi editor. Or Vim I guess. When I type vi [filename] it seems to know what I'm asking for. ;)

> **darkod said:**
> Double check the configuration of /etc/network/interfaces again. You don't have to enter 'network', it works without it, and sometimes you can make a typo in it.

Keep it simple at start, only:
address
netmask
gateway
dns-nameservers (optional)

Which editor are you using? Since you are not used to ubuntu server, maybe you are not editing the file correctly. I prefer nano since it's easy to use (at least to me).

In any case, make sure the content of the file /etc/network/interfaces is what you expect it to be.

---

### Post by Groodles on 2012-06-27
Could you post the output of:

```
cat /etc/network/interfaces
```

Also I'm guessing that because you said you're using "server" that you have no GUI installed?  (hence no network-manager getting into the mix).

---

### Post by darkod on 2012-06-27
> **theM4dM4n said:**
> I am using the vi editor. Or Vim I guess. When I type vi [filename] it seems to know what I'm asking for. ;)

I have no idea what you mean by that. So, is the problem solved or not?

I mentioned the editor because the problem is not displaying the file, the problem is whether it will be edited correctly and the changes saved. If you exit the editor without the changes being saved, you haven't done anything, right?

I remember vi being little bit confusing when I first used it, so since I've been using nano and personally I find it much easier.

If you prefer vi, no problem, just make sure the changes are edited correctly and saved.

---

### Post by mschersten on 2012-06-27
Can you try it, for now at least, with dhcp?  You might need a static ip later, but at least getting it to work dynamically will be a start.  For this, etc/network/interfaces can just read

```
auto eth0
iface eth0 inet dhcp
```

Here's a tip: don't just go into your file with vi and delete everything and replace it with that.  Rename the file first, then put those lines into another file, like

```
cd /etc/network
sudo mv interfaces static
sudo vi interfaces
```

Also, just changing the file does nothing.  It's only read when the network service starts.  So, after you change the file, you should just be able to do

```
sudo service networking restart
```

although I seem to remember problems with this in some releases, so you might have to do

```
sudo service networking stop
sudo service networking start
```

or

```
sudo /etc/init.d/networking restart
```

Worst case scenario, reinstall with the box connected to the router, and let the installation disk try to set up dhcp.  This is a drastic, heavy-handed route, but if you've tried everything and just want to get past this hurdle, it's worth a shot.  Since the server isn't even networked yet, you probably don't have anything worth saving, unless you've been keeping a diary in vi :)  Don't do that yet, though.

---

