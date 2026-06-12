---
title: "High load, no obvious reason"
date: 2017-08-02
forum: Server Platforms
---

### Post by psychofrog on 2017-08-02
High guys,

so for some time, one of my servers is experiencing high load over all time. 
It always goes down for quite some time, though.

Theere were no errors until i rebooted with /forcefsck since i wanted to check the filesystem (check seemed to be good).
No, the load nearly always is somewhere around 1.00 or more, but also goes down to 0.2 from time to time. 

When checking top or syslog i can't find any obvious reason.

Could you help a newbie out here?

Thanks!

---

### Post by ajgreeny on 2017-08-02
> No, the load nearly always is somewhere around 1.00 or more, but also goes down to 0.2 from time to time. 
What do you mean by this statement?

Are those figures percentage cpu resource or something else?  Both seem extremely low to me; not anything I would be concerned about, so tell us more and give us either better figures or explain more clearly.

---

### Post by psychofrog on 2017-08-02
> **ajgreeny said:**
> What do you mean by this statement?

Are those figures percentage cpu resource or something else?  Both seem extremely low to me; not anything I would be concerned about, so tell us more and give us either better figures or explain more clearly.

Hi,

i'm speaking of the current system load. When running "top" it can be found under "load average" in the upper right corner. I'm sorry, I only know this as load...

---

### Post by ajgreeny on 2017-08-02
What is the server actually doing most of the time, and is it a GUI, command line, or headless server?

---

### Post by psychofrog on 2017-08-03
It's providing different services: 

- Redmine
- Sharing some folders to other servers via NFS
- Hosting a virtual machine (fileserver)

It is a Ubuntu 12.04 (upgrade-plans are developing) and command line.

---

### Post by cariboo on 2017-08-03
top should tell you what is causing the problem.

I'm running the following on my server:

[LIST]
[*]Logitech media server
[*]Serviio
[*]Calibre server
[*]Media wiki
[*]Samba
[*]NFS
[/LIST]

---

### Post by psychofrog on 2017-08-09
I've observated top for quite some time no, unfortunately it only seems, that nfsd is causing some load. But there has been no change in configuration or anything else. (screenshot showing load currently falling. shot up right after i took it)

---

### Post by Doug S on 2017-08-09
> **psychofrog said:**
> It is a Ubuntu 12.04 (upgrade-plans are developing) and command line.My recommendation is to not worry about it, unless it persists after upgrading or whatever. There were issues with erroneous reported load averages back in 2012. First, the reported load averages were too low, even 0 for high high load. Then reported load averages were too high. The magnitude of the error was a function of the work/sleep frequency of the load(s). I do not know if or when fixes were ever backported to 12.04.

You also mention a VM. My experiences with VM's on 12.04 were not good, although high load on the host should have showed up in top (if I recall correctly). VM's on 16.04 work well (at least in my experience).

---

