---
title: "Base Install, Outgoing Internet works. Nothing Incoming"
date: 2012-01-09
forum: Server Platforms
---

### Post by PensFan66 on 2012-01-09
I just built an Ubuntu Squid server - The server itself can browse the Internet, and internally the Squid works as it should (using it as a Reverse Proxy) - but any traffic coming from the Internet seems to be blocked to the Server.
 
I have forwarded port 80 to the server (Squid) and even tried forwarding 10000 for webmin and 22 for SSH and none of them work.
 
UFW is off ... and Im stump now ..
 
Am I missing something obvious?
 
Thanks!

---

### Post by jonobr on 2012-01-10
In the terminal


```
sudo tcpdump -i any port 22
```
Then SSH to the machine,
if you see no output on tcpdump, the problem is elsewhere

then control c and try web traffic 

```
sudo tcpdump -i any port 80
```
Do web stuff to the server.
if you see no output on tcpdump, the problem is elsewhere

now webmin (you mentioned port 10000)

```
sudo tcpdump -i any port 10000
```
Do webmin stuff to the server.
if you see no output on tcpdump..... you can guess the rest:P

---

### Post by PensFan66 on 2012-01-10
Ah - good point, forgot about tcpdump .... Off to try....
 
** EDIT **
 
Well, I get packets from all internal requests but nothing from Internet requests.
 
Using DD-WRT - I have ports going to other devices without issue - I can move 80 to an IIS machine for a test and it works.   Move it to the Ubuntu server, nothing .... Added to DMZ to avoid port filtering, no luck either ... No packets....
 
I dont get it  :)

---

### Post by jonobr on 2012-01-10
Hey there

All things being equal, if your tcpdump shows nothing for the above traffic, and no packets appear when you ssh or port 80,
then there are no packets hitting your interface.

To definitately test, you could place a windows box with wireshark on the same segment and trace again to see if packets go to your server.
Im pretty sure you wont see anything.

Forwarding to other devices but not this one machine indicates configuration or blocking issues on the router or ISP

---

