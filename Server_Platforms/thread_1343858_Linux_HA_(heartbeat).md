---
title: "Linux HA (heartbeat)"
date: 2009-12-02
forum: Server Platforms
---

### Post by Zefal on 2009-12-02
Hope someone can help, got 2 ubuntu servers running squid and want then running in active passive HA mode with floating IP. Installed heartbeat on both servers and configured with identical ha.cf, haresources and authkey files (apart from slightly different ucast line obviously).

Baically it seems to work in that failover works and floating IP stays up on standby proxy. But I have an issue where the 'primary' machine boots up heartbeat, takes over resource (floating IP) and then immediately shuts itself (heartbeat) down! to which then the standby machine sees heartbeat drop and takes over IP resource. So seems standby machine works fine, but primary starts up and then shuts itself down..

Config files look like: (commented lines are things I've tried to get it working)

ca.cf:

use_logd on
#udpport 694
keepalive 2
warntime 15
deadtime 30
initdead 30
ucast eth0 10.100.10.149
node uksl-proxy03
node uksl-proxy04
auto_failback on


haresources:

uksl-proxy03 10.100.10.80
#uksl-proxy03 IPaddr2::10.100.10.80/24/eth0

authkeys (chmod 600):

auth 1
1 sha1 password



Log file on primary looks like this: (you can clearly see it start up and then shutdown for no apparent reason):

ingres@uksl-proxy03:~$ tail -f /var/log/ha-log
heartbeat[13739]: 2009/12/01_14:50:04 info: No pkts missing from uksl-proxy04!
heartbeat[13739]: 2009/12/01_14:50:06 info: killing HBFIFO process 13743 with signal 15
heartbeat[13739]: 2009/12/01_14:50:06 info: killing HBWRITE process 13744 with signal 15
heartbeat[13739]: 2009/12/01_14:50:06 info: killing HBREAD process 13745 with signal 15
heartbeat[13739]: 2009/12/01_14:50:06 info: Core process 13743 exited. 3 remaining
heartbeat[13739]: 2009/12/01_14:50:06 info: Core process 13745 exited. 2 remaining
heartbeat[13739]: 2009/12/01_14:50:06 info: Core process 13744 exited. 1 remaining
heartbeat[13739]: 2009/12/01_14:50:06 info: uksl-proxy03 Heartbeat shutdown complete.
logd[13645]: 2009/12/01_14:50:06 info: logd_term_write_action: received SIGTERM
logd[13645]: 2009/12/01_14:50:06 info: Exiting write process
logd[14239]: 2009/12/01_14:51:58 info: logd started with /etc/logd.cf.
logd[14239]: 2009/12/01_14:51:58 WARN: Core dumps could be lost if multiple dumps occur.
logd[14239]: 2009/12/01_14:51:58 WARN: Consider setting non-default value in /proc/sys/kernel/core_pattern (or equivalent) for maximum supportability
logd[14239]: 2009/12/01_14:51:58 WARN: Consider setting /proc/sys/kernel/core_uses_pid (or equivalent) to 1 for maximum supportability
logd[14244]: 2009/12/01_14:51:58 info: G_main_add_SignalHandler: Added signal handler for signal 15
logd[14239]: 2009/12/01_14:51:58 info: G_main_add_SignalHandler: Added signal handler for signal 15
heartbeat[14340]: 2009/12/01_14:51:58 info: Enabling logging daemon
heartbeat[14340]: 2009/12/01_14:51:58 info: logfile and debug file are those specified in logd config file (default /etc/logd.cf)
heartbeat[14340]: 2009/12/01_14:51:58 WARN: Core dumps could be lost if multiple dumps occur.
heartbeat[14340]: 2009/12/01_14:51:58 WARN: Consider setting non-default value in /proc/sys/kernel/core_pattern (or equivalent) for maximum supportability
heartbeat[14340]: 2009/12/01_14:51:58 WARN: Consider setting /proc/sys/kernel/core_uses_pid (or equivalent) to 1 for maximum supportability
heartbeat[14340]: 2009/12/01_14:51:58 info: Version 2 support: false
heartbeat[14340]: 2009/12/01_14:51:58 info: **************************
heartbeat[14340]: 2009/12/01_14:51:58 info: Configuration validated. Starting heartbeat 2.1.4
heartbeat[14341]: 2009/12/01_14:51:58 info: heartbeat: version 2.1.4
heartbeat[14341]: 2009/12/01_14:51:58 info: Heartbeat generation: 1259593610
heartbeat[14341]: 2009/12/01_14:51:58 info: glib: UDP multicast heartbeat started for group 239.0.0.43 port 694 interface eth0 (ttl=1 loop=0)
heartbeat[14341]: 2009/12/01_14:51:58 info: G_main_add_TriggerHandler: Added signal manual handler
heartbeat[14341]: 2009/12/01_14:51:58 info: G_main_add_TriggerHandler: Added signal manual handler
heartbeat[14341]: 2009/12/01_14:51:58 info: G_main_add_SignalHandler: Added signal handler for signal 17
heartbeat[14341]: 2009/12/01_14:51:58 info: Local status now set to: 'up'
heartbeat[14341]: 2009/12/01_14:52:00 info: Link uksl-proxy04:eth0 up.
heartbeat[14341]: 2009/12/01_14:52:00 info: Status update for node uksl-proxy04: status active
harc[14349][14355]: 2009/12/01_14:52:00 info: Running /etc/ha.d/rc.d/status status
heartbeat[14341]: 2009/12/01_14:52:00 info: Comm_now_up(): updating status to active
heartbeat[14341]: 2009/12/01_14:52:00 info: Local status now set to: 'active'
heartbeat[14341]: 2009/12/01_14:52:01 info: remote resource transition completed.
heartbeat[14341]: 2009/12/01_14:52:01 info: remote resource transition completed.
heartbeat[14341]: 2009/12/01_14:52:01 info: Local Resource acquisition completed. (none)
heartbeat[14341]: 2009/12/01_14:52:01 info: uksl-proxy04 wants to go standby [foreign]
heartbeat[14341]: 2009/12/01_14:52:02 info: standby: acquire [foreign] resources from uksl-proxy04
heartbeat[14371]: 2009/12/01_14:52:02 info: acquire local HA resources (standby).
heartbeat[14341]: 2009/12/01_14:52:04 WARN: Shutdown delayed until current resource activity finishes.
heartbeat[14341]: 2009/12/01_14:52:04 WARN: Gmain_timeout_dispatch: Dispatch function for send local status was delayed 1410 ms (> 1010 ms) before being called (GSource: 0x8411430)
heartbeat[14341]: 2009/12/01_14:52:04 info: Gmain_timeout_dispatch: started at 1719797007 should have started at 1719796866
heartbeat[14341]: 2009/12/01_14:52:04 WARN: Gmain_timeout_dispatch: Dispatch function for check for signals was delayed 1450 ms (> 1010 ms) before being called (GSource: 0x8411650)
heartbeat[14341]: 2009/12/01_14:52:04 info: Gmain_timeout_dispatch: started at 1719797011 should have started at 1719796866
heartbeat[14341]: 2009/12/01_14:52:04 WARN: Gmain_timeout_dispatch: Dispatch function for check for signals took too long to execute: 70 ms (> 50 ms) (GSource: 0x8411650)
ResourceManager[14385][14395]: 2009/12/01_14:52:04 info: Acquiring resource group: uksl-proxy03 IPaddr2::10.100.10.80/24/eth0
IPaddr2[14407][14461]: 2009/12/01_14:52:06 INFO:  Resource is stopped
ResourceManager[14385][14475]: 2009/12/01_14:52:06 info: Running /etc/ha.d/resource.d/IPaddr2 10.100.10.80/24/eth0 start
IPaddr2[14504][14538]: 2009/12/01_14:52:06 INFO: ip -f inet addr add 10.100.10.80/24 brd 10.100.10.255 dev eth0
IPaddr2[14504][14540]: 2009/12/01_14:52:06 INFO: ip link set eth0 up
IPaddr2[14504][14542]: 2009/12/01_14:52:06 INFO: /usr/lib/heartbeat/send_arp -i 200 -r 5 -p /var/run/heartbeat/rsctmp/send_arp/send_arp-10.100.10.80 eth0 10.100.10.80 auto not_used not_used
IPaddr2[14477][14546]: 2009/12/01_14:52:06 INFO:  Success
heartbeat[14371]: 2009/12/01_14:52:06 info: local HA resource acquisition completed (standby).
heartbeat[14341]: 2009/12/01_14:52:06 info: Standby resource acquisition done [foreign].
heartbeat[14341]: 2009/12/01_14:52:06 info: Initial resource acquisition complete (auto_failback)
heartbeat[14341]: 2009/12/01_14:52:06 info: remote resource transition completed.
heartbeat[14341]: 2009/12/01_14:52:06 info: Heartbeat shutdown in progress. (14341)
heartbeat[14548]: 2009/12/01_14:52:06 info: Giving up all HA resources.
ResourceManager[14562][14572]: 2009/12/01_14:52:07 info: Releasing resource group: uksl-proxy03 IPaddr2::10.100.10.80/24/eth0
ResourceManager[14562][14587]: 2009/12/01_14:52:07 info: Running /etc/ha.d/resource.d/IPaddr2 10.100.10.80/24/eth0 stop
IPaddr2[14616][14638]: 2009/12/01_14:52:07 INFO: killed previously running send_arp for 10.100.10.80
IPaddr2[14616][14647]: 2009/12/01_14:52:07 INFO: ip -f inet addr delete 10.100.10.80/24 dev eth0
IPaddr2[14616][14649]: 2009/12/01_14:52:07 INFO: ip -o -f inet addr show eth0
IPaddr2[14589][14651]: 2009/12/01_14:52:07 INFO:  Success
heartbeat[14548]: 2009/12/01_14:52:07 info: All HA resources relinquished.
heartbeat[14341]: 2009/12/01_14:52:07 WARN: 1 lost packet(s) for [uksl-proxy04] [511:513]
heartbeat[14341]: 2009/12/01_14:52:07 info: No pkts missing from uksl-proxy04!
heartbeat[14341]: 2009/12/01_14:52:09 info: killing HBFIFO process 14345 with signal 15
heartbeat[14341]: 2009/12/01_14:52:09 info: killing HBWRITE process 14346 with signal 15
heartbeat[14341]: 2009/12/01_14:52:09 info: killing HBREAD process 14347 with signal 15
heartbeat[14341]: 2009/12/01_14:52:09 info: Core process 14345 exited. 3 remaining
heartbeat[14341]: 2009/12/01_14:52:09 info: Core process 14346 exited. 2 remaining
heartbeat[14341]: 2009/12/01_14:52:09 info: Core process 14347 exited. 1 remaining
heartbeat[14341]: 2009/12/01_14:52:09 info: uksl-proxy03 Heartbeat shutdown complete.
logd[14244]: 2009/12/01_14:52:09 info: logd_term_write_action: received SIGTERM
logd[14244]: 2009/12/01_14:52:09 info: Exiting write process

Please help, I know this config works as I have live proxy setup like this, but it is old ubuntu version (7 I think) and old squid version. Am i missing something obvious or has a bug been introduced.

Many Thanks,

Paul

---

