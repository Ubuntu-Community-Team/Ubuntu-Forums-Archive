---
title: "DNS, domain controller, DHCP, file server?"
date: 2011-02-14
forum: Virtualisation
---

### Post by 1clue on 2011-02-14
Hi,

I have a problem in two places and I would like to only have to solve it once.

Our office is about to move.  There are four people.  Currently we're subleasing from a bigger company, the business relationship has dissolved.  They have the Windows domain controller, the DHCP server (which I actually had to set up) file server, and all that.  Oddly enough, I'm not content with the setup I have at home either, and I would like to set up the same sort of thing here.  We use Windows, Mac and Linux in the office.  Yea, 4 people right?  Worse yet, at home it's the same thing and there's just one of me.

So the question is, can I reasonably put that on a VM without totally trashing my network if something breaks?  We don't have a Windows Domain Controller license, and I hate to use a workgroup.

So here's the rub:  It The office systems we're going to keep are the Windows boxes.  The Linux gear is already either virtualized or it's old and not worth taking along, or it belongs to the people who are staying.

Long story short, I think we need to use VMware since that's able to run on any host platform.

I wanted to try out the UEC stuff but I certainly don't have hardware for it at home, and I doubt we can justify that much hardware at work either, especially if it has to be VT-capable.  So we're stuck with running VMs on Windows over there, Linux at home.

So this VM would contain:
1.  Cross-platform authentication, Mac, Windows and Linux.  It would be really neat if this were a one-login style setup.
2.  DHCP server.
3.  DNS, preferably something that can hook up with the DHCP server and move the name appropriately.
4.  Print server.
5.  Web-based admin panel (webmin?)
6.  Possibly a Samba server hooked to a real disk or two.

I'd like to hear from somebody who has actually done something like this on a VM and had it running for awhile.  I'm nervous about putting that much critical hardware on a VM.

I think, now, that I would have two copies of this thing at the office, split across separate hardware.  Primary and backup.

Thanks.

---

### Post by HermanAB on 2011-02-16
Howdy,

That is really basic stuff and is no big deal.  There are millions of web and mail servers running on VMs. You can use either Vmware or Virtualbox, both are rock solid.

---

### Post by mciverza on 2011-02-16
If you run a Zentyal, it'll offer all the services you have listed above and more.
Zentyal is based on ubuntu server. 

Have a look at it at [www.zentyal.org](www.zentyal.org)
and download it (free) at [www.zentyal.org/downloads/](www.zentyal.org/downloads/)

If tried it and was really impressed. All config is via a pretty web-interface, so no need to show any Command Line Interface stuff to scare the Windows users.

---

### Post by 1clue on 2011-02-16
I've always been cautious about having core network services on a VM, I'm too skeptical that the VMware/KVM/whatever service will stay running.

Mail and web, I don't really care where that stuff is, but to have the network completely stop because of a VM down, that's a tough one as far as I'm concerned, and that's why I asked.

I've been running VMs for testing for years.  Just never for core infrastructure.

Thanks.

---

### Post by HermanAB on 2011-02-19
Well, why would a Linux VM stop working?  Linux machines can run for many years non-stop with zero maintenance, till the hardware fails.

The vast majority of web and mail servers are virtualized.  Many large organizations virtualize *everything*, even laptop computers.  A virtualized laptop allows you to deploy a single image to everybody and when Windows screws up, you log in over SSH to the underlying Linux and upload a new VM.

---

### Post by CharlesA on 2011-02-19
Can I give a +1 to turnkey linux? They have a ton of Virtual appliances that are ready to go.

---

### Post by 1clue on 2011-02-19
In the past, we've had security updates or other system updates, both on Linux or on Windows, that have broken VMware entirely.  If that happens and the core network services are on VMs, then you no longer have a DHCP server or a DNS server or any of another number of things that you would really rather keep, and if those things are gone then basically your network is trashed.

Any kernel upgrade trashes the VMware modules.  Any upgrade of whatever it is that VMware uses trashes the ability of VMware to run.  I want to avoid that on core systems, or have some way of delaying the upgrade of the backup systems for a couple weeks, and have daily notification of broken services on the primary.

At this point I'm considering something like putting a VMware-only operating system on the bare metal.  Not sure what the product name is, but for the office I want the absolutely most reliable, least fuss host.

---

### Post by 1clue on 2011-02-19
BTW, I will almost certainly use some of the turnkey linux images.  Some of them are perfect, and some more are exactly what our customers would want to install as well.

---

### Post by CharlesA on 2011-02-19
I think you are looking for ESXi, as it's a baremetal hypervisor.

---

