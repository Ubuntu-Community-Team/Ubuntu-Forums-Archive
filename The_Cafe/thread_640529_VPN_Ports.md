---
title: "VPN Ports"
date: 2007-12-14
forum: The Cafe
---

### Post by Ebuntor on 2007-12-14
Hi,

I need to open several ports in my router to let a friend connect to a virtual private network (VPN) via a company laptop but I can't figure out which ports are needed.
Simply turning off the router firewall is a solution (and it does work) but it's hardly a safe one.
 I understand there are several different types of VPN's but I have no idea which one I'm dealing with. 

This isn't a Ubuntu related question so I assumed this was the best forum. :)

Thanks in advance

---

### Post by mips on 2007-12-14
[http://www.vpntools.com/vpntools_articles/network-ports.htm](http://www.vpntools.com/vpntools_articles/network-ports.htm)
[http://www.speedguide.net/faq_in_q.php?category=97&qid=188](http://www.speedguide.net/faq_in_q.php?category=97&qid=188)
[http://www.techontour.com/networking/2007/11/03/ports-needed-for-vpn-passthrough/](http://www.techontour.com/networking/2007/11/03/ports-needed-for-vpn-passthrough/)
[http://www.vpntools.com/vpntools_articles/port-for-vpn.htm](http://www.vpntools.com/vpntools_articles/port-for-vpn.htm)

What connectivity are you trying to allow? What vpn client are you using?

---

### Post by Ebuntor on 2007-12-14
> **mips said:**
> [http://www.vpntools.com/vpntools_articles/network-ports.htm](http://www.vpntools.com/vpntools_articles/network-ports.htm)
[http://www.speedguide.net/faq_in_q.php?category=97&qid=188](http://www.speedguide.net/faq_in_q.php?category=97&qid=188)
[http://www.techontour.com/networking/2007/11/03/ports-needed-for-vpn-passthrough/](http://www.techontour.com/networking/2007/11/03/ports-needed-for-vpn-passthrough/)
[http://www.vpntools.com/vpntools_articles/port-for-vpn.htm](http://www.vpntools.com/vpntools_articles/port-for-vpn.htm)


Thank you, I already tried a few of those ports, but no luck so far. Maybe the other ones will work. :)

> 
What connectivity are you trying to allow? What vpn client are you using?I wish I knew, that's why I started this thread. The friend I'm helping is using a company laptop.

It's running Windows and all the software (the client etc.) is installed but for the rest everything, the whole OS and most apps, are locked down. Some kind of security system is running and I simply don't have access to the settings. 

I'll see if I can find the name of the client, let's hope that's something I can access.  ;)

---

### Post by popch on 2007-12-14
You could find out what ports are used by running a network sniffer while the VPN connection is being used. A network sniffer listens to traffic on your subnet and shows all packages by IP address and port.

I can not tell from off the top of the head what the sniffer is called, but I believe it's something like ether-ape. Use the 'admin' variant.

---

### Post by n3tfury on 2007-12-14
> **Ebuntor said:**
> Thank you, I already tried a few of those ports, but no luck so far. Maybe the other ones will work. :)

I wish I knew, that's why I started this thread. The friend I'm helping is using a company laptop.

It's running Windows and all the software (the client etc.) is installed but for the rest everything, the whole OS and most apps, are locked down. Some kind of security system is running and I simply don't have access to the settings. 

I'll see if I can find the name of the client, let's hope that's something I can access.  ;)

yeah, just don't post the company name and other info here.  i'm glad you haven't so far.

popch, that's a good idea.

---

### Post by mips on 2007-12-14
> **popch said:**
> 
I can not tell from off the top of the head what the sniffer is called, but I believe it's something like ether-ape. Use the 'admin' variant.

Yes, it's EtherApe and it is in the repos.

---

### Post by Ebuntor on 2007-12-14
> **mips said:**
> Yes, it's EtherApe and it is in the repos.

Ok, thank you, I'll try that. :)

---

### Post by Ebuntor on 2007-12-14
> **n3tfury said:**
> yeah, just don't post the company name and other info here.  i'm glad you haven't so far.

popch, that's a good idea.

Hmm, forgive my ignorance but why would posting the company name be a problem? I mean I'm just asking a support question about one of their laptops?

---

### Post by mips on 2007-12-14
> **Ebuntor said:**
> Hmm, forgive my ignorance but why would posting the company name be a problem? I mean I'm just asking a support question about one of their laptops?

I think he is referring to the companies network settings etc. Security risk!

---

### Post by n3tfury on 2007-12-14
> **mips said:**
> I think he is referring to the companies network settings etc. Security risk!

yes.  posting the name of and subsequent programs that are security related is just not a nice thing to do.

---

