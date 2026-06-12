---
title: "Crontab + paths"
date: 2009-12-15
forum: Server Platforms
---

### Post by chrislynch8 on 2009-12-15
Hi,

We have a complex custom FreeBasic script that we use to check that our Comms are up. We are checking the PPPoE, VPN, etc. and restarting/reapairing anything that is found to be down.

We are passing variables the to .bin file from a .sh file and this is run via the CRONTAB for the root user.

We have seen that one occasions we are getting issues with the PATH. Sometimes when trying to start OpenVPN from the script via CRON we get errors in Openvpn.log saying 
```
sh: ifconfig: command not found
``` 
We know the command is there as the script is calling ifconfig to check the tun0 interface etc. 

For all our commands in the script i.e. ifconfig, ifup, ifdown, ping, grep and so on we are defining the PATH to the commands. But when we are calling **/etc/init.d/openvpn start** we find that the PATH it uses if wrong.

In the root CRONTAB file we have defined the PATH thinking this would solve the issue, so far we haven't had the issue again. we want to make sure it never happens again, so we are changing the script to test the PATH at the beginning of its run but if it finds an issue **how do we resolve it**. Is it possible to edit the PATH during the run of the script, or stop the script to edit the PATH and run again....

Rgds
Chris

---

### Post by car1 on 2009-12-15
At any time in the script you can edit the $PATH variable, and if you use export to export this variable it's value will be available in any new processes you invoke from that point on:

"export PATH=$PATH:/usr/whatever/bin:/usr/local/whatever/bin"

---

### Post by chrislynch8 on 2009-12-17
Hi,

We have added the PATHs to the CRONTAB and we include a check at the start of the Script to check that the PATH includes /usr/mjk. Running under CRON this is find and running from the terminal this is fine as the /usr/mjk is included in the /etc/crontab /etc/environment /etc/logins.defs 

But when we run it via Midnight Commander the PATH /usr/mjk is not used. MidNight Commander seems to be taking it PATH Variable from somewhere else. 

Where is it getting the PATH from because I would like include our own /usr/mjk path - this where we keep all our custom scripts and programs.

Rgds
Chris

---

