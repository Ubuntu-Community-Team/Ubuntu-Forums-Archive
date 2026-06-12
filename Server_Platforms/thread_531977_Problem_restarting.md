---
title: "Problem restarting"
date: 2007-08-22
forum: Server Platforms
---

### Post by Viruk on 2007-08-22
Hi, 

I have been running a dapper server for almost a year now and its been working great. I have just started to monitor it with Cacti (so installed snmpd), however when I try to restart the server it stops responding before restarting. 

I usually run ubuntu servers with only power and network plugged in but I have had to connect this server to one of the KVMs to check out what was going on. 

Everything appears to be running ok while the server is up, its just the restart that causes problems. 

This problem has happened 3 times now, the first twice it happened when restarting the server via Putty, then this morning I checked it while connected to the KVM. 

When I tried to restart it I saw the usual messages (such as * INIT: Switching to runlevel: 6, * INIT: Sending processes the TERM signal, followed by [OK] at the end of each line) up to the point where snmpd is mentioned. I get the line "Stopping network management services: snmpd snmpdtrapd" but there is no [OK] displayed. The messages about services stopping then continue. 

The last two lines I see are:
* will now reboot
[42949466.540000] Restarting system.

Then the system appears to hang at this point, keyboard stops responding (caps lock/num lock stop having an effect) and the system just sits there. 

If I then hit reset on the server itself it starts up and appears to run ok again. 

Has anyone got any ideas what might be giong on or what I need to do to resolve this?

---

### Post by a9k on 2007-08-23
I would try a couple things:

1) Check that snmpd shuts down from the init script manually.
run the command [COLOR="Blue"]ps ax | grep snmp[/COLOR] which should give you the pid's of running snmp programs. Then run[COLOR="Blue"] /etc/init.d/snmpd stop[/COLOR] and rerun the ps bit above -- the snmp programs should be gone. If not, the init script isn't doing a good job of killing them. If it does kill off the snmpd with out hanging then try the next thing.

2) I would make sure the server is still capable of restarting without snmpd. (Past kernel upgrades have messed up my restart/shutdown due to ACPI tweeks)
I would edit the snmpd/snmptrapd init.d scripts and insert an exit near the top.
Then restart (it shoudl still screw up the first time but the second time you should be rid of snmpd and it should restart OK. If not, something else is holding up reboot.

---

### Post by Viruk on 2007-08-29
Thanks for your response. I have not had time to check this out yet but I'll have a look when I can and post back what I find :)

---

