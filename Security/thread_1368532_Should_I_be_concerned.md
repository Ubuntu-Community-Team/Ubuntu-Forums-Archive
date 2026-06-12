---
title: "Should I be concerned?"
date: 2009-12-30
forum: Security
---

### Post by teward on 2009-12-30
I've got numerous incoming blocked ICMP connections being logged in my firewall.  Should I at all be concerned by this?  they're external network IPs, not local IPs of my network.

---

### Post by rookcifer on 2009-12-30
Normal Internet probes.  Nothing to worry about.

---

### Post by sgosnell on 2009-12-30
You should be concerned if they weren't blocked.  If all the unwanted incoming stuff is blocked, don't worry, be happy.

---

### Post by Project PWNED on 2009-12-31
You will notice that certain attacks come out of certain countries. I cannot name specific countries, like I did previously, or my comment will be removed and I will be "warned" because citizens of that country are hurt by the truth. I manage multiple servers across the world, and have gone through so many firewall logs that I don't do it anymore. You will notice that if you block huge blocks of IP addresses or switch your SSH port to something non-standard like 1234 or 2222 (which a lot of people do so its not helpful anymore), you will cut down on a lot of failed logins and probes.

If you would like to hear about the country I specifically have a problem with, send me a private message, because citizens from that country have voiced concerns to the moderators that I have "personally attacked" them when no member names have even been mentioned because I do not personally know of a forum user from that country.

---

### Post by teward on 2009-12-31
Well, its primarily targetting the ICMP protocol with no port, and the occasional two other ports.  the SSH port on my comp is non-standard so they cant get there.

And the firewall is blocking most else.  just wondering, though.  thanks.

---

### Post by BkkBonanza on 2009-12-31
No doubt this is not a problem. But a few notes about your post...

ICMP is a connectionless protocol so you can receive ICMP packets but not connections.
ICMP is used by ping and traceroute and by other protocols to send conotrl/error messages.

You may have ICMP packets logged because you ping'd someone or tracerouted someone. When you do this the response is to send ICMP messages back to you.
Or it may be someone did that to you and your machine either drops them or fires back a response to them. This is all typical and not cause for suspicion.

A typical scan of a network may start with using ICMP to create a list of machines that are "alive". For this reason some admins will drop all ICMP packets and enhance their ability to be invisible. Nonetheless there are other types of scans that may show presence. If you set your router to drop all inbound ICMP then you no longer have the ability to traceroute/ping others (because you don't get the responses) and they won't see you either.

Finally, moving your ssh to another port doesn't mean "they can't get you there", it just means that default scan scripts for ssh won't detect you initally. Anyone who scans non-regular ports will find you there and then has the same attack vectors as if you were on the default port. Just mentioning this so you don't mistakenly think that changing ports makes you "safe". It just cuts out most of the "flak" from the bulk of the scanning that continually flies around the net.

---

### Post by teward on 2009-12-31
Regarding the SSH port, I'm versed enough in computer security that when I'm on my home network (not the on-campus network provided by my University) to block incoming connections to the port which I run SSH on through the built in firewall on the router.  Nevertheless, I change the port every week (yes, I'm paranoid).

Other than that, i'm running WireShark to trace the packets as they come in, although I blocked all ICMP connections to my computer.

---

