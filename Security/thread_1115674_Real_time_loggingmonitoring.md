---
title: "Real time logging/monitoring"
date: 2009-04-04
forum: Security
---

### Post by k0d3k on 2009-04-04
Is it possible to have some sort of real time monitoring or logging of commands and receive notification of these events?  For example, lets say I have a directory /opt/logs/.  Inside /opt/logs are just plain log files.  If anyone uses a more or a vi on these log files, I would like to be notified in real time of this.  Would something like a file integrity monitor like OSSEC or OSIRIS work or am I completely off?  I would assume I could monitor the .bash_history but this would not be real-time as the .bash will only be written upon exit of the shell, correct?  

Any ideas would be greatly appreciated :)

---

### Post by lensman3 on 2009-04-04
Take a look at the "sa" and "ac" commands.  These are more user and process oriented instead of file oriented.

---

