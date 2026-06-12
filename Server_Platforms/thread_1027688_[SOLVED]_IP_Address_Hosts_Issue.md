---
title: "[SOLVED] IP Address Hosts Issue"
date: 2009-01-01
forum: Server Platforms
---

### Post by dlader on 2009-01-01
I am new at this and I know I must be missing somethign but here goes.
I have my local websever set up and running fine.  I can reach the server webpage by entering my IP address ([http://xxx.xxx.x.x](http://xxx.xxx.x.x)) but when I enter the hostname it goes to the internet to resolve instead of using the hostname I have in the hosts file.  From the server, if I ping the IP address or the hostname, it works fine.  I hope this is clear enough to garner and answer.  I simply want to be able to type in [http://hostname/](http://hostname/) and go to the webpage.  This server is on an internal network and not available to the internet.  Any help would be appreciated.

---

### Post by Copernicus1234 on 2009-01-01
You should be able to just edit your /etc/hosts file. Mine looks like this:

$ cat /etc/hosts
127.0.0.1	localhost
127.0.1.1	hackbox

Just add the ip and the hostname of your machine in there, I suspect its not in there now.

---

### Post by dlader on 2009-01-01
This is my current hosts file.

127.0.0.1     localhost.localdomaine   localhost
192.168.2.3   laderlaw.com laderlaw

# The following lines are desirable for IPv6 capable hosts
::1      localhost ip6-localhost  ip6-loopback
fe00::0  ip6-localnet
ff00::0  ip6-mcastprefix
ff02::1  ip6-allnodes
ff02::2  ip6-allrouters
ff02::3  ip6-allhosts

As as aside, I am using Firefox for my browser and I have not tried it on any others.  I am using a Belkin router for the internal network.

---

### Post by Iowan on 2009-01-01
I have a machine set up that way, but I have several set up using:
127.0.0.1 localhost
127.0.1.1 hostname.domain hostname

---

### Post by MJN on 2009-01-02
> **dlader said:**
> From the server, if I ping the IP address or the hostname, it works fine. That pretty much shows the HOSTS file is working properly then. I suspect the problem lies elsewhere.

Post the output of [B]wget [http://laderlaw](http://laderlaw)

[/B](I am assuming you are trying to access the website from the server and not another machine on the LAN)

Mathew

---

### Post by dlader on 2009-01-02
I apologize for not making myself clear.  I am attempting to reach this site from two other computers on the network.  The server is on the network.  This is all behind a Belkin router.  I can reach the site at the server with either the IP address or the hostname.  However, when I try to reach it from the other two computers, I can only reach it by the IP address.  When I try to use the hostname, my sytem goes out to the internet is appears and does not go to my inhouse server.

---

### Post by MJN on 2009-01-02
> **dlader said:**
> I apologize for not making myself clear.No problem - when you're not sure what the problem it's easy to leave important bits out!

> I am attempting to reach this site from two other computers on the network.You need to add your  **192.168.2.3   laderlaw.com laderlaw** to the HOSTS files on your other two computers. A hosts file is only applicable to the machine it is on. (This means it doesn't scale well which is why DNS was invented - to enable you to enter the record once, in one place, and it be available to all)

Mathew

---

### Post by dlader on 2009-01-02
Perfect.  It works just as you said.  Thank you for your help.

---

