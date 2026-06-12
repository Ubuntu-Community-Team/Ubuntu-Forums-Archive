---
title: "Security flaw question"
date: 2009-02-24
forum: Security
---

### Post by screaminfakah on 2009-02-24
Hey,
I read that the X Windows format is easily IP spoofed?
So why use it if it is so vulnerable to this attack??

[http://en.wikipedia.org/wiki/IP_address_spoofing](http://en.wikipedia.org/wiki/IP_address_spoofing)

I thought Ubuntu & Mac were top dogs when it comes to vulnerabilities.

---

### Post by cariboo on 2009-02-24
You obviously didn't read the whole article.

> Defense against spoofing

Packet filtering is one defense against IP spoofing attacks. The gateway to a network usually performs ingress filtering, which is blocking of packets from outside the network with a source address inside the network. This prevents an outside attacker spoofing the address of an internal machine. Ideally the gateway would also perform egress filtering on outgoing packets, which is blocking of packets from inside the network with a source address that is not inside. This prevents an attacker within the network performing filtering from launching IP spoofing attacks against external machines.

It is also recommended to design network protocols and services so that they do not rely on the IP source address for authentication.

Ubuntu has a firewall installed by default, although it doesn't filter anything until you set up some rules. [Iptables]("http://help.ubuntu.com/community/IptablesHowTo") is the name of the firewall and the preffered gui is [GUFW]("http://gufw.tuxfamily.org/index.html").

Jim

---

### Post by screaminfakah on 2009-02-25
I did read the entire article but if you search "do I need a firewall in Ubuntu" there is a slew of people claiming that you do not need one because iptables does it for you.  
So what your saying is unless you configure iptables it does not filter packets?

Thanks for the link to the gui.  Firestarter has been a bit of a pain to screw with and I have no patience for that so maybe I will give this one a try.

---

### Post by cdenley on 2009-02-25
> **screaminfakah said:**
> Hey,
I read that the X Windows format is easily IP spoofed?
So why use it if it is so vulnerable to this attack??

[http://en.wikipedia.org/wiki/IP_address_spoofing](http://en.wikipedia.org/wiki/IP_address_spoofing)

I thought Ubuntu & Mac were top dogs when it comes to vulnerabilities.

I'm not exactly a security expert, so I may not fully understand this, but how is one application more or less vulnerable to IP spoofing than another?

---

### Post by HermanAB on 2009-02-25
Some misunderstandings here.  The netfilter system is a set of kernel modules that form part of the network stack.  Iptables is a utility used to configure netfilter.  

The idea of a network firewall is mainly a Windows thing, since on a Windows system, there are lots of undocumented services running.  Therefore the only way to get a Windows box under control, is to fit a Linux box in front of it and configure that to filter the connection and prevent malicious packets from reaching the Windows box.  Most network routers and firewalls do indeed run Linux.

On a Linux system, things are under strict control and the default Ubuntu install doesn't need any special netfilter rules for its protection.  The simple fact is that Ubuntu by default doesn't have any network listeners. Therefore any incoming malicious packet will simply be dropped on the floor. Once you start to do something advanced, like run a LAN behind the Linux box, then you should configure a firewall, since you don't know who will plug what into a network socket.

Cheers,

Herman

---

### Post by movieman on 2009-02-25
> **screaminfakah said:**
> 
I read that the X Windows format is easily IP spoofed?
So why use it if it is so vulnerable to this attack??


In the good old days, X11 would listen on port 6000 and anyone could connect to your system so long as you gave permission for their system to connect; since the authentication was IP-based, anyone who could spoof a valid IP address could connect and do naughty things like logging keypress events.

Today X11 is normally configured to only listen on the local host, so this is a non-issue; if they're logged into your local system as you, and thereby able to connect to the local X-server, you're toast anyway. To run X11 programs from a remote system, you normally use SSH forwarding, which can't be spoofed in the same way.

---

### Post by screaminfakah on 2009-02-26
Thanks for the clarification guys.  Im still in the learning process with all of this fun stuff!

---

### Post by hyper_ch on 2009-02-28
if you are behind a NAT router, set that one up correctly and don't worry too much about that stuff in Ubuntu. However when you want to start offering servers on your install you might want to dig deeper into that thematics.

---

