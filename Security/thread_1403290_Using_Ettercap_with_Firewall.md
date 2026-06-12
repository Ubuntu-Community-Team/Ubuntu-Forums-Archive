---
title: "Using Ettercap with Firewall"
date: 2010-02-10
forum: Security
---

### Post by therikoxide on 2010-02-10
I bridged a connection using ettercap and have collected a few ips that I would like to block (IP Lag). Similar to what zone alarm and cain and abel accomplish in windows.

I have tried adding the ip to iptables and tried using ufw to no avail.

---

### Post by kiranmurari on 2010-02-10
Hi,

You should use the following ufw commands, so that it configures iptables to
block an IP address.
```
$ sudo ufw enable
$ sudo ufw deny from **A.B.C.D**
```where **A.B.C.D** is the IP you wanted to block.      

Please the How-To: UFW at the following link:
[http://ubuntuforums.org/showthread.php?t=823741](http://ubuntuforums.org/showthread.php?t=823741)

---

### Post by therikoxide on 2010-02-10
I have already tried that and that blocks the traffic to my computer but it doesn't do anything for the bridge that I am doing an arp attack on.

---

### Post by kiranmurari on 2010-02-10
For blocking ARP traffic, you can use ebtables. The rules would be,
```
$ sudo ebtables -A INPUT -i br0 -p ARP -j DROP
$ sudo ebtables -A FORWARD -i br0 -p ARP -j DROP
```If br0 is not the name of your bridge, replace br0 with your bridge name.

---

### Post by therikoxide on 2010-02-10
Im not trying to stop all traffic, just certain ips. I am not trying to defend against ARP attacks.

---

### Post by kiranmurari on 2010-02-11
Hi,

Can you can list out what type of attacks you wanted to block?

---

### Post by kiranmurari on 2010-02-11
Hi,

If you wanted to drop traffic from a specific IP, you can add the following rule:
```
# iptables -I INPUT -i br0 -s A.B.C.D -j DROP
```where,
br0 - Name of the bridge.
A.B.C.D - IP address to be blocked.

Hope this helps.

---

### Post by therikoxide on 2010-02-11
Thank you for your help thus far. I am still unable to do what I hope to do tho.

I am using ettercap and gathering IPs by doing an ARP attack. I want to find a way to interrupt the data stream to certain ips. I am using unified bridging if that makes a difference.

Example: On Xbox live I can arp attack and find the ips of the people I am playing the game with. I would like to be able to "lag" them out of the lobby of the game. (Like what one can do with Zone Alarm and Cain and Abel).

---

### Post by HPD2 on 2010-02-11
You do know that doing that that is against the Xbox Live TOU and is considered cheating correct.
TOU
["use any unauthorized means to modify or reroute, or attempt to modify or reroute, the Service"]("http://www.xbox.com/en-US/legal/LiveTOU.htm") -Section 5 bullet 6. 
["damage, disable, overburden, or impair the Service (or the networks connected to the Service) or interfere with anyone else's ability to access or use the Service"]("http://www.xbox.com/en-US/legal/LiveTOU.htm") - Section 5 bullet 7
COC
["Don't cheat in a game unless cheats have been deliberately enabled."]("http://www.xbox.com/en-us/legal/codeofconduct.htm") - Section 1 bullet 9

You should read these.
[Code of Conduct]("http://www.xbox.com/en-us/legal/codeofconduct.htm")
[Terms of Use]("http://www.xbox.com/en-US/legal/LiveTOU.htm")

---

### Post by cariboo on 2010-02-11
> **HPD2 said:**
> You do know that doing that that is against the Xbox Live TOU and is considered cheating correct.
TOU
["use any unauthorized means to modify or reroute, or attempt to modify or reroute, the Service"]("http://www.xbox.com/en-US/legal/LiveTOU.htm") -Section 5 bullet 6. 
["damage, disable, overburden, or impair the Service (or the networks connected to the Service) or interfere with anyone else's ability to access or use the Service"]("http://www.xbox.com/en-US/legal/LiveTOU.htm") - Section 5 bullet 7
COC
["Don't cheat in a game unless cheats have been deliberately enabled."]("http://www.xbox.com/en-us/legal/codeofconduct.htm") - Section 1 bullet 9

You should read these.
[Code of Conduct]("http://www.xbox.com/en-us/legal/codeofconduct.htm")
[Terms of Use]("http://www.xbox.com/en-US/legal/LiveTOU.htm")

With the above, this thread is closed. We don't support this type of activity in the forums.

---

