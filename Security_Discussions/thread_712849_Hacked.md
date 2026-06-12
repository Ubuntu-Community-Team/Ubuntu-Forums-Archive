---
title: "Hacked??"
date: 2008-03-02
forum: Security Discussions
---

### Post by jsvidyad on 2008-03-02
Hi!!


   How do you find out if you have been hacked??  I was working using my non-sudo account. Suddenly, I was logged out for absolutely no reason. I did not try to log out. I logged back in and scanned my computer using nmap from the same machine. It gave the result:
4984/tcp open  netbios-ssn

What is netbios-ssn??

Also, when I tried to run freshclam after this, I got an error message saying:
ERROR: Log File /var/log/clamav/freshclam.log.
 Does this mean someone altered my logs??

I did not have this problem earlier and freshclam was running fine earlier. I uninstalled clamav , reinstalled it and now freshclam runs fine.

I checked the system monitor. nautilus and trackerd were hogging the system resources. what is trackerd??

   I have firestarter set up and my machine is behind a router. I checked and no other computers other than mine are connected to the wireless network. The router by default does not allow any connections from the internet to machines in the LAN.

   Are these symptoms of my computer being hacked?? Do I need to worry?? Reinstall maybe??

---

### Post by euler_fan on 2008-03-02
[This thread]("http://ubuntuforums.org/showthread.php?t=709663") might be a place to start.

You might also try downloading [one of these LiveCD's]("http://www.darknet.org.uk/2006/03/10-best-security-live-cd-distros-pen-test-forensics-recovery/") and scanning your system with them using rkhunter, chkrootkit, and clamav. No guarentees it'll find anything even if it's there, but it's a place to start.

[This liveCD]("http://www.e-fense.com/helix/contents.php") has both rkhunter and chkrootkit by default but not clamav. Not a major loss as most of what clamav scans for are windows virii.

When in doubt, reinstall and change all your passwords.

---

