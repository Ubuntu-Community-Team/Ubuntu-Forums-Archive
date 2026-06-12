---
title: "What is the command 'exe' in top?"
date: 2010-04-02
forum: Security
---

### Post by anonymousturtle3 on 2010-04-02
When I type sudo top on my friend's Ubuntu 9.10 machine, there is a process called 'exe' running with the PID 12258. This process does not appear on my Ubuntu 9.10 machine and whenever I kill it, it returns a few minutes later. It seems suspicious but I have never experienced a virus on a Linux OS. The process does not have administrative privileges (it is supposedly started by the user and not the system) so it shouldn't be too much to worry about but I would like some information from people who know what this process is.

Thanks for your help.

---

### Post by Pjotr123 on 2010-04-03
No worries. Could be some legitimate application that's running by means of mono, like Tomboy or F-spot. Those have .exe extensions as well, strangely enough. Check for instance /usr/lib/tomboy or /usr/lib/f-spot.

---

