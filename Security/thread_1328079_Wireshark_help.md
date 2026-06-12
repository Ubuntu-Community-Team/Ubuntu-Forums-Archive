---
title: "Wireshark help"
date: 2009-11-16
forum: Security
---

### Post by GHOST_TUX on 2009-11-16
Hello I am fairly new to to wireshark and I don't really understand if a am getting traffic from my machine, other machines on the network or both (I am seeing a lot of stuff scroll by but no http addresses.) I have included a session that I saved in the attachments. If anyone can tell me if wireshark is seeing websites that i goto on other pc's.

---

### Post by Kinstonian on 2009-11-16
You could use display filters.  In the "Filter" box type something like:

ip.addr == 111.222.333.444 && http

Or to see just HTTP requests your computer made, use something like:

ip.src == 111.222.333.444 && http.request

You can find the display filters you can use [here](http://www.wireshark.org/docs/dfref/).

---

### Post by GHOST_TUX on 2009-11-16
yes i know about filters but i found an article on wireshark and i think i may need to have to put in my WPA key or switch the network to unsecured temporarly.  can you still sniff with the AP being secured?

---

### Post by GHOST_TUX on 2009-11-16
when i have my laptop hooked up using Ethernet i am able to sniff the traffic from my but not anything else? how come? (i don't see the HTTP for other pc's on my network using ethernet)

---

### Post by FuturePilot on 2009-11-16
[http://www.wireshark.org/faq.html#promiscsniff]("http://www.wireshark.org/faq.html#promiscsniff")

---

### Post by GHOST_TUX on 2009-11-16
thank you for the help! but i found the problem, i just needed to do an arp poising attack which resulted in a man in the middle attack and i was able to capture all the traffic from the poisoned systems.  here is the article i followed: [http://openmaniak.com/ettercap_arp.php](http://openmaniak.com/ettercap_arp.php)

---

### Post by Logan1985 on 2009-11-16
> **GHOST_TUX said:**
> thank you for the help! but i found the problem, i just needed to do an arp poising attack which resulted in a man in the middle attack and i was able to capture all the traffic from the poisoned systems.  here is the article i followed: [http://openmaniak.com/ettercap_arp.php](http://openmaniak.com/ettercap_arp.php)

Just for your own knowledge, the reason for this is that on switched networks, you do not see traffic that is not meant for you.

You will see broadcast (floods to all nodes) traffic on your segment, multicast (a group of nodes) if you are part of it, and unicast (single destination node) traffic for you only.

On a switched network, a virtual circuit is established between the sender and the reciever, so only they see the traffic, as opposed to in a hub environment where all traffic is flooded out of all ports. So, even in wireshark with your NIC enabled for promiscuous mode, you will not see direct traffic between other nodes. 

Ways to get around this in a switched environment is to use port mirroring if your switch supports it, or, as you have discovered, MITM.

Sorry if you already knew what I just said...and if you don't and you are interested, read a few articles as I have only scratched the surface. 

You may find this of use - [http://computer.howstuffworks.com/lan-switch.htm](http://computer.howstuffworks.com/lan-switch.htm)

---

### Post by Nenu on 2009-11-20
hi...I would just like to hijack this thread with a couple of really stupid questions (I am new forgive me ;) ).

What is Wireshark actually used for...in a basic way please?

Is it really needed? 

As I said stupid questions but I am just learning.

---

### Post by movieman on 2009-11-20
> **Nenu said:**
> What is Wireshark actually used for...in a basic way please?

Monitoring network traffic. For example, when I was setting up IPSEC between my computers at home I needed to capture the traffic to see why they weren't managing to connect, and then again after I finally got the connection configured to verify that the network packets were actually being encrypted.

> Is it really needed?

It is any time you want to see what's actually going across your network rather than guess :).

It's also interesting to demonstrate just how insecure a shared network connection is: for example, you can watch someone else using their web browser and it will decode all the the HTML files which are passing between the web server and their browser. For that matter, I needed to do that to myself in order to figure out what URLs the Windows software was using to talk to my ethernet webcam.

---

### Post by Nenu on 2009-11-20
Thanks :)

So if I understand you it is used if you are on a shared network or networking between computers.  Is that right?

So if I only use my laptop on a secure (home) internet connection and don't link to other computers I don't really need it.

Although lets be honest if I have to ask such basic questions I probably couldn't use it even if I wanted to lol.

---

### Post by Logan1985 on 2009-11-20
Wireshark extends far further than just basic network traffic sniffing. It has uses in various aspects of networking and networked applications. 

I use it all the time for VoIP troubleshooting for example. It can "record" voice conversations, show the setup process, show what codec is in use, and a whole load of other stuff.

If you want to learn about it then there's no reason not to analyse traffic sent to and from your pc/router..but it's not going to show an awful lot. 

Even if you had 4 PC's in your house...if they are connected with a switch, you will not see traffic to/from other machines without certain techniques..either by way of switch feature, or a man in the middle attack.

If you use a hub however, you will see all traffic to/from all hosts.

---

