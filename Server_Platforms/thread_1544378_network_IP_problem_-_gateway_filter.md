---
title: "network IP problem - gateway filter?"
date: 2010-08-02
forum: Server Platforms
---

### Post by nicolasdiogo on 2010-08-02
hello,

i am having network problems with a server

i am trying to update its packages with apt-get but every repo times out
i checked with traceroute and packets get as far as the router 
to check i unplugged this box and set my laptop with same ip as this box
and i can search the web just fine : thus i assume there is firewall rules on gateway
what can i do check what the problem is?

thanks

---

### Post by arrrghhh on 2010-08-02
Do you not have control over the router?  Is there a proxy server between you and the open internet?  Do you not have direct internet access through this router?

Can you ping anything on the internet from the server?  What server sources are you using in your sources.list?

---

### Post by nicolasdiogo on 2010-08-02
thanks

i can ping anything

but i can not get any http (port 80) traffic with the server.

my laptop works fine using the same IP as the server.

thus i am trying to find the difference between the server and my laptop 

would i be correct to think that it should be the /etc/network/interfaces
??

just occurred to me.

---

### Post by arrrghhh on 2010-08-02
That interfaces file contains the configuration information for your network interfaces...

If you have a static IP, have you defined DNS?  If you can ping [www.google.com](www.google.com), your DNS stuff should be fine.

If your laptop has the same IP on the same interface, then I don't know what the difference could be, unless your router defines access by MAC address.

You said you cannot get any http (port 80) traffic on the server.  How did you test this?  Have you tried wget or linx or something?

You're sure there's no proxy server before you get to the open internet?  At work to get updates I have to pipe requests thru a proxy server, there is no access to the internet directly.

---

### Post by nicolasdiogo on 2010-08-02
got it..

it was my lack of attention..

this server is the KVM server for a number of VMs.

while the VMs have their own intranet network IP (192.168.88.0/24) - for example

my server has NIC on DMZ and intranet *BUT* both NICs had their gateway set as intranet

since the intranet has a gateway with firewall filtering traffic - it was dropping packets from the server as it originated from *DMZ*

that is surely a bit of a stupid mistake by it did help to explain it to someone else..

many thanks

it is all sorted now.

Cheers!

---

### Post by arrrghhh on 2010-08-02
Glad it's fixed.  Please use the "Thread Tools" dropdown to mark the thread '[SOLVED]'!

---

