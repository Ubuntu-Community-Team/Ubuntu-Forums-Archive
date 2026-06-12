---
title: "What do i need or skip - Router - VPN - UFW - Logwatch - Tripwire"
date: 2015-12-25
forum: Security
---

### Post by patrikmellq on 2015-12-25
I want to feel secure with my new Ubuntu computer, but i don't want to be paranoid.
I reckon, Router, UFW, VPN and Logwatch should give me a secure desktop - same as windows 10 with F-Secure firewall - any opinions?
I like logwatch as i use online email software, so if there is a change in system i get email alert in real time from Logwatch.

Any opinios?
I can install and configure Tripwrie, but it need alot of Daily work checking reports and update after every change you make on computer, is not practical and that is why i prefer logwatch.

Cheers

---

### Post by matt_symes on 2015-12-25
Hi

> **patrikmellq said:**
> I want to feel secure with my new Ubuntu computer, but i don't want to be paranoid.
I reckon, Router, UFW, VPN and Logwatch should give me a secure desktop - same as windows 10 with F-Secure firewall - any opinions?
I like logwatch as i use online email software, so if there is a change in system i get email alert in real time from Logwatch.

Any opinios?
I can install and configure Tripwrie, but it need alot of Daily work checking reports and update after every change you make on computer, is not practical and that is why i prefer logwatch.

Cheers

You're more likely to get compromised through your browser or other applications software.

Concentrate your efforts there.

The suggestions you listed are also fine, maybe overkill for a desktop, apart from UFW. 

You plan on running VPN server or client software on your desktop ?

See what others think.

EDIT:

Thread moved to **security** sub forum.

Kind regards

---

### Post by HermanAB on 2015-12-27
"You're more likely to get compromised through your browser or other applications software."

Yup.  That is one reason to disable sudo, since a compromised sudo enabled user account can potentially wreck the whole system.

Use loooooooooooooooong unique passwords for each and every account and use Keepass to keep track of them all.

Make separate user accounts for all services, so that a compromise of one service cannot wreck the whole system.

Install a MAC system such as AppArmor, or switch distros to one with SELinux, to enforce separation between services, so that a compromise of one service or user account cannot wreck the whole system.

Watch your logs.

That's it really.

---

### Post by Irihapeti on 2015-12-27
Before we ask the OP to go to too much trouble, let's wait until they've told us what they plan to use the machine for.

---

### Post by kevdog on 2015-12-29
Before you go the entire SELinux route -- ouch!!! - maybe just learning iptables is a good idea -- and I'm not just talking ufw here.  I think that its a lot more practical and honestly a lot easier perhaps than SE Linux or AppArmor profiles IMO.  
[IMG]http://imgs.xkcd.com/comics/security.png[/IMG]

---

