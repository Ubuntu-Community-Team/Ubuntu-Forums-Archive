---
title: "NTP Server: Synchronises by remains at Stratum 16"
date: 2006-11-23
forum: Server Platforms
---

### Post by charlie. on 2006-11-23
I've installed the ntp daemon from the ntp-simple package. I've configured it to sync to "igubu.saix.net" (196.25.1.1) and re-started it. ntpq says that this server is "reachable" and selected as the "sys.peer", but ntptrace continues to state that the local server is stratum 16. (It should be stratum 3 after synchronizing, igubu.saix.net is stratum 2.)

I'm running a clean install of Dapper 6.06.1, i386, installed from the alternate CD as a "server" (command-line only).

Attached are four files:
1. My ntp.conf from /etc/ntp.conf, showing the two servers that i've added.
2. The output from "ntpq -p -c as", showing that igubu.saix.net is found and chosen as the sys.peer, and reachable.
3. A tail from /var/log/daemon.log, showing messages that ntpd spewed out, including a message clearly stating that it has synchronized to 196.25.1.1, the IP address that igubu.saix.net resolves to.
4. The output from ntptrace, showing that localhost is stratum 16 and that there are no "upstream" ntp servers.

UDP port 123 has been forwarded to my PC's IP address on my D-Link DSL-504T router.

Please help?

---

### Post by am4c130d on 2006-11-30
From the info supplied - 

ntp.conf is good
ntpq indicates two stratum 2 peers, one is selected and the other is backup
log confirms that you a synced to a stratum 2 source - but only after initially running on internal clock (normal)
ntptrace - is bogus.

Your poll times on ntpq -p indicate that you ran these commands almost immediately after restarting ntp.  If you try them after a day, and poll time is 1024, then you are completely stable and using the longest intervals between polls.  ntptrace should then show saix as the first line, and whatever saix's source is as the second line.  It seems plausible that you ran ntptrace before any peers were considered reliable enough to become the master clock source.  ntp does take a few minutes to gain synchronisation, and for a peer to be preferred to local clock.  Hope that helps.

---

### Post by charlie. on 2006-12-01
Thanks, that makes sense.

I've timed it: after about 20 minutes, the stratum returned from ntptrace *does* change to 3.

During those 20 minutes, no clients will sync with this NTP server. This means that an client PC that drifted away from the NTP server (say during a  long power outage) would only be able to get back in sync 20 minutes after the power was restored. If that drift was more than say 5 minutes, things could stop working. (Take kerberos, for example.)

For this reason, I dumped ntp and replaced it with OpenNTPd, which syncs in about 2 minutes and has a configuration file only four lines long. (Later, I dumped the whole server, because it was just a sandbox after all.)

---

### Post by am4c130d on 2006-12-01
20 minutes seems excessive, my own experience is closer to a few minutes, but I've never timed it - and have not used ntptrace as my reference, only ntpq -p, where as soon as I see an asterisk by a source I am comfortable I'm in sync.  Thinking about it, it can't realistically be a much shorter period of time without the client (your server) pounding the time reference.  It's only after multiple updates and correlations can a client be certain that it has the exact time, understands the latency and jitter associate with that servers clock signals.  When an association is first made, the default update time is 64 seconds and moves to 1024 seconds (17 minutes) when the system is fully stable.  As this is a one off, i.e. only when the system boots, and typically time servers are supposed to be stable devices, this should not normally be a problem.

No client should sync to a time server with a stratum of 16, this value means unsynchronized - i.e. it is a bad reference.

An alternative approach is to use ntpdate from cron every 24 hours.  ntpdate is a one off time sync from an ntp server.  Then configure ntp.conf to use the internal PC clock as the reference, with a stratum of say 10 (I think that's default), and let your clients sync to that instead.  That should mean that your server/PC is good reference source almost immediately it has booted.  Obviously the real time clock on your server/PC is not as precise as a stratum 1 or 2 source, but it's probably good enough for 99% of applications.

Sorry to hear it didn't work out for you.

Thanks

Alan

---

