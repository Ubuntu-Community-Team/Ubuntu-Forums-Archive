---
title: "First time scripting, running script as root on startup."
date: 2010-07-29
forum: Server Platforms
---

### Post by jesuscamp on 2010-07-29
I am trying to run my script at startup but it doesn't run the script as root. 

Do I need to add my root username and password in the script, or somewhere else?

Thanks, let me know if you need more info I get back asap.

---

### Post by Groodles on 2010-07-30
couple of methods of doing this.

You could add your script to the /etc/init.d/ and then enable it with update-rc.d

or

You could add it to root's crontab with the @reboot directive.



Either method will run the script with root's credentials.

---

