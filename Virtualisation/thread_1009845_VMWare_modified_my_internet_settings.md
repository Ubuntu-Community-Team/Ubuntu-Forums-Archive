---
title: "VMWare modified my internet settings?"
date: 2008-12-13
forum: Virtualisation
---

### Post by Captain Jack on 2008-12-13
Hi all,

So, I installed VMWare Workstation 6.5.1 on Gutsy last week. The Internet was working great with my DWA-552 PCI wireless card. Two days after installing VMWare I went away to work with my PC running and when I came back the internet did not work on the host OS. So I rebooted and when I did, no signal detected in Ubuntu. I verified that the wireless card was not defective by putting it in another computer and testing it. So I decided that it would not be a bad idea to just go ahead and format the Ubuntu partition and install Ubuntu again. Now, I am afraid the same problem will happen again. Has anyone ever had a similar problem before?

---

### Post by bodhi.zazen on 2008-12-13
Well, how did you install VMWare Workstation ? 

Off the top of my head, this is an issue if you use the "any-any-update" or patch.

---

### Post by Dedoimedo on 2008-12-14
Any firewall rules? Subnet clashes?
Dedoimedo

---

### Post by Captain Jack on 2008-12-14
> **bodhi.zazen said:**
> Well, how did you install VMWare Workstation ? 

Off the top of my head, this is an issue if you use the "any-any-update" or patch.

I used a .bundle and followed the instructions on [https://help.ubuntu.com/community/VMware/Workstation](https://help.ubuntu.com/community/VMware/Workstation). I used the how-to madwifi thread and switched to WICD because my DWA-552 crashed using the default network manager. I tried using virtualbox OSE however, it caused my computer to lock up again. That made me have to format again.

---

