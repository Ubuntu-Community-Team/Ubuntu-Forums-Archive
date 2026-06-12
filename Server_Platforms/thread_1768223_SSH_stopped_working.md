---
title: "SSH stopped working"
date: 2011-05-26
forum: Server Platforms
---

### Post by Comrie19 on 2011-05-26
I am running a headless home file server with ssh, samba, webmin and webgui for Transmission.
It was all working fine on my lan until I tried to set ssh to listen on a different port (I read it was safer to do so if you wanted access from the internet). Now I cannot ssh into my server and as far I can tell using webmin the ssh process is no longer running and I cannot restart it. I have restored my unmodified sshd_config file.

I hope someone can help.

After restoring my original config file and rebooting I am back and working.

---

### Post by lykwydchykyn on 2011-05-26
Using webmin, try to restart ssh (I know you said it wouldn't work).

Then go to webmin's log viewer (under system=>system logs) and take a look at the /var/log/daemon.log or /var/log/syslog files to see if there are any errors tagged sshd.

---

### Post by Comrie19 on 2011-05-26
There was an error: 
Server init: ssh respawning too fast, stopped

But as I said, reverting to the original config file and a reboot got me back up and running.

Thanks for the quick response though.

---

