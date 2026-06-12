---
title: "Security"
date: 2010-09-06
forum: Security
---

### Post by olddai on 2010-09-06
I have only just got online and would like to know if it is worth installing an anti-virus + firewall on my computer. I am running Ubuntu 10.04. Thanks every one!

---

### Post by olddai on 2010-09-06
I have installed Clamtk via synaptic but i was informed that: The antivirus engine is reporting an outdated engine and that a newer version is available. Also how do i update the program? Anyone please

---

### Post by OpSecShellshock on 2010-09-06
Anti-virus is not necessary and the firewall is already there. Clamtk won't tell you much because it's really only looking for Windows malware (and maybe a sprinkling of really old and obvious Linux stuff).

---

### Post by Rubi1200 on 2010-09-06
> **OpSecShellshock said:**
> Anti-virus is not necessary and the firewall is already there. Clamtk won't tell you much because it's really only looking for Windows malware (and maybe a sprinkling of really old and obvious Linux stuff).
+1
See here for more information:
[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

(by the way, this is probably about to be moved to Recurring Discussions soon :-))

---

### Post by howefield on 2010-09-06
Have a browse through these links, your questions are well taken care of there, and if you have any left unanswered after that, post again.


[https://help.ubuntu.com/community/Security](https://help.ubuntu.com/community/Security)
[https://help.ubuntu.com/community/Antivirus](https://help.ubuntu.com/community/Antivirus)
[https://help.ubuntu.com/community/Linuxvirus](https://help.ubuntu.com/community/Linuxvirus)

---

### Post by olddai on 2010-09-06
Thanks for all the replies and links everyone

---

### Post by uRock on 2010-09-06
> **olddai said:**
> I have installed Clamtk via synaptic but i was informed that: The antivirus engine is reporting an outdated engine and that a newer version is available. Also how do i update the program? Anyone please
In the past, I have installed the new ClamTK from the Clam website. They appear to release a new GUI every couple of months.

---

### Post by rookcifer on 2010-09-06
> **olddai said:**
> I have only just got online and would like to know if it is worth installing an anti-virus + firewall on my computer. I am running Ubuntu 10.04. Thanks every one!

No to AV.  And unless you are running a server (ssh, VNC, Apache, samba) then you don't really need a firewall, though it doesn't hurt to turn on UFW anyway.

---

### Post by OpSecShellshock on 2010-09-06
> **rookcifer said:**
> No to AV.  And unless you are running a server (ssh, VNC, Apache, samba) then you don't really need a firewall, though it doesn't hurt to turn on UFW anyway.

I agree, it doesn't hurt, and in fact may help new users. Having ufw enabled should have the result of making users more conscious of when they're running something that is listening for connections to be initiated from the web. That way they won't be starting a server process without having to go out of their way to enable it to work, which (hopefully) will result in greater awareness of how information flows in day-to-day use.

That said, it's not absolutely necessary since iptables is already there, doing its thing.

---

