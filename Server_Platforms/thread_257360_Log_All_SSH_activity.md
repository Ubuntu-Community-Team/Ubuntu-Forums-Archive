---
title: "Log All SSH activity"
date: 2006-09-14
forum: Server Platforms
---

### Post by emiliorecio on 2006-09-14
Hi, there are any way to log ALL the ssh user activity. Im interested in log all commands that user use in my machine when he is in my machin via ssh. THANKS!

---

### Post by Klaidas on 2006-09-14
Do you mean every cd, mkdir, ALL commands done while using SSH? :|

---

### Post by kidders on 2006-09-14
Hmm... interesting idea. I figure you might as well approach this problem as if SSH weren't involved at all. SSH terminals aren't quite as "indirect" as, say, FTP ones, so things users type aren't easily intercepted.

This may be a totally stupid suggestion, but you *could* periodically poll all ~/.bash_history files and log any changes. That would, of course, be simple to circumvent.

I'm off to look for less brutal approaches ... I'll post back if I find one :-)

---

### Post by emiliorecio on 2006-09-14
Hi. Yes ALL commands i wanth to log. 
Few years ago i know there are a program that redirect all keys presed by user loged in telnet to the tty.

---

