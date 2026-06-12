---
title: "detect packet sniffers?"
date: 2013-06-24
forum: Security
---

### Post by kr651129 on 2013-06-24
Is there some good software anyone recomends to detect packet sniffers?

---

### Post by TylerD75 on 2013-06-25
That can only be done if someone installed a packet sniffer on your computer (intentionally or by a virus).
ifconfig should tell you if your interface is in promiscuous-mode, which usually indicates that a sniffer is running.
Unless of course you have a root-kit installed on your computer (which would possibly replace the ifconfig command with a modified one).
If you suspect your computer to be compromised, you could try tripwire to detect any root-kits.

If you suspect that someone has placed a packet sniffer on your LAN/network, you should replace any hubs with switches, as that will stop broadcasting to ALL computers on your network.
But then again, if there's a router/gateway with a packet sniffer installed (out of your control) you have a problem. 

You can prevent sniffing by using an encrypted VPN to some external VPN provider, or by simply not using HTTP or other unencrypted connections.  But sniffing is a passive attack, which means no actual activity is required from the sniffer, which in turn makes this VERY hard to detect remotely.

Martin

---

### Post by Cheesemill on 2013-06-25
> **TylerD75 said:**
> If you suspect that someone has placed a packet sniffer on your LAN/network, you should replace any hubs with switches, as that will stop broadcasting to ALL computers on your network.

This doesn't really help. Most switches can be made to fall back into hub mode by overloading the MAC address table with invalid data.

---

### Post by TylerD75 on 2013-06-25
True, and I didn't really mean it as a solution, just a suggestion...

---

### Post by kr651129 on 2013-06-25
It's not that I think there is a packet sniffer on my network, I'm just wondering in general.  I've used them on my own network before and was just looking to understand the other side of the security a little more by asking the question.

---

### Post by CharlesA on 2013-06-25
Most of the packet sniffers I have used - Wireshark, TCPdump whatever have been used via port mirroring, so they would be hard to detect anymore.

---

### Post by unspawn on 2013-06-25
> **TylerD75 said:**
> ifconfig should tell you if your interface is in promiscuous-mode, which usually indicates that a sniffer is running.Not quite. [I'll recycle an old post](http://www.linuxquestions.org/questions/linux-security-4/ifconfig-donot-report-the-promiscous-mode-when-ethereal-is-running-658957/#post3229656) if I may.> **TylerD75 said:**
> If you suspect your computer to be compromised, you could try tripwire to detect any root-kits.Not at all. First of all if one suspects a machine is compromised then *the best thing to do to aid an intruder is to make any changes to the file system* (including modifying, deleting, installing or re-installing *anything* or rebooting the machine) or more destructively: advise the "victim" to re-install the OS from scratch. (The latter is particularly common advice but without proper analysis the loophole(s) could easily be exposed again.) Secondly after-the-fact tools like Samhain, AIDE, debsums or even tripwire *require hashes to be generated and stored before usage*. And even if hashes were stored beforehand these tools still can only detect changes to the file system. So if a "true" rootkit (there's not that many anymore) properly hides files that weren't part of the hash set they won't detect those. And they won't detect processes running in plain sight, processes running in memory only or processes that are properly hidden (see 'unhide'). This should illustrate why proper incident handling procedure and post-mortem analysis (using a Live CD on the corpse or an image of the system with forensics software), apart from those situations where tools are suspected to be used that reside in memory only, *still* have a value.HTH

---

