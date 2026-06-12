---
title: "Security Suite"
date: 2008-07-19
forum: Security
---

### Post by plainhunt on 2008-07-19
Hi, can anyone advise on the best free Security Suite for Ubuntu 8 with anti-virus, firewall etc.

Thanks in advance!
Dan

---

### Post by mehtdosa11 on 2008-07-19
> **plainhunt said:**
> Hi, can anyone advise on the best free Security Suite for Ubuntu 8 with anti-virus, firewall etc.

Thanks in advance!
Dan
hi dan,

well, the one of the main advantages of linux is that you don't really need to use these tools. there are apparently only 50-100 virus out there for linux, against 4 million allegedly for windows ! as an ex-window's newbie myself it's pretty hard to understand at first.

however there are available in the repositeries [use add/remove] a firewall called 'firestarter' and an anti-virus tool called 'clamAV' if you feel you must have something. but there are no 'security suites' as in the windows way.

more educated members of the forum will be able to tell you more, as i'm sure they will!

steve

---

### Post by hyper_ch on 2008-07-19
> **mehtdosa11 said:**
> a firewall called 'firestarter'
Firestarter is NOT A FIREWALL

The firewall in linux is called iptables and firestarter is - an outdated - interface to configure it. It is not a firewall in the way you know from windows. It is a package filtering.

However by default you don't have any need to alter the default configuration of iptables as there are no services installed that require filtering.

Only when you start installing services you have to start thinking about iptables.

And antivirus is also generally not needed. There are no viruses out in the wild for linux.

---

### Post by spike_strip on 2008-07-19
> **hyper_ch said:**
> Firestarter is NOT A FIREWALL

The firewall in linux is called iptables and firestarter is - an outdated - interface to configure it. It is not a firewall in the way you know from windows. It is a package filtering.

However by default you don't have any need to alter the default configuration of iptables as there are no services installed that require filtering.

Only when you start installing services you have to start thinking about iptables.

And antivirus is also generally not needed. There are no viruses out in the wild for linux.

I sure am glade hyp never gets tired of saying this. 

It relay is very fundamental part of Linux security!

---

