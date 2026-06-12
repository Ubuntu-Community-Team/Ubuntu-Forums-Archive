---
title: "What do I need to do this network?"
date: 2007-10-23
forum: Server Platforms
---

### Post by mexlinux on 2007-10-23
Hi:
In the company network, I want to be able to control the internet access of the users.
I mean I want to be able, to certain users to use only email, plus the internat networked applications.
For others I want them to be able to also browse the network, but then be eble to restrict some websites.
And for others I want them to do anything they want.
What do I need?

I guess that I need something like:

                 [CENTER]  Internet Router
                              |
               Internet Linux Server
        (this will do what my question is)
                              |
                         Switch
                              |
             ------------------------------------------------------
             |                       |                       |                       |
       192.168.1.x    192.168.2.x   192.168.3.x      192.168.4.x[/CENTER]


And lets say that:
 192.168.1.x will have full access
 192.168.2.x will have restricted browsing
 192.168.3.x will be able only to email
 192.168.4.x will be the email/web server


So, what do I need to put in the "Internet Linux Server"

---

### Post by HermanAB on 2007-10-23
You need Squid Cache and SquidGuard:
[http://www.aeronetworks.ca/squidguard-howto.html](http://www.aeronetworks.ca/squidguard-howto.html)

Cheers,

Herman

---

### Post by mexlinux on 2007-10-23
Thanks Herman, it seems interesting I'll get to read all the information about squid.

Now my second question, I have that network built already, but without the "Internet Linux Server"

I think I guess a server with two NICs, but then inside what do I need to have it get client connections from one NIC and redirect to the Internet on the other NIC?

---

### Post by CromagDK on 2007-10-25
You could use iptables (already included in ubuntu as far as i remember.)
It is possible to redirect and so on in iptables.

---

