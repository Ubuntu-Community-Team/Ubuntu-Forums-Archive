---
title: "CUPS Webinterface missing information from page_log"
date: 2011-11-29
forum: Server Platforms
---

### Post by lynix on 2011-11-29
I run a small CUPS server that serves users from a NIS domain. The page_log contains valid entries like this:

```
haring lynix 125 [29/Nov/2011:12:38:42 +0100] 1 1 - 141.21.4.100 Microsoft PowerPoint - 1 - Motivation.ppt A4 one-sided
```

As you can see, there is a valid user name, job name, etc.

However, in the CUPS webinterface job list for that printer, the job name is displayed as "unknown", and instead of the user name there is the string "{job_originating_user_name}".

Can anyone tell me where to look for the cause of this? There is no error message in the logs, and I already tried reinstalling CUPS (1.5.0) and the printers.


Thanks in advance

lynix

---

