---
title: "Auto Run &amp; Auto Tasking MTA Server On The VPS"
date: 2024-03-28
forum: Ubuntu Dev Link Forum
---

### Post by arianvixor on 2024-03-28
[FONT=arial]How can I make the Apache web server and Mysql database connect to a game server and work every time the Linux VPS is restarted, and in addition, we can get the sources in a GitHub repository automatically after the server is restarted?[/FONT]

---

### Post by TheFu on 2024-03-28
> **arianvixor said:**
> [FONT=arial]How can I make the Apache web server and Mysql database connect to a game server and work every time the Linux VPS is restarted, and in addition, we can get the sources in a GitHub repository automatically after the server is restarted?[/FONT]

Pulling code automatically from a github repo that isn't under your control is extremely dangerous.  There are far too many examples where that method hacked the server after other projects were poisoned with C&C code or worse.

You'll need to be clearer on what you mean by *"make the Apache web server and Mysql database connect to a game server and work every time"*.  Both are servers, so I'm confused about having a server connect to general use https or DBMS servers.  Usually, it is the other way around.

Apache would connect to the app-server which would connect to the DBMS.  For this to happen, you just need to start the DBMS first, then the app-server, followed by apache last.

---

### Post by TheFu on 2024-03-30
A few days ago, an example happened: [https://www.phoronix.com/news/XZ-CVE-2024-3094](https://www.phoronix.com/news/XZ-CVE-2024-3094) . This one isn't THAT bad, unless you use beta Linux versions.

If you use python, [https://arstechnica.com/security/2024/03/pypi-halted-new-users-and-projects-while-it-fended-off-supply-chain-attack/](https://arstechnica.com/security/2024/03/pypi-halted-new-users-and-projects-while-it-fended-off-supply-chain-attack/)

Almost every coding language gets hit with some important repos that are hosted publicly being modified with hacked code.
[https://arstechnica.com/security/2024/02/github-besieged-by-millions-of-malicious-repositories-in-ongoing-attack/](https://arstechnica.com/security/2024/02/github-besieged-by-millions-of-malicious-repositories-in-ongoing-attack/)

Canonical's snap packages have been hit a few times with malicious code: 
[https://www.theregister.com/2024/03/28/canonical_snap_store_scams/](https://www.theregister.com/2024/03/28/canonical_snap_store_scams/)

Be careful out there.

---

