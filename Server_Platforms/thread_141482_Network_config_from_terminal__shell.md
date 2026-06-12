---
title: "Network config from terminal / shell"
date: 2006-03-08
forum: Server Platforms
---

### Post by jjenkov on 2006-03-08
Can anyone tell me how I can configure the IP address etc. for an Ubuntu server from the shell, with a command? I have tried "netsetup" but it doesn't exist.

All I can find is information on how to use the gui tool... which doesn't exist on ubuntu servers. 

Any help is greatly appreciated!

---

### Post by jjenkov on 2006-03-08
Sorry, wrong forum... messy forum site indeed!

Can anyone tell me where I can find the HOWTO forums where I am supposed to post this question? I sure can't find it, and I have spent half an hour looking now. It s...s

---

### Post by gmclachl on 2006-03-08
Not sure what you mean, but you could look at 
  /etc/netowrk/interfaces 

 George

---

### Post by jjenkov on 2006-03-08
What I need to do is to configure the IP address of the server. For some reason the server uses DHCP, and I don't want that. Even if I do want the server to obtain an IP via DHCP, how do I see what IP the server has been given? And how to I set a static IP if I want to ? I am used to Red Hat's very easy netsetup command. What does Ubuntu have that matches it?

---

### Post by jjenkov on 2006-03-08
Oh, and I want to do all that from a shell. Not from the GUI, which I don't think the ubuntu server has installed.

---

### Post by tukuyomi on 2006-03-08
> DHCP, how do I see what IP the server has been given?
```
ifconfig
```

> And how to I set a static IP if I want to?
```
sudo nano /etc/network/interfaces
```
Then edit the file as this
```
# The primary network interface
iface eth0 inet static     <- eth0: replace with the name of your interface (given by ifconfig), static instead of dhcp
	address 192.168.0.1     <- the IP address you want
	netmask 255.255.255.0     <- Subnet mask
	gateway 192.168.0.254     <- Gateway address
auto eth0
```

---

