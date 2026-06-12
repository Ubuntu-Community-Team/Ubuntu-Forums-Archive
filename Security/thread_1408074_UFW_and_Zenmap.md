---
title: "UFW and Zenmap"
date: 2010-02-15
forum: Security
---

### Post by uRock on 2010-02-15
This is the difference in the output of a port scan using Zenmap on the same system with UFW turned off and then with it turned on. It is obvious that UFW works.

---

### Post by uRock on 2010-02-16
Tomorrow I will run the same test against Firestarter. I will include whether or not Firestarter announces a port scan in progress. This test is very fun to watch while running Wireshark.

I also plan on testing against the Windows 7 factory firewall to see how it stands up.

---

### Post by cariboo on 2010-02-16
Are you running the port scans from outside you internal network?

---

### Post by uRock on 2010-02-16
> **cariboo907 said:**
> Are you running the port scans from outside you internal network?

No. I just wanted to see what the OS firewalls do to block port scans. I am sure that with NAT things will be much different. I also don't know how many laws I might be breaking, if any, by doing port scans across media that I don't own. That does give me an idea for a great use of my spare time in the Cisco labs.

---

### Post by uRock on 2010-02-16
Scanned a Windows 7 system with Zenmap.

---

### Post by dogdo on 2010-02-16
> **iRock said:**
> Scanned a Windows 7 system with Zenmap.

Hold on 992 ports filtered and 10 ports open-so the windows 7 firewall was turned on when you scanned the client???

Thats a terrible result-why not install comodo firewall set to high security and post back the zenmap scan of that?

---

### Post by uRock on 2010-02-16
> **dogdo said:**
> Hold on 992 ports filtered and 10 ports open-so the windows 7 firewall was turned on when you scanned the client???

Thats a terrible result-why not install comodo firewall set to high security and post back the zenmap scan of that?

Yup, the stock firewall was running.

I have NAT on the router. I scanned from within the network. I only boot Windows 7 once or twice a week. I plan on running more tests against Ubuntu. Though I may install a firewall on my wife's W7 system and see how it does.

Is Comodo free?

---

