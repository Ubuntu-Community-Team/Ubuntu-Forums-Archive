---
title: "Can't find lokkit on Synaptic"
date: 2009-04-17
forum: Security
---

### Post by mrl777 on 2009-04-17
Hello,

I cannot find lokkit on the synaptic package manager.  I have multiverse enabled.  I cannot install it from the "http://packages.ubuntu.com/dapper/i386/lokkit/download"?  It gives me a dependency error.   Gees man... the Linux stuff is a pain in the.....  I may as well go back to XP.

Also, I have someone geting to my system and locking me out of the internet.  How can I reload the critical files that deal with internet / networking.  I have to reload the OS when this happens.

Also, I need to monitor what IP address the system is communicating with and then block them.  I don't want to write scripts. NO NO NO. I just want to click and create a rule to block it.

Sheesssss....

---

### Post by Cybie257 on 2009-04-17
> **mrl777 said:**
> Hello,

Also, I need to monitor what IP address the system is communicating with and then block them.  I don't want to write scripts. NO NO NO. I just want to click and create a rule to block it.

Sheesssss....

Install Firestarter Firewall. This will show you what is going on and let you configure those IP to be blocked. Not a lot of experience with it, bt if I remember correctly, you can just right click on suspicious connections (IP's) and block them. That seems like the easiest route for now. :)

-Cybie

EDIT: I wasn't sure what lokkit was at first (never used it). Firestarter would probably do you fine. So try that to solve the lokkit issue. :) As far as I see, lokkit is just another firewall. Maybe better, maybe not??? hope this helps.

---

### Post by cariboo on 2009-04-18
Lokkit is just another firewall gui. The prefered iptables frontend is either ufw for the console or gufw. Ufw is installed by default, gufw is in the repositories.

Jim

---

### Post by Chemical Imbalance on 2009-04-18
What ^ said.  Firestarter is deprecated as well as Lokkit (no longer developed and maintained).  These are all only gui front-ends to the firewall in the linux kernel--remember that.

Also, I highly recommend you update to a newer version of Ubuntu from your current Dapper install.  All updates and support will cease for this version on June 1st, 2009.

---

### Post by nutsy.ben on 2010-08-08
> **mrl777 said:**
> Hello,

I cannot find lokkit on the synaptic package manager.  I have multiverse enabled.  I cannot install it from the "http://packages.ubuntu.com/dapper/i386/lokkit/download"?  It gives me a dependency error.   Gees man... the Linux stuff is a pain in the.....  I may as well go back to XP.

Also, I have someone geting to my system and locking me out of the internet.  How can I reload the critical files that deal with internet / networking.  I have to reload the OS when this happens.

Also, I need to monitor what IP address the system is communicating with and then block them.  I don't want to write scripts. NO NO NO. I just want to click and create a rule to block it.

Sheesssss....

Go back to XP ... ^^
Ubuntu is designed for patient and rigorous persons !!

Otherwise, firestarter gives much better results. It's stable and never failed me.

---

