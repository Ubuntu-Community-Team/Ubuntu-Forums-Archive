---
title: "A question about security"
date: 2008-04-28
forum: Virtualisation
---

### Post by akimatsu123 on 2008-04-28
Hi,

I am running win xp professional through virtualbox on hardy. i have win xp sp2 installed. usually, i would also install a virus scanner and zonelabs firewall.

i was just wondering, is this necessary for virturalization? i would rather not because it eats up my RAM. is there a danger, for example, that someone will hack into my windows, then hack into my ubuntu through the shared folder which shows up as a network?

in that face, i was thinking they would be able to change any settings or documents they want, since no sudo permissions exist in windows. is this a threat? i would really, really prefer not to install zonelabs and a virus scan. 

if it helps, i have firestarter installed on hardy. 

thanks,

---

### Post by JohnFH on 2008-04-28
You don't need to install firewalls or anti-virus s/w on Windows if you have configured your virtual machine to have no network card.  Attacks then have to come through your secure Ubuntu OS first.

---

### Post by agent8131 on 2008-04-29
> **akimatsu123 said:**
> 
 is there a danger, for example, that someone will hack into my windows, then hack into my ubuntu through the shared folder which shows up as a network?


Is there a danger?  Yes.  Is it very likely?  No.

A virtual Windows machine can still be compromised.  I run both a firewall and anti-virus on my virtual Windows machine.  However, whether you need that depends on your risk assessment.  Most likely a compromise to the Windows system won't result in a compromise to the Ubuntu host.  Someone who compromises your Windows system would most likely use it to send spam or engage in further internet attacks.  So you should think about what you use the Windows system for, does it have any valuable data, if it were compromised would it be easier to just start fresh than to constantly deal with securing Windows and similar issues.

One great thing about virtualization is that you can always keep extra disk images.  So if you have a system you know is clean you can make a backup and if the one you run becomes compromised just copy from the backup and secure whatever caused the compromise.

There's also some middle ground, like relying on the Windows XP firewall and setting your virus scanner to its fastest settings.  I haven't used ZoneAlarm in a while; I gave it up because it was too bloated and there are plenty of alternatives.

---

