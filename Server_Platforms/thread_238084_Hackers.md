---
title: "Hackers"
date: 2006-08-17
forum: Server Platforms
---

### Post by renaissance on 2006-08-17
Hackers use my server to attack one of the US server. How i can find the hackers who use my coputer ? is there any logfile or something like that ?

---

### Post by bluenova on 2006-08-17
I think you mean a Cracker, a Hacker is someone who programs.

---

### Post by Klaidas on 2006-08-17
How do they attacks?
The type of attack depends on a log file

---

### Post by Sam on 2006-08-18
Check /var/log/auth.log to check connections made to your computer. The application logwatch (same package name) will send you daily reports for any attack attempt or successful login.

---

