---
title: "Find apache procs"
date: 2009-06-05
forum: Server Platforms
---

### Post by Matthijs on 2009-06-05
Hello there,

I have an question :)

When someone on my server starts an apache process (example mail.php) i want to check that process, Where did that program start? I then use:
```
ls -lsa /proc/$PID
```
where $PID is the running apache proc (it can be found with an 'ps auxf' command). 

When i run that ls command, it shows me the directory (cwd) of the apache process. let say /home/website/public_html/ . In that directory there are a bunch off files, including mail.php. But is still don't know what program is/was running!

With the mod_status module from apache, you can get an webpage that show all running procs WITH pid! the program apachetop does a similar thing. 

Is there a way to find the running process of an apache PID ?

lets say i want to find:
apachepid 23114 -> /home/website/public_html/mail.php
apachepid 2331 ->/home/website/public_html/joomla/c99_shell.php (hack attempt)

I really hope there is. Thank you in advance.

---

