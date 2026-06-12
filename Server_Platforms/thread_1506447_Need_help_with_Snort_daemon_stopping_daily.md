---
title: "Need help with Snort daemon stopping daily"
date: 2010-06-10
forum: Server Platforms
---

### Post by Steve227 on 2010-06-10
I'm having an issue with Snort daemon stopping daily at around 6:30am.  I've been searching for an answer on this for a while.  I'm stuck.

Snort is working fine when machine rebooted, or manually with "sudo /etc/init.d/rc.local start", but then stops everyday around the same time.

From looking at the system messages, it looks like the issue may be with something being reset at the same time as the log rotation.

----------------------

From /var/log/messages:

Jun  8 06:25:03 snort -- MARK --
Jun  8 06:36:42 snort kernel: [4815245.823051] device eth1 left  promiscuous mode
Jun  8 06:36:42 snort kernel: [4815245.823060]  audit(1275993402.213:133): dev=eth1 prom=0 old_prom=256 auid=4294967295
Jun  8 06:36:42 snort syslogd 1.5.0#1ubuntu1: restart.
Jun  8 07:05:03 snort -- MARK --

Jun  9 06:52:36 snort -- MARK --
Jun  9 06:53:11 snort kernel: [67206.491051] device eth1 left promiscuous mode
Jun  9 06:53:11 snort kernel: [67206.491062] audit(1276080791.357:5): dev=eth1 prom=0 old_prom=256 auid=4294967295
Jun  9 06:53:14 snort syslogd 1.5.0#1ubuntu1: restart.
Jun  9 07:12:36 snort -- MARK --

Jun 10 06:12:38 snort -- MARK --
Jun 10 06:26:28 snort kernel: [151877.354770] device eth1 left promiscuous mode
Jun 10 06:26:28 snort kernel: [151877.354781] audit(1276165588.597:9): dev=eth1 prom=0 old_prom=256 auid=4294967295
Jun 10 06:26:29 snort syslogd 1.5.0#1ubuntu1: restart.
Jun 10 06:52:38 snort -- MARK --

----------------------

Start up in /etc/rc.local:

/usr/sbin/snort -D -u snort -g snort \
        -c /etc/snort/snort.conf -i eth1

----------------------

System Info:

Ubuntu 8.04.4 LTS

Snort Version 2.7.0

----------------------

Thanks in advance for your help.

---

### Post by Steve227 on 2010-06-15
Anyone?  This is still an issue for me.  Thanks.

---

### Post by WinstonChurchill on 2010-06-15
Did you set up that rc.local script yourself? When I installed Snort, the package had an init script included at /etc/init.d/snort. Maybe you should just let it use that one?
I'd do this and see if it fixes it:
```
sudo aptitude purge snort
sudo aptitude install snort
```If you've made any configuration changes at all, make sure to save the config files somewhere else so you don't lose them (the 'purge' will delete them) - if that's the case, try running for awhile without your changes, and if it stops being weird, you know it was some config you did that's causing the problem.

---

