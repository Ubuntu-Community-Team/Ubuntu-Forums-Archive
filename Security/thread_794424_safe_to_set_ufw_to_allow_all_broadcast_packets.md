---
title: "safe to set ufw to allow all broadcast packets?"
date: 2008-05-14
forum: Security
---

### Post by zeus77 on 2008-05-14
I'm using ufw, the "uncomplicated firewall", and have a fairly standard setup where everything except incoming port 22 (ssh) gets denied.  However, my syslog gets filled up with tons of junk like this:
```
[UFW BLOCK INPUT]: IN=eth0 OUT= MAC=[scrubbed] SRC=[scrubbed] DST=255.255.255.255 LEN=207 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=631 DPT=631 LEN=187
```
which I believe are broadcast packets from CUPS printers on the network, etc.  I would like to keep ufw logging enabled, but would like these events to stop appearing in the log.  One simple solution is to just allow all packets destined to 255.255.255.255 (i.e. those destined to the standard limited broadcast address) which can be accomplished with
```
sudo ufw allow to 255.255.255.255
```
Is there any danger in allowing all incoming broadcast packets?  

Thanks,
zeus77

---

### Post by zeus77 on 2008-06-12
anyone?

---

### Post by kevdog on 2008-06-12
Isnt that the cups driver listening on the loopback interface?  I think its safe to allow all incoming packets that originate from the loopback address of 127.0.0.1.

---

### Post by kevdog on 2008-06-12
Sorry -- I just reread your problem,  How are you setting your logging parameter in your ruleset?  Also do you want to allow incoming traffic on port 631 or do you want to block it and not log it, or do you just want to allow incoming traffic for your LAN, and block access from everywhere else?

---

### Post by brian_p on 2008-06-12
> **zeus77 said:**
> anyone?

What is the setting for browsing in your /etc/cupsd.conf? On or off?

---

### Post by The Cog on 2008-06-14
The packet is coming **in** on eth0 - it is coming from another PC. So his cups config on this PC is irrelevant.

You should **not** allow all broadcasts in - it would be entirely possible for an attacker to perform a complete connection to any service using broadcast packets. You should either allow broadcasts to UDP port 631 from port 631, or stop logging the drops, or stop worrying about the log messages. 

Alternatively, if you're not running any listening services turn the sodding firewall off and stop wasting time and sleep over it.

---

### Post by brian_p on 2008-06-14
> **The Cog said:**
> The packet is coming **in** on eth0

I realise that.

>  - it is coming from another PC. So his cups config on this PC is irrelevant.

It's entirely relevant.

Option 1: If he wants to know what printers are available on the network he will want "Browsing On" in his cupsd.conf to pick up the broadcast UDP announcements. Firewalling port 631 will work against this.

Option 2: If he does not want to know what printers are available on the network he will want "Browsing Off" so that cups does not listen to the broadcast UDP announcements. Firewalling doesn't add anything.

> Alternatively, if you're not running any listening services turn the sodding firewall off and stop wasting time and sleep over it.

We could be in agreement here but bear in mind he may want to print to the local machine.

---

### Post by zeus77 on 2008-06-17
Thanks for the replies.  I do not need cups browsing (and it is currently set to off).  I do, however, print to cups printers on the network and would not want to block, say, status messages from the printer... though I doubt these are broadcast messages, but really have no idea.

Also, I **do** need a firewall, as I have listening services and only want to allow access to specific IP addresses.

I guess I need to figure out how to stop logging the drops... would be nice to only stop logging the frequent CUPS broadcasts, but maybe that's not possible.  If you have any clues here, I'd appreciate it.  Otherwise, thanks to all for the info.

zeus77

---

### Post by brian_p on 2008-06-17
> **zeus77 said:**
> Thanks for the replies.  I do not need cups browsing (and it is currently set to off).  I do, however, print to cups printers on the network and would not want to block, say, status messages from the printer... though I doubt these are broadcast messages, but really have no idea.

Intriguing. With 'Browsing Off' my cups can see no network printers (lpstat -a shows only local printers). How does yours manage to print?

> I guess I need to figure out how to stop logging the drops... would be nice to only stop logging the frequent CUPS broadcasts, but maybe that's not possible.

Have a peek at /usr/share/ufw/after.rules. Anything there which might solve your problem?

---

