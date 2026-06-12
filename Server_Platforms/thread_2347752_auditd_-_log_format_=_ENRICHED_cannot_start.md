---
title: "auditd - log_format = ENRICHED cannot start"
date: 2016-12-28
forum: Server Platforms
---

### Post by John Paul Morris on 2016-12-28
Hi,

I have installed auditd on a Ubuntu 16.04 server and I am trying to update the auditd.conf file to have the log_format set to ENRICHED.

When I do this auditd will not start until I change it back to RAW.

The 'ENRICHED' option should resolve all uid, gid, syscall, architecture, and socket address information before writing the event to disk  - [http://man7.org/linux/man-pages/man5/auditd.conf.5.html](http://man7.org/linux/man-pages/man5/auditd.conf.5.html) 

If I run the command 'systemctl status auditd.service' I get:

```
â&#8212; auditd.service - Security Auditing Service
   Loaded: loaded (/lib/systemd/system/auditd.service; enabled; vendor preset: enabled)
   Active: failed (Result: exit-code) since Wed 2016-12-28 14:53:05 GMT; 13s ago
  Process: 3155 ExecStartPost=/sbin/auditctl -R /etc/audit/audit.rules (code=exited, status=0/SUCCESS)
  Process: 3154 ExecStart=/sbin/auditd -n (code=exited, status=6)
 Main PID: 3154 (code=exited, status=6)


Dec 28 14:53:05 its-lab-server auditctl[3155]: failure 1
Dec 28 14:53:05 its-lab-server auditctl[3155]: pid 0
Dec 28 14:53:05 its-lab-server auditctl[3155]: rate_limit 0
Dec 28 14:53:05 its-lab-server auditctl[3155]: backlog_limit 320
Dec 28 14:53:05 its-lab-server auditctl[3155]: lost 7
Dec 28 14:53:05 its-lab-server auditctl[3155]: backlog 0
Dec 28 14:53:05 its-lab-server auditctl[3155]: backlog_wait_time 15000
Dec 28 14:53:05 its-lab-server systemd[1]: Failed to start Security Auditing Service.
Dec 28 14:53:05 its-lab-server systemd[1]: auditd.service: Unit entered failed state.
Dec 28 14:53:05 its-lab-server systemd[1]: auditd.service: Failed with result 'exit-code'.
its-ansible-svc@its-lab-server:~$ systemctl status auditd.service
```

and if run sudo journalctl -xe I get

```
-- Unit auditd.service has begun starting up.
Dec 28 14:53:05 its-lab-server audit: CONFIG_CHANGE audit_backlog_limit=320 old=320 auid=4294967295 ses=4294967295 res=1
Dec 28 14:53:05 its-lab-server systemd[1]: auditd.service: Main process exited, code=exited, status=6/NOTCONFIGURED
Dec 28 14:53:05 its-lab-server auditd[3154]: Option ENRICHED not found - line 6
Dec 28 14:53:05 its-lab-server auditctl[3155]: No rules
Dec 28 14:53:05 its-lab-server auditctl[3155]: enabled 1
Dec 28 14:53:05 its-lab-server auditctl[3155]: failure 1
Dec 28 14:53:05 its-lab-server auditctl[3155]: pid 0
Dec 28 14:53:05 its-lab-server auditctl[3155]: rate_limit 0
Dec 28 14:53:05 its-lab-server auditctl[3155]: backlog_limit 320
Dec 28 14:53:05 its-lab-server auditctl[3155]: lost 7
Dec 28 14:53:05 its-lab-server auditctl[3155]: backlog 0
Dec 28 14:53:05 its-lab-server auditctl[3155]: backlog_wait_time 15000
Dec 28 14:53:05 its-lab-server auditd[3154]: The audit daemon is exiting.
Dec 28 14:53:05 its-lab-server systemd[1]: Failed to start Security Auditing Service.
-- Subject: Unit auditd.service has failed
-- Defined-By: systemd
-- Support: [http://lists.freedesktop.org/mailman/listinfo/systemd-devel](http://lists.freedesktop.org/mailman/listinfo/systemd-devel)
-- 
-- Unit auditd.service has failed.
-- 
-- The result is failed.
Dec 28 14:53:05 its-lab-server audit[1]: SERVICE_START pid=1 uid=0 auid=4294967295 ses=4294967295 msg='unit=auditd comm="systemd" exe="/lib/systemd/systemd" hostname=? addr=? terminal=? res=failed'
Dec 28 14:53:05 its-lab-server systemd[1]: auditd.service: Unit entered failed state.
```

so it looks like ENRICHED is not an option but the documentation says otherwise. Any help appreciated.

JPM

---

### Post by howefield on 2016-12-28
Thread moved to the "*Server Platforms*" forum, probably a better fit.

---

### Post by John Paul Morris on 2016-12-28
Thanks

---

