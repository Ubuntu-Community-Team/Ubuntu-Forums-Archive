---
title: "Nessus Scan &quot;Damage&quot;?"
date: 2013-02-08
forum: Security
---

### Post by Roskow on 2013-02-08
I'm in a college cyber security program and experimenting with different tools. I'm throwing Nessus at Virtual Machines.  

I have heard that Nessus is very aggressive and could cause "Damage". I'm thinking this is similar to recovering from a DoS attack at most, but thought I would check. 

Also, since I'm hitting classmates VMs I figured the worst that would happen is having to go back one Snapshot.

---

### Post by haqking on 2013-02-08
> **Roskow said:**
> I'm in a college cyber security program and experimenting with different tools. I'm throwing Nessus at Virtual Machines.  

I have heard that Nessus is very aggressive and could cause "Damage". I'm thinking this is similar to recovering from a DoS attack at most, but thought I would check. 

Also, since I'm hitting classmates VMs I figured the worst that would happen is having to go back one Snapshot.

Any vulnerability scanner and certainly Nessus can cause potential issues such as DoS, but alot depends on type of scan and the plugins you have.

They are also very noise in terms of a IDS or IPS etc.

That being said all scanners now do default scans with "dangerous" plugins disabled.

it depends on what you ask it to do, I suggest reading the guide at [http://static.tenable.com/documentation/**nessus**_5.0_user_guide.pdf]("http://static.tenable.com/documentation/nessus_5.0_user_guide.pdf")

---

### Post by Roskow on 2013-02-08
Well the "Damage" description I read was vague, so I guess I wanted to be sure that was just DoS related and there wasn't something else I was missing. 

My understanding is you might knock out a server.  It's more of a warning for Admins to schedule a test during off hours and use of the server being pen tested isn't critical.  

Just wanted to see if that is basically accurate. If there is another damage potential I wanted to know if I'm going to break something.

---

### Post by haqking on 2013-02-08
> **Roskow said:**
> Well the "Damage" description I read was vague, so I guess I wanted to be sure that was just DoS related and there wasn't something else I was missing. 

My understanding is you might knock out a server.  It's more of a warning for Admins to schedule a test during off hours and use of the server being pen tested isn't critical.  

Just wanted to see if that is basically accurate. If there is another damage potential I wanted to know if I'm going to break something.

You mentioned pen-tested ?

Doing a vulnerability assessment and a pen-test are 2 completely different things you know that right ?

Nessus is a vulnerability scanner.

Carrying out a vulnerability assessment is not a pen-test, however during a pen-test you might carry out a scan from something like Nessus or Nexpose, OpenVAS, etc.


When you configure Nessus to do a scan there is an option to disable all plugins considered dangerous, and you can look through the plugins

And yes you might knock out a server ;-)  Pen-testing and vulnerability assessment presume you know what you are doing 

You can see all 53 thousand or so plugins available currently here [http://www.tenable.com/plugins/index.php?view=all](http://www.tenable.com/plugins/index.php?view=all)

Make sure you utilize policies for safe checks and dangerous checks save you configuring it each time

Peace

---

### Post by Roskow on 2013-02-08
Okay thanks for the feedback.

---

### Post by Ms. Daisy on 2013-02-09
Depending on the network architecture, you can kill a firewall and your own scan when transversing firewalls. I'm sure there are numerous other ways for things to go wrong. The key is to read the documentation and keep an eye on things.

---

