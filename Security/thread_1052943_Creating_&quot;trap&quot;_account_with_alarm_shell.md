---
title: "Creating &quot;trap&quot; account with alarm shell"
date: 2009-01-28
forum: Security
---

### Post by PacSci on 2009-01-28
I'm in the process of securing my server (it runs Hardy), and as part of it, I came up with the idea to create one or two "trap" accounts that, when logged in to, would run a script that would notify me and block their IP address, before immediately logging them out.

How would I go about setting up such a system? Would I just write a script that would do what I needed and then exit with a status of 1, then set that as the trap accounts' shell? (And is it possible to see the IP that an SSHing person is using from inside a script?)

---

### Post by cdenley on 2009-01-28
Sounds kind of like a honeypot. Rather that waiting until they guess a correct password, I think using something like denyhosts or fail2ban would be more effective. Actually, I think you can configure fail2ban to ban hosts based on successful logins for a particular user. You can also filter based on login attempts on your trap account, even if the account doesn't exist. All ssh authentication attempts should get logged to /var/log/auth.log, successful or unsuccessful.

---

