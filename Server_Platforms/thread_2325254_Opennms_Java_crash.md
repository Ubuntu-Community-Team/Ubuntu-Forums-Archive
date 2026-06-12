---
title: "Opennms Java crash"
date: 2016-05-20
forum: Server Platforms
---

### Post by paintballer4lfe on 2016-05-20
Since opennms has a terrible support system i'm stucking having to post my issue here.
I am new to the SNMP management side, especially network monitoring scripts.

But i had my opennms working for a few days no issues, i shut down my VM guest running ubuntu server and the server itself and opennms so i could install a new NIC add on card.
After i added it and reconfigured my windows VM guest to use one port off of the new card i went to power on my Ubuntu.

Opennms wouldn't load and now im getting java errors and VMware opennms monitor errors. I've had a few issues previously with opennms and i just did clean installs(java 7 and 8 issues).
It fixed those problems but now this is something completely different and im not sure what to do or where to start.

I have attached the the log file with a few different tries to load opennms if someone could help me that'd be great. [ATTACH]269185[/ATTACH]

---

### Post by paintballer4lfe on 2016-05-23
Update for anyone who is looking at this for more help.

I added a few HP iLO poller configs into the poller-configuration.xml and it was causing the java errors.
That's what fixed my issue.

---

