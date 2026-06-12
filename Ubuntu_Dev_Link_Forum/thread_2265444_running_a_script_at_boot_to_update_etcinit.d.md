---
title: "running a script at boot to update /etc/init.d"
date: 2015-02-15
forum: Ubuntu Dev Link Forum
---

### Post by Skaperen on 2015-02-15
i want to run a script at boot time that:
1.A updates or replaces [FONT=courier new]/etc/init.d[/FONT] and/or [FONT=courier new]/etc/rcN.d[/FONT]
1.B needs to run **before** anything in [FONT=courier new]/etc/init.d[/FONT] and/or [FONT=courier new]/etc/rcN.d[/FONT]
2. coded in Python, preferably **2.7** (so Python should be ready to execute ... this is **not** a question _about_ Python)
3. accesses the network via gateway (maybe using [FONT=courier new]rsync[/FONT] and/or [FONT=courier new]curl[/FONT]/[FONT=courier new]wget[/FONT] via [FONT=courier new]subprocess.call()[/FONT] to a host in another LAN)

so where should i insert a call of this script in the early initialization?

---

### Post by ian-weisser on 2015-02-15
1A seems dodgy...or perhaps ill-designed. What are you trying to do that would need to replace it's own start/stop/restart instructions and boot priority every time it runs?
I suspect a less intrusive way is possible.

1B and 3 conflict. Lots of init tasks need to run in order to bring the network up, yet you seem to want to run your task before any of those (even before the filesystem is mounted!)

Sysvinit's replacements, Upstart (12.04, 14.04) and systemd (15.04) offer simple ways to easily control which services come up and when. Lots of extra benefits.

FYI, an ongoing goal of Ubuntu developers is to demote Python2 from main to universe.

---

### Post by Skaperen on 2015-02-17
it is not replacing IT'S OWN
it will be loading new ones over the network
ONE **example** is an NFS mount (need to do this in the script which will get specific instructions over the local networks)
my script will be getting the filesystem over the net which can have new init scripts
it's not about which services i want to come up .... this script is about loading which services scripts need to be there
one option if my script needs to be a sequenced init is to force a reboot in a way to use new devices
this will be run in an AWS EC2 instance.  think "attached EBS volume" or "dynamic configuration".

---

