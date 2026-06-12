---
title: "No connection to SSH after updates / reboot"
date: 2011-04-02
forum: Server Platforms
---

### Post by pazza98 on 2011-04-02
Hi. I'm running Ubuntu 10.04 LTS. Last night I was doing some admin on this box, it's running apache and ASSP for spam filtering. Once I finished I started some updates.

sudo aptitude

I checked for updates and applied them, but fell asleep. This morning, my session had timed out at continue. I reconnected and saw a message stating a reboot was required.

I've rebooted, my usual services are running, eg apache and ASSP. I can view pages on apache and the admin page for ASSP. I'm remote from the system, so connecting over the internet and when I try to connect, it fails

"PuTTY Fatal Error

Network error: Connection refused."

I've got access to another system on the same network, this gets the same result. If I can get the system rebooted, is SSH likely to start working again?

Quite urgent, however at least my services are working. However I'm not happy that I can't access the system myself.

Any suggestions or insight?

I don't know if this is my own fault for leaving updates unattended or if an update caused the problem. Thanks.

---

### Post by CharlesA on 2011-04-02
Try to telnet to port 22 (or whatever port SSH is running on), to see if it gives you are response.

---

### Post by pazza98 on 2011-04-02
Result of connection attempt with telnet:

Microsoft Telnet> open x.x.x.x 22
Connecting To x.x.x.x...Could not open connection to the host, on port 22: Connect failed

---

### Post by pazza98 on 2011-04-02
Incident resolved. I managed to get remote hands to the linux box. After another reboot, SSH is now working again.

Does anyone know if there's a way to check any log files for a reason why SSH didn't come up after the previous reboot? Is there a boot log or something which would show an error when attempting to start sshd?

---

### Post by CharlesA on 2011-04-02
Could check dmesg, but I doubt it would show anything about sshd. Could try checking /var/log/boot.log to see if it fails to start at boot or not.

---

### Post by pazza98 on 2011-04-02
I couldn't find anything good in either of those logs, however the aptitude log file in 

/var/log

Contained

[UPGRADE] openssh-client 1:5.3p1-3ubuntu5 -> 1:5.3p1-3ubuntu6
[UPGRADE] openssh-server 1:5.3p1-3ubuntu5 -> 1:5.3p1-3ubuntu6

Perhaps the openshh-server upgrade was the problem, especially as I wasn't able to complete the actions (only in terms of hitting enter to continue, which I think would bring me back to the aptitude interface).

Likely cause?

---

### Post by d3v1150m471c on 2011-04-02
post the output of this please and remove any personal information.
```

sudo nmap -sS -p 22 your.ip.goes.here

```

edit:
nvm, didn't notice that you'd solved the problem.

---

### Post by CharlesA on 2011-04-02
> **pazza98 said:**
> I couldn't find anything good in either of those logs, however the aptitude log file in 

/var/log

Contained

[UPGRADE] openssh-client 1:5.3p1-3ubuntu5 -> 1:5.3p1-3ubuntu6
[UPGRADE] openssh-server 1:5.3p1-3ubuntu5 -> 1:5.3p1-3ubuntu6

Perhaps the openshh-server upgrade was the problem, especially as I wasn't able to complete the actions (only in terms of hitting enter to continue, which I think would bring me back to the aptitude interface).

Likely cause?
Could be.

I haven't heard of an update to openssh-server causing it to not start. *shrugs*

It kinda sounds like sshd wasn't started back up after the update.

---

### Post by pazza98 on 2011-04-02
Found something else looking through various logs:


Apr  2 10:28:05 cat-ubuntu init: ssh main process (731) terminated with status 255
Apr  2 10:28:05 cat-ubuntu init: ssh main process ended, respawning
Apr  2 10:28:05 cat-ubuntu init: ssh main process (825) terminated with status 255
Apr  2 10:28:05 cat-ubuntu init: ssh main process ended, respawning
Apr  2 10:28:05 cat-ubuntu init: ssh main process (830) terminated with status 255
Apr  2 10:28:05 cat-ubuntu init: ssh main process ended, respawning
Apr  2 10:28:05 cat-ubuntu init: ssh main process (833) terminated with status 255
Apr  2 10:28:05 cat-ubuntu init: ssh main process ended, respawning
Apr  2 10:28:05 cat-ubuntu init: ssh main process (836) terminated with status 255
Apr  2 10:28:05 cat-ubuntu init: ssh main process ended, respawning
Apr  2 10:28:05 cat-ubuntu init: ssh main process (839) terminated with status 255
Apr  2 10:28:05 cat-ubuntu init: ssh main process ended, respawning
Apr  2 10:28:06 cat-ubuntu init: ssh main process (842) terminated with status 255
Apr  2 10:28:06 cat-ubuntu init: ssh main process ended, respawning
Apr  2 10:28:06 cat-ubuntu init: ssh main process (845) terminated with status 255
Apr  2 10:28:06 cat-ubuntu init: ssh main process ended, respawning
Apr  2 10:28:06 cat-ubuntu init: ssh main process (848) terminated with status 255
Apr  2 10:28:06 cat-ubuntu init: ssh main process ended, respawning
Apr  2 10:28:06 cat-ubuntu init: ssh main process (852) terminated with status 255
Apr  2 10:28:06 cat-ubuntu init: ssh main process ended, respawning
Apr  2 10:28:06 cat-ubuntu init: ssh main process (855) terminated with status 255
Apr  2 10:28:06 cat-ubuntu init: ssh respawning too fast, stopped

in daemon.log

Looks like terminated with status 255 is the key to this. I guess after it was rebooted, it started up again, without the previous issue. Was there any way I could have remote started ssh without using ssh to connect or have physical access?

---

