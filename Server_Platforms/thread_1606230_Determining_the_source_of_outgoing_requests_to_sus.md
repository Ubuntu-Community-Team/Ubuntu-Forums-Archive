---
title: "Determining the source of outgoing requests to suspicious IP Addresses"
date: 2010-10-26
forum: Server Platforms
---

### Post by mistypotato on 2010-10-26
Hi,

My Firestarter logs show periodic outgoing connection attempts to IP addresses in countries such as Malaysia, China, Russian Federation etc...

Fortunately, Firestarter appears to be blocking them.

I suspect these are not good and _want to find out exactly what process is initiating these outgoing connections_.

What's the best way to approach this?

thx

---

### Post by the_original_billq on 2010-10-26
> **mistypotato said:**
> Hi,

My Firestarter logs show periodic outgoing connection attempts to IP addresses in countries such as Malaysia, China, Russian Federation etc...

Fortunately, Firestarter appears to be blocking them.

I suspect these are not good and _want to find out exactly what process is initiating these outgoing connections_.

What's the best way to approach this?

thx

Get familiar with tcpdump and wireshark...

Capture packets off to a file, something like:

  tcpdump -n -c 10000 -w tcpdump.out

Then analyze using wireshark:

  wireshark -r tcpdump.out

Check the man pages for tcpdump and wireshark, as there are many options.
You can also do the capture straight out of wireshark, but being able to schedule it with tcpdump can be handy if you see activity in the middle of the night.

Good luck....

-Bill

---

### Post by mistypotato on 2010-10-26
Sounds like 2 good options.

thx Bill

---

### Post by mistypotato on 2010-10-26
Well,
I've got Wireshark installed.

Do you run Wireshark as Root?

Unless I run it as Root, I get nothing even though my user account has admin rights.

When I run it as root, it works.

---

### Post by the_original_billq on 2010-10-26
> **mistypotato said:**
> Well,
I've got Wireshark installed.

Do you run Wireshark as Root?

Unless I run it as Root, I get nothing even though my user account has admin rights.

When I run it as root, it works.

Yes, you need root privilege to open your NIC in promiscuous mode.

---

### Post by endotherm on 2010-10-26
tcpdump is a good method and will catch stuff even when you are not looking, but it may be simpler to check the outgoing port on the communication, and using 
```
netstat -npe > ~/connections.txt
``` check the connections file to determine what process on your PC is sending out on that port.

---

### Post by the_original_billq on 2010-10-26
> **endotherm said:**
> tcpdump is a good method and will catch stuff even when you are not looking, but it may be simpler to check the outgoing port on the communication, and using 
```
netstat -npe > ~/connections.txt
``` check the connections file to determine what process on your PC is sending out on that port.

Nice!

You could also add a bit of awk..

```

netstat -npe|awk '$4 ~ /:YOUR_PORT/ {print $NF}' > ~/connections.txt

```

to make it easy to digest.

---

