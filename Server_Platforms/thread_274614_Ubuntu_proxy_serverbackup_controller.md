---
title: "Ubuntu proxy server/backup controller"
date: 2006-10-10
forum: Server Platforms
---

### Post by c0d3sl1ng3r on 2006-10-10
Hi all.

I'm a Windows sysadmin (sorry) but having used Ubuntu on one of my laptops and as a home server I'd like to start planning its inclusion into our network at work.

We currently have a cluster of Win2K machines, a Smoothwall box primarily used to serve up VPN tunnels (don't ask), and a woefully inadequate hardware firewall device whcih is soon to be replaced with something more appropriate.

Does anyone have any experience of rolling out a Ubuntu proxy server and, has anyone used one as a backup controller ?

I've played with Linux backup tools to snapshot Windows clients and network shares onto a NAS device and was impressed at how cleanly it performs. Other backup measures are also in place but I'd like to begin planning Ubuntu integration, hence the double barrelled question.

Thoughts on viability and practicality would be appreciated, and any helpful hints or (polite) suggestions.

Thanks in advance :)

---

### Post by drakkan on 2006-10-10
You can not use a linux server as backup domain controller if your primary domain controller is a windows server.

Linux (and so ubuntu) perform great as vpn server,firewall and proxy server. You can use squid with ntlm authentication as proxy server so the proxy works like a Microsft ISA server (integrated authentication for domain users). You can also restrict internet access for particular windows users or groups and in some hours of the day. You can also control bandwidth usage.

I'm using such configurations since several years with almost zero problem,

be aware of this ubuntu specific bug

[https://launchpad.net/bugs/64425](https://launchpad.net/bugs/64425)

regards
drakkan

---

### Post by PhilKarras on 2008-04-22
So, how does one get the proxy to work on a Windows domain? I've got it working on a workgroup network but when I take it to a domain network it simply shuts down IE when IE is told to use the proxy server for Internet access. I have reset the interfaces & localnets files and I have a good_dest_doms file, etc, as I said it works as expected on a workgroup network but not the domain network where I really need it.

Is there an article somewhere that explains the needed settings?

Thanks for any help in this area.

---

