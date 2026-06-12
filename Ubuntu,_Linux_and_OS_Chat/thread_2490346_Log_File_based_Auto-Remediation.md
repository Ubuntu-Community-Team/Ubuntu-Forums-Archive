---
title: "Log File based Auto-Remediation"
date: 2023-08-31
forum: Ubuntu, Linux and OS Chat
---

### Post by vx4-evaluator on 2023-08-31
Although open source log management projects exist, and its always been possible to script out incident response auto-remediation, what open source projects focus on this at scale? It seems like many sysadmins have to re-invent the wheel every time something goes wrong. We all rely on forums like this by searching on errors found in logs. No doubt devs are working to fix software so that errors do not occur, but there's so many OS logs beyond syslog that it's pretty time consuming and sometimes frustrating, especially when app logs are included. In fixing day to day issues, I've come across many logs that I didn't even know existed. 

So what prevents the development of a simple AI system where errors in logs kick off an automated forum search or general web search and then use a tactic similar to hardware probes that attempt to fix an issue by working through a series of troubleshooting test scripts? As an abstraction, I am reminded of Prolog type fwd/bwd chaining based on Logic or Condition-Action Rules. Seems like it would be no more complex than following a logic tree type flow chart, although the logic tree would end up being massive in the end. No doubt seemingly endless iterations would be required to perfect such an effort. Has anyone heard of such a thing? Seems like automation could be helpful here.

---

### Post by TheFu on 2023-08-31
A competent admin does these things automatically.  As for log management, journalctl is amazing for searching logs, centralizing logs, and managing log growth by event time or purely log size.

Admins are lazy.  We use devops tools to handle nearly anything that can be automated.  At scale, alarms are directed to the team that needs them.  If backup software fails, the alarm goes to the team responsible for backup failures.  If a specific application fails, then that team would be notified.  That way, the experts are engaged and given the opportunity to handle the issues quickly and efficiently.  I know this scales to over 100K systems.  Almost always, alarms go to the application support team.  The admin for the system gets just an information notification.  Sharing the load.  

Plus, any automation for corrective actions becomes part of the expert's team so they fix it once and it gets fixed everywhere in the enterprise ... unless the team is just stupid.  I've see that and I've gotten into arguments with those people.  One team wrote terrible software.  Every night, their software would fail because it allowed bad inputs.  They'd be up most of the night manually massaging the bogus data so it would pass unenforced requirements and not crash their part of the long chain of software that was the "nightly batch run".  I suggested that they reject all bogus inputs a ... er ... input time and push that issue upstream to the prior tool allowing the bad data through.  Keep doing that for each program in the chain and eventually, there won't be any bad data getting into the system.  Seems pretty obvious, right?  After all, their job was to process good data, not bad data. The earlier in the process bad data was prevented, the better.

Anyway, which tools have you looked at already?  There are many, usually tied to monitoring and alarming already on the systems.  This makes sense, as those tools already monitor logs, so seeing what actually failed and correcting it automatically could work sometimes.  This assumes the issue isn't too complex.

---

### Post by vx4-evaluator on 2023-08-31
I agree that doing things automatically is a mark of skillful administration. I'll look at journalctl more closely. My approach in the past has been around Splunk and detailed configuration of syslog.conf. Logging aggregation is easy compared to automating incident response with heavy scripting. The security realm has SIEM tools for zero-day response because there's no debate that automation is required for analysis and response based on vast streams of incoming data. I come from a Solaris/AIX/HPUX background from back in the day when we didn't spend much time sifting through syslogs until a user reported an actual problem. I wouldn't call that proactive but there weren't enough sysadmins in any given org to have extra time to spend on it. We typically set up automated log parsing to alert on keywords and the rest got ignored. Now i'm interested in something more cognitive.

---

### Post by TheFu on 2023-08-31
> **vx4-evaluator said:**
> I agree that doing things automatically is a mark of skillful administration. I'll look at journalctl more closely. My approach in the past has been around Splunk and detailed configuration of syslog.conf. Logging aggregation is easy compared to automating incident response with heavy scripting. The security realm has SIEM tools for zero-day response because there's no debate that automation is required for analysis and response based on vast streams of incoming data. I come from a Solaris/AIX/HPUX background from back in the day when we didn't spend much time sifting through syslogs until a user reported an actual problem. I wouldn't call that proactive but there weren't enough sysadmins in any given org to have extra time to spend on it. We typically set up automated log parsing to alert on keywords and the rest got ignored. Now i'm interested in something more cognitive.

I was a UNIX admin too. I used logwatch to get to the point ... and I still do, at home.
Everywhere I worked, we had custom admin scripts that handled most installations, maintained desired configs and looked for intruders.  They were all a little different, but basically the same.   Admins we centralized to avoid an admin taking shortcuts to get a working, but non-secure, system.  I've seen that in far too many organizations when I traveled in a software development company and did lots of installs around the world.

I'd look to embedding this sort of work in your devops tool and if it doesn't handle it nicely, get a better devops tool.  Make your infrastructure constantly improving by having it controlled by code. That's a key take-away from devops.  Of course, most outstanding organizations have been doing something like devops since the 1980s, it took some marketing types to assign a name and try to sell a product around it. We also gained just a few tools that we can all talk which makes understanding easier when we change jobs.  There's no 6 week period of learning the names of scripts and liabilities of those scripts they've been using 30 yrs anymore, though I have to say some devops setups are pretty bad too.  Often, devops tools will grow to be worse than the problem they were supposed to fix (cough ... puppet).

---

