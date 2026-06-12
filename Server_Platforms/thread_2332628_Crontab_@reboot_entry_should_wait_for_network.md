---
title: "Crontab @reboot entry should wait for network"
date: 2016-08-02
forum: Server Platforms
---

### Post by smeerbartje on 2016-08-02
In my crontab I have a "@reboot" entry which triggers a shell script which sends out the actual external IP to mail email address. This USED to work for 14.04 LTS, but not for 16.04 LTS. For some reason, the shell script gets triggered at the moment the network is not active yet. I have "dead.letters" in my home directory which look like this:

```
Host 'server' has booted up.
External address is:
Internal addres is: 192.168.x.x
Date: Thu Jul 28 11:18:52 UTC 2016

dig: couldn't get address for 'resolver1.opendns.com': failure
mail: Cannot open smtp.gmail.com:587

```
Any idea how to fix this? How can I let a crontab @reboot entry wait for the network stack to be fully loaded?

---

### Post by Tadaen_Sylvermane on 2016-08-03
Create a proper systemd service is what I would do.

---

