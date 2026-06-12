---
title: "Need a different firewall than IPtables"
date: 2011-12-18
forum: Security
---

### Post by pksings on 2011-12-18
I'm looking for a linux firewall program for my workstation that allows HPLIP to work, IPtables does not. Are there any other firewalls that can be installed on a linux box?      A full week of trying to get IPtables to work with HPLIP only find out that it simply cannot is enough effort expended with it.

Thanks

---

### Post by haqking on 2011-12-18
> **pksings said:**
> I'm looking for a linux firewall program for my workstation that allows HPLIP to work, IPtables does not. Are there any other firewalls that can be installed on a linux box?      A full week of trying to get IPtables to work with HPLIP only find out that it simply cannot is enough effort expended with it.

Thanks

Netfilter/IPTables is the firewall built into the Linux Kernel which all the popular "Firewalls" manipulate and control.  I say "Firewalls" as things like UFW/GUFW/Firestarter/Smoothwall etc all are front ends for IPTables/Netfilter configuration.

So either way it will come down to your specific rules that you are using regardless of the interface you use for it.


What exactly is the issue ? is it msdns related ?
Cheers

---

### Post by Lars Noodén on 2011-12-18
IPTables is your only option for the Linux kernel.  You do have different front ends for it like UFW and [GUFW](https://help.ubuntu.com/community/Gufw)

If you want to try a different packet filter than IP Tables, then perhaps the main one is [PF](http://home.nuug.no/~peter/pf/).  For that, you'll have to switch from Linux to BSD.

---

### Post by HermanAB on 2011-12-18
Hmm, try:
$ sudo iptables -F

to flush all the garbage rules you collected and see if the printer now wants to work.  If it still doesn't then whatever the problem, it is not iptables (anymore).

---

### Post by Dangertux on 2011-12-18
For HPLIP msdns support you may wish to try to add these lines to your iptables script, it should allow the multicast discovery protocol which is likely what is failing.

```

iptables -A INPUT -p udp --sport 427 -j ACCEPT
iptables -A INPUT -p udp --sport 5353 -j ACCEPT

```Let me know if this works.

Note : these need to go before any rules that drop or reject multicast traffic.

---

