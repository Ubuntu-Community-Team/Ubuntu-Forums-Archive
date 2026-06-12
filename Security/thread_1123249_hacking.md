---
title: "hacking?"
date: 2009-04-12
forum: Security
---

### Post by JakeHinojosa on 2009-04-12
it it possible for somebody to hack into a computer running ubuntu? and i dont mean like the remote desktop viewer thing, i mean like people from the next country able to somehow get access to your computer or being able to see what you do. is it possible?

---

### Post by lykwydchykyn on 2009-04-12
> **JakeHinojosa said:**
> it it possible for somebody to hack into a computer running ubuntu? and i dont mean like the remote desktop viewer thing, i mean like people from the next country able to somehow get access to your computer or being able to see what you do. is it possible?

Depends what services you are running.  If you run something like ssh and connect to the internet without a firewall or NAT, you'll have bots trying to brute-force you all day.

I believe there have been some browser exploits here and there for firefox (now patched) as well.

---

### Post by defaultusername on 2009-04-12
JakeHinojosa,

Most of the techniques used by blackhats require only minor alterations to become cross-platform issues. The underlying methodology for attacking Windows is the same for any platform. Linux just offers a smarter security config and a more technically adept userbase.

---

### Post by Tunisian_CrAcKeR on 2009-04-12
firestarter is the best way to protect your system from hacking ):P

---

### Post by hyper_ch on 2009-04-12
> **Tunisian_CrAcKeR said:**
> firestarter is the best way to protect your system from hacking ):P

what does firestarter do? My impression is you don't know at all what firestarter is otherwise you wouldn't give such a statement.

---

### Post by Dr Small on 2009-04-12
> **Tunisian_CrAcKeR said:**
> firestarter is the best way to protect your system from hacking ):P
Firestarter is only a GUI for iptables. It's not the 'one-stop-protect-all' application.

---

### Post by the8thstar on 2009-04-12
I use GUFW which is the GUI version of UFW (uncomplicated firewall). I wonder if it uses iptables or not.

---

### Post by lykwydchykyn on 2009-04-12
> **the8thstar said:**
> I use GUFW which is the GUI version of UFW (uncomplicated firewall). I wonder if it uses iptables or not.

Basically, it's like this:
 - The Linux kernel has a firewall module built in.  It's called **netfilter** and it's quite awesome.  Many commercial firewall products are based on Linux + netfilter
 - Iptables is a command used to control netfilter.  Using iptables, you can directly specify rules for netfilter to use in filtering and routing network packets.
 - UFW, GUFW, Firestarter, Guarddog, et al are front ends for netfilter.  Presumably many of them use iptables as a middleman to send rules to netfilter.  They all ultimately use netfilter though.  

No particular firewall in Linux is really any more effective than another, they just vary in their ease of use or the amount of netfilter features they expose. 

If you are exposing network services to the internet, and you're worried about security, do some reading on how to secure the particular service you're running.  Firewalls basically block ports, which is useless if you need the ports to be open in the first place.

---

### Post by the8thstar on 2009-04-13
Yes, GUFW is super easy. On my config, any incoming traffic is denied. Plus I connect through wifi to a DSL router that has its own hardware firewall. I guess I'm pretty secure.

---

### Post by sahabcse on 2009-04-13
Hi

For more information about firestarter and GUFW please follow below url

[http://sahabm.blogspot.com/2009/04/firewall-for-ubuntu-gufw.html](http://sahabm.blogspot.com/2009/04/firewall-for-ubuntu-gufw.html)
[http://sahabm.blogspot.com/2008/12/firewall-and-internet-saring.html](http://sahabm.blogspot.com/2008/12/firewall-and-internet-saring.html)

---

### Post by WatchingThePain on 2009-04-13
I just configure iptables as I have found the gui's to be more of a nuisance.
With Ubuntu firestarter is probably the easiest way to set up the Linux firewall.
Any computer can get hacked but there's no need to get paranoid.
Also you should be careful about what you let through your firewall.

---

