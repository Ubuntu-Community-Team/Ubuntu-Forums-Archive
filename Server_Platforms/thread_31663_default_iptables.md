---
title: "default iptables"
date: 2005-05-04
forum: Server Platforms
---

### Post by oilz on 2005-05-04
Hi,

I'm new to linux. I recently installed ubuntu, and thinks it's fantastic.
I'm learning linux as I'm going, and currently looking at iptables.

On a default install of ubuntu, regarding iptables, looking at the filter table, there are no rules in any of the chains.

Is this correct? Shouldn't things be locked down? Or have I not understand this correctly?

Thanks

---

### Post by ubuntu_demon on 2005-05-04
[QUOTE=oilz]Hi,

I'm new to linux. I recently installed ubuntu, and thinks it's fantastic.
I'm learning linux as I'm going, and currently looking at iptables.

On a default install of ubuntu, regarding iptables, looking at the filter table, there are no rules in any of the chains.

Is this correct? Shouldn't things be locked down? Or have I not understand this correctly?

Thanks[/QUOTE]
 this is correct.
If you want to add iptables rules you should use a gui firewall like firestarter or add them by hand.

edit : no firewall is necessary unless you are paranoid or running server

---

### Post by vybegallo on 2005-05-04
Just to elaborate on the previous answer a little bit:

 Yes, by default there are no iptable rules set and everything is allowed to leave or enter IP stack. On the other hand, by default there are no services listening on the network interface - there are some listening on loopback but they can only be reached from the machine itself.
 So, if I wanted to own your box I could not use vulnerabilities in any daemons and  would have to find a flaw in the kernel's IP stack  and do an attack against it - most likely buffer overflow. It is not completely unheard of to have these kinds of vulnerabilities in kernel but I have not seen them in a long while. Exploiting these should they surface would not be a trivial task either. 
 Now, if you wan to be really paranoid, you could drop/reject everything coming in before it even reaches IP stack. You would be protected in the off-chance that such a kernel flaw is discovered. On another hand,  if you enable netfilter code in kernel - this is what you do when you use iptables - you are opening itself up to a possible compromise of netfilter code itself. Again, I do not remember seing netfilter bugs that would lead to a possibility of a compromise, all bugs that I have seen would lead to either letting some packets through that it should not have let through or blocking packets that should not have been blocked. Nevertheless, there is a theoretical possibility that remote-root-compromise type bugs in netfilter do exist and are just waiting to be discovered.
 So, from a pure security standpoint it boils down to what part of Linux kernel code you trust more - IP stack or netfilter. Pretty tough call to make.
 There is also a pretty popular myth that when you drop all unsolicited incoming packes, you become "invisible" on the internet. This is not really true. You do become somewhat "stealthy" but by no means invisible. There are numerous ways to discover if IP address is alive besides ping. From obvious - "I have just received HTTP request from you, you must be there" to not so-obvious like sniffing a traffic on the net and seing packets going back and forth between you and some other machine. Depending on how your upstream router is configured, pinging you and getting no responce could actually mean that you are alive because otherwise upstream router would send ICMP host unreachable back. Actually, about half of the routers on the internet will do it.
 
 The point is I was trying to make is "why bother?"

 Now that I have proven beyound any doubt that firewalls are utterly unnecessary :-), let's see why it is worth bothering.
 What if I install foo-server that by default allows anybody do connect and do stuff, i.e MySQL root password is empty by default and it will listen on all interfaces unless you change config? Will I remember to uninstall/stop/disable/reconfigure it after - or before - I am done playing? If you have firewall rules defined, it does not matter that much. It will not be exposed unless you go and change your firewall config.
  There is a bazillion other reasons when you do want to have a firewall running. The problem for any distribution that wants to enable firewall by default is that it would have to come up with default set of rules that would seem "reasonable" for most people. The Ubuntu solution was to have no listening ports and no firewall rules in default install. It is a very secure setup. If you want to add/remove/change software, espasially servers, it is assumed that you should have some understanding of what you are doing.

---

### Post by LordHunter317 on 2005-05-04
[QUOTE=vybegallo] On the other hand, by default there are no services listening on the network interface - there are some listening on loopback but they can only be reached from the machine itself.[/quote]Actually, loopback services can be bounced attack from the local subnet, if you're very careful.  But defending against this is somewhat complicated, and the attack is complicated itself.   It's not worth worrying about, and the kernel includes a piece of code called rp_filter to protect against it.
 
>  Exploiting these should they surface would not be a trivial task eitherNonsense.  Buffer overflows aren't complicated.  Exploiting it to something beyond a DOS would be difficult, but that's because of where the code is located, not because of the exploits.
 
> Now, if you wan to be really paranoid, you could drop/reject everything coming in before it even reaches IP stack.And it really would be paranoid, as it'd be completely and totally useless.  If you block everything you can talk to no one.  There's an eaiser way to do this: disconnect the network cable.
 
> So, from a pure security standpoint it boils down to what part of Linux kernel code you trust more - IP stack or netfilter.Netfilter is effective part of the IP stack.  It's a hook mechanism for code like iptables to do it's work through, no more, no less.
 
>  Pretty tough call to make.There's no call to make, as you take both or leave both, more or less.  If you enable iptables and use it as a firewall, you get the full IP stack, netfilter, and the iptables kernel bits in kernel.  There's no way to change that.  
Seeing as there's not much you can do against vulnerabilities in those pieces of code (besides fixing the bugs in the first place) they're simply not worth worrying about.
 
>  Depending on how your upstream router is configured, pinging you and getting no responce could actually mean that you are alive because otherwise upstream router would send ICMP host unreachable back. Actually, about half of the routers on the internet will do it.You can't prove that a host is a live based on that.
 
> The point is I was trying to make is "why bother?"Depending on his needs, he may need it.  Ubuntu's default configuration admittedly doesn't require one, but lots of configurations beyond the default will.
 
> There is a bazillion other reasons when you do want to have a firewall running. The problem for any distribution that wants to enable firewall by default is that it would have to come up with default set of rules that would seem "reasonable" for most people.A drop-ALL incoming policy and ask about outgoing seems to work very well for Windows XP SP2.   The problem is that Ubuntu currently has no trivial way to ask for permission to open firewall ports.

---

