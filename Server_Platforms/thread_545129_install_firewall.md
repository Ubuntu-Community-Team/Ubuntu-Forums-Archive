---
title: "install firewall"
date: 2007-09-07
forum: Server Platforms
---

### Post by ess on 2007-09-07
I have just installed Ubuntu on my Dell laptop, and wondered if I should install a Firewall...since I use the laptop in various locations....

At home, I have a D-Link wireless router and it has a built-in firewall...so, I guess I should be safe when I use the laptop at home.

but I am quite concerned as to when I use the laptop whilst on the move. 

I have already installed Firestarter...but I have noticed that I need to start it manually every time I boot my computer....enter the admin password...etc...

So, my question is:

Is there any other firewall that I can install to protect myself whilst on the move without having to start it manually?

or

Is it possible to configure FireStarter to start automatically without requiring admin password?

Thanks
Ess

---

### Post by ifconfig on 2007-09-07
Hi.

I can be wrong, but isn't it the gui you have to start manually?
Firestarter itself is running anyway.

Magnus

---

### Post by ess on 2007-09-07
Hi Magnus

Thanks for your reply.

So, can I assume that my Ubuntu is protected by default...and there is no need to start, or even install, FireStart every I start the computer?

I am just paranoid about malware and Trojan horses...or worse rootkits, being installed on my machine.

cheers, 
Ess

---

### Post by banewman on 2007-09-07
Firestarter is a GUI for iptables - a firewall that starts at boot time but is normally terminal only. So, every time you start the comp, iptables runs with the settings from firestarter.  :lolflag:

---

### Post by ess on 2007-09-07
Thanks banewman

That indeed answered my question.

Cheers, 
Ess

---

### Post by Brazen on 2007-09-07
yeah, iptables is installed and running no matter what.  It is part of the network stack built into the kernel.  Firestarter is just a gui for configuring iptables.  Once you use firestarter to create and save some settings, then firestarter's job is done and the rest is handled by iptables.

And to be completely accurate, the firewall is actually called "Netfilter", iptables is just the interface for configuring Netfilter.

---

### Post by ifconfig on 2007-09-21
> **ess said:**
> Hi Magnus

Thanks for your reply.

So, can I assume that my Ubuntu is protected by default...and there is no need to start, or even install, FireStart every I start the computer?

I am just paranoid about malware and Trojan horses...or worse rootkits, being installed on my machine.

cheers, 
Ess

Sorry, I haven't replied to you. I had some problems with firewalling myself.
It's good you got it confirmed.

//Magnus

---

