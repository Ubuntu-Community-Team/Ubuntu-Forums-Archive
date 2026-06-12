---
title: "multi clients point to one syslog server and orginize logs"
date: 2011-06-22
forum: Server Platforms
---

### Post by e24ohm on 2011-06-22
Folks:
I am currently running one syslog server; however, I need to monitor an ASA and Aventail vpn appliance. I have my logging enabled for the ASA; however, is it possible to log the Aventail entries to a different location? Can I put an entree in based on IP address?

For example:
Local4.* /var/logs/asa/asa.log

Local4.* /var/logs/avantail/aventail.log

---

### Post by e24ohm on 2011-06-22
would I have to change the local4.* to another localx.* level?

---

### Post by e24ohm on 2011-06-22
Not sure if I have this right, but the Local4 is a ID for the item wanting to be monitored, so in order to monitor different devices I will have to change the localX on the device or client.

Then I will have to update my syslog config file to reflect the different localX IDs from my client.

I guess a few ID will have to log more then one device.

---

