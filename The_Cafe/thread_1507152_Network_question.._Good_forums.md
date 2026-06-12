---
title: "Network question.. Good forums ?"
date: 2010-06-11
forum: The Cafe
---

### Post by lostinxlation on 2010-06-11
I have some questions to ask and am looking for the internet boards where there are some people who can answer the extremely geeky questions about network communications.
Does anyone have recommendations ?

---

### Post by juancarlospaco on 2010-06-11
here

---

### Post by bruno9779 on 2010-06-11
> **juancarlospaco said:**
> here

+1

---

### Post by new_tolinux on 2010-06-11
> **juancarlospaco said:**
> here
Being a bit more specific, one of those subforums should be the correct place to put your question:
[Absolute beginner talk](http://ubuntuforums.org/forumdisplay.php?f=326)
[General help](http://ubuntuforums.org/forumdisplay.php?f=331)
[Networking & wireless](http://ubuntuforums.org/forumdisplay.php?f=336)

---

### Post by lostinxlation on 2010-06-11
> **new_tolinux said:**
> Being a bit more specific, one of those subforums should be the correct place to put your question:
[Absolute beginner talk]("http://ubuntuforums.org/forumdisplay.php?f=326")
[General help]("http://ubuntuforums.org/forumdisplay.php?f=331")
[Networking & wireless]("http://ubuntuforums.org/forumdisplay.php?f=336")
 
Aren't they the places for Ubuntu related questions ?

---

### Post by LowSky on 2010-06-11
> **lostinxlation said:**
> Aren't they the places for Ubuntu related questions ?

Well if you are trying to run a network using Ubuntu it would make perfect sense to ask your question here.

---

### Post by Phrea on 2010-06-11
> **lostinxlation said:**
> Aren't they the places for Ubuntu related questions ?

Or Linux in general. :)

---

### Post by lostinxlation on 2010-06-11
> **LowSky said:**
> Well if you are trying to run a network using Ubuntu it would make perfect sense to ask your question here.
 
The question is more generic, related to TCP.

---

### Post by coutts99 on 2010-06-11
> **lostinxlation said:**
> The question is more generic, related to TCP.

Just post it here

---

### Post by pricetech on 2010-06-11
What do you want to know ???

---

### Post by lostinxlation on 2010-06-11
> **pricetech said:**
> What do you want to know ???
 
here is the question.
 
TCP is said as connection-oriented protocol, but TCP is a Transport Layer entity that doesn't set up the actual communication path. So, how could TCP be connection-oriented ? 
My understanding of the term, connection-oriented, is something like ATM or Frame Relay on data link layer.  They set up the connection from sending host to receiving host, first, then transfer the data along the same path, and tear down the path once the communication is over. I don't see the same picture with TCP as TCP is a transport layer entity and doesn't "establish" the connection.
 
What am I misunderstanding ?

---

### Post by koenn on 2010-06-11
it does set up a connection, with the so-called "3-way handshake" 
it also tears it down afterwards 
furthermore, it keeps track of what's been tansmitted on one side and what's been received at the other, so that retransmits can be triggerd when needed, and if packets arrive in the wrong order, they are reordered before they are passed to the application.

So, although the route that each individual packet takes may differ (network level, IP), TCP provides an end-to-end connection between 2 end-points
It's main purpose is to provide an error-free, reliable connection over an unreliable network. 


was this a homework question ?

---

### Post by juancarlospaco on 2010-06-11
> **lostinxlation said:**
> 
 
What am I misunderstanding ?

**UDP**

will help you to understand tcp
supposssse you have an old Hub, it make collisions, 
you stablish a connection and mooooves some bytes there, 
when packets destroy each other:
TCP says: Wait!, i dont receive ACK, something goes wrong, resend me the packet
UDP: I dont care, send the next packet now


Also tcp is slower because of these flow control, 
is oriented to take care on the connection.

udp is faster, it only sends and sends, 
maybe theres nothing on the other side.

---

### Post by pricetech on 2010-06-11
Studying for Network Plus ??

Actually there's a treasure trove of such information already on the web from very reliable sources.  Much more so than what you might find here on forums.

Frankly, to give you a proper answer I'd look it up anyway and I"m already certified (A+ Net+ Security+) and do networking on a day to day basis.

It's one of those "textbook" questions / answers that you don't encounter on a regular basis.

---

### Post by koenn on 2010-06-11
> **pricetech said:**
> Studying for Network Plus ??

Actually there's a treasure trove of such information already on the web from very reliable sources.  Much more so than what you might find here on forums.

Frankly, to give you a proper answer I'd look it up anyway and I"m already certified (A+ Net+ Security+) and do networking on a day to day basis.

It's one of those "textbook" questions / answers that you don't encounter on a regular basis.

LOL, 
While I was writing I was actually thinking both "this sounds an awful lot like something you'd write on an exam" and "wikipedia probably has a better explanation than what I'm writing here".

---

### Post by juancarlospaco on 2010-06-11
Go to Youtube type on Search *"Warriors of the Net"* and see that one
:)

---

### Post by doas777 on 2010-06-11
one of the tough things to grasp are the differances between physical, logical, and virtual. TCP is a virtual protocol so it creates virtual connections. IP is a logical protocol so it creates logical connections. Ethernet and the related L1 protocols create a physical connection.

these are all "connections" but only a physical connection can exist by itself (but it can't do anything useful). virtual and logical connections require the connections under them (an IP connection requires an physical conn; a virtual conn requires both a logical one and a physical one ).

one poster mentioned above that you will understand it better by working with UDP for a bit. I too was confused on the abstract differences between connectionless and connection-orriented, until i worked a bit with the forwarding of DNS traffic through firewalls. had a "the scales fell from his eyes" moment. epiphanies are rare. enjoy them when they come.

---

### Post by lostinxlation on 2010-06-11
> **koenn said:**
> it does set up a connection, with the so-called "3-way handshake" 
it also tears it down afterwards 
furthermore, it keeps track of what's been tansmitted on one side and what's been received at the other, so that retransmits can be triggerd when needed, and if packets arrive in the wrong order, they are reordered before they are passed to the application.
 
So, although the route that each individual packet takes may differ (network level, IP), TCP provides an end-to-end connection between 2 end-points
It's main purpose is to provide an error-free, reliable connection over an unreliable network. 
 
 
was this a homework question ?
 Ok, then the connection-oriented/connectionless used in transport layer aren't the same scheme to those in data link layer ?
 
It's not a homework question. My school years were over 2 decades ago.

---

### Post by doas777 on 2010-06-11
> **lostinxlation said:**
> Ok, then the connection-oriented/connectionless used in transport layer aren't the same scheme to those in data link layer ?
 
It's not a homework question. My school years were over 2 decades ago.
nope. they all stack on top of each other. L2 protocols connect machines on a single network, L3 (IP) connects machines across differant networks, and a L4 protocol (TCP/UDP) connects an **application** on PC A, to a specific **application** on PC B. you use the lower layers (1-3) to get to the remote PC, and L4 to get to the specific application you want to connect to. after all, connecting to a PC is useless unless you are connecting to an application on it like a webserver, mailserver, or a client application port.

L2 gets you from your PC to your Router, L3 gets you from your router to the remote server, and L4 gets you to the specific server app you want.

---

### Post by lostinxlation on 2010-06-11
> **doas777 said:**
> nope. they all stack on top of each other. L2 protocols connect machines on a single network, L3 (IP) connects machines across differant networks, and a L4 protocol (TCP/UDP) connects an **application** on PC A, to a specific **application** on PC B. you use the lower layers (1-3) to get to the remote PC, and L4 to get to the specific application you want to connect to. after all, connecting to a PC is useless unless you are connecting to an application on it like a webserver, mailserver, or a client application port.
 
L2 gets you from your PC to your Router, L3 gets you from your router to the remote server, and L4 gets you to the specific server app you want.
OK, thanks.

---

### Post by koenn on 2010-06-11
> **lostinxlation said:**
> Ok, then the connection-oriented/connectionless used in transport layer aren't the same scheme to those in data link layer ?
 
correct. it's like daos77 said. a data-link would be rather something of a physical connection between hosts, a tcp connection more like a 'virtual' connection between 2 hosts : 1 host sends out a stream of bytes, the other receives the exact same stream "as if" they're connected directly.

---

