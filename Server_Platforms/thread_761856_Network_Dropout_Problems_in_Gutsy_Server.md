---
title: "Network Dropout Problems in Gutsy Server"
date: 2008-04-21
forum: Server Platforms
---

### Post by daphreak on 2008-04-21
I am currently running at file server with gutsy and from time to time it stops responding to anything on the network (pings, ssh, samba). It becomes inaccessible from the LAN and from the outside. Sometimes I can "wait it out" and it will begin working again. Sometimes I have to find a monitor and keyboard and manually /etc/init.d/networking restart.

Interestingly enough, I have found some stimulus such as pings seem to reduce the amount of time I have to wait for it to come back up. Is there a feature in hardware for maybe the network card to sleep and save power?

Any ideas? I will be upgrading to Hardy server soon for the LTS so my problems may or may not disappear in transit, but if it is a hardware issue I need to address it.

---

### Post by ryanradford on 2008-04-21
Do you see anything interesting if you:

tail -f /var/log/syslog

Another thing to try. Type ifconfig when the server is "down" and see if the address has changed to a dynamic one. You may have to kill the dhcp process if you configured a static address but haven't rebooted the server:

ps auxw | grep dhclient

sudo kill (pid)

Just my initial thoughts. The syslog should tell you if there is something going on, but more information would be helpful.

---

### Post by daphreak on 2008-04-22
Aha! It appears dhclient is running. I suppose that is kind of unnecessary with my static IP. Is there a way I can disable it on that specific interface?

EDIT: Syslog contains lots of dhcp errors, so that further confirms this is likely the culprit.

---

