---
title: "Can't get syslog-ng to work..."
date: 2008-03-04
forum: Server Platforms
---

### Post by grittyminder on 2008-03-04
I'm trying to send *all* syslog data from a remote location to a local syslog-ng server. However, nothing is showing up in the local syslog.

Here is what I've done so far:
1) Installed syslog-ng package
2) Modified syslog-ng.conf with the following configuration:

source s_ext {
        udp(port(5140));
};

destination df_ext { 
    file("/var/log/syslog_ext.log"); 
};

log {
    source(s_ext);
    filter(f_at_least_info);
    #filter(f_syslog);
    #filter(f_at_least_warn);
    #filter(f_at_least_err);
    destination(df_ext);
};

(I was experimenting with different filters trying to see if anything would show up.)
3) Restarted syslog process, rebooted server, etc.

Here is what I've done so far to troubleshoot:
- The syslog-ng process is running. This has been confirmed with ps.
- There is a UDP process bound to port 5140. This has been confirmed with netstat.
- syslog data is actively being sent from the remote location to port 5140 on the syslog server via UDP. This has been confirmed with tcpdump.
- Port 5140 is *not* open on the local syslog server. This has been confirmed with nmap localhost.

So I guess that syslog-ng is bound to port 5140 but is not listening or something? I'm confused.

---

### Post by grittyminder on 2008-03-05
In case it wasn't clear from the first post (and it wasn't) I need help! I've used the default syslog daemon in the past (sysklogd) but have no experience with sytslog-ng. I've examined numerous tutorials and have reviewed what I've done over and over to no luck. I have a feeling that I'm missing something obvious. Any ideas?

---

