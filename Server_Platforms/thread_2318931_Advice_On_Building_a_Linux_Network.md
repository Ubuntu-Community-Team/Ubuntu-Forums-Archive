---
title: "Advice On Building a Linux Network"
date: 2016-03-30
forum: Server Platforms
---

### Post by Nuraas on 2016-03-30
Hi All,

I currently works at a company using solely windows networks (With a Mac dotted around) but being the only guy in the office that has had any sort of experience using Linux (Desktop Mostly) I have been asked to do some testing to look at replacing the Windows servers on a Hyper V with a Linux alternative. this would need to be able to support both windows and linux clients and if possible Mac (we have mac servers for that if not.)

Now for the testing I will be using ProxMox as I have been given little to no budget as its more just a proof of concept. I want to make it as competative as possible though as because not only am I a self confessed linux fan boy but I know that linux servers are incredibly robust if properly configured.

so to my question, I basically need to replace the following.

Domain Controller. I assume this will be the easiest to replace as there isnt much to a DC however Please note all the Interfaces will need to be GUI for the time being (I am trying to stear the guys towards CLI but baby steps :P)

Member Server, Applications (Deployment Server) and MIS

I need to be able to set up teaming which I assume can be done within ProxMox. Mainly I am looking for as much advice as you guys and girls can possibly give me :) I am looking forward to working within a linux enviroment :)

Thanks in advance.

---

### Post by Thirtysixway on 2016-04-23
Are you wanting to just have a Linux hypervisor + windows VMs ? Or are you trying to replace all windows servers win linux servers?

So for your domain controller you can look at [Samba]("https://wiki.samba.org/index.php/Setup_a_Samba_Active_Directory_Domain_Controller") which can act as a DC.  Though depending on your use of it, it may be better to just keep windows for this. As much as I love Linux, AD on a windows server will definitely be more stable/reliable for your windows clients.  I worked at a place that used to manage a bunch of samba DCs, and it can become compatibility hell when you start updating/upgrading windows PCs.  If your company can afford the license, I would recommend it.

I'm not sure what your Member/MIS servers are used for.  Deployment server - is this PXE booting and installing new PCs ?

If teaming == interface bonding, yes that's possible to do with Linux. It's fairly straight forward but will depend on what switch you're plugging into.

---

