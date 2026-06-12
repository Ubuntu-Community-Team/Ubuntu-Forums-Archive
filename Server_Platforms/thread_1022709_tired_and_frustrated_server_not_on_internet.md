---
title: "tired and frustrated: server not on internet"
date: 2008-12-27
forum: Server Platforms
---

### Post by shammick on 2008-12-27
Hi, I've installed Ubuntu Desktop with LAMP, for the purpose of setting up a server for a personal website. After getting it working and accessible from the internet, I've messed something up and it's no longer accessible online. I can still access it via localhost and through the local network when I type in the ip address of the local computer on another computer in the network, but I cannot access it by typing the name of the website. My router port 80 is forwarded properly to the right static address.

I've been fiddling for hours with router settings, config and database names, but obviously I'm missing something. Have looked at the forums, but can't seem to find anything that applies to me. I'm a newbie with ubuntu/linux, so the learning curve is quite steep. Any help would be deeply appreciated. Many thanks.

---

### Post by namdung on 2008-12-27
> **shammick said:**
> Hi, I've installed Ubuntu Desktop with LAMP, for the purpose of setting up a server for a personal website. After getting it working and accessible from the internet, I've messed something up and it's no longer accessible online. I can still access it via localhost and through the local network when I type in the ip address of the local computer on another computer in the network, but I cannot access it by typing the name of the website. My router port 80 is forwarded properly to the right static address.

I've been fiddling for hours with router settings, config and database names, but obviously I'm missing something. Have looked at the forums, but can't seem to find anything that applies to me. I'm a newbie with ubuntu/linux, so the learning curve is quite steep. Any help would be deeply appreciated. Many thanks.

How is ur Server connected to the Internet?
How many NICs does ur server have? If 2 then one will have a Public IP and the other a local Private IP. If one, u may use NAT to ensure that both the local IP and the Public IP is pointing to the same PC (NIC).

Any Firewall issues? 
Are u able to ping the Public IP?
Ping the website name and see if its the Private IP or the Public IP it's resolving to.

---

### Post by volkswagner on 2008-12-27
Did you check to see if your ISP changed your ip address?

What happens when you try to access it from outside your LAN, time out, errors, what?

To access it locally with host names you will need DNS running or add host names and ip address's to the /etc/hosts files on all machines.

Does the server have a working internet connection?

Do you have a firewall running on your server?

If you have it working locally, it sounds like a router or external ip issue.

---

### Post by hrod beraht on 2008-12-27
Ping the website name and see what IP address it's resolving to. I bet you a nickel it's *not* the external IP address of your router.

Bob

---

### Post by pdtpatrick on 2008-12-27
Looks like we are all waiting for you to answer those questions ...

---

### Post by shammick on 2008-12-27
Hi all,


Thanks for the replies. ISP had indeed changed ip address on me, and the  dynamic dns service (everydns.net) I had linked the domain name to wasn't updating properly. I manually changed the ip address it was pointing to and it is now working. Thanks! :)

---

### Post by Iowan on 2008-12-27
Good news - mark this one [SOLVED] (Thread tools).

---

