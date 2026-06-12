---
title: "Snort maxing a CPU on return from suspend?"
date: 2010-05-10
forum: Security
---

### Post by uRock on 2010-05-10
I am running Lucid on this machine, but I have had this problem on every machine with Snort. When I awaken the system from suspend or hibernation, snort pegs out one of the CPUs.

Any clues why this happens?

Thanks,
Ronnie

---

### Post by uRock on 2010-05-10
Is this a normal thing?

---

### Post by Rubi1200 on 2010-05-11
Hi, uRock.

I was under the impression that Suspend/Hibernate can be problematic with Ubuntu. Have you seen similar problems, for example, after rebooting or taking other actions?

And, since I assume you are running servers, why are you using Suspend/Hibernate?

Also, and I don't know if this helps, but I did see some posts on the Snort forums about high CPU usage. However, they seemed to be mostly related to MySQL.

Hope this helps somehow.

---

### Post by iponeverything on 2010-05-11
I can definitely see why suspend would cause problems for snort. 

Add a script to /etc/acpi/resume.d to have snort comeback last and add a sleep to make sure the network devices that its holding handles for have time to get their act together.

---

### Post by uRock on 2010-05-11
I'll give resume.d a looking at.

I've not had any other problems with sleeping/suspending my ubuntu machines.

I only run snort for a NIDS class I am taking. No servers, yet.

I hadn't thought about Snort needing to come online after the NIC is situated. I am running snort on a Netbook with most of the signatures commented out.

Thanx for the replies?

---

