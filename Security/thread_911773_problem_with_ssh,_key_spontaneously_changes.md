---
title: "problem with ssh, key spontaneously changes"
date: 2008-09-06
forum: Security
---

### Post by jctsunami on 2008-09-06
I've tried searching the forums/google for a solution but I haven't had much luck.

Basically my ssh server seems to spontaneously change authentication keys every now and then. What will happen is I might be able to successfully get the server key and login and go about as usual. After a couple of minutes however, I'll get kicked off with a message like "connection reset by peer". I will try to log back in and what should go straight to the password dialog doesn't and tells me that the key has changed. I've tried deleting the known_hosts file on the local computer but my correct password doesn't work at all.

What will eventually happen after a couple more minutes is that my repeated attempts will continue to fail until i get another dailog that says the key changed, and this time back to the original key. I should note that the original key matches that in the rsa key file on the server. Also a reset of the network card on the server will also seems to trigger the key to revert to the original correct key.

I know this was just descriptive with little actual output, but I'm hoping someone may have encountered this before. Also I should mention that this seemed to have happened after I assigned it a permanent hostname and IP address. Also  I doubt it is a man in the middle attack as ssh claims since the network that connects the server to my remote computer is trusted (school network)

---

### Post by phaid on 2008-09-06
It does sound like a man in the middle attack, you can't preclude that because it's a 'trusted' network.  Just to clarify, when you try and connect your ssh client is saying the destination machine has a different key?  If it's not an attack, maybe either something like a round-robin dns is in place or maybe they have some weird dhcp thing going?  If the destination key is changing, don't trust that it is the machine you are trying to connect to.

What you can try doing when you start a successful session, from the source machine
ping the destination to get the ip address
do arp -a ip address of the destination machine

That will give you the MAC address of the machine
when the issue occurs, do the same thing and compare them - if the ip address has changed, ping the original one and do an arp -a against the original

People can spoof mac addresses, so that's not 100%, but it could say if something weird is occurring on the network.

Also, you can do a telnet hostname 22
telnet will connect on the ssh port and you should see some information about the machine that you are connecting to

---

### Post by The Cog on 2008-09-06
Is it possible that you have two machines with the sami IP address? And you get connected to whichever one your ARP table has in its cache at the time?

---

### Post by rogeriopvl on 2008-09-07
> **The Cog said:**
> Is it possible that you have two machines with the sami IP address? And you get connected to whichever one your ARP table has in its cache at the time?

I would go for that, it already happened to me.

---

