---
title: "Best Antivirus &amp; FIrewall?"
date: 2005-10-23
forum: Server Platforms
---

### Post by Breaks on 2005-10-23
Hey all, whats the best Antivirus and Firewall for ubuntu? anyone got any preferences etc?? and also, i dont need to worry about spyware do i when running ubuntu? if so whats the best anti spyware program also?

Thanks in advance for any replies and information.

Breaks.

---

### Post by Kyral on 2005-10-23
[QUOTE=Breaks]Hey all, whats the best Antivirus and Firewall for ubuntu? anyone got any preferences etc?? and also, i dont need to worry about spyware do i when running ubuntu? if so whats the best anti spyware program also?

Thanks in advance for any replies and information.

Breaks.[/QUOTE]
AV: Not needed unless you are running a mail server or something
Firewall: Might be needed. Firestarter is a good GUI one. Learn IPTables if you are really interested
Anti-Spyware: Not needed PERIOD

---

### Post by Breaks on 2005-10-23
Surely mail server or not you should at least run some sort of anti virus no? i mean viruses full stop can affect any computer running the platform its designed to attack? and thanks for the information :).

**:: Edit ::**

Someone mentioned something called chkrootkit to me? anyone have anymore information on this?

Thanks again in advance :).

Breaks.

---

### Post by Darkhack on 2005-10-23
Antivirus = ClamAV is in my opinion the best.  Easy to install and configure.  Once installed, just set up a cronjob to run freshclam and it will keep it updated.

Firewall = I am actually quite shocked to say the least of the number of people recommending Firestarter.  Not that its bad or anything, but it seems to me that people are really over looking GuardDog which has FAR more options for configuration.  I personally only use Firestarter because it has better support for viewing live activity where as GuardDog is general configuration and doesnt show much of the current status.  So in other words.  Use both GuardDog and Firestarter.  But also learning IPTables is never a bad thing.  Also be sure to scan your system using Nessus and nmap.

Anti-Spyware = Not even an issue.  Don't need one, AT ALL! (its a good thing)

chkrootkit = Check Root Kit is a defense against the closest thing that comes to malware/virus in the linux world.  A rootkit a nasty little program that allows hackers to compromise your system as root.  Most distrobutions automatically set up chkrootkit as a cronjob so that the end user wont have to manually check, although its a good idea to run this yourself every so often.

Thats about it!  Just be sure to take my suggestion of using both GuardDog/Firestarter and running Nessus/nmap thats the most important step to security.

---

### Post by ubutthead on 2005-10-23
What about also setting up Tripwire?

---

### Post by fannymites on 2005-10-23
Antivir or Klamav.  Both have gui's and always on background guards if you think you need em.
Guarddog firewall.  Easy to set up and passes every firewall test I've tried.

---

### Post by Breaks on 2005-10-24
Thanks all for the information, its really appreciated :).

---

