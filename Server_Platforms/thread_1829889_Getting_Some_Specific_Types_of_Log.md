---
title: "Getting Some Specific Types of Log"
date: 2011-08-20
forum: Server Platforms
---

### Post by nathanpc on 2011-08-20
I'm want to get some logs from my server, but not general logs like **syslog** that gives me a lot of random logs. I want to know how I can get logs of things like logins(with time, IP and username), commands that the user ran, process running at the time and things like this.

---

### Post by Toz on 2011-08-20
Have a look at the package **acct**:
> Description-en_CA: The GNU Accounting utilities for process and login accounting
 GNU Accounting Utilities is a set of utilities which reports and
 summarizes data about user connect times and process execution statistics.
 .
 "Login accounting" provides summaries of system resource usage based on
 connect time, and "process accounting" provides summaries based on the
 commands executed on the system.


Here is a link with a basic summary: [http://easyybloger.blogspot.com/2011/05/enable-process-accounting-in-ubuntu.html]("http://easyybloger.blogspot.com/2011/05/enable-process-accounting-in-ubuntu.html")

---

