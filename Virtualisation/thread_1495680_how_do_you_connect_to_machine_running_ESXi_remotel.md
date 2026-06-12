---
title: "how do you connect to machine running ESXi remotely?"
date: 2010-05-28
forum: Virtualisation
---

### Post by karmic-koala on 2010-05-28
The vSphere client it seems is not free and only meant for Windows. What app do we use to connect to machine running ESXi to install virtual machines, etc

---

### Post by BobVila on 2010-05-28
> **karmic-koala said:**
> The vSphere client it seems is not free and only meant for Windows. What app do we use to connect to machine running ESXi to install virtual machines, etc
The vsphere client is free - it's really the only way to get stuff like that done. I do all my esxi administration from a windows vm.

---

### Post by karmic-koala on 2010-05-28
Not fair, what about us Linux users. And isn't that windows app limited for 60 day use, I thought it was.

---

### Post by BobVila on 2010-05-28
> **karmic-koala said:**
> Not fair, what about us Linux users. And isn't that windows app limited for 60 day use, I thought it was.

I know! It's really one of the only reasons I have a Windows VM at all, but such is life, I suppose. I've never come across a time limit with the app... the licenses from VMware are free and I've been running a few esxi servers for well over a year here.

---

### Post by stephanhughson on 2010-06-17
If you are on a 60 day trial, then you've probably downloaded something better/different to the normal basic vSphere client.

You can download the free version by visiting [https://ip-address-of-your-esxi-host](https://ip-address-of-your-esxi-host) and there's a download link.

---

### Post by TheFu on 2010-06-19
Yes, it sucks that VMware has made a conscious decision to neglect non-MS users. They are also developing more and more scripted controllers using powershell instead of perl, as they have historically done. I don't know if they are stopping development or support of the perl control programs.

Is VMware making a good business decision to concentrate on MS-Windows?  Yes.  OTOH, it is very difficult to find a single business of any non-trivial size that doesn't have at least 1 MS-Windows PC.  OTOH, ignoring 90+ % of the desktop market would be crazy for them.  I was at a client this week that is 100% microsoft, but also has 2 ESX VMware servers. I really wanted a Linux machine to automate some tasks, but couldn't convince myself to introduce a different OS into their infrastructure. The day-to-day admins barely know how to spell "linux."

---

