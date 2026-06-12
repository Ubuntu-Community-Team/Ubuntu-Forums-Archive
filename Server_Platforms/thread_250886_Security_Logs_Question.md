---
title: "Security Logs Question"
date: 2006-09-04
forum: Server Platforms
---

### Post by Jeff D on 2006-09-04
Hi all new to Linux and it's ways and I have a question about the logs.  Without having knowledge of how crackers work, or what to look for what should I as a beginner user be looking for in my logs and what logs should I be watching that will have the most pertinent information of cracker activity.  Thanks in advance for any help.

---

### Post by Jussi Kukkonen on 2006-09-04
Depends partly on the services you run. /var/log/auth.log is probably the most important: it logs all logins, failed logins, root sessions, sudo uses, failed sudo attempts... 

The most common cracker tactic is a a dictionary attack on common services (trying lots of common logins/passwords). If you run a sshd or some other common service, expect a *lot* of login attempts -- I seem to have had over 3000 failed login attempts last week, and I don't even have a static IP!

If you don't run services with open ports, there isn't much the crackers can do -- or much that you should be looking out for. Even with open ports, sensible configuration keeps things reasonably secure: e.g. my ssh-server doesn't normally accept password-logins at all (just public-key logins), so dictionary attacks aren't usable. I'd say understanding your services and their configuration is far more important than watching logs, although you can learn from them.

---

### Post by Jeff D on 2006-09-04
Good to know, I don't run any open port services.  It's just good to know as a beginner what I should be looking out for with the logs.  I'm not paranoid but I'm sure I'll still check the logs every few days.  I just use Ubuntu for basic internet stuff at tha moment.
  Thanks for your reply Yussi.

---

