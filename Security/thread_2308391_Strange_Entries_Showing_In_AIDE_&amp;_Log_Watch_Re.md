---
title: "Strange Entries Showing In AIDE &amp; Log Watch Reports"
date: 2016-01-02
forum: Security
---

### Post by james188 on 2016-01-02
Good day all,

**This is from my AIDE report:**

Entry /var/log/audit/audit.log was changed so that hash cannot be calculated for it
```
Attribute size has been changed
Attribute ctime has been changed
Attribute mtime has been changed
Entry /var/log/audit/audit.log in databases has different attributes: 1ac027cfbd 1a00200fbd
```

**From Log Watch Report:**

**Kernel Begin:**

```
 62 Time(s): audit: audit_backlog=8198 > audit_backlog_limit=8192
 1 Time(s): audit: audit_lost=12729 audit_rate_limit=0 audit_backlog_limit=8192
 1 Time(s): audit: audit_lost=12730 audit_rate_limit=0 audit_backlog_limit=8192
 1 Time(s): audit: audit_lost=12731 audit_rate_limit=0 audit_backlog_limit=8192
 1 Time(s): audit: audit_lost=14604 audit_rate_limit=0 audit_backlog_limit=8192
 1 Time(s): audit: audit_lost=14605 audit_rate_limit=0 audit_backlog_limit=8192
 1 Time(s): audit: audit_lost=14606 audit_rate_limit=0 audit_backlog_limit=8192
 1 Time(s): audit: audit_lost=1526 audit_rate_limit=0 audit_backlog_limit=8192
 1 Time(s): audit: audit_lost=1527 audit_rate_limit=0 audit_backlog_limit=8192
 1 Time(s): audit: audit_lost=1528 audit_rate_limit=0 audit_backlog_limit=8192
 1 Time(s): audit: audit_lost=15724 audit_rate_limit=0 audit_backlog_limit=8192
 1 Time(s): audit: audit_lost=15725 audit_rate_limit=0 audit_backlog_limit=8192
 1 Time(s): audit: audit_lost=15726 audit_rate_limit=0 audit_backlog_limit=8192
 1 Time(s): audit: audit_lost=17210 audit_rate_limit=0 audit_backlog_limit=8192
 1 Time(s): audit: audit_lost=17211 audit_rate_limit=0 audit_backlog_limit=8192
 1 Time(s): audit: audit_lost=17212 audit_rate_limit=0 audit_backlog_limit=8192
 1 Time(s): audit: audit_lost=17213 audit_rate_limit=0 audit_backlog_limit=8192
 1 Time(s): audit: audit_lost=22758 audit_rate_limit=0 audit_backlog_limit=8192
 1 Time(s): audit: audit_lost=22759 audit_rate_limit=0 audit_backlog_limit=8192
 1 Time(s): audit: audit_lost=22760 audit_rate_limit=0 audit_backlog_limit=8192
 1 Time(s): audit: audit_lost=2680 audit_rate_limit=0 audit_backlog_limit=8192
 1 Time(s): audit: audit_lost=2681 audit_rate_limit=0 audit_backlog_limit=8192
 1 Time(s): audit: audit_lost=2682 audit_rate_limit=0 audit_backlog_limit=8192
 1 Time(s): audit: audit_lost=30802 audit_rate_limit=0 audit_backlog_limit=8192
 1 Time(s): audit: audit_lost=30803 audit_rate_limit=0 audit_backlog_limit=8192
 1 Time(s): audit: audit_lost=30804 audit_rate_limit=0 audit_backlog_limit=8192
 1 Time(s): audit: audit_lost=33537 audit_rate_limit=0 audit_backlog_limit=8192
 1 Time(s): audit: audit_lost=33538 audit_rate_limit=0 audit_backlog_limit=8192
 1 Time(s): audit: audit_lost=33539 audit_rate_limit=0 audit_backlog_limit=8192
 1 Time(s): audit: audit_lost=33540 audit_rate_limit=0 audit_backlog_limit=8192
 1 Time(s): audit: audit_lost=34704 audit_rate_limit=0 audit_backlog_limit=8192
 1 Time(s): audit: audit_lost=34705 audit_rate_limit=0 audit_backlog_limit=8192
 1 Time(s): audit: audit_lost=34706 audit_rate_limit=0 audit_backlog_limit=8192
 1 Time(s): audit: audit_lost=35178 audit_rate_limit=0 audit_backlog_limit=8192
 1 Time(s): audit: audit_lost=35179 audit_rate_limit=0 audit_backlog_limit=8192
 1 Time(s): audit: audit_lost=35180 audit_rate_limit=0 audit_backlog_limit=8192
 1 Time(s): audit: audit_lost=39785 audit_rate_limit=0 audit_backlog_limit=8192
 1 Time(s): audit: audit_lost=39786 audit_rate_limit=0 audit_backlog_limit=8192
 1 Time(s): audit: audit_lost=39787 audit_rate_limit=0 audit_backlog_limit=8192
 1 Time(s): audit: audit_lost=40916 audit_rate_limit=0 audit_backlog_limit=8192
 1 Time(s): audit: audit_lost=40917 audit_rate_limit=0 audit_backlog_limit=8192
 1 Time(s): audit: audit_lost=40918 audit_rate_limit=0 audit_backlog_limit=8192
 1 Time(s): audit: audit_lost=65 audit_rate_limit=0 audit_backlog_limit=8192
 1 Time(s): audit: audit_lost=66 audit_rate_limit=0 audit_backlog_limit=8192
 1 Time(s): audit: audit_lost=67 audit_rate_limit=0 audit_backlog_limit=8192
 1 Time(s): audit: audit_lost=6701 audit_rate_limit=0 audit_backlog_limit=8192
 1 Time(s): audit: audit_lost=6702 audit_rate_limit=0 audit_backlog_limit=8192
 1 Time(s): audit: audit_lost=6703 audit_rate_limit=0 audit_backlog_limit=8192
 41 Time(s): audit: backlog limit exceeded
 1 Time(s): audit_log_start: 12052 callbacks suppressed
 1 Time(s): audit_log_start: 13792 callbacks suppressed
 1 Time(s): audit_log_start: 1411 callbacks suppressed
 1 Time(s): audit_log_start: 16630 callbacks suppressed
 1 Time(s): audit_log_start: 168 callbacks suppressed
 1 Time(s): audit_log_start: 18074 callbacks suppressed
 1 Time(s): audit_log_start: 24122 callbacks suppressed
 1 Time(s): audit_log_start: 3348 callbacks suppressed
 1 Time(s): audit_log_start: 3383 callbacks suppressed
 1 Time(s): audit_log_start: 3445 callbacks suppressed
 1 Time(s): audit_log_start: 3491 callbacks suppressed
 1 Time(s): audit_log_start: 4371 callbacks suppressed
 1 Time(s): audit_log_start: 4442 callbacks suppressed
 1 Time(s): audit_log_start: 5590 callbacks suppressed
 1 Time(s): audit_log_start: 8195 callbacks suppressed
```

Should I be worried about these entries?

Thanks,
James

---

